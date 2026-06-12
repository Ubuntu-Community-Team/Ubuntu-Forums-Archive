---
title: "XFCE - small fonts"
date: 2005-10-14
forum: Desktop Environments
---

### Post by lol on 2005-10-14
hi,

After an upgrade, somes fonts in XFCE became really small, and I don't recall modifying any settings. The problem appears for the gnome-terminal font and the font of the XFCE interface, like the menu, window titles, etc. (and maybe others that I haven't noticed yet).

What I don't understand is:

1 - I tried to change the font in the XFCE "User Interface" settings. That's better for some stuff, but the font of the menu hasn't changed (same for the terminal).

2 - I don't have any problem if I log in a Gnome session, even with the gnome-terminal (with the same profil).

Any idea?
thx.

---

### Post by Miguel on 2005-10-19
I would try to specify a resolution (dpi) in my xorg.conf. I don't know exactly the variables,  but it is something like displaywith  and displayheight.

However, I wouldn't bet on it. The command to check your screen dpi resolution is

xdpyinfo | grep resolution

I remember there was some info on how to change it on a thread that contained this command. I don't think many threads contain the word "xdpyinfo", so searching for it could help. 

Sorry for not being more explicit now.

---

### Post by blueninja on 2007-03-28
Hi,

I had the same issue when I added xubuntu-desktop to my gnome-based feisty:  the menu, window title, taskbar text button label, and desktop icon label fonts became too small to be readable, all others are normal.

After perusing through the xfce tag, I found x1a4's suggestion and it solved my small fonts issue.  He suggested to reset xfce's configuration:

To reset Xfce configuration remove the ~/.config/ directory

mv ~/.config ~/.config.bkp

and restart Xfce.

You will of course have to reconfigure the fonts and sizes to your liking afterwards.

Cheers!

---

### Post by Copter on 2007-04-12
Hi!

Same problem on my Xubuntu 6.10 box. After checking some 'User Interface' templates all my XFCE fonts were messed up. I have fixed some of it by changing them back to normal but still all my QT based apps have font sizes like 8 or so. They look the same ugly in Kate, Skype, Kile and many more.

I will try that config remove / modify trick.

copter :]

---

### Post by fwojciec on 2007-04-12
Edit /home/*username*/.config/xfce4/Xft.xrdb
Add "Xft.dpi: 96" to the end of the file - that assumes that your DPI is set to 96 in Gnome/KDE, the idea is to make the DPI setting consistent in all desktop environments.
Restart XFCE (don't save the session - just in case XFCE overwrites this setting - or just edit the file while in Gnome session).

That should fix it.

---

### Post by theadventuresofanidealist on 2007-04-21
fwojciec.....you the man!

---

### Post by Rumpanzle on 2007-05-17
Thanks a lot from me, too!

---

### Post by ZuLuuuuuu on 2007-11-19
Hi, I installed Xubuntu 7.10 and have the same problem. But there is no Xft.xrdb file (I enabled show hidden files). How can I change my dpi setting to 96 permanently on Xubuntu 7.10?

("echo "Xft.dpi: 96" | xrdb -merge" command worked so it is definately dpi problem but this solution is not permanent)

---

### Post by Tampler on 2008-01-13
> **ZuLuuuuuu said:**
> Hi, I installed Xubuntu 7.10 and have the same problem. But there is no Xft.xrdb file (I enabled show hidden files). How can I change my dpi setting to 96 permanently on Xubuntu 7.10?

("echo "Xft.dpi: 96" | xrdb -merge" command worked so it is definately dpi problem but this solution is not permanent)

You can create the file Xft.xrdb in /home/yourhomefolder/.config/Xft.xrdb with the following line:

Xft.dpi: 96

After that just open /etc/X11/xorg.conf and add the following lines in Section "Files":

FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
FontPath "/usr/share/X11/fonts/100dpi"

It's work for me.

---

