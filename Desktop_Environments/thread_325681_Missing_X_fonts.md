---
title: "Missing X fonts"
date: 2006-12-26
forum: Desktop Environments
---

### Post by Levander on 2006-12-26
I started up emacs today, and instead of the really big ugly font I usually get - I got this this really small font instead.  Asking around, surprsing changes in emacs' font is usually due to there being a problem with the fonts specified in your X configuration.  This stuff happened right after I ran nvidia-xconfig to install hardware acceleration on my machine.

Here is the output from "grep -i font Xorg.0.log":

```

(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/X11/fonts/misc,
        /usr/share/X11/fonts/100dpi/:unscaled,
        /usr/share/X11/fonts/75dpi/:unscaled,
        /usr/share/X11/fonts/Type1,
        /usr/share/X11/fonts/100dpi,
        /usr/share/X11/fonts/75dpi,
        /usr/share/fonts/X11/misc,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/TTF/,
        /usr/share/fonts/X11/OTF,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/CID/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/
        X.Org Font Renderer : 0.5
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) Initializing built-in extension XFree86-Bigfont
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
FreeType: couldn't open face /usr/share/X11/fonts/Type1/a010013l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019043l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022004l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n022004l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019004l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019004l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019023l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019023l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019003l.pfb: 1
FreeType: couldn't open face /usr/share/X11/fonts/Type1/n019003l.pfb: 1

```

And, here's the only section of my xorg.conf file that seems to specify where the fonts go:

```

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

```

The TTF, OTF, and CDI subdirectories of /usr/share/fonts/X11/ that I am getting errors saying they are not found Xorg.0.log don't exist on my system.  But, as you can see, they are not referred to in my Xorg.conf file either.  

Really don't know anything about how fonts work for X11, so I'm looking for some tips as to how to get started.

Hopefully, there's some good simple documentation available to read?

---

