---
title: "Installing Splash Screen"
date: 2007-02-06
forum: Desktop Environments
---

### Post by CarlosinFL on 2007-02-06
I am wondering if anyone knows how to install this .tar.gz splash image from gnome-look.org

[http://gnome-look.org/content/show.php?content=50468](http://gnome-look.org/content/show.php?content=50468)

I can un-tar the file but have no idea how to install this.

Anyone?

---

### Post by gavintlgold on 2007-02-06
This link was on the website:

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

It seems to be the directions...

---

### Post by p!=f on 2007-02-06
There's README inside the archive with the installation procedure. I followed it and it works perfectly. :)

---

### Post by CarlosinFL on 2007-02-07
I have been attempting this on my Debian box and so far get the following error...

```
cwilliams@slave:~$  sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-fingerprint.so). Nothing to configure.

```

Also it (Source Forge Instructions) never specifies if you "uncomment" the VGA line in the /boot/grub/menu.lst file. I added the =791 but by default it is commented out. Do I uncomment that?

---

### Post by dckirba on 2007-02-09
I've had problems with this usplash. I followed the instructions in the readme but I just get a blank screen and then straight to login window.

I did edit menu.lst to change the resolution.

Cheers,
David K

---

### Post by Lukich on 2007-02-12
Hey, David.  I have exactly the same problem.  Did you figure it out at the end?

---

### Post by dckirba on 2007-02-13
No luck so far! Actually it kinda goofed up my sound and I had to spend some time getting that back. I think I'll try it at home on my computer there and see how it goes. Followed the instructions to the dot though :(

Cheers,
David K

---

### Post by dzul1983 on 2007-02-13
I followed the instructions, and I do get the fingerprint background.. but the bit on the left side is a bit messed up.. there's just a big black square box where it should say, Press Alt+F1 for Verbose and all that lot.. maybe I should try reinstalling it.. anyone know how to remove it?

I noticed that when you run the update-initramfs -u thing, the kernel version doesn't match the one I'm using.. so I used dpkg-reconfigure linux-image-$(uname -r) instead..

---

### Post by whayong on 2007-02-13
> **dzul1983 said:**
> anyone know how to remove it?


Also interested in info on this.

---

### Post by dzul1983 on 2007-02-13
this seem to work..

update-alternatives --config usplash-artwork.so

choose the stock splash screen and run

dpkg-reconfigure linux-image-$(uname -r)

to update initramfs..

as for the screen resolution.. you're supposed to add vga=791 to the end of the kernel option for the kernel version you're using.. works for me.. hope it works for you guys too..

---

### Post by ramjet_1953 on 2007-02-13
Install [COLOR="Red"]gnome-splashscreen-manager[/COLOR] from the repositories, using Synaptic.

It has a GUI interface and makes things MUCH easier.

Regards,
Roger :cool:

---

