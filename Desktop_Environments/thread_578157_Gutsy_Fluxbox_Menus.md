---
title: "Gutsy Fluxbox Menus"
date: 2007-10-16
forum: Desktop Environments
---

### Post by nlvivar on 2007-10-16
I used Fluxbox on my old computer in Feisty, but I have upgraded to the Gutsy RC. How the update-menus command throws my applications into many different parts of the Fluxbox menu.

For example I now have a menu heading called "Applications" that wasn't there before, and the old "Apps" is still there. So now I hunt for applications in two places.

I don't really want to edit the menu by hand or manually. The update-menus command never worked exactly how I wanted it, but it was close enough in Feisty. It now works horribly in Gutsy. Worst case in point: in Gutsy, my Firefox command is now missing.

Any help in understanding how to get update-menus to behave would be appreciated. -Noel

---

### Post by TeaSwigger on 2007-10-16
Honestly don't know; going to wait a bit before jumping into gutsy. But if it's somehow of any help, I found my fluxbox auto generated menu here: /etc/X11/fluxbox/fluxbox-menu.

What happens if you remove (move, not delete just to be safe) the above auto generated menu? Perhaps you could quickly determine what else is being used. Any insights in the Fluxbox menu thread?
[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

---

### Post by nlvivar on 2007-10-17
I did see that post, but I thought that it was a bit too involved. Not much time right now, nor do I think that it may even be worth it.

I've just been booting up in XFCE now, until I figure out what I want to do. In Gutsy, XFCE feels a little faster than in Feisty, so my old computer is able to hack it.

I'll try your suggestion at some point, and I'll let you know. Hopefully, I can do the same for my OpenBox menus too.

As for holding off on Gutsy, I can understand. I just decided to take the plunge.

---

### Post by mojoman on 2007-10-17
I've experienced something related. I run Feisty and got my own menu which includes the Debian menu. Everything was nice and orderly sorted under apps. Then I installed Deluge from a .deb. After I did update-menus the Debian menu my old had  apps-<all application stuff> but it also had a new entry, applications, which contained network-deluge.

I also use Debian Lenny and I also installed Deluge on this partition. On THAT Debian menu there is no entry called apps, only an entry called applications and it got all my applications under the usual sub-entries. 

So, my take on this is that we're seeing different versions of the Debian menu, and when you got applications compiled for a different menu than the one you're using the system simply mixes them.

It's not the end of the world as I only use the Debian menu for those applications that I don't use a lot but had I used it more it would have freaked me out totally.

/mojoman

---

### Post by nlvivar on 2007-10-17
That's funny. I experienced the same exact thing in Feisty also. I think that I went into Deluge's .desktop file and fixed something, and that solved the problem, if you're interested.

As for my desktop in Gutsy, in the past few days, I've slowly watched as application after application has migrated for "Apps" to "Applications." I'm sure that it's the same problem with the .deskop files, but I don't want to go in by hand and edit approximately half of all my applicatons.

---

### Post by mojoman on 2007-10-18
I had a look at deluge's .desktop and it looks like this:
```

[Desktop Entry]
Version=1.0
Name=Deluge BitTorrent Client
Comment=Bittorrent client written in PyGTK
Exec=deluge
Icon=deluge-torrent
Terminal=false
Type=Application
Categories=Network
StartupNotify=true
MimeType=application/x-bittorrent;

```
Aha, I thought, Application and Network seem to correspond to Applications and Network in the Debian menu (even though the 's' in 'applications' was missing in the .desktop file). Now, just to be sure I had a look at an application from the 'apps' part of the menu as well and gaim had, among other, the following entry:
```

Type=Application
Categories=Network;InstantMessaging;
```
Now, that lead me to conclude that these are not the entries that decide where on the Debian menu an application will show up. If it were, they would obviously differ as their location on the menu differ. Any ideas on this? I don't mind doing the editing by hand as it only this one application.

/mojoman

---

### Post by nlvivar on 2007-10-18
Well, Deluge was the only on in the "Applications" menu when I was using Feisty, but now that I've upgraded to Gutsy, about 1/2 of all my progjrams have moved out of "Apps."

I'm not sure if this has anything to do with it, but it looks like the applications that have stayed in "Apps" have "GNOME;GTK;" in their Categories. Those without it, are spread out now in "Applications" and "Games" and other menus.

I guess what I'm saying is, if you're planning on moving to Gutsy at any point, I wouldn't bother hand editing the .desktop files. I would just hand edit your fluxbox menu.

---

### Post by nlvivar on 2007-10-18
I haven't read through them all, but these will probably help us.

[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/update-menus.1.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man1/update-menus.1.gz)
[http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/menufile.5.gz](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/menufile.5.gz)
[http://bardolph.ling.ohio-state.edu/cgi-bin/dwww/usr/share/doc/menu/html/?type=file](http://bardolph.ling.ohio-state.edu/cgi-bin/dwww/usr/share/doc/menu/html/?type=file)

---

### Post by mojoman on 2007-10-18
> **nlvivar said:**
> Well, Deluge was the only on in the "Applications" menu when I was using Feisty, but now that I've upgraded to Gutsy, about 1/2 of all my progjrams have moved out of "Apps."

I'm not sure if this has anything to do with it, but it looks like the applications that have stayed in "Apps" have "GNOME;GTK;" in their Categories. Those without it, are spread out now in "Applications" and "Games" and other menus.

I guess what I'm saying is, if you're planning on moving to Gutsy at any point, I wouldn't bother hand editing the .desktop files. I would just hand edit your fluxbox menu.

I'll probably hold of the migration to Gutsy for a while so that's not an issue. However, editing the fluxbox menu can't be the answer to this issue because it's the Debian menu, which appears as a submenu to the fluxbox menu, that needs changing. So, the question is, how do you get the Debian menu to sort this application the way it sorts other applications. 

ps: When it comes to menu, Lenny uses version 2.1.36, Feisty uses 2.1.32 and Gutsy uses 2.1.34. ds

---

### Post by RedSquirrel on 2007-10-22
I have added a new section to my howto with instructions for making an acceptable menu for Fluxbox on gutsy. It involves using fluxbox-generate_menu and the Debian menu together.

This doesn't address the unusual behavior of the Debian menu on gutsy, but it does at least allow you to create a reasonable menu without too much fuss.

[http://ubuntuforums.org/showthread.php?t=371144](http://ubuntuforums.org/showthread.php?t=371144)

---

