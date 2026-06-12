---
title: "Not Getting GNOME GUI"
date: 2005-04-30
forum: Desktop Environments
---

### Post by edlsoft on 2005-04-30
I ran the ubuntu Live CD. Great! 
Then installed ubuntu to my hard drive using the Install CD. 
GRUB loader works fine.
When I booted from hard drive, got to the login prompt.
I typed in my user ID and password and wound up at my home directory.

Something wrong. How do I get to the GNOME GUI?

---

### Post by tread on 2005-04-30
type startx after you login?

---

### Post by gunnyman on 2005-04-30
to make gnome start automatically, from the command prompt,
sudo dpkg-reconfigure gdm

---

### Post by edlsoft on 2005-04-30
[QUOTE=tread]type startx after you login?[/QUOTE]

Thanks for reply--Tried that already.

---

### Post by edlsoft on 2005-04-30
[QUOTE=gunnyman]to make gnome start automatically, from the command prompt,
sudo dpkg-reconfigure gdm[/QUOTE]

Thanks. I got the message :  Package 'gdm' is not installed

A more basic problem is that the system didn't allow me to set up my root password.

How do I do this?

---

### Post by Nob on 2005-04-30
the best thing is to get ubuntu instalation cdrom... and install it from there, not from live cd :)
u set root password when you enter root terminal in gnome, and there u change passwd ;) 
but u have to get gnome working :( 
i suggest reinstall

---

### Post by neighborlee on 2005-04-30
[QUOTE=Nob]the best thing is to get ubuntu instalation cdrom... and install it from there, not from live cd :)
u set root password when you enter root terminal in gnome, and there u change passwd ;) 
but u have to get gnome working :( 
i suggest reinstall[/QUOTE]
-------------
he said he used 'install cd' which I presume means not the liveCD for which I presume still there is no option to install to HD...

btw is this a goal ?


cheers
neighborlee

---

### Post by Nob on 2005-04-30
sorry, i missed that line... ;)

still - reinstall

---

### Post by derrick1985 on 2005-05-01
1. It doesn't ask you for a root password. When you set up your user account, it use's that for a root password (since you are the one installing Ubuntu, why wouldn't you be root?)

2. Did you type 'server' at the install prompt, or just press enter? If you typed server, it does just a base install, no gui's at all.

---

### Post by edlsoft on 2005-05-01
[QUOTE=Nob]the best thing is to get ubuntu instalation cdrom... and install it from there, not from live cd :)
u set root password when you enter root terminal in gnome, and there u change passwd ;) 
but u have to get gnome working :( 
i suggest reinstall[/QUOTE]

Yes, that did the trick. Ran t he Install CD again and this time selected, I think,
the default option and it reinstalled flawlessly, and got the GNOME GUI.
Also found the root terminal (am still learning ubuntu). The CD player ran
right out of the box whereas on another distro I spent hours and hours
trying to get sound to work. ubuntu is terrific.

Thanks to all who replied.

---

