---
title: "Dell video settings set to safe/no mode after kernel update"
date: 2011-01-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by joedoe47 on 2011-01-27
*ok, I have nooo idea where to post this so please forgive me if I posted this in the wrong area.*

So I have a dell laptop inspirion n4010 and I installed a remastered version of ubuntu 10.10 that I made on a virtual machine (and actually it seemed to work flawlessly on the virtual machine, everything was perfect; all I wanted was to change the splash screen and add a couple programs on it, nothing too complex like adding things into skel, etc.) Then I took out the iso from that virtual machine and installed it on my laptop (because my previous installation broke and was too lazy to figure it out) [INDENT]Any who, after I installed my simple remaster of Ubuntu 10.10 64bit I then ran into a problem. The screen resolution was stuck on 1280x1024 (this thing can go up to 1366x768) but I was unable to change it from the monitors section. after research I found out that in my grub2 menu it was set to...[/INDENT]> quiet splash nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap:mad: every time I update the Linux kernel that freaking line of text is added to grub.cfg I would like to know and ask if anyone knows what could be done (other than to edit his manually each time) to fix this from happening?

if you require something just let me know (I have a lot of time free so just post/reply and I'll get it to right away) :(

---

### Post by wojox on 2011-01-27
Look in 

```
/etc/default/grub
```

You should see it in there.

---

### Post by joedoe47 on 2011-01-28
well this is all it says (I can't belive I didn't check there) I changed it, thanks ^.^
:guitar:

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash[COLOR=Red] _**nomodeset video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap**_[/COLOR]"
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
GRUB_GFXMODE=1280x1024

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

---

