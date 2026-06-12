---
title: "How to adjust the boot up screen resolution"
date: 2010-08-07
forum: Desktop Environments
---

### Post by zzzliperzzz on 2010-08-07
Hello folks,

I just want to know how to adjust the screen resolution of my boot up screen.
My PCs maximum resolution is 1366x768 but I think my boot up screen only uses
600x400. I doesn't look nice for me. The logo of Kubuntu is too big and the colors
are not the true colors of the Kubuntu Boot up screen.

Any help will be appreciated. Thanks.:D

---

### Post by NewDisciple on 2010-08-07
Here is how I fixed it.
> sudo gedit /etc/default/grub
Here is a copy of my config file:
> # If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
[COLOR="DarkRed"]#GRUB_GFXMODE=1680x1050
GRUB_GFXPAYLOAD_LINUX=1680x1050[/COLOR]
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Edit the line in red with your resolution.  If the second line is not present add it and then save the file.
Next step is to open a terminal and run update-grub.

---

### Post by StephanG on 2010-08-09
Hey :)

Just wanted to let you know that I've had a similar problems with resolutions.

The solution I found was actually very simple.

I just used the DVI-D port on my graphics card, and it automatically detected and set my resolution to match my monitor's capabilities.

I was using a DVI-D to VGA converter, so the proper cable isn't even necessary.

---

