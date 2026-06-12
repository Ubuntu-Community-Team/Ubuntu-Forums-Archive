---
title: "desktop effects Messed up after a crash"
date: 2007-09-28
forum: Desktop Effects &amp; Customization
---

### Post by K-a-M-u-Z-u on 2007-09-28
I'm using ubuntu feisty on a IBM Thinkpad R40.
i had a problem with the fan on the laptop and it stoped working while i wasn't home.when i came back the computer was hang(I guess its related to the heat...)
i had to turn the laptop off, i fixed the fan by myself, and then i'v turned up the laptop.
ubuntu was working, but the compiz effects didnt worked.
i have tryed typing in the terminal "compiz --replace" but it didnt worked.
so i thought maybe to reinstall compiz
i did
sudo apt-get remove compiz
and then:
sudo apt-get install compiz
then
compiz --replace
NOTHING
so ithought abount installing Compiz-Fusion.
that's where the problems started...
i used [this]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") guide.
after i installed the video driver(ATI) i rebooted, and XORG failed to restart.so i'v Copied the BACKUP Xorg.conf and rebooted.
ubuntu came up ok, but something was wrong...
its looked all messed up:
1.Each windows i have opend was snaped to the top-left corner of the window without the title bar, so no moving the windows, no resizing them,no minimizing...no control at all.
2.I can't do COPY PASTE.
3.I can't swith between windows.

when i put the command:
compiz --replace
i get this error:
> fatal:failed test:texture_from_pixmap support
checks indicate that it's impossible to start compiz on your system.
i tried changing the window manager but it didnt helped.
does anyone has a clue how to fix compiz?(i guees i will have to go back with the display driver or something like that...)
Damm...i cannot use linux like that so i'm on XP...baaaa....it sucks! :( pls help... :(

---

### Post by polygone on 2007-09-28
I am an idiot.  I tried.  My suggestion would have been to check and see if XGL is running, but you weren't using it to begin with.  I have to use it with the fglrx drivers.

---

### Post by K-a-M-u-Z-u on 2007-10-01
mm...up?
i tried to install the 7.10 beta hopfully the new packages will fix the problem...but no change... :(

---

### Post by K-a-M-u-Z-u on 2007-10-03
:(
I am starting to get used to windows...i'm afraid i will get too used to it.... :confused:
NO ONE HAS ANY SUGGGESTION?

---

