---
title: "Stargate Atlantis Usplash"
date: 2009-01-11
forum: General Help
---

### Post by Lukasz Tarkowski on 2009-01-11
This is my first Splashy theme!

```
sudo apt-get build-dep splashy libsplashy1

then

sudo apt-get install splashy

gksudo gedit /boot/grub/menu.lst

find and add vga=794 to both

# defoptions=quiet splash vga=794

/boot/vmlinuz-2.6.24-23-generic root=UUID=299998d9-7106-4c42-9b97-069aa444436a ro quiet splash vga=794

then  update-initramfs -u

```

```
This will remove Usplash,  you will need to reinstall usplash if you wan't to use Usplash,  
then do sudo apt-get remove splashy and then sudo apt-get install Usplash.  then sudo update-initramfs -u
```
**Do not Extract**

Sorry if it is in the wrong section

---

### Post by dkev on 2009-01-11
Nice picture! Wheres the progress bar?

---

### Post by Lukasz Tarkowski on 2009-01-11
If you download the theme, then you will be able to see it :D
I know I could use a digital camera to take it. hmm
I will try to make a better preview soon!

---

### Post by Lukasz Tarkowski on 2009-01-12
_I have updated it the picture :D_
Just look at the top of this topic!
But here the same one

---

### Post by binbash on 2009-01-12
WOW wow, very good picture.I hope the progress bar stuff is also cool.i am gonna give it a try

---

### Post by Lukasz Tarkowski on 2009-01-18
This is My first grub theme!
It is based on Stargate Atlantis Tv show!
I have included a preview and a zipped theme.
> Don't forget to extract the theme
You will need startup manager
```
Sudo apt-get install startupmanager
```

```
gksudo gedit /boot/grub/menu.lst

find and add vga=794 to both

# defoptions=quiet splash vga=794

/boot/vmlinuz-2.6.24-23-generic root=UUID=299998d9-7106-4c42-9b97-069aa444436a ro quiet splash vga=794

then  update-initramfs -u
```

---

### Post by blackened on 2009-01-18
Sad to see the show end. Your theme looks nice though.

---

### Post by overdrank on 2009-01-18
I do love the show :)

---

### Post by Lukasz Tarkowski on 2009-01-18
Don't forget to extract hehe :P
Thank You All

---

### Post by Lukasz Tarkowski on 2009-01-21
My laptop doesn't like virtual box so no more progress bar pictures :(
Its a to bigger of a problem to take my pictures with my digicam

---

### Post by davidself1001 on 2009-01-23
I can't get the grub or the gnome screens to work.  I get nothing but misaligned screensize if I try any grub screen and I get a black screen when I try the gnome screen.  In fact, I have not been able to get any gnome screen to work except the default and the fingerxxx one (the one with the hand showing fingerprints).  I noticed that the .so file for the ones that work have a different icon in the /usr/lib/usplash folder after being added with start-up-mgr.  The ones that work the icon looks like a text file icon but the ones that don't (even though they both have a .so extention) work have and icon like an executable file.  What am i missing?

---

### Post by davidself1001 on 2009-01-23
Any ideas on why some .so files work for usplash (and have different icons to represent the file) and some don't?

---

### Post by Lukasz Tarkowski on 2009-01-24
Sorry I am new to this.  

```
sudo apt-get install startupmanager!
```

---

### Post by Lukasz Tarkowski on 2009-02-04
I have updated The Stargate Altantis Splash screen,  I have moved to Splashy themes now :D

Opps there is a grub theme here I will make a quick fix :D

---

### Post by randyklein99 on 2009-07-12
This gave me a good idea that I have no idea how to implement.  I would like to see the progress bar be the icons on the gate lighting up, as it dials earth or so.

---

