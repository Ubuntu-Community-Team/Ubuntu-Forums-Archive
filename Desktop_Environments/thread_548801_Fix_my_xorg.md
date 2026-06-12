---
title: "Fix my xorg"
date: 2007-09-11
forum: Desktop Environments
---

### Post by mrcold on 2007-09-11
I have messed up my xorg configuration, and am currently running from the live CD.  I know how to "sudo dpkg-reconfigure..." if i can get to a command line, but this time after i get the standard X-server error screen, it dumps me into just a blank screen where i can type, but i can't make any commands.  Perhaps if i knew the right command to "log-in" to my account, i could fix it, but as of right now i don't know how to do that.  Is there a way to get to it from the liveCD?

I apologize if this is confusing, i am somewhat new to all of this...

---

### Post by odiseo77 on 2007-09-11
Hi, have you tried booting in single user mode, and then executing 'dpkg-reconfigure xserver-xorg' ? ...Anyway, if you want to do it from the live cd, you can chroot your ubuntu installation and run the previous command (though I'd suggest you to do the first method).

Regards.

---

### Post by mrcold on 2007-09-11
i do not know how to boot into single user mode.. could you elaborate on this perhaps?
I can fix the problem if i can just get into the xorg configuration process.

Thanks for the quick reply

---

### Post by odiseo77 on 2007-09-11
To boot into single user mode, simply reboot your system, then you'll see the grub menu (you know, the menu where you can choose between several OS's and/or kernels to boot). You'll see two entries for your current kernel; the second one must say something like 'safe mode' or 'single user mode', something like that (don't remember now), choose this one, et voilà, at the end of the boot process you'll have a command line where you can type the command to reconfigure your X server :)

---

### Post by mrcold on 2007-09-11
That doesn't really sound familiar to me, BUT, like i said i am new to this.  I am going to go try that now.  Thanks.

---

