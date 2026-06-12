---
title: "help!I can't use keyboard in natty on Dell XPS 15z"
date: 2011-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wsubt on 2011-08-12
help....

---

### Post by ~!geek!~ on 2011-08-12
Although not able to help a lot. But if you are able to use the keyboard for a few moments, you should try ctrl+alt+f1 or ctrl+alt+f2 to get to one of the tty console available. It the keyboard works in this mode, your problem is gdm or other graphics related. You may try creating new test user from here after logging in using > sudo adduser <newusername>. Now try to boot and try logging in using new user if you can. If it fails again go to one of the consoles and try reinstalling graphics i.e. gdm etc. search internet for appropriate packages and disable graphics driver. 

you may also try to boot in recovery mode. 

If none of above work for you, use live usb (or cd) to confirm if its a hardware problem (altho not expecting this.)

---

### Post by wsubt on 2011-08-12
> **~!geek!~ said:**
> Although not able to help a lot. But if you are able to use the keyboard for a few moments, you should try ctrl+alt+f1 or ctrl+alt+f2 to get to one of the tty console available. It the keyboard works in this mode, your problem is gdm or other graphics related. You may try creating new test user from here after logging in using . Now try to boot and try logging in using new user if you can. If it fails again go to one of the consoles and try reinstalling graphics i.e. gdm etc. search internet for appropriate packages and disable graphics driver. 

you may also try to boot in recovery mode. 

If none of above work for you, use live usb (or cd) to confirm if its a hardware problem (altho not expecting this.)

I can use keyboard when I run natty as live USB. but when I install it, keyboard cannot be used any more.

---

### Post by wsubt on 2011-08-12
> **wsubt said:**
> I can use keyboard when I run natty as live USB. but when I install it, keyboard cannot be used any more.

I can use keyboard in ubuntu 10.04.X. but this version doesn't support wireless and some other hardware.

---

### Post by ferrangil on 2011-09-23
Same problem here. On a general thread about XPS 15z, an user says to edit a file with pico, but... the keyboard is not working! How we are supposed to be able to type that?? From windows+nodepad? Hahaha!
[http://ubuntuforums.org/showpost.php?p=11163517&postcount=91](http://ubuntuforums.org/showpost.php?p=11163517&postcount=91)


Also, another users says we need to boot with acpi=noirq, but where I can set up that? On grub? I just clicked letter 'e' while on grub and I see some paramethers for the ubuntu boot, but...
[http://ubuntuforums.org/showpost.php?p=10971111&postcount=38](http://ubuntuforums.org/showpost.php?p=10971111&postcount=38)

Share your progress!

EDIT: I just added  acpi=noirq at the end of the line that started as "linux /boot..." or something similar and then keyboard worked!
Now trying to figure out where in the new grub I should add this to make the change permanent (otherwise on next reboot keyboard won't work again).

---

