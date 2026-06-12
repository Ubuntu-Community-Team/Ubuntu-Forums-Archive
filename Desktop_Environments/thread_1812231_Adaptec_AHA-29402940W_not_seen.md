---
title: "Adaptec AHA-2940/2940W not seen"
date: 2011-07-26
forum: Desktop Environments
---

### Post by fmouse on 2011-07-26
I'm building a new desktop with Ubuntu 11.04, Kernel 2.6.38-10-generic-pae.  I have an old but perfectly serviceable Adaptec AHA-2940 which I want to move from my old Linux box to my new Ubuntu system.  Almost the only purpose of this card is to support a venerable but very well-made HP flatbed scanner which still works perfectly and gets used frequently.

The card is supported on the old system by the aic7xxx kernel module, however the new Ubuntu system, with the "new" aic7xxx driver won't recognize the card.  The hardware sees the card, and presents a summary of devices connected to it (or not) during POST, however once Linux is running, the card doesn't show up with lspci.

Where do I go from here?  Do I need to custom-build a kernel and build the legacy aic7xxx driver (which the kernel docs say will be removed at some point) or is there some other way to get the OS to recognize the card?

---

### Post by henrypearce on 2011-09-05
Hello.  I have the same problem in that I want to use one of these cards for my Epson GT30000 scanner.  I am new to Linux (this week end) and have no idea how to build a custom kernel.

---

### Post by haqking on 2011-09-05
> **henrypearce said:**
> Hello.  I have the same problem in that I want to use one of these cards for my Epson GT30000 scanner.  I am new to Linux (this week end) and have no idea how to build a custom kernel.

Hi henry, glad to see you posted. Sorry couldnt of been more help in IRC, it seems that there is not much information on this adapter within Ubuntu at least at first glance.

Most of what i have seen involves a custom kernel for most distros.

Perhaps someone here will have more direct experience with the controller itself under Linux and be able to help.

if not then the Scsi to USB adapter might be your only option.

Best of luck and hope you get it sorted.

regards
haqking

---

### Post by fmouse on 2011-09-06
This turned out to be an anomaly with the mainboard, possibly also a Linux kernel bug since the MS Windows kernel deals with the situation more creatively and works around it.  There was some discussion of it on the Linux kernel list, since Linux should be able to do this too.  See [https://lists.linux-foundation.org/pipermail/bugme-new/2010-September/025647.html](https://lists.linux-foundation.org/pipermail/bugme-new/2010-September/025647.html) and also google for Linux and DP43BF, the model spec of the mainboard.

The workaround/fix is to pass "pci=assign-busses" to the kernel via grub.  Add this to the GRUB_CMDLINE_LINUX var in /etc/default/grub and run update-grub.

---

### Post by henrypearce on 2011-09-07
Thanks for the resopnse.  That sounds like good news.  pardon me for being incompetent but how do I do that and what is Grub?  (I was hoping thay Linux would bring a bright new world free of MS but it is turning out to be a nightmare!).  Regards.  Henry

---

### Post by fmouse on 2011-09-07
> **henrypearce said:**
> Thanks for the resopnse.  That sounds like good news.  pardon me for being incompetent but how do I do that and what is Grub?  (I was hoping thay Linux would bring a bright new world free of MS but it is turning out to be a nightmare!).  Regards.  Henry

Grub is the boot manager in Ubuntu.  As with any OS, including Windows, there's a small program written to the beginning sectors on your hard drive which is read by the computer when it starts up, and which directs the loading of the operating system kernel.

You'll need to use your favorite text editor - pico is the native text editor if you can't boot to a GUI - or gedit if you get as far as a GUI desktop.  You'll need to become root (the master system admin account) and as root, edit the file /etc/default/grub, which sets the default values for grub.  When you look at this file in your editor, my comment re. GRUB_CMDLINE_LINUX will make sense, and there are a number of other helpful comments in this file as well.  Then, still as root, run the update-grub command, as noted in the file comments, and then reboot your computer.

As Linux goes, Ubuntu is probably the easiest distribution to get up and running, but if you hit snags, which isn't uncommon, some knowledge of Linux (and by inference, Unix) fundamentals is pretty important, such as the concept of doing things as the root user, and how the standard Linux file system is laid out.  There are some good books out there.  My impression has been that the IDG books are generally first rate.  These are the (no insult intended!) the "xxxxx for Dummies" books available at most book stores.  There is a "Linux for Dummies" book available which you might find helpful.

As far as troubleshooting goes, one of the main differences between Linux and Windows is that when tracking down a Windows problem, sooner or later you hit a "black box" and can go no further because the internals are proprietary.  With Linux, almost every problem is solvable if you have the knowledge, and if you don't, then there are generally a lot of friendly people on forums and mailing lists, and in users groups, who can help you out.  Linux still has some rough edges, and probably always will, but it has improved vastly in this regard over the past 10 years or so.  Don't give up, Henry, just keep working at it, and ask questions if you run into problems.

---

### Post by henrypearce on 2011-09-08
_***Thank you for that.  I now have got as far as ***_

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

_***I am assuming I now add to this list the line***_

GRUB_CMDLINE_LINUX"pci=assign-busses2

[U][I][B]I'm not sure if it is good that the water is so deep but I do know it is just below my nose!

Regards.
Henry[/B][/I][/U]

---

### Post by fmouse on 2011-09-08
You don't need to add any lines, and the line you suggest is incorrect since you dropped the "=" sign after the variable name, added a "2" after "busses", and ommitted the final quote.  Computers are picky about this kind of thing!!  Just use your editor to edit this file and change the existing line:```
GRUB_CMDLINE_LINUX=""
``` so that reads ```
GRUB_CMDLINE_LINUX="pci=assign-busses"
``` Save the file.  Then run, as root, update-grub and reboot.

If your problem is related to this anomaly, then this will fix it.  If it doesn't, then something else is at fault.

This is pretty simple stuff, as Linux goes.  Don't worry about it.  You can change the line back to what it was if it doesn't work.

---

### Post by fmouse on 2011-09-08
You might also google for the model number of your mainboard and the word Linux and see if this problem turns up in the results.  Or google for the mainboard model number spec and in quotes, "pci=assign-busses".  This will tell you if other people using the same hardware you're using have had the same problem.

---

