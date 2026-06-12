---
title: "Steam Font Issue"
date: 2009-07-14
forum: Gaming &amp; Leisure
---

### Post by Buuntu on 2009-07-14
I recently installed steam through wine.  Everything works fine except some fonts are really hard to read.  It seems to only be a couple things in the main screen and in my friends list but it's very hard to read those.  I installed tahoma.ttf as well as all the microsoft fonts to my wine directory but it didn't solve the problem.  Any ideas?

---

### Post by PureLoneWolf on 2009-07-15
Hi there

Searching around shows that you need to get tahoma.ttf, marlett.ttf and Lucida Console fonts into your ~/.wine/drive_c/windows/fonts directory.

If you already installed msttcorefonts, you can copy them over directly, if you have a dual boot (or virtualbox) installation, you can copy them over directly.

Personally, as space isn't a real issue to me, I just copied over all of my MS fonts from my Virtualbox XP installation to the wine folder as I wasn't totally sure which ones were needed.

Hope that helps

---

### Post by Buuntu on 2009-07-15
Ok, I installed all of the fonts from the WINDOWS folder into my wine folder but that didn't fix it.  I looked in the fonts folder and I can't seem to find the Lucidia Console fonts you mention.  Can I install those using the terminal?

---

### Post by PureLoneWolf on 2009-07-15
That's strange then, when I copied all of my windows fonts to the /home/USERNAME/.wine/drive_c/windows/fonts and restarted Steam, everything was perfect.

Worst case, reboot in case Wine is leaving something open.

Beyond that I don't know, sorry I can't be more help...like I said, that worked for me.

*EDIT*
Just noticed..the folder name is Fonts not fonts (capital F)... maybe this made a difference if you used a command line to copy?

---

### Post by Buuntu on 2009-07-15
Oh ok, I had copied them over to ~/.wine/drive_c/Fonts on accident instead of windows/Fonts.  That fixed it, thanks a ton man.

---

### Post by kostkon on 2009-07-15
> **Buuntu said:**
> Ok, I installed all of the fonts from the WINDOWS folder into my wine folder but that didn't fix it.  I looked in the fonts folder and I can't seem to find the Lucidia Console fonts you mention.  Can I install those using the terminal?
For *Lucida* fonts check [this blog post]("http://ubuntu-unleashed.com/2008/05/howto-install-mac-fonts-on-ubuntu.html").

---

