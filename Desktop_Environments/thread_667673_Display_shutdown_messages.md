---
title: "Display shutdown messages"
date: 2008-01-14
forum: Desktop Environments
---

### Post by oshcraft on 2008-01-14
Hi,

I am using Gutsy with Gnome and have to debug the shutdown scripts. For this I would like to see the shutdown messages like "unmounting local filesystes... done" etc.

For Grub I am using boot option nosplash and I am not using boot option quiet:
```
$ grep "# defoptions" /boot/grub/menu.lst
# defoptions=nosplash
```

When I shutdown, I see a text message "System is shutting down, please wait..." and the shutdown messages are hidden. Does someone know how to disable this message and show the output of the shutdown scripts instead?

Thanks for help

---

### Post by Mister.Vash on 2008-01-14
Before making any changes, make sure to make a backup copy of your /boot/grub/menu.lst so that you can revert any changes in case of an error

Without seeing the full menu.lst file, my first guess is that it is because of the quiet option.  The first uncommented line starting with the word **title** should be  your default menu entry and should contain your boot options underneath ( unless you have changed the line starting with default to something other than 0 ).  Under that first entry, you should have a **kernel** line.  On the kernel line, remove the word **quiet** - you can also remove the word splash from that line.

If you have troubles, post your menu.lst for review


Don't use this example verbatim as your options will be different and it will break, modify your existing entry.  What you should wind up with is something similar to this 

title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=/dev/hda1 ro
initrd          /boot/initrd.img-2.6.22-14-386

whereas before editing, you would probably have had an entry containing the quiet and splash options
title           Ubuntu 7.10, kernel 2.6.22-14-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-386 root=/dev/hda1 ro **quiet splash**
initrd          /boot/initrd.img-2.6.22-14-386

---

### Post by oshcraft on 2008-01-15
I also suspected the quiet boot option to be the cause. That's wy I have removed it from the default options. It is strange, during bootup I see (verbose) startup messages but not on shutdown.

Here my default boot entrry:
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/vmlinuz-2.6.22-14-generic root=/dev/mapper/vgmain-lvroot ro nosplash
initrd		/initrd.img-2.6.22-14-generic
quiet

I also added boot option "noquiet" and run "update-grub". Did not change anything.

Then there is this "quiet" option at the bottom. It does not seem to be a boot option but something related to Grub. I have no clue what it stands for. I removed it from the menu.lst, but again nothing changed. Here I did not run "update-grub" as this change can be read by Grub itself and "update-grub" would recreate this option.

My current boot options:
```
$ cat /proc/cmdline
root=/dev/mapper/vgmain-lvroot ro nosplash noquiet
```

Of couse I completetly rebooted after each change.

---

### Post by mister_p_1998 on 2008-01-15
On a similar note, how would I go about changing the default ie first entry in the grub menu
I want to change the default one of Ubuntu to XP, so XP boots on timeout. (not for me, for the wife... Honest!)
Do I just cut & paste the XP menu entry and place it at the top of menu.lst?
Steve

---

### Post by oshcraft on 2008-01-15
See: [ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

Instead of copying, edit the default option and set #updatedefaultsentry to true to prevent changes if new kernels are added.

However, this is not related to this thread.

---

### Post by hamidaddin on 2008-01-15
I prefer using graphical interfaces. There is a very nice tool called startupmanager (can be installed by Synaptic). 

You can use it to change the default OS to be booted, the waiting time, the boot loader colors and theme..etc.

I've included some screen shots for those who are interested.

---

### Post by Mister.Vash on 2008-01-15
I did see an older bug report regarding the shutdown mesages going to a different tty when using the power button
[https://bugs.launchpad.net/ubuntu/+bug/18637](https://bugs.launchpad.net/ubuntu/+bug/18637)

During shutdown, can you try switching between the consoles via the CTRL+ALT+F1 and the CTRL+ATL+F7 to see if anything shows?

If that doesn't show anything, try doing a "sudo reboot" from tty1 ( CTRL+ALT+F1 ) to see if you can at least see the shutdown messages from there, if you do see them, it might be a video resolution issue as I've seen people mention that as one of the causes that the console does not display properly display at times.  The following has some details on setting the resolution.  It may not be pertinent since you do see messages during boot
[https://help.ubuntu.com/community/ChangeTTYResolution](https://help.ubuntu.com/community/ChangeTTYResolution)

---

### Post by oshcraft on 2008-01-15
Yup, this bug report brought the solution.

Shutdown messages are shown on TTY7 whereas TTY1 is active during shutdown and showing the text splash message.

It's quite strange because for a very short time, the shutdown messages are shown in the current TTY. Then it's either overwritten or the TTY is changed. Also it is not possible to turn off this text splash using boot option quiet. This is annoying and does not seem to be solved (the bug report is closed).

However, I was able to debug the shutdown scripts on TTY7. Thanks for your help.

---

