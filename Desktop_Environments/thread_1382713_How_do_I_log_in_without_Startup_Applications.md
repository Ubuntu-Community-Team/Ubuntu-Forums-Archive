---
title: "How do I log in without Startup Applications?"
date: 2010-01-16
forum: Desktop Environments
---

### Post by jeffehobbs on 2010-01-16
I have an item in my Ubuntu 9.10 Gnome Startup Applications that is freezing my system (Boxee beta). Is there a way to log into the Gnome desktop while somehow restricting those items from starting up?

I should also mention that grub's "safe mode" boot is not working for me either, as it hangs on NTP loading -- long story short (too late) I uninstalled network-manager and network-manager-gnome and now everything has gone to heck. I don't have network so I can't SSH.

Any thoughts?

---

### Post by Locutus_of_Borg on 2010-01-16
it has been a long time since ive used gnome or gdm so i dont remember if there is an option for an empty or new session from the login manager, but you could, instead of logging in at gdm, switch to a new VT (ctrl+alt+F3 for example) and log in to a text console, then just delete the autostart entry for boxee.  that would probably be located in ~/.config/autostart/ but might possibly also be in /etc/xdg/autostart/, if the latter, you will need to 'sudo rm' the file, which will probably be something like boxee.desktop, if the entry is in ~/.config/autostart, then simply 'rm ~/.config/autostart/boxee.desktop' should do the trick.  then simply logout by typing 'exit' and switch back to gdm by pressing ctrl+alt+F7 (or is it F1?)

---

### Post by jeffehobbs on 2010-01-16
I should also mention that my box is set to auto-login to the account that freezes, so I never even see the Login Manager.

---

### Post by d3v1150m471c on 2010-01-16
system>preferences>startup applications... does this help? If not try getting "bum" with synaptic. 

Also, if you know what process is freezing your pc on startup press ctrl+alt+F1 to access the tty1 terminal and:

pkill nameofprogramorprocesshere

leave tty1 with ctrl+alt+F7

---

### Post by jeffehobbs on 2010-01-16
I can't get to the Gnome menus, because Boxee beta comes up and freezes (maybe because there's no network?). I see -- grub prompt, then the new Ubuntu load screen, then the box auto-logins to my account, auto-starts Boxee beta; and I get a black screen with a cursor (and can't get out).

I'm willing to take the drive out of the box, hook it up to another box and temporarily remove whatever file controls autostarted items in 9.10 -- I'd like like to know for sure what file or files they are that I should look for.

UPDATE: cntl+alt+F1 gives me a prompt that reads: 

* Starting NTP server ntpd

and a flashing cursor and nothing else.

---

### Post by d3v1150m471c on 2010-01-16
right, see above. try killing boxee beta with tty1 and then taking it out of your startup programs when you exit tty1

---

### Post by d3v1150m471c on 2010-01-16
also, on your login screen you can switch gnome to gnome safe mode and you could possibly manipulate it from there.

---

### Post by Locutus_of_Borg on 2010-01-16
> **jeffehobbs said:**
> I should also mention that my box is set to auto-login to the account that freezes, so I never even see the Login Manager.

at GRUB, change the kernel boot line to end with: init=/bin/sh

---

### Post by d3v1150m471c on 2010-01-16
> **Locutus_of_Borg said:**
> at GRUB, change the kernel boot line to end with: init=/bin/sh

you'll need to press esc to manipulate this and press "e" to edit the boot line

---

### Post by sisco311 on 2010-01-16
> **jeffehobbs said:**
> I can't get to the Gnome menus, because Boxee beta comes up and freezes (maybe because there's no network?). I see -- grub prompt, then the new Ubuntu load screen, then the box auto-logins to my account, auto-starts Boxee beta; and I get a black screen with a cursor (and can't get out).

I'm willing to take the drive out of the box, hook it up to another box and temporarily remove whatever file controls autostarted items in 9.10 -- I'd like like to know for sure what file or files they are that I should look for.


Reboot the computer and select Recovery Mode from the grub menu.

You may have to hold down the Shift key during bootup in order to see the menu.

Wait for all the boot-up processes to finish.

Select *Drop to root shell prompt* option from the Recovery Mode menu.

The startup applications are in the ~/.config/autostart/ directory, type:
```
cd /home/**username**/.config/autostart/
ls
```
to list them. Replace **username** with your login name.

rename the one witch causes problems:
```
mv ./**nameofthefile.desktop** ./**nameofthefile.desktop.noexec**
```


type:
```
exit
```
and choose to resume a normal boot.

---

### Post by jeffehobbs on 2010-01-16
*Wait for all the boot-up processes to finish.*

This hangs at the ntp prompt I described above.

Maybe I should just shoot myself in the face.

---

### Post by sisco311 on 2010-01-16
> **jeffehobbs said:**
> *Wait for all the boot-up processes to finish.*

This hangs at the ntp prompt I described above.

Maybe I should just shoot myself in the face.

Oh, sorry I missed that.

At the grub menu highlight the *Recovery Mode* option, press e for edit, move the cursor at the end of the linux line, delete the *ro and single* boot options, type **rw init=/bin/bash** and press Ctrl+x to boot in a root shell without starting ntp.

rename the .desktop file and press Ctrl + Alt + Del to reboot.

If the problem still persist, try to boot again on the root shell and disable ntp:
```
update-rc.d -f ntp remove
```

If update-rc.d is not installed, then remove the /etc/rc2.d/S23ntp symbolic link manually.

---

### Post by jeffehobbs on 2010-01-16
UPDATE: I have managed to start the box off a CD but I can't seem to mount the drive with my home directory in a read/write fashion. Is there something special I need to do? I can *see* the file I need to get rid of in the ~/.config/autostart directory.

Sorry about all this, it seems to be a Perfect Storm of bad karma.

---

### Post by sisco311 on 2010-01-16
> **jeffehobbs said:**
> UPDATE: I have managed to start the box off a CD but I can't seem to mount the drive with my home directory in a read/write fashion. Is there something special I need to do? I can *see* the file I need to get rid of in the ~/.config/autostart directory.

Sorry about all this, it seems to be a Perfect Storm of bad karma.

Start the file manager as root:
```
gksu nautilus
```

Be very careful witch file you delete.

If the ntpd daemon is causing your problems, then you may have to remove the /etc/rc2.d/S23ntp symbolic link to prevent the daemon to start up.

---

### Post by jeffehobbs on 2010-01-16
GOOD NEWS EVERYONE!

I booted off the Ubuntu 9.10 CD, used the terminal to delete the file that was freezing in ~/.config/autostart, changed /etc/network/interfaces back to the default, rebooted, reinstalled .deb files of network-manager and network-manager-gnome and everything works again! Hallelujah!

Thank everyone very much for your help, it just goes to prove that Ubuntu users are the best people in the world.

Thanks again!

---

### Post by jeffehobbs on 2010-01-16
POSTSCRIPT: If any Gnome/Ubuntu dev is reading this thread, in MacOS X you hold down shift to log in without Login Items firing up. 

[http://support.apple.com/kb/TA20716?viewlocale=en_US](http://support.apple.com/kb/TA20716?viewlocale=en_US)

This might be a nice feature to consider for Ubuntu/Gnome in the future.

---

