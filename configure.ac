AC_INIT([mate-doc-utils], [1.6.2], [https://github.com/mate-desktop/mate-doc-utils])
AM_INIT_AUTOMAKE([1.9 no-dist-gzip dist-xz])

AC_CONFIG_MACRO_DIR([m4])

dnl ----------------------------------------------------------------------------
dnl  In the interest of portability, we do not use GNU awk extensions,
dnl  even though they rule.  To prevent accidental use and subsequent
dnl  bug reports after busted tarballs were shipped, we use -W compat
dnl  whenever our awk is gawk.
dnl ----------------------------------------------------------------------------
AC_PROG_AWK
if test x$AWK = xgawk; then
   GDU_AWK='gawk -W compat';
else
   GDU_AWK=$AWK;
fi
AC_SUBST(GDU_AWK)

AC_PROG_LN_S

gdu_cv_have_gdu=yes
MATE_DOC_DEFINES

AC_ARG_ENABLE([build-utils],
	AC_HELP_STRING([--enable-build-utils],
	[build and install the build utilities [default=yes]]),
	,
	enable_build_utils=yes)
AM_CONDITIONAL(ENABLE_BUILD_UTILS, test x$enable_build_utils = xyes)

if test x$enable_build_utils = xyes; then
AM_PATH_PYTHON([2.4])
fi

PKG_CHECK_MODULES(MATE_DOC_UTILS, [
	libxml-2.0 >= 2.6.12
	libxslt    >= 1.1.8
	rarian
])

GETTEXT_PACKAGE=mate-doc-utils
AC_SUBST(GETTEXT_PACKAGE)
AC_DEFINE_UNQUOTED(GETTEXT_PACKAGE, "$GETTEXT_PACKAGE")

IT_PROG_INTLTOOL([0.35.0])
AX_GLIB_GNU_GETTEXT

AC_CONFIG_FILES([
	Makefile
	data/Makefile
	data/icons/Makefile
	data/icons/hicolor/Makefile
	data/icons/hicolor/48x48/Makefile
	data/icons/hicolor/48x48/status/Makefile
	data/icons/hicolor/scalable/Makefile
	data/icons/hicolor/scalable/status/Makefile
	data/templates/Makefile
	data/watermarks/Makefile
	doc/Makefile
	doc/mate-doc-make/Makefile
	doc/xslt/Makefile
	po/Makefile.in
	rng/Makefile
	rng/mallard/Makefile
	tools/Makefile
	tools/mate-doc-utils.pc
	xslt/Makefile
	xml2po/Makefile
	xml2po/xml2po.pc
	xml2po/xml2po/Makefile
	xml2po/xml2po/modes/Makefile
	xml2po/examples/Makefile
	xslt/common/Makefile
	xslt/docbook/Makefile
	xslt/docbook/common/Makefile
	xslt/docbook/html/Makefile
	xslt/docbook/omf/Makefile
	xslt/docbook/utils/Makefile
	xslt/mallard/Makefile
	xslt/mallard/cache/Makefile
	xslt/mallard/common/Makefile
	xslt/mallard/html/Makefile
	xslt/gettext/Makefile
])

AC_CONFIG_FILES([tools/mate-doc-tool], [chmod +x tools/mate-doc-tool])
AC_CONFIG_FILES([tools/mate-doc-prepare], [chmod +x tools/mate-doc-prepare])

AC_OUTPUT
