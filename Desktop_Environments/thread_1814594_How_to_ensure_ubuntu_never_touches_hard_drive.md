---
title: "How to ensure ubuntu never touches hard drive"
date: 2011-07-29
forum: Desktop Environments
---

### Post by dlvonde on 2011-07-29
Hello All,
 
I just created a bootable USB drive with Ubuntu 11.04 32-bit with 1gb persistent space. My intentions for this installation is just to install/configure Skype and use it periodically on my laptop when I am out of town to talk to the family.  I am using it by inserting the usb drive in my laptop then pushing a function key to invoke a  boot menu during bootup.  I pick the usb drive and boot from it so it doesn't touch the mbr of the hard drive installed in the laptop.
 
My concern is I need to keep ubuntu (or myself!) from making any changes to the existing hard drive in the laptop when running ubuntu. Some of the things I'd like to do are:
 
1 - Remove the "install to hard drive" option from the bootloader
2 - Tell ubuntu to stop adding the "install to hard drive" icon on the desktop. I keep deleting it and it keeps coming back. My other changes of course are staying so I know the update is working.
3 - Keep my hard drive from mounting automatically. This should take care of the rest of my issues, right?
 
I'm not afraid of monkeying around with configuration files and I vaguely remember having to make such modifications in a unix classs back in college :). I was just wondering if there is a simpler way. Ubuntu has come a long way! It's really slick!
 
I realize the drive could be mounted again and etc. etc. but I'll be the only one using it so I'd have to be intent on changing the hdd in that case.

---

### Post by dlvonde on 2011-07-29
so I intended to install ubuntu to the usb drive but it's acting like I just have a "live" version on usb that keeps pushing the actual install.  

What I really want is to have the usb drive bootable and boot straight into an actual installed ubuntu where everything is on the usb drive..but I don't really want a "live" version plus an installed version on the usb key..do I need to use 2 usb keys or burn the iso to a cd/dvd then install to the usb?

---

### Post by jerrrys on 2011-07-29
maybe this is what your looking for

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Megaptera on 2011-07-30
Ubuntu Privacy Remix may also interest you:

[https://www.privacy-cd.org/en](https://www.privacy-cd.org/en)

Can also run from USB [https://www.privacy-cd.org/en/tutorials/upr-on-usb-drive](https://www.privacy-cd.org/en/tutorials/upr-on-usb-drive)

Or "Lightweight Portable Security" (LPS) creates a secure end node from trusted media on almost any Intel-based computer (PC or Mac). LPS boots a thin Linux operating system from a CD or USB flash stick without mounting a local hard drive. Administrator privileges are not required; nothing is installed. 

More info [http://www.spi.dod.mil/lipose.htm](http://www.spi.dod.mil/lipose.htm)

---

### Post by dlvonde on 2011-08-02
thanks everyone..I decided I'll just leave it as is.  I'm really only going to be booting into it for Skype and that works beautifully so I'm happy with that.
 
thanks

---

### Post by Megaptera on 2011-08-02
You're welcome, and as they say "If it ain't broke, don't try and fix it".

---

### Post by ciscoboy on 2011-08-02
I'm using a live version of ubuntu right now (10.04), and have been using it for a few weeks now. I got my hands on it using a program called unetbootin. It works by downloading a iso of the linux and version that you want(there isn't all the linux versions) through the internet, or using a linux iso downloaded from somewhere else. (This is where high speed is really handy)

 Then, it copies and decompiles the iso on a USB drive with another program, boot loader. If you google unetbootin download, it will bring you to the homepage of the website where you can download it. 

When you will have downloaded the program, there's gonna be a space at the bottom where you can set how much room to reserve for things like downloaded programs. Give yourself as much room as you can, because it's gonna go fast. To give you an example, I set mine at 3 GB and it's tight.

Hope it works for you.

Ciscoboy

P.S.: I can't be completely sure that this setup doesn't completely touch the hard drive, but I do know that all of the programs are downloaded on the USB, not the HDD. However, I do believe that this is what you are looking for.

---

