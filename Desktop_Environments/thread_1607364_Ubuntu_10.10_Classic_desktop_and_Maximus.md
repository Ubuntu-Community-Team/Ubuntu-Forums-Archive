---
title: "Ubuntu 10.10 Classic desktop and Maximus"
date: 2010-10-27
forum: Desktop Environments
---

### Post by ramhanuman on 2010-10-27
I'm running Ubuntu 10.10 Maverick Meerkat Netbook on my Dell Latitude. I'm trying to fix two things. 

1) I want to disable maximus but I went to gconf-editor apps>maximus but there was only one key titled exclude_class, i double clicked it and tried adding Nautilus/nautilus to the list and it didn't work. Does anyone know how to disable the auto-maximization in Ubuntu 10.10?

2) I'm trying to get my files on my desktop to show but when i go to apps>nautlis>preferences>show_desktop it says "this key is not writable". How do I fix this problem?

Thank you.

---

### Post by kerry_s on 2010-10-27
log out, select ubuntu desktop, log in

don't bother installing netbook if you don't want it, just use the normal desktop installer next time.

the new netbook interface is unity, it's done with mutter. there is no maximus installed, mutter does it all.

---

### Post by ramhanuman on 2010-10-27
is there any way to keep the unity interface but disable mutter and show desktop files?

---

### Post by ramhanuman on 2010-10-29
bump

---

### Post by Earl_Maroon on 2010-10-29
From what I heard Unity currently lacks the appropriate window management capabilities to be used non-fullscreen. It is going to need a lot of work if it's to be the default DE in 11.04.

Don't quote me on this though. I haven't rechecked my sources.

---

### Post by kerry_s on 2010-10-29
> **ramhanuman said:**
> is there any way to keep the unity interface but disable mutter and show desktop files?

if you disable mutter, there won't be nothing but a background.

you can tweak the normal desktop to be more netbook friendly, i just showed my friend how to on mine, so he can go home & do it on his. does not require composite, just a few ppa's for the app's.

using dockbarx + window buttons + window title + maximus + cardapio

dockbarx = left menu icons
window buttons = the window buttons
window title = shows the window title
cardapio = menu
maximus = maximises apps

---

### Post by kilaka on 2010-12-01
Thanks a bunch kerry_s.

The steps to install everything and the references are below.

Dockbar:
[http://gnome-look.org/content/show.php/DockbarX?content=101604](http://gnome-look.org/content/show.php/DockbarX?content=101604)
sudo add-apt-repository ppa:dockbar-main/ppa
sudo apt-get update
sudo apt-get install dockbarx
sudo apt-get install dockbarx-themes-extra - don't exactly know what it does

Maximus:
sudo apt-get install maximus

Windows applet:
[http://gnome-look.org/content/show.php?content=103732](http://gnome-look.org/content/show.php?content=103732)
Download at the bottom.

cardapio
[https://launchpad.net/cardapio](https://launchpad.net/cardapio)
sudo add-apt-repository ppa:cardapio-team/unstable
sudo apt-get update
sudo apt-get install cardapio

Install everything and add the applets.
My result is attached.
A great working environment!!!
Thanks to Ubuntu who made such a customizable environment and all the developers who created these wonderful apps.

---

### Post by brunocarv on 2010-12-20
Please help me Ic cant install 
Windows applet
I went to :
[http://gnome-look.org/content/show.php?content=103732](http://gnome-look.org/content/show.php?content=103732)

but there has a 3. estep to install that I cant do:
3) ./configure --prefix=/usr --with-gconf-schema-file-dir=/usr/share/gconf/schemas

What I have to do?? Please!! I hate lose space!

thanks

---

### Post by brunocarv on 2010-12-20
I find the window applets in 
add to panel clicking in the panel

but now I discovered that my problem is with MAXIMUS!!
It isent working... I use a netbook, I want maximus working!!!

Kilaka, just 

sudo apt-get install maximus

is not working

obs: I use Ubuntu 10.10

thanks

---

### Post by kilaka on 2010-12-20
> **brunocarv said:**
> I find the window applets in 
add to panel clicking in the panel

but now I discovered that my problem is with MAXIMUS!!
It isent working... I use a netbook, I want maximus working!!!

Kilaka, just 

sudo apt-get install maximus

is not working

obs: I use Ubuntu 10.10

thanks
This post is for the desktop version.
Perhaps the netbook version uses a different panel?

---

### Post by xcorpion on 2011-01-06
hi
i just step in
i m having a problem with my hp compaq cq41-208au
i was using win7 and then i install ubuntu 10.10 via internet.
after installing ubuntu it asks me for update and i accept it buh after it also ask me smthng grub and didnt notice what it says and just click restart
after i got a screen which says 
error : no such device : bed4e5bc-7d2e-486e-a365-14e5de8d236c
grub rescue>

<Note: i have two partitions sda1 sda2 both are HPFS/NTFS
and my win7 is install in sda1 and ubuntu in sda2 and sda1 is boot*

help me out plz i m f**K freakin out with this prob

---

