---
title: "password problem"
date: 2006-02-17
forum: Desktop Environments
---

### Post by christine on 2006-02-17
I just installed ubuntu on a friends computer and it asks for the user name and password and Im 100% sure of the name and password but now its saying its wrong. Ive tried every combination and even upper/lower case but nothing helps .How can I reset the password without having to reinstall.? E-mail @teklas41@yahoo.com if you can help with this please.:confused:

---

### Post by schilcha on 2006-02-17
I know of two ways how to come around this:
1) boot into rescue mode (select a line with "rescue" from the grub menu appearing just after the bios-messages -- you might have to press ESC when indicated to make the menu appear). 
    Enter the root-pwd, which is most likely just nothing. 
    Enter the command "passwd username", where username is the name of the user you want to change the password for. 
    Reboot.

If that doesn't work, try approach 2:
2) Boot from live-cd
    Mount the root-partition of the installed system (e.g. sudo mount /dev/hda1 /mnt)
    cd /mnt
    chroot .
    passwd username
    exit
    umount /mnt
    reboot

Good Luck!

---

### Post by IwilBubuntu on 2006-02-17
I have a similar problem with a computer.  Bios reports 1st boot cdrom, 2nd boot hard disk.  While rebooting and pressibg the esc key at the proper time, the option times out without activating.  I tried to boot with the live cd, which hangs the computer (unresponsive), forcing me to shut down manually.  I suspected a keyboard problem but after switching with a known good keyboard, the same results.  Any other suggestions?

---

### Post by IwilBubuntu on 2006-02-17
Success!!  By accident, the username and password got me in!  Don't ask me how, why, or whatever, but the presence of capitals in the user name may have been the cause.  I repeatedly typed in the same username and password several times, and after shutting off the computer manually and through the logoff/shutdown, it just worked!  Yes, YES :) :)  So if it dosen't work try try again.

---

