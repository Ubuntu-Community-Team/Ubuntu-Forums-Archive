---
title: "Fuzzy fonts"
date: 2007-06-01
forum: Desktop Effects &amp; Customization
---

### Post by mystery on 2007-06-01
Hi all,

I use Dapper LTS with Kubuntu as the desktop.

Most times my Kubuntu log-in screen font is fuzzy, and after log in, most fonts are fuzzy in most applications.  Restarting X repeatedly, until sharp fonts appear, will fix it temporarily.  The number of restarts needed varies, and the restart that eventually works takes a second or so longer than those that don't.  If the computer is left on but not used for a while the fuzzy fonts reappear.

Subpixel hinting is on and MS core fonts are installed.  GTK STYLES "Use my KDE style in GTK applications" is checked, and GTK FONTS has "Use another font" checked and is using Bitstream Vera Sans.

Any help would be appreciated.  I note that there has been one other post on this topic from another Ubuntu forum user, but it went unanswered.  A Google search failed to turn up anything that works.

Many thanks.

---

### Post by renzokuken on 2007-06-01
using the correct video driver sorted this for me.

what grafix chipset/card have you got?

---

### Post by mystery on 2007-06-02
Thanks for the quick response.

The video chipset is a SIS 661FX.
The monitor is a BENQ FP71E.

The current settings are:

Monitor "Plug and Play"
Driver "Vesa"

No other combination seems to work.  If I try to select the SIS driver it reverts to vesa.

---

### Post by mystery on 2007-06-04
Thanks renzokuken.  You gave me the right stuff.  The problem was solved by installing a GeForce video card.  Everything's peachy.  Fonts are great.

---

