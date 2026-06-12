---
title: "Dapper Desktop: Amarok &amp; Fonts"
date: 2006-06-10
forum: Desktop Environments
---

### Post by Shonkin57 on 2006-06-10
Dapper's default gnome desktop works great. Really. And I'm very pleased w/ how it recognized my Compaq Presario 2545US laptop's hardware, even the physical volume controls (Winduhs Ex-P) doesn't do that). Unlike SuSE 10.1, Ubuntu 6.06 also kept the wireless driver for the rt2500 chip cards (such as my pcmcia Hawking). All good!

But the problems: Amarok and KDE fonts (unrelated to one another)

* Amarok (no I didn't upgrade this time out--this is my second install of Ubuntu Dapper and I didn't have good luck w/ Amarok 1.4 upgrade). But Amarok 1.3 will not play (same for 1.4) my windows partition's iTunes music files, which are mostly stored in mp3 format. It acts like it is playing them, but instead rushes through the entire stack (about 1 second a piece) and reports it finished playing them all. Sigh. I'll go back to the tried and true XMMS if I must, but Amarok looked so promising.

* Font difficulties. I may have contributed to this one by installing at one point the Enlightenment desktop and then installing and running additional KDE apps on the KDE desktop (keeping, however, gnome's gdm Xwin manager as the default rather than kdm). When I reloaded the first time, KDE came up with Enlightenment running inside of it! I elected to remove Enlightenment and all files I could find related to it (all this through the Synaptic package manager rather than manually). I then reloaded KDE and it was okay, except that all the fonts seem very small -- I increased their size on my 15 inch LCD to as much as 18 pt on some fonts. And in the kde term program, the fonts (both menu and actuall application) are teeny tiny, like 6 pt or something. I have no idea how to fix them.

Okay, that's the ugly. Other than that, I'm very happy with Dapper and send out kudos to all and sundry involved.

Thanks,
Shonkin57
--
Born again Democrat who can't wait to see my allegedly born-again misleader leave the White House.

---

### Post by Shonkin57 on 2006-06-12
An update: Amarok now works, thanks to the posts of others that helped me resolve the problem. I also was able to update to Amarok 1.4 w/ no problems.

Fonts issues remain, but are not serious.

Thanks,
Shonkin57
--
Born again Democrat who can't wait to see my allegedly born-again misleader leave the White House.[/QUOTE]

---

### Post by shuttleworthwannabe on 2006-06-12
Install kcontrol (sudo aptitude install kcontrol), and launch kcontrol from the run an application by entering a command (or in Terminal). A KDE control center will open and then set the fonts there under appearances>fonts.

I have created a panel shortcut for kcontrol
HTH

---

### Post by Shonkin57 on 2006-06-13
Hmm. Interesting. I've been going through KDE's Actions menu via the "Settings > Appearance and Themes > Fonts" program. I tried what you said, and the program Kcontrol is installed and did run. But after I set fonts there and exited it returned a "no term on 0:0" or close to it message to me. Odd. I can't even log into gnome, however, only kde. So I do have problems here, most likely of my own making. Sigh.

---

### Post by shuttleworthwannabe on 2006-06-13
Strange..hmmm...it worked for me. I prefer the aptitude approach, because it allows you to remove, if you need to, all the packages related to kcontrol at the time of installing.
 
It looks like you may have installed the whole KDE desktop with this and over-ridden GNOME?? I am not sure. Did not happen to me though.
 
Oh, what error do you get in terminal when you launch kcontrol?
 
If you can login KDE, try installing ubuntu-desktop again.

---

