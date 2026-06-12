---
title: "Desktop not displaying"
date: 2010-07-25
forum: Desktop Environments
---

### Post by DaisukeJigen on 2010-07-25
So I installed Ubuntu a couple months ago.  Everything works fine except my desktop fails to display correctly.  No icons appear, and the background image gets shifted to the right a little bit (and wraps around).  When I shut down my machine, the desktop will appear as it should for the last second before leaving.

---

### Post by howefield on 2010-07-25
> **DaisukeJigen said:**
> So I installed Ubuntu a couple months ago.  Everything works fine except my desktop fails to display correctly.  No icons appear, and the background image gets shifted to the right a little bit (and wraps around).  When I shut down my machine, the desktop will appear as it should for the last second before leaving.

Suppose you have gone through the auto adjustment menu options of your monitor ?

What do you mean by not getting icons, is this in the menus and desktop or only specific icons ?

---

### Post by DaisukeJigen on 2010-07-25
Menus and everything work fine.  By icons I mean anything that would be on the desktop.  The drive icons, a few random folders and files, and a link to Windows Media Player fail to appear.

---

### Post by howefield on 2010-07-25
Check that show_desktop is checked in gconf-editor.

Press the Alt + F2 keys together and type 

```
gconf-editor
```

and press run.

Navigate to apps > nautilus > preferences > show desktop

---

### Post by jerrykenny on 2010-07-25
bump Howefields suggestion to look at your screens resolution first..

Try manually reducing your resolution, and or refresh rate.

---

### Post by DaisukeJigen on 2010-07-25
Dropping to 1280x800 fixed the problem, but then everything is giant.  I'd rather deal with no desktop than have to work in that resolution.  XP has no problems displaying in the higher resolutions.  Oh well, maybe when I can afford to get new hardware.

---

### Post by randywilharm on 2010-07-25
try this in the terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

This will reset everything to the default.

---

### Post by DaisukeJigen on 2010-07-25
> **randywilharm said:**
> try this in the terminal:

sudo dpkg-reconfigure -phigh xserver-xorg

This will reset everything to the default.

 Also didn't help.  A quick google seems to indicate many other have a variety of issues with my video card, but no real fixes. 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

---

### Post by randywilharm on 2010-07-25
If you remove the card from the PC, make sure you remove the driver first.

After that, your onboard video card should work,

and at least the your monitor should work, too.

---

