---
title: "compiling seamonkey error"
date: 2006-02-11
forum: Desktop Environments
---

### Post by ram32 on 2006-02-11
hi!
when i compile seamonkey, i got this error:

nsFontMetricsXft.cpp:(.text+0x5422): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0x547a): undefined reference to `XftDrawGlyphFontSpec'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::DrawString(unsigned short const*, unsigned int, int, int, int, int const*, nsRenderingContextGTK*, nsDrawingSurfaceGTK*)':
nsFontMetricsXft.cpp:(.text+0x58a2): undefined reference to `XftGlyphExtents'
nsFontMetricsXft.cpp:(.text+0x58fa): undefined reference to `XftDrawGlyphFontSpec'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::CacheFontMetrics()':
nsFontMetricsXft.cpp:(.text+0x5b4a): undefined reference to `XftLockFace'
nsFontMetricsXft.cpp:(.text+0x5f70): undefined reference to `XftUnlockFace'
nsFontMetricsXft.cpp:(.text+0x6016): undefined reference to `XftTextExtents16'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::~nsFontMetricsXft()':
nsFontMetricsXft.cpp:(.text+0x63e3): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::~nsFontMetricsXft()':
nsFontMetricsXft.cpp:(.text+0x6633): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsFontMetricsXft.o): In function `nsFontMetricsXft::~nsFontMetricsXft()':
nsFontMetricsXft.cpp:(.text+0x6883): undefined reference to `XftFontClose'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::~nsDrawingSurfaceGTK()':
nsDrawingSurfaceGTK.cpp:(.text+0x46): undefined reference to `XftDrawDestroy'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::GetXftDraw()':
nsDrawingSurfaceGTK.cpp:(.text+0x43e): undefined reference to `XftDrawCreate'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::~nsDrawingSurfaceGTK()':
nsDrawingSurfaceGTK.cpp:(.text+0x7d6): undefined reference to `XftDrawDestroy'
../../dist/lib/components/libgfx_gtk.a(nsDrawingSurfaceGTK.o): In function `nsDrawingSurfaceGTK::~nsDrawingSurfaceGTK()':
nsDrawingSurfaceGTK.cpp:(.text+0x836): undefined reference to `XftDrawDestroy'
collect2: ld returned 1 exit status
make[3]: *** [seamonkey-bin] Error 1
make[3]: Leaving directory `/home/ram32/src/mozilla/obj-i686-pc-linux-gnu/xpfe/bootstrap'
make[2]: *** [tier_99] Error 2
make[2]: Leaving directory `/home/ram32/src/mozilla/obj-i686-pc-linux-gnu'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/ram32/src/mozilla/obj-i686-pc-linux-gnu'
make: *** [build] Error 2

my .mozconfig:
# Options for client.mk.
mk_add_options MOZ_CO_PROJECT=suite
mk_add_options MOZ_CVS_FLAGS=-tz9
mk_add_options MOZ_OBJDIR=@TOPSRCDIR@/obj-@CONFIG_GUESS@

# Options for 'configure' (same as command-line options).
ac_add_options --enable-default-toolkit=gtk2
ac_add_options --enable-application=suite
ac_add_options --enable-extensions=default
ac_add_options --disable-freetype2
ac_add_options --enable-xft
ac_add_options --enable-update-channel=default
ac_add_options --disable-tests
ac_add_options --disable-debug
ac_add_options --enable-optimize="-O3 -march=pentium3 -funroll-loops -ffast-math -fomit-frame-pointer -mfpmath=sse,387 -msse -mmmx"
ac_add_options --enable-single-profile
ac_add_options --disable-logging
ac_add_options --enable-static
ac_add_options --disable-shared


help me, please!

---

