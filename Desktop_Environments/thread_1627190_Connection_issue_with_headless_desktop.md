---
title: "Connection issue with headless desktop"
date: 2010-11-21
forum: Desktop Environments
---

### Post by marktyler on 2010-11-21
I'm having a problem connecting from my machine to my headless Ubuntu box. I have autologin enabled, this works. 

vino-server is running
```

mark@htpc:~$ ps -ef | grep vino
mark      2375  1545  0 21:16 ?        00:00:01 /usr/lib/vino/vino-server --sm-disable

```

I seem to be able to connect...
```

mark@htpc:~$ netstat -an
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:6543            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:6544            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:51486           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.4:5900        192.168.1.13:62838      ESTABLISHED
tcp        1      0 192.168.1.4:5900        192.168.1.13:62836      CLOSE_WAIT 
tcp        1      0 192.168.1.4:5900        192.168.1.13:62786      CLOSE_WAIT 

```

But I never get a screen thrown back. I can ssh -X -Y and then chuck the odd screen back onto my Mac but no-can-do with vnc. Tried screensharing (says it's connecting but never gets anywhere) and a separate vnc app to connect - same deal.

I have attempted KMS switch..
```

mark@htpc:~$ cat /etc/modprobe.d/i915-kms.conf 
options i915 modeset=0

```

but it still seems to be using it...
```

mark@htpc:~$ dmesg | grep drm
[   18.376488] [drm] Initialized drm 1.1.0 20060810
[   18.752504] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0

```

xorg.conf
```

mark@htpc:~$ cat /etc/X11/xorg.conf
Section "Device"
        Identifier      "Onboard Intel Graphics"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        HorizSync       31-101
        VertRefresh     60-160
EndSection

Section "Screen"
        Identifier      "Basic Screen"
        Monitor         "Generic Monitor"
        Device          "Onboard Intel Graphics"
        SubSection "Display"
            Modes		"1600x1200"
        EndSubSection
EndSection

```

grub
```

mark@htpc:~$ cat /etc/default/grub 
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" nomodeset"

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
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Version
```

mark@htpc:~$ uname -a
Linux htpc 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

```

Can someone advise?

---

### Post by marktyler on 2010-11-30
Bump.

---

### Post by endotherm on 2010-11-30
do you have desktop effects running on the remote desktop? if so, there shoudl be a setting in the vnc client utility to disable x damage. tweak it, adn see if things improve. 
another option is to ssh in and run 
```
metacity --replace
``` to disable compiz

---

### Post by marktyler on 2010-12-06
Still not working. About the only thing I can do is SSH and run gnome-session to flick the desktop back. It's far from ideal and one thing I wish they'd sort out as even my Windows machine behaves when run headless.

---

