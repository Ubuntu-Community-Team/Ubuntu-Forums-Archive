---
title: "LXDE - Switch User?"
date: 2010-01-16
forum: Desktop Environments
---

### Post by Telecaster72 on 2010-01-16
Hi, i am using Karmic w/ GDM login manager with LXDE and i am quite happy with it, my gf uses Gnome with her user account. I get no "switch user" option in my logout window in LXDE though and this is somewhat a big problem. Does anyone have a solution to this? Something i could write as a .desktop file or something, something she could easily click to get into her account without interrupting my session. 

Any input would be greatly appreciated!

---

### Post by byStanderone on 2010-01-16
,,,visit this thread: [http://ubuntuforums.org/showthread.php?t=1269788](http://ubuntuforums.org/showthread.php?t=1269788)

---

### Post by Telecaster72 on 2010-01-17
byStanderone - Thanks! that might be it, i'll give it a try!

---

### Post by mkvnmtr on 2010-01-17
I just installed the LXDE desktop on my Gnome 9.04 today and I have a switch user option when I go to log out. I believe I got it out of the regular repositories . I did not enable anything special and I just clicked on IXDE which is a mega package. It did not include the package LXDE desktop.

---

### Post by Telecaster72 on 2010-01-18
byStanderone > Ok so i tried the Gnome-panel with the lxde-logout as done in the post you linked to and that gives me the regular gnome panel but also with lxde-logout which is the exact same one i get in lxpanel. So back to square one ;-) Maybe i did it wrong, a looong day at work behind me, i like the Gnome Panel too though and after changing all default Nautilus to Thunar i might keep it this way.

mkvnmtr > That is very interesting, i did it the same way and did not get switch user. Thanks!

It seems like somehow i have to edit lxde-logout to include Switch User. The script in /usr/bin only says what icon to use and so...
```
#!/bin/sh
lxsession-logout --banner "/usr/share/lxde/images/logout-banner.png" --side=top
```

lxsession-logout looks like this when opened in Leafpad:
```
ELF
``` wtf? how do i view a binary? (I know... i cant skip the basics of Linux;)

the lxde-logout.desktop file in /usr/share/applications says:
```
[Desktop Entry]
Encoding=UTF-8
Name=Shutdown
Name[zh_TW]=&#38364;&#27231;
Comment=Shutdown, Reboot or change session
Icon=stock_exit
Exec=lxde-logout
NoDisplay=true
```
I think i might have added the "change session" earlier

The mystery continues, i know i am missing something elementary here but i'm too tired to do this now, thanks for checking in, i'll post if i come up with something...must.....get...sleeepp...

Edit: I added the "switch user" applet to the panel and that works for now, still would like to have it in the log out thingie where it belongs...

---

### Post by mkvnmtr on 2010-01-18
I can not seem to get a screeenshot of the window but it is a LXDE log out window. I did nothing to get it. In fact I had not even thought of it until I say your post. Wonder where it came from.

---

### Post by oschonrock on 2010-04-16
here is an official response on this subject:

[https://lists.launchpad.net/lubuntu-desktop/msg01142.html](https://lists.launchpad.net/lubuntu-desktop/msg01142.html)

ie need to use gdm instead of lxdm, or wait until lxdm gets this feature.

---

