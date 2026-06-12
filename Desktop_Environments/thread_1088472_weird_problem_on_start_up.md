---
title: "weird problem on start up"
date: 2009-03-06
forum: Desktop Environments
---

### Post by ninja123 on 2009-03-06
Hello all,

On start-up, there comes this screen asking for 

'Enter your password to perform administrative tasks'

Is there anyway of auto-login?? cant i disable this screen??

The weirder thing is however:

After i give password and login, i get a 'welcome' screen with installation of OS.

here is a snapshot: chk attachment.


How do i remove this menu on start-up?

I have this easy peasy running on my system.

Please help

---

### Post by afeasfaerw23231233 on 2009-03-06
Are you running a live cd/usb and didn't install it to the harddrive yet?
If you have already install it to your local drive then I can help with the login issue. 
System > admin > login window > Security> check "enable automatic login"

---

### Post by ninja123 on 2009-03-06
Well i had used a lice usb to install ubuntu but even if i have no device say usb or live cd plugged in, this is always the screen i get on startup and i have to quit before i proceed.

Also regarding the login setting, well i have this enable login automatically checked however, i am always asked password on boot :(

---

### Post by ajgreeny on 2009-03-06
It sounds as if you have somehow managed to end up with a hard disk install which acts like a live CD, which is something I have never come across before.  Certainly the attachment picture is precisely the screen you get using the live CD, so if that is what you see even when no CD or usb is present, I think something has gone very wrong and I suggest you start over from scratch and reinstall.

It would be worth running the live CD, mounting your hard disk, by using nautilus and double clicking on the drive icon to see what is on the hard disk.

---

### Post by ninja123 on 2009-03-06
could it be something to do with the boot menu?

i see Oses not even present in my system in the menu.lst in GRUB.

In easy peasy, in administration->install this is the same screen that pops up.

Could I conigure this??

Please is there no way without uninstalling the OS??????? please help

---

### Post by zerocool929 on 2009-03-07
Any help on this would be greatly appreciated as I am running into the exact same issue.  I have a netbook that I installed XP onto.  From XP, I created a new partition and installed Easy Peasy on it from a USB stick (using unetbootin).  Installation seemed to go perfect and I have the following options on boot:

Easy Peasy 1.0, kernel 2.6.27-8-eeepc
Easy Peasy 1.0, kernel 2.6.27-8-eeepc (recovery mode)
Easy Peasy 1.0, memtest86+
Other operating systems:
Windows NT/2000/XP

When I select the first option, it boots to ubuntu and I get the standard Username and Password prompts.  It then boots to the Easy Peasy screen and then prompts "Enter your password to perform administrative tasks". 

After entering that password, it goes to the homescreen but immediately loads the install screen shown in the screenshot in the first post.  In my case I get the error "Language Crashed" but its still the same issue.

If I quit the process I can use ubuntu just fine however its really annoying that it pops up.

I am completely new to Linux distro's so I apologize in advance if any of the above was technically ignorant.  I am just stating my observations as the screens pop up.  

Would really appreciate some help on this one.

---

### Post by phpadik on 2009-03-07
This is a really weird problem. Have you tried reinstalling the OS?

Anyway, my live CD doesn't show up the Install window upon logon. I think there's something really wrong.

---

### Post by zerocool929 on 2009-03-07
Figured it out (actually my buddy did).

Preferences - Sessions - Uncheck "Ubiquity".

The install program is set to load at startup.  This solved it.

---

