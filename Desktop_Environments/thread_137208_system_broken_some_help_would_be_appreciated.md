---
title: "system broken some help would be appreciated"
date: 2006-02-27
forum: Desktop Environments
---

### Post by hollowhead on 2006-02-27
I've managed to break my system by trying to remove a user.  I get on entering metacity internal error failed to initialise HAL!  I know what HAL is now. Cannot access any devices such as internet, also synaptic.  Anything that requires a password doesn't start and then a message appears (eventually) saying the password has already been entered and is incorrect (it hasn't). Is there any way of fixing this w/o reiinstall?

---

### Post by r4ik on 2006-02-27
In a terminal ~$ sudo apt-get install hal ?

---

### Post by Mustard on 2006-02-27
[QUOTE=r4ik]In a terminal ~$ sudo apt-get install hal ?[/QUOTE]

Well, that might not work if things are busted. It might be necessary to run in recovery mode, assuming that recovery mode still works.

With regards to the OP, what user did you remove?

Try getting to recovery mode anyway and see it things are working from there.  Recovery mode should put you at a root prompt.  You could perhaps look at your logs in the /var/log folder and see what changes you might have made.

---

### Post by r4ik on 2006-02-27
My capabillity has it's limits no prob.
Learning everyday.

---

### Post by hollowhead on 2006-02-28
Thanks for your replies.  Confession time I removed SU which I'd had to create see [http://ubuntuforums.org/showthread.php?t=91596&highlight=hollowhead](http://ubuntuforums.org/showthread.php?t=91596&highlight=hollowhead).  I cannot access any devices that require a password. This includes the internet. I can print.  I only boot from a floppy anyway since grub alters my windblows partition and have succesfully booted using rescue or normallly.  If I type su at the prompt I get "sorry".  If I type sudo somecommand I get "root has no password".  This is true but in etc/passwd there is no root entry.  I would prefer not to reinstall partly cause of the effort and partly cause I have some xfig files I don't want to lose.  I had them copied onto a usbflash but this concidentally has just failed.  I tried plugging a usb hard drive and usb floppy in but nothing appeared on the desktop.  I have bought a new usb flash drive and will try that to retrieve my files tha always worked well as ordinary user.  I cannot even mount a floppy drive w/o being root (what is it about ubuntu and floppies?).

My question is there used to be a way of booting from a rescue disk mounting the system and restoring root password.  Is this still possible and how do I do it?  This is very embarrasing and totally my fault but any help would be very useful.

---

### Post by codejunkie on 2006-02-28
[QUOTE=hollowhead]Thanks for your replies.  Confession time I removed SU which I'd had to create see [http://ubuntuforums.org/showthread.php?t=91596&highlight=hollowhead](http://ubuntuforums.org/showthread.php?t=91596&highlight=hollowhead).  I cannot access any devices that require a password. This includes the internet. I can print.  I only boot from a floppy anyway since grub alters my windblows partition and have succesfully booted using rescue or normallly.  If I type su at the prompt I get "sorry".  If I type sudo somecommand I get "root has no password".  This is true but in etc/passwd there is no root entry.  I would prefer not to reinstall partly cause of the effort and partly cause I have some xfig files I don't want to lose.  I had them copied onto a usbflash but this concidentally has just failed.  I tried plugging a usb hard drive and usb floppy in but nothing appeared on the desktop.  I have bought a new usb flash drive and will try that to retrieve my files tha always worked well as ordinary user.  I cannot even mount a floppy drive w/o being root (what is it about ubuntu and floppies?).

My question is there used to be a way of booting from a rescue disk mounting the system and restoring root password.  Is this still possible and how do I do it?  This is very embarrasing and totally my fault but any help would be very useful.[/QUOTE]
insert your ubuntu install cd enter ```
rescue
``` at the cd's boot prompt follow the instructions and it will chroot into your system as root now you can enable the root account on your system with ```
passwd root
``` and make any other changes you needed to do like reinstalling hal, when your done you can reboot your computer by entering ```
init 6
```remove the cd and boot ubuntu normally.

---

### Post by hollowhead on 2006-02-28
Thanks code junkie.  Two questions.  First when I put the cd it tries to install but first asks if there are any parameters I want to pass first if memory serves me correct.  It is at this point I type rescue?  Second, if set the root passwd will it create the su user as well? It should do shouldn't it?  Ta.

---

### Post by hollowhead on 2006-02-28
Code junkie, sorry for ignorant reply should have read your post properly before hitting the keyboard.  I followed your instructions, followed the instructions and got to sh3 prompt.  Unfortunately typing "passwd root" led to the following response, "Cannot determine your username".  As did trying to cange passwds for existing users or create a new one just to see what happened.  I did manage to mount a floppy and cp the files I wanted to retrieve off it (a world first never managed to access a floppy in this distro before).  Any other ideas as what I can do?

---

### Post by Mustard on 2006-02-28
Make a backup of your home folder and reinstall?  It seems like the system is pretty fubared.  What other drives/partitions do you have on the system?

---

### Post by hollowhead on 2006-03-01
I guess thats what I will have to do.  It used to be possible to edit etc/paswd and add rootofallevil to the root line in it and this reset the root passwd.  Is this still possible?

---

