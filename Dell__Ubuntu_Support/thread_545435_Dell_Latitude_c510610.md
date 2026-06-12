---
title: "Dell Latitude c510/610"
date: 2007-09-07
forum: Dell  Ubuntu Support
---

### Post by Hells.Tears on 2007-09-07
I'm running Xubuntu and xfce

I've been trying for ages and don't seem to be working...

I have these FN keys which change the keycodes of other selected keys.

I have these 2 keys 176 and 174 and I'm wanting them to increase(176) and decrease(174) volumes.

I have xbindkeys and xmodmap to help me but still aint working...

Could anyone post a stepped guide to use these propperly.

---

### Post by Afishionado on 2007-09-07
Until someone more helpful comes along, here's an article Google picked up:

[http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html](http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html)

---

### Post by neptho on 2007-09-07
Here's the setup for the whole set of keys to make them X11 friendly for xmodmap:

```
%cat ~/.xmodmaprc
keycode 160 = XF86AudioMute
keycode 174 = XF86AudioLowerVolume
keycode 176 = XF86AudioRaiseVolume
keycode 162 = XF86AudioPlay
keycode 164 = XF86AudioStop
keycode 144 = XF86AudioPrev
keycode 153 = XF86AudioNext
keycode 168 = XF86AudioMedia
```

Here's a sample xbindkeys configuration (Note the keycodes above, matching below).  This has the advantage of directly tying the key to an application instead of setting hotkeys on another level (although I think it's possible to do this natively with XFCE):
```
%cat ~/.xbindkeysrc
"amarok -t"
  m:0x0 + c:162
  XF86AudioPlay
"amarok -s"
  m:0x0 + c:164
  XF86AudioStop
"amarok -r"
  m:0x0 + c:144
  XF86AudioPrev
"amarok -f"
  m:0x0 + c:153
  XF86AudioNext
"amixer sset Master 1+"
  m:0x0 +  c:176
  XF86AudioRaiseVolume
"amixer sset Master 1-"
  m:0x0 +  c:174
  XF86AudioLowerVolume
"amixer sset Master toggle"
  m:0x0 + c:160
  XF86AudioMute
```

You can start xmodmap automatically; but if you want custom applications, xbindkeys is a much easier tool to use.  There's more information on how to setup keys  [on the Gentoo wiki](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys), which translates pretty easily to Ubuntu/Debian.

For XFCE 4 there is no utility to add to startup, but XFCE 4 uses a startup directory: 
```
%mkdir ~/Desktop/Autostart
%sudo apt-get install xbindkeys
%ln -s /usr/bin/xbindkeys ~/Desktop/Autostart/xbindkeys
```

(Edit: I used xbindkeys when I ran GNOME, because I had some issues with different applications wanting to forever steal the keys for their own nefarious purposes.  I now use xmodmap, started automatically with my KDE login; I have the applications setup to use the XF86 keys, and all works fine... I just wish I could bind global keys for multiple applications (play for Amarok ~ play for Codeine...)

---

### Post by BLTicklemonster on 2007-11-25
I've got the same laptop (probably modified? it has a 1.2 gig cpu and 512 megs ram) and am running gutsy on it. Everything pretty much runs great, except I don't have the take a screenshot function when I press prnt scrn, and of course, with an ati card, the extra desktop effects don't work at all.

Other than that, it's a great laptop, and is running fine.

---

