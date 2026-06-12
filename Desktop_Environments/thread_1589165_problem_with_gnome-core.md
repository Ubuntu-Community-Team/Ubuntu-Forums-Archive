---
title: "problem with gnome-core"
date: 2010-10-06
forum: Desktop Environments
---

### Post by zuku on 2010-10-06
I have installed minimal gui on my ubuntu 10.04 using these comands:

sudo apt-get install gnome-core gdm network-manager-gnome indicator-applet-session notify-osd

after installation I have gnome in version 2.30.2 but there isn't any terminal any synaptic manager here anything!, can someone help me how to upgrade from this version or install something?

---

### Post by Dustin2128 on 2010-10-06
I'd recommend sudo apt-get install ubuntu-desktop, that gives you all the standard packages. After that, if you want something light on resources, grab lxde or fluxbox.

---

### Post by zuku on 2010-10-06
but how? there isn't here any terminal I have only links in Programs menu

---

### Post by Dustin2128 on 2010-10-06
> **zuku said:**
> but how? there isn't here any terminal I have only links in Programs menu
ctrl-alt-F1 for a fullscreen terminal, then ctrl-alt-F7 when you're done to get back into X. After that, reboot (relogin might be sufficient though). The standard installed packages should be there.

---

### Post by zuku on 2010-10-06
thanks, all working now ;)
I have additional question: system is booting without display grub menu, you know hot to fix it? sudo update-grub didn't work.

I have lvm on my disks:
/dev/sda1 - /boot
/dev/vgroup/root - /
/dev/vgroup/swap - swap

---

### Post by Dustin2128 on 2010-10-06
> **zuku said:**
> thanks, all working now ;)
I have additional question: system is booting without display grub menu, you know hot to fix it? sudo update-grub didn't work.

I have lvm on my disks:
/dev/sda1 - /boot
/dev/vgroup/root - /
/dev/vgroup/swap - swap

hm, post your grub.cfg, I'll take a look.

---

### Post by zuku on 2010-10-07
I'm using Grub 2, here is /etc/default/grub:

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" splash"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

pressing SHIFT during boot doesn't help too.

---

### Post by Dustin2128 on 2010-10-07
Grub is not quite my area of expertise, you might consider making a separate thread under general help.

---

### Post by zuku on 2010-10-07
ok thx for help ;)

---

