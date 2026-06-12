---
title: "OOPS!  Moved my boot loader!"
date: 2008-12-05
forum: General Help
---

### Post by coachnate on 2008-12-05
Ok, sorry if this has already been helped before.  I searched through the forums and found an article from Feb that was along my lines - but was in the archive.  

Problem: I decided I wanted to install Ubuntu on an external hard drive, but was unaware that it would move the boot loader in the process.  Now I can't boot anything without the external plugged in (makes sense, but not what I want).  Any idea how to move the boot sector back to the correct spot (on my internal hard drive)?

I greatly appreciate any help - thanks in advance.

---

### Post by utsuprainfra on 2008-12-05
reinstall your bootloader to the main hard disc, and make sure that in the bios it tries to load the hard disc before removable media?  Not sure about the removable media and what the external drive is considered as, but you understand?

---

### Post by coachnate on 2008-12-05
Sorry - I'm a total newby to Ubuntu.  I've recently graduated with a CIS degree, and I think I should invest some learning in *nix stuff.  I've seen a little bit of Ubuntu and it looks really interesting, so any help (as mentioned before) is very appreciated - I would love to join this world! :)

Moral of the story, unfortunately 'reinstalling the bootloader' isn't fully clear to me.  Please clarify, or redirect to an article if one's available.

---

### Post by caljohnsmith on 2008-12-05
If I were in your shoes, first I would install Grub to the MBR (Master Boot Record) of your external drive, and you can also restore a Windows MBR to your internal drive if you want to. Then all you have to do is change your BIOS to boot the external Ubuntu drive when you want to boot Ubuntu. If you have Windows on your internal drive, you can even add an entry in your Grub's menu.lst to boot Windows from the Grub menu. If that sounds good to you, then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands. Then to restore a Windows MBR to your internal drive:
```
sudo lilo -M  /dev/sda mbr
```
Then reboot, set your BIOS to boot the Ubuntu drive, and you should at least get the Grub menu on start up. Let me know if you get that far or if you run into problems. :)

---

### Post by MarblePanther on 2008-12-05
This comes in handy ;)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by coachnate on 2008-12-30
Sorry for the long delay - didn't mean to post and run, but got busy with the holidays.  I appreciate the help, all.  I'll try some of this and let everyone know how it went.

Thanks!

---

