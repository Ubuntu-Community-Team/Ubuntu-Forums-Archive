---
title: "iriver T10 ogg/mp3 player... blah."
date: 2005-12-26
forum: General Help
---

### Post by lasermike026 on 2005-12-26
I just got an iriver T10 as a gift.  It doesn't seem to work for linux because of some proprietary driver/protocol/thingy.... blah.  But I'll put it to the forums, has anyone got an iriver T10 working in linux and/or ubuntu breezy?

Thanks in advance,
Mike

---

### Post by brainkilla on 2005-12-26
[http://www.misticriver.net/showthread.php?t=32822](http://www.misticriver.net/showthread.php?t=32822)

---

### Post by sciurus on 2005-12-26
EDIT: Oops, you said T10, not H10.

The problem is that to be compatible with Microsoft's DRM, iRiver switched its players from UMS to MTP mode and made Windows Media Player 10 responsible for building the player's media database. This means that when you connect the player to a computer you will see it as a drive and be able to copy songs to it, but they won't show up on the player's menus. There is a command-line program for Linux and OS X that can update the media database, but MTP prevents the program from accessing the database.

Luckily there is a workaround:
1. Use a small device (paper clip) to press the reset button
2. Connect the player to the PC with the USB cable
3. Click and hold the Select key of the H10 ("o" button) and then the Power button until the "Emergency Connect..." message appears and then disappears on the H10's LCD screen. Keep pushing the button while "Emergency Connect..." messages appears on the screen.
4. Now the player will work in UMS mode.
5) Copy your songs, then run [http://easyh10.sourceforge.net/manual_cui.html#id4481065](http://easyh10.sourceforge.net/manual_cui.html#id4481065)

I'd take it back or sell it and get a Archos Gmini 202 or 402. They can be switched from MTP to UMS mode in their preferences. Also, a used Iriver H320/H340 would work with Linux and has killer features.

---

### Post by lasermike026 on 2005-12-26
Will the H10 workaround work for the T10?

Thanks in advance.

---

### Post by xtacocorex on 2006-03-12
This is a website with firmware what will take your MTP iRiver T10 and convert it to a UMS device.

[http://www.mtp-ums.net/index.php](http://www.mtp-ums.net/index.php)

I just did this tonight with my T10 and it works.

---

