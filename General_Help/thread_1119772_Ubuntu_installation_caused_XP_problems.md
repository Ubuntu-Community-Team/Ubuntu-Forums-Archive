---
title: "Ubuntu installation caused XP problems"
date: 2009-04-08
forum: General Help
---

### Post by Gazzy on 2009-04-08
Hi,I recently installed Ubuntu for the first time after not using a Linux system before. After a good start using it I wanted to view my c: drive, couldn't see it from Ubuntu so tried to access a drive called "6.3 GB Media" it said I had to mount so I just clicked ok and thats where the problems came from. First Ubuntu crashed saying something like the window manager wasn't loaded and then wouldn't load on next restart, it said I had to do a manual disk check because the automatic one had failed so I did then it found at least 50 errors to which I clicked yes to fixing it still didn't run after this and can only be run under one of the other options available i.e. Gnome. After these problems I had problems with XP not recognising the network card and it seem's to be because of the Ubuntu installation as I had no such issues before. Ubuntu still recognises the network card fine under Gnome but XP simply won't. I'm really stuck here if anyone has any ideas I'd be greatful thanks.

---

### Post by cariboo on 2009-04-08
Ubuntu doesn't make any changes to your Windows installation. THe only thing I can think of that would cause networking to stop working is if you had to install some firmware to make your network card work in Ubuntu. It should be a simple matter to update your network card drivers in WIndows.

I would suggest you install ntfsprogs to help you deal with your NTFS partition. Ntfsprogs is in the repositories and you can use Add/Remove Programs and SYnaptic Package Manager to install it.

Jim

---

