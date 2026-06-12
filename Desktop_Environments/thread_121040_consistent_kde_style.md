---
title: "consistent kde style"
date: 2006-01-24
forum: Desktop Environments
---

### Post by kubuntu2k6 on 2006-01-24
Hey! downloaded the iso and installed Kubuntu 5.10 last night and it's really cool! :cool: 

Changed the kde style but it doesn't apply to the Adept Manager (etc?), so wanted to change the kde-style for root. I guess one is not supposed to run kde as root so I tried running kcontrol as root, but that didn't change the style. Not used to be running kde so I don't really know what file(s) to copy to /root to get the consistent look. So how do you do it? Thanks.

---

### Post by kubuntu2k6 on 2006-01-24
Copied the files in the kde config directory over to root and that fixed the style issue.

However it turns out that Adept Manager doesn't integrate well with the kde style 'Keramik' I'm using anyway :p surprise surprise. And I can't find a gtk2 theme to match it. gtk2-engines-geramik is a no go, as is gtk-qt. 

Going to kde-look.org too see if there's a style out there that can make this desktop look good, and going to gnome-look.org to see if there's a gtk2 theme to match it. And then I'm going ice skating in hell :cool:

---

### Post by Jucato on 2006-01-24
[QUOTE=kubuntu2k6]Hey! downloaded the iso and installed Kubuntu 5.10 last night and it's really cool! :cool: 

Changed the kde style but it doesn't apply to the Adept Manager (etc?), so wanted to change the kde-style for root. I guess one is not supposed to run kde as root so I tried running kcontrol as root, but that didn't change the style. Not used to be running kde so I don't really know what file(s) to copy to /root to get the consistent look. So how do you do it? Thanks.[/QUOTE]

Strange, it worked for me. And I didn't need to copy any files. I tried it two ways:
1. kdesu konqueror > settings:/, or
2. kdesu kcontrol

In each case, it applied the changes to the root account's  style. So I have two color styles now, one for the root, and one for my own user. And if I needed to use a style that's not in the root's directory, I just imported (not copied) it from my (user) kde directory.

Good luck finding a GNOME style! Tell me if you found a good one (window decorations, icons, cursors EXCEPT colors). I like KDE, but lately I've been longing for a GNOME look. :)

---

### Post by kubuntu2k6 on 2006-01-24
Yes, that is probably the correct way to do it (don't know why running kcontrol as root didn't work for me).

Actually with QIndustrial/Industrial I did find the kde/gnome style integration I was looking for :) 

[shot1]("http://hem.bredband.net/jonwik/kubuntu.png")
[shot2]("http://hem.bredband.net/jonwik/integr1.png")
[shot3]("http://hem.bredband.net/jonwik/integr2.png")

Well usually I prefer lightweight WM's instead of DE's so don't really know about gnome window decorations, although think it can be just about any WM - the only reason I want a window titlebar is for shading the window instead of iconify it, and window decorations can't get cleaner than a 1px black border. Window operations are most effectively done with keybindings imo.. can't stand to have to move the mouse all over the place just to do simple stuff.

There are some good gnome gtk2-thems (industrial,leech,glossy p,smoothmilk,purple-haze,aero...) and icon-themes (gnant,gargantuan,d3a,glossy-glass,kreski-lines,noia-warm...) floating around though. Oh, and this is THE cursor-theme, I use it for any WM/DE, using it now.. using it tomorrow :cool: 
[http://www.gnome-look.org/content/show.php?content=5533](http://www.gnome-look.org/content/show.php?content=5533)

Just my humble $0.02

---

