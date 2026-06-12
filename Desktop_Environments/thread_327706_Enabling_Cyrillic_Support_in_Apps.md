---
title: "Enabling Cyrillic Support in Apps"
date: 2006-12-29
forum: Desktop Environments
---

### Post by elcasey on 2006-12-29
I've got a few questions about enabling Cyrillic support in both GNOME and applications, specifically Russian.

How can I change my keyboard layout from US English to Russian "on the fly?" In OSX, for example, there is a flag in the menubar. I click on it, select "Russian" and go about my business in Russian. I don't know how to enable this in GNOME, but I'd very much like to. Note, however, that I do not want my entire WM in Russian! I'm not a native speaker and I'm functional rather than fluent (for now).

Second, and this is the big one for me, I'd like to enable Cyrillic support in multimedia apps, specifically Beep and XMMS. I use XMMS more than anything else, but I've noticed that even in Rhythmbox I get a bunch of garbage when it opens files with Russian filenames. Are there that many Russophobic developers, or does something need to be globally enabled?

I've looked at a program called RusXMMS, but I couldn't decipher whether it was a standalone app or a plugin, and either way it never showed up in any menu and XMMS still doesn't support Cyrillic.

I listen to a lot of Russian music, both MP3 and internet radio, and I'm getting kind of tired of looking at nonsense instead of artist and track names.

HELP! Thanks in advance! :mrgreen:

---

### Post by elcasey on 2006-12-29
OK, I've seriously narrowed down one of the problems. I found a [tutorial for Cyrillic XMMS](http://5ko.free.fr/en/xmms.html), but I don't have the "microsoft-cp1251" fonts installed.

I've found several packages for these, all available via apt-get, but there's still problems. The problem with the stock Edgy fonts is that fonts are no longer in [FONT="Courier New"]usr/lib/X11/fonts/misc[/FONT] (for Cyrillics), they are now in [FONT="Courier New"]/etc/X11/fonts/misc[/FONT]. This was changed in my xorg.conf file and all my fonts look  500% better now.

BUT, none of the packages for cp1251, even the ones supposedly for Edgy, install to the correct directory! Every package I try to install gets to "setting up fonts" and then I get the following message:
[FONT="Courier New"]warning: /usr/lib/X11/fonts/75dpi does not exist or is not a directory[/FONT] (or /misc, or whatever)

I even tried a "sudo mkdir /etc/X11/fonts/misc" for the first package to no avail. No reason it would work with "/75dpi" on the second package.

So...how do install the microsoft-cp1251 font package into the **correct** directory now?! ](*,) ](*,)

---

