---
title: "Brightness and suspend problem"
date: 2019-07-08
forum: Desktop Environments
---

### Post by gnouf1 on 2019-07-08
Hi !
I installed xubuntu on my new Thinkpad E495 laptop and I have two important problem.
CPU : AMD Ryzen 7 37000U
RAM: 16Go
No GPU
Distro: Xubuntu 18.04 LTS

1) I can't change my screen brightness and all GRUB modification i try or software don't work.
All I can say is when i use fn keys or my cursor values in backlight files change but not my brightness :/
xbacklight respond :
```
outputs have backlight property
```
xrandr:
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected 1920x1080+0+0 0mm x 0mm
   1920x1080     77.00* 
```

My GRUB:
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
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

```

2) And when I suspend my computer i can't wake up him. Keyboard light are on but not his screen when i try :/

Thanks by advance,
sorry for my english I'm french.

---

### Post by him610 on 2019-07-09
You should be using *radeon* or *amdpro* driver. Can you please verify by showing results of *inxi -Fxz* within code tags?
> 1)...can't change my screen brightness
Have you tried clicking on the Computer icon in the panel? There should be a brightness control that allows adjustment.
> 2)...suspend my computer i can't wake
Others have reported similar behavior, might be best to avoid suspend and use shutdown/turnon, or never suspend.

---

