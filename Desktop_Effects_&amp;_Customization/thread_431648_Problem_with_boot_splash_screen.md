---
title: "Problem with boot splash screen"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by look2 on 2007-05-03
Hi ! 

I did try to install another boot splash screen, but it didn't work out as I hoped. 
I tried to install "Fingerprint" from [www.gnome-look.org](www.gnome-look.org). I followed the attached readme file. But When I booted the pc again it didnät work. I was only getting text, saying what the PC was doing. like: 
"loading files needed for boot" 

I started to mess around a bit, and all I get now is some kind of strange "test splash" It likes like the ones you sometimes kan see on TV when there is no program. Like a test for the monitor. 

Anyone know what I might have done wrong and how I can fix it ?

---

### Post by rolf-c on 2007-05-03
I've used Fingerprint in the past.  Are these the steps you followed?

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765?](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765?)

```
Prerequisites

1 - In order to install this theme, you should have Usplash well configured and installed. If you don't please try

    sudo apt-get install usplash

or in debian systems

    su
    apt-get install usplash

2- You also need a booting screen resolution of 1024x768. To set it, please open your grub configuration file

    sudo gedit /boot/grub/menu.lst

find the paragraph about your current kernel version, and add the string

    vga=791

at the end of the kernel section, without modifying pre-existing values.

For example if this is your current configuration

    title Debian GNU/Linux, kernel 2.6.17-10-generic
    root (hd0,4)
    kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=en_EN
    initrd /boot/initrd.img-2.6.17-10-generic
    boot

you should add the string to this line

    kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=en_EN

which will become

    kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda5 ro quiet splash locale=en_EN vga=791


Installation

Now that everything is well set, we'll install the new theme. Fisrt of all copy the file contained in this directory, named 'usplash-theme-fingerprint.so' insto your Desktop. Now open a terminal and digit

    cd
    cd Desktop
    sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
    sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
    sudo update-alternatives --config usplash-artwork.so

And choose the righ value (write the number displayed near the file called 'usplash-theme-fingerprint.so' then press Return to confirm)

Now update your system booting process by digiting in terminal

    sudo update-initramfs -u
```

---

### Post by look2 on 2007-05-03
Yes, that was the steps...

---

### Post by rolf-c on 2007-05-03
That should work.  One gotcha in there  is this:

```
root (hd0,4)
```

You need to replace 0,4 with whatever is correct for your system.  hd0,1 is fairly common.  For me, it's hd0,5.

---

### Post by rolf-c on 2007-05-03
Also this other thread is a good guide:

[http://ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash](http://ubuntuforums.org/showthread.php?t=30341&highlight=grub+splash)

---

### Post by look2 on 2007-05-03
Just added vga=791 to that line, never changed anything else so the entry there shuld be ok.... 

The link you posted is for editing the picture in grub? I want the change the picture when the system is starting up...
any other suggestions ?

---

