---
title: "running script when connecting USB stick"
date: 2005-09-21
forum: Desktop Environments
---

### Post by blockme on 2005-09-21
hi there. I couldn't find an information about this. maybe someone can help me.

I am using a decrypted hard disc (cryptoloop - because the new thingie in 2.6 kernel was slower and couldn't handle the gpg key on usb disk).

when i am mounting this partition, my gpg key on my usb disc is beeing used. for this i have my usb disc to be mounted and unmounted again.

is it possible to run something like the following script automated when pluggin in the usb stick?

- automount usb stick (KDE is only mounting it when dbl-clicking the stick)
- mount crypted device (will ask for password)
- unmount usb stick

- plop usb stick out of the com (<- j/k)

any ideas? thanks for help!

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=blockme]hi there. I couldn't find an information about this. maybe someone can help me.

I am using a decrypted hard disc (cryptoloop - because the new thingie in 2.6 kernel was slower and couldn't handle the gpg key on usb disk).

when i am mounting this partition, my gpg key on my usb disc is beeing used. for this i have my usb disc to be mounted and unmounted again.

is it possible to run something like the following script automated when pluggin in the usb stick?

- automount usb stick (KDE is only mounting it when dbl-clicking the stick)
- mount crypted device (will ask for password)
- unmount usb stick

- plop usb stick out of the com (<- j/k)

any ideas? thanks for help![/QUOTE]
Well, one idea would be to have a script running in the background that just sleeps most of the time in a loop, but periodically checks (with lsusb and/or mount) to see if your USB stick is mounted.  The auto-mounting itself should be done by gnome-volume-manager or a hotplug script.  The backgroud script could then just use some sort of simple X-dialog to prompt for your password and mount he crypt device and unmount the USB stick.  You could put the script in your KDE Autostart folder (or the Gnome equivalent).

---

### Post by blockme on 2005-09-22
thx for reply!

you were talking about a hotplug script... what is this script? where do i find it? couldn't I extend this script to run my own script when mounting?

what package do I have to install for automount or do I have to edit init.d?

---

### Post by cwaldbieser on 2005-09-22
[QUOTE=blockme]thx for reply!

you were talking about a hotplug script... what is this script? where do i find it? couldn't I extend this script to run my own script when mounting?

what package do I have to install for automount or do I have to edit init.d?[/QUOTE]
Well, the hotplug system is already installed on your system by default, I think.  Here is a related post: [http://ubuntuforums.org/showthread.php?t=15357&highlight=hotplug](http://ubuntuforums.org/showthread.php?t=15357&highlight=hotplug)
If you do "man hotplug" you will get lots of info.

Basically, the hotplug system is an event driven system that you can use to run your own scripts or other executables in response to a removable device being plugged in.  Since I mostly use KDE, I wrote my own "automounter" for my USB devices.

The reason I suggested the second script in addition to the hotplug script is that hotplug pretty much works in the background, detached from any terminal.  Therefore, it can't pop up a dialog and ask you for your password.  Instead, the hotplug script needs to alert your interactive script that an interesting event has happened-- there are many ways to do this.  You could use a lock file, or try to send a signal, etc.

Let me know if you need any help.  I don't think it should be difficult to cobble something together.

---

### Post by blockme on 2005-09-22
ah I see. Thanks for this information. I will think about it and see how to solve this. Right now I don't like the idea that some kind of script is looping all the time ;-) (no idea how demons work though)

---

### Post by cwaldbieser on 2005-09-22
[QUOTE=blockme]ah I see. Thanks for this information. I will think about it and see how to solve this. Right now I don't like the idea that some kind of script is looping all the time ;-) (no idea how demons work though)[/QUOTE]
The majority of programs are just some big loop.  Even your OS!  Demons typically have some sort of loop, too (though you could argue that "inetd" is the "loop" for some of them.  

If you don't like the idea of the interactive script polling every so often, you can just have it suspend itself.  The hotplug script could send it a resume signal to start it back up.  It could do its thing and then suspend itself again.

---

### Post by blockme on 2005-09-27
still working on this ;-)

right now I am wondering if the X-commands are KDE/Gnome specific? Where do I find a short information about programming a small dialog for KDE or X?

thx again

---

### Post by sudo-fu on 2007-03-23
I have the same question for Gnome. Is there a simple way to autostart a script when a drive is mounted manually (not automount)? There should be, but I didn't find any answers yet.

---

### Post by puqing on 2007-03-23
> **sudo-fu said:**
> I have the same question for Gnome. Is there a simple way to autostart a script when a drive is mounted manually (not automount)? There should be, but I didn't find any answers yet.

Those files under /etc/modprobe.d should be helpful. 'man modprobe.d' describes the format and usage of the files.

---

### Post by sudo-fu on 2007-03-23
I looked at the manpages but didn't understand what this has to do with modprobe. Can anyone explain please? It shouldn't be a big deal. All I want is to automatically run a script from a device when that device is manually mounted.

---

