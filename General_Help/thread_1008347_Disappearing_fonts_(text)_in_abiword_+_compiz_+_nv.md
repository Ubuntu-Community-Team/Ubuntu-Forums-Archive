---
title: "Disappearing fonts (text) in abiword + compiz + nvidia"
date: 2008-12-11
forum: General Help
---

### Post by Ivo Moelans on 2008-12-11
I installed abiword from the repositories on my system (Ubuntu Intrepid; Nvidia GeForce4 MX 4000; Nvidia driver 96.43.09). When I open a document, or try to create one, the fonts are not showing. They are there, but are not rendered. Clicking repeatedly on the document window shows them flickering.
This is with compiz working. When I disable compiz the fonts are rendered as they should. I already tried disabling individual effects, but that doesn't seem to help.
The disk analyzing program xdiskusage has the same problem.

Any thoughts?

---

### Post by gettinoriginal on 2008-12-11
There seems to be a bug (already reported to abiword), but aside from that, have you tried to change the color of the font to see if that makes a difference ??

You may also try this to see if it helps:

System -> Preference -> Appearance -> Fonts, then select subpixel smoothing (LCDs) then clicked details and selected Hinting: Full.

---

### Post by Ivo Moelans on 2008-12-11
Yes, I tried both and it doesn't seem to help. 
I don't think it is a bug in abiword because xdiskusage has exactly the same problem. I also can't make the rain effect in compiz work. I'm beginning to suspect that it is a problem with the nvidia driver for my (legacy) card or with the card itself.
Nevertheless, thank you for your reply.

---

### Post by Bo Rosén on 2009-02-08
I have an Nvidia Geforce MX 440, proprietary driver and had Metacity Compositing manager enabled and have the same problem. The text is invisible, though flickers occasionally.
When I disabled the compositing manager everything was fine.

Interestingly, with the compositing manager enabled, Open Office 2.4 doesn't render fonts for its menus! So, no File, Edit etc ;-)

---

### Post by lvlo on 2009-02-08
There are new beta legacy drivers from NVIDIA. Take a look: [http://www.nvnews.net/vbulletin/showthread.php?t=126954](http://www.nvnews.net/vbulletin/showthread.php?t=126954)

---

### Post by Bo Rosén on 2009-02-09
Thanks. Good to know it's been fixed. I can live without compositing so will probably wait.

---

### Post by nortexoid on 2009-05-01
For nvidia folks, this seems to have been fixed, as documented in the bug report [https://bugs.launchpad.net/bugs/301816](https://bugs.launchpad.net/bugs/301816).

In the compiz setting manager, select workarounds and check "Force Synchornization between X and GLX".

---

