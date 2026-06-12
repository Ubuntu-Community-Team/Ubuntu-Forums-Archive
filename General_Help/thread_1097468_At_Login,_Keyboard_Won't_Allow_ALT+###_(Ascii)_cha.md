---
title: "At Login, Keyboard Won't Allow ALT+### (Ascii) chars"
date: 2009-03-16
forum: General Help
---

### Post by Greyhaven7 on 2009-03-16
I installed Ubuntu "inside windows" and was prompted to enter my username and password of choice. The password I chose included a special character that can only be typed by way of ALT+### on the numpad. Once I waited about 45 min for Ubuntu to finish its install I was prompted to login... but couldn't because it wouldn't allow me to hit ALT+anything (yes NumLock is on) (apparently you shouldn't use TOO strong of a password, lol). 

As this is my first attempt at using Linux, I'm not very impressed that it would allow you to select a character when choosing your password that it wouldn't allow you to enter when trying to actually use said password.

I'm using a Compaq laptop with Saitek keyboard. Tried another keyboard with no luck. 

I need to know how to get it to; 
1. accept NumPad ASCII chars
2. how to UNDO the 10 Gig allocation I just made (WITHOUT REFORMATTING the whole drive... but since I haven't even logged in to Ubuntu yet, I don't care if this involves wiping the 10 gig virtual partition thing it made for itself)
...OR ...
3. how to get it to change my password

Thanks, and Sorry guys, I've had a long day and I was really looking forward to a quick and easy install. :(

---

### Post by jocko on 2009-03-16
To change the password:
Boot into recovery mode. If you don't see the boot menu, press Esc when you see this message flashing by:```

GRUB Loading stage1.5.

GRUB loading, please wait...
Press 'ESC' to enter the menu... 3
```In the boot menu, select a line ending with "(recovery)". Once it has finished booting you should get a menu where you can select what you want to do, highlight the "root" option to get to a root terminal.
Once you get the terminal, type this command:
```
passwd [COLOR=Red]username[/COLOR]
```(where [COLOR=Red]username[/COLOR] of course is your login name).
You'll be asked to type in the new password twice.
To continue booting, type the command:
```
init 2
```

---

### Post by Greyhaven7 on 2009-03-16
... it's really that easy? :D 
Thank you so much 
I don't even have to enter the old password? (hmmmm, isn't that a bit unsettling somehow?) Please tell me that this doesn't work once you've logged in once or something... or that you can encrypt the drive so that's not possible to just go change the pw.

---

### Post by SamNSane on 2009-03-16
> **Greyhaven7 said:**
> ... it's really that easy? :D 
Thank you so much 
I don't even have to enter the old password? (hmmmm, isn't that a bit unsettling somehow?) Please tell me that this doesn't work once you've logged in once or something... or that you can encrypt the drive so that's not possible to just go change the pw.

It is possible to password protect the bootloader and / or rescue mode, the easiest method involving installing startupmanager (That's the actual name of the package.), running it, and using the settings on the Security tab. Of course that wouldn't protect you from someone who booted your system with a live CD or by some other method. So then you would have to turn off booting by any means other than your HD in your BIOS, and then put a BIOS setup password on the system.

If you password protect rescue mode or anything else with startupmanager, remember that those passwords don't change when you change your user password. So don't set them the same and then think several user password changes later that you can use your latest password to unlock rescue mode.

Ask me how I know.

;)

---

### Post by jwbrase on 2009-03-16
> **Greyhaven7 said:**
> I installed Ubuntu "inside windows" and was prompted to enter my username and password of choice. The password I chose included a special character that can only be typed by way of ALT+### on the numpad. Once I waited about 45 min for Ubuntu to finish its install I was prompted to login... but couldn't because it wouldn't allow me to hit ALT+anything (yes NumLock is on) (apparently you shouldn't use TOO strong of a password, lol). 

As this is my first attempt at using Linux, I'm not very impressed that it would allow you to select a character when choosing your password that it wouldn't allow you to enter when trying to actually use said password.

I'm using a Compaq laptop with Saitek keyboard. Tried another keyboard with no luck. 

I need to know how to get it to; 
1. accept NumPad ASCII chars
2. how to UNDO the 10 Gig allocation I just made (WITHOUT REFORMATTING the whole drive... but since I haven't even logged in to Ubuntu yet, I don't care if this involves wiping the 10 gig virtual partition thing it made for itself)
...OR ...
3. how to get it to change my password

Thanks, and Sorry guys, I've had a long day and I was really looking forward to a quick and easy install. :(

Alt+#### is an input method specific to Windows. Linux doesn't use it. You used Wubi, which is Windows program that installs Ubuntu. So Wubi could use the Alt+#### method because it was operating within Windows. When you booted up Ubuntu, you were no longer in Windows, so Alt+#### didn't work anymore. As far as I know, there's no way within Linux to do anything equivalent to Alt+####, so it does seem like a weakness in the Wubi installer that it would accept characters for a username or password that aren't on the keyboard for whatever language it's installing Ubuntu in. It's also a weakness of Linux not to have such an input method. You can set up special keyboard layouts and such, but you can only do that once you're logged in.

---

### Post by jocko on 2009-03-16
> **Greyhaven7 said:**
> ... it's really that easy? :D 
Thank you so much 
I don't even have to enter the old password? (hmmmm, isn't that a bit unsettling somehow?) Please tell me that this doesn't work once you've logged in once or something... or that you can encrypt the drive so that's not possible to just go change the pw.

Yep. From recovery mode you have complete access to every file on the system.

How is that unsafe? A potential saboteur would still have to get into your house, find the computer and boot into recovery mode to do any harm. Just lock the door before you leave your house, and your computer is as safe as it can be...

Even if you encrypt your partitions, put a password on grub, inactivate booting from cd in bios and activate password protection on bios, someone that can get into your house can still open up the case, reset the bios, boot from a cd and format your hard drive... so there's no point in being too paranoid...

---

### Post by SamNSane on 2009-03-16
> **jocko said:**
> Yep. From recovery mode you have complete access to every file on the system.

How is that unsafe? A potential saboteur would still have to get into your house, find the computer and boot into recovery mode to do any harm. Just lock the door before you leave your house, and your computer is as safe as it can be...

Even if you encrypt your partitions, put a password on grub, inactivate booting from cd in bios and activate password protection on bios, someone that can get into your house can still open up the case, reset the bios, boot from a cd and format your hard drive... so there's no point in being too paranoid...

Although there are systems -- like a couple of my notebooks -- that do HD encryption through the controller. The BIOS on them can't be reset by any brute force method, and removing the drive and placing it in another system wouldn't get anyone access to the contents. (There are disadvantages, too. If you forget your BIOS password it's a new motherboard for you. And if you encrypted the drive itself via the BIOS provisions... Ouch!)

But I think the point is that you can take reasonable precautions to make it difficult-to-virtually-impossible to get to the data on the drive of some systems. But if all the interloper wants is to re-use the system (provided it's not equipped with one of those encrypt-from-the-controller drives and an unresettable BIOS with the boot password set), then, yeah, it's a forgone conclusion.

---

### Post by Greyhaven7 on 2009-03-16
> **jocko said:**
> To change the password:
Boot into recovery mode. If you don't see the boot menu, press Esc when you see this message flashing by:```

GRUB Loading stage1.5.

GRUB loading, please wait...
Press 'ESC' to enter the menu... 3
```In the boot menu, select a line ending with "(recovery)". Once it has finished booting you should get a menu where you can select what you want to do, highlight the "root" option to get to a root terminal.
Once you get the terminal, type this command:
```
passwd [COLOR=Red]username[/COLOR]
```(where [COLOR=Red]username[/COLOR] of course is your login name).
You'll be asked to type in the new password twice.
To continue booting, type the command:
```
init 2
```

This worked up to right before I would have gotten a menu to pick "root" and get a terminal... it froze after printing this line:

[     4.999500] usbhid: v6:USB HID core driver

Should it sit there for a loooong time and then proceed? Am I just being impatient or did it actually pop an error?

Thanks again for your help. I hope this works...



UPDATE: Unplugging all my USB perifs (keyboard and mouse) allowed it to get past this spot... the rest of the above steps WORKED PERFECTLY! 

Thank you all so much! Now that I've gotten my god-forsaken broadcom card working with ndiswrapper my next step is to get the ATI vid card to allow me to use different resolutions on both monitors.

---

