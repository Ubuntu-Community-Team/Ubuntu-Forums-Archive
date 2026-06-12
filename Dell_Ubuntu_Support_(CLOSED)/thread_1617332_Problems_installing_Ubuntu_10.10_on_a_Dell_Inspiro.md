---
title: "Problems installing Ubuntu 10.10 on a Dell Inspiron 8100"
date: 2010-11-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by beamland on 2010-11-09
Hello everyone

Already searched around in several forums to no avail.

I wanted to setup Ubuntu 10.10 32bit on my old Dell Inspiron 8100. I can chose installation language and keyboard layout and am able to chose wether to install or run in live mode from CD.

Whatever method I've choosen, I finally run in some kind of a blank / black screen. I'm not able to CTRL-ALT-F1 to get a console.

I was able to install it using text mode. But when booting I can't see anything useful on the screen, no text, no fancy splash screen or so. I can hear the sound when login screen usually would appear. Trying to switch to a console fails.

However, running a PartEd Magic CD in live mode works perfectly, so I'm sure the hardware is fine.

The specs are:
- Dell Inspiron 8100, Pentium 3, 933MHz, 15" UXGA
- 512MB Ram
- 30GB Hdd
- 32MB Nvidia GeForce 2 Go

Any ideas what to do in order to get graphics card work correctly?

Thanks anyone in advance for some help.

---

### Post by gibbylinks on 2010-11-09
Sounds like you need to add "nomodeset" to grub

When booting hold down the **shift** key after the BIOS screen to enter the grub menu.

Press **E** to edit the grub command line.

add the word "**nomodeset**" (without the quotes) after quiet  splash

Then **ctrl-x** to boot.

See if that works. If it does you'll need to make it permanent

To make it permanent open terminal and enter

```
sudo gedit /etc/default/grub
```add nomodeset as shown below in red

> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **[COLOR=Red]nomodeset[/COLOR]**"
GRUB_CMDLINE_LINUX=""

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
#GRUB_INIT_TUNE="480 440 1"                      save the file and type

```
sudo update-grub
```You should then be able to boot normally without having to edit grub.

Hope that helps

---

### Post by beamland on 2010-11-09
Update: I reinstalled in text mode and added SSH Server. I'm now able to access a console via ssh. But whatever I'm trying, I'm not able to

Doing a "DISPLAY=:0.0 sudo xrandr -q" works and gives this:
```
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
TV-1 connected 800x600+0+0 (normal left inverted right x axis y axis) 304mm x 228mm
   800x600        50.0*
   720x576        50.0
   640x480        50.0
   720x400        50.0
   640x400        50.0
   512x384        50.0
```

Stopping GDM in either way:
a) service gdm stop
b) /etc/init.d/gdm stop

Stops it but on the notebooks screen nothing changes. No cursor blinking, not able to switch to console via CTRL-ALT-F1 or F2.

In /etc/X11 there's no xorg.conf

See attached /var/log/Xorg.0.log for more info.

---

### Post by beamland on 2010-11-09
gibbylinks, you rock! Adding nomodeset after the quiet splash did the trick. THANK YOU VERY MUCH! It saved me a lot of headache!

---

### Post by pbhound on 2010-12-11
i am having the same issue.. i am in windows and run the live load/install and then it reboots to a black screen. my set up is almost identical i have a 20HDD instead of the 30HDD. i am having a problem getting to the part that you are describing.

thanks in advanced.

---

### Post by pbhound on 2010-12-12
ok i have gotten it installed but now when it reboots the screen is black and i cannot get into the grub... can anyone help me? (trying to install ubuntu 10.10 netbook.)

---

### Post by pbhound on 2011-02-18
> **pbhound said:**
> ok i have gotten it installed but now when it reboots the screen is black and i cannot get into the grub... can anyone help me? (trying to install ubuntu 10.10 netbook.)

this worked for me thanks.

---

