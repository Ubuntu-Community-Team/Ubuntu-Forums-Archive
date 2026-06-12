---
title: "Just Received Mini 9  Error Installing 8.10"
date: 2008-11-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by zenarcher on 2008-11-26
I just received two new Dell Mini 9's about an hour ago.  I have increased the RAM from 1GB to 2GB in both and would like to do a standard install of Ubuntu 8.10.

I made a USB Live CD, using the 'Create a USB Startup Disk" on my main computer, from my regular install disk.  It seems that should work.

Starting the Mini 9 with the USB drive in place, I reach the point where I can choose to try the Live CD or do an Install.  When I choose to do the install, the process continues, allowing me to choose a language.  I pick English and the install proceeds to where I see the standard Ubuntu wallpaper, then a black screen and mouse pointer...does it a couple more times, then I get an error box.

Likewise, none of the repositories for the Dell Ubuntu 8.04 work, either.  I get a 404 error on all of them.  So, at the moment, I cannot upgrade to 8.10, nor even update 8.04.  I really need the regular Ubuntu 8.10, so I can use my 2GB of RAM.

Any help appreciated!

The error says "The Configuration Defaults for GNOME Power Manager have not been installed correctly.  Contact your system administrator."

Does anyone have an idea what I'm doing wrong here?  I really would like to install the standard Ubuntu 8.10, so it will be the same on my netbook as on my desktop.

Thanks,
zenarcher

---

### Post by zenarcher on 2008-11-27
Okay, then, so I'm guessing that everyone else who has received a new Mini 9, then did a fresh install of Ubuntu 8.10, from a jump drive, has not received any error like this in doing so.  No response from anyone on the Dell forum, either.  So, what am I doing wrong?  What does GNOME Power Manager have to do with anything, when you are trying to do an fresh install?  The current installed Ubuntu isn't even running yet?

Cheers,
zenarcher

---

### Post by armandh on 2008-11-27
I would start with a new down load and CD.
then I would use a partition disk such as G-parted to wipe the old one then try a new load of 8.10.

I have not tried it yet as I put 8.10 on a usb HDD for testing but I did try the dell reload and it did work.

audio in 8.10 takes one line of code added in terminal with gedit
[http://ubuntuforums.org/showthread.php?t=981602](http://ubuntuforums.org/showthread.php?t=981602)
remember to save B4 rebooting
.

---

### Post by zenarcher on 2008-11-27
Call me stupid, I guess.  Apparently, I had a bad download or burn, although everything checked okay.  I had not used the 32 bit disk I had made before, but only the 64 bit ones.  

I downloaded the 32 bit 8.10 again and burned a new disk, then a new USB start disk and it's installing now, just fine, it seems.

Thanks for the help.

Cheers,
zenarcher

---

### Post by Ric_ on 2008-11-27
Zenarcher: do you have  the hsdpa modem in the mini 9? and does it work in ubuntu?

Ric

---

### Post by zenarcher on 2008-11-27
I don't think so. I'm not sure! *LOL*  I have wireless and ethernet, but that's all I'm sure of right now.  I don't see HSDPA on my list of options I selected.

My install finally worked fine with 8.10.  I have no sound right now, so have to figure that one out.

Cheers,
zenarcher

---

### Post by armandh on 2008-11-27
see my note above in post 3 about sound

---

### Post by zenarcher on 2008-11-28
I did see your note on sound and thanks much for that.  It's working perfectly now!

Cheers,
zenarcher

---

### Post by armandh on 2008-11-28
you are welcome and please spread the word to others with the same issues

---

### Post by zenarcher on 2008-11-28
I sure will.  It saved me a lot of effort, as I got two of the Mini 9's.  My wife wanted one to use at work, so I ended up getting two of them.  She's not particularly interested in the technical end, but loves gadgets, so it's my job to keep them running the way she wants, so two was an obvious choice. 

Cheers,
zenarcher

---

### Post by THE TECH on 2008-12-03
So was I incorrect in downloading 8.10 directly onto my Mini and thinking I would be able to install it?

---

### Post by ArKay on 2008-12-04
> **THE TECH said:**
> So was I incorrect in downloading 8.10 directly onto my Mini and thinking I would be able to install it?

Sadly, yes.
You either need to turn the .iso into CD or DVD and use an external player, or make a bootable USB drive (like a flash drive, USB key, etc.) and then boot from that and install from there.

An SD card/Memory stick in the card reader will not work as it cannot be booted from.

When you power up use the boot device option to choose what you want to install from, boot from that device and away you go.

---

