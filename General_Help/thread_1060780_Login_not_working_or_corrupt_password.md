---
title: "Login not working or corrupt password"
date: 2009-02-05
forum: General Help
---

### Post by Uig on 2009-02-05
I have a problem logging in to Ubuntu. The computer starts and fires up Ubuntu then asks for login name and password in the normal way only when I type them in they get rejected. I have rebooted the machine and tried many times and am certain that I haven't got any silly problems like caps lock etc going on.

Can anyone help or do I just have to reinstall since non of my login names or passwords are working. It was all working fine yesterday and the day before that. No new software has been loaded for ages and no system settings have been knowingly changed.

---

### Post by geirha on 2009-02-05
Does your password contain non-ascii characters? And do they work in the login-screen. Try typing some of the special characters in the username box, and see if the correct symbols show.

Also, are you able to log in at the console? Hit Ctrl+Alt+F1 at the login screen and type your username and password.

---

### Post by Uig on 2009-02-05
Thanks for you ideas, I have tried logging in after hitting Ctrl+Alt+F1 and Ctrl+Alt+F2 but no joy and have also tried that with two different usb keyboards. The problem computer is a dell laptop with inbuilt key board I just thought that trying an external might work. With all the keyboards including the built in one, special characters print fine. My password is alphanumeric.

Any other thourghts?

---

### Post by geirha on 2009-02-05
Hm. Boot into recovery mode to get a root shell, then create a new user 
```

adduser *username*
# Give it sudo privileges while you're at it:
adduser *username* admin

```
Reboot and see if you can login with that new user.

---

### Post by Uig on 2009-02-05
I can get a root shell up but I get asked for the root password which doesn't work and am not alowed to add a new user.

---

### Post by geirha on 2009-02-05
Hm. I guess you'll need to do it from the live-cd then. Boot the ubuntu CD, mount the linux-partition by right-clicking it in nautilus (the file browser) and selecting mount.

If it's the first partition you mount, it will be mounted to /media/disk, chroot into that:
```
sudo chroot /media/disk
```

Then try adding a user as before.

---

### Post by JackVrouwes on 2010-04-20
> **geirha said:**
> Hm. I guess you'll need to do it from the live-cd then. Boot the ubuntu CD, mount the linux-partition by right-clicking it in nautilus (the file browser) and selecting mount.

If it's the first partition you mount, it will be mounted to /media/disk, chroot into that:
```
sudo chroot /media/disk
```

Then try adding a user as before.
I have the same problem as Uig. I am using Karmic AMD64 on an Asus motherboard.  An error message advising to turn on ECC in the BIOS came on the first time the problem appeared out of the blue.  I then set ECC to "Basic."

I followed the suggestions by geirha, and entered the commands after the root@ubuntu:/# prompts.  After regular shutdown and reboot the same "authentication failed" appeared on booting after I entered the password.  This happened also after trying both the original and new users, and after completing new "passwd username" commands.

Is there a bug in Karmic that somehow corrupts/disables passwords?  Or is the place where passwords are stored somehow corrupted?  Please help!

---

