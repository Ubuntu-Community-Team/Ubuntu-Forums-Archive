---
title: "fonts disappeared"
date: 2007-06-05
forum: Desktop Environments
---

### Post by fishyf on 2007-06-05
Hi,
my fonts disappeared from most of my apps. Firefox and the terminal still work, but the menus and many other apps just have no writing. I can't even tell what time it is!

I'm running feisty and was modifying the fonts when I accidently started another fonts preferences window (one was already open). This window had no visible fonts. When I killed it, my preferences fonts had disappeared. Being from the Windows world, I thought a reboot would fix it, but that just meant that all other fonts disappeared.

Since I have a terminal, I should be able to fix this. Anyone know what the commands are?

I was running compiz desktop effects and turned them off (well I assume I turned them off, I couldn't see any writing on the dialog box). But I don't think compiz should affect fonts anyway.

Otherwise, I'm running the latest version of feisty on a dell latitude.

More details: I had just installed Tahoma (following these instructions [http://wiki.zhekov.net/tahomadapper](http://wiki.zhekov.net/tahomadapper)) and selected tahoma for applications and was checking it out with. Admiring the results I decided to modify the other fonts from Verdana to Tahoma when I started the second fonts preferences dialog box with the aforementioned consequences.

Thanks for any help

---

### Post by fishyf on 2007-06-05
Fixed.

I tried the gconfeditor, but since you can't see any fonts, I couldn't see any writing and therefore I couln't change any settings.

But the command
gconftool-2 --type string --set /desktop/gnome/interface/font_name "Serif 12"
fixed it. Very ugly, but now I assume I can use the normal menu items to fix things.

---

