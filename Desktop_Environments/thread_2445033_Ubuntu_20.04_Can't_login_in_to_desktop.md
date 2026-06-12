---
title: "Ubuntu 20.04 Can't login in to desktop"
date: 2020-06-08
forum: Desktop Environments
---

### Post by darkxbunny on 2020-06-08
Hello everyone.
I was update my Ubuntu 19.10 to Ubuntu 20.04, and then my ubuntu-desktop stopped loading. After login in - black screen, and return me to users list.
What I was trying to do:
```

[COLOR=#000000][FONT=&amp]Ctrl-Alt-F2[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]nomodeset[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt-get purge nvidia*[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo dpkg-reconfigure xserver-xorg[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]dconf reset -f /org/compiz/[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]setsid unity[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]mv ~/.config/compiz-1/compizconfig ~/.config/compiz-1/compizconfig.dump[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt update[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt upgrade[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt remove ubuntu-desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt remove ubuntu-unity-desktop[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt remove unity[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt autoremove[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt autoclean[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt install ubuntu-desktop ubuntu-unity-desktop unity[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt install --reinstall xserver-xorg-core[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt install --reinstall xserver-xorg[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt install --reinstall xorg[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]rm /home/user/.config[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]rm /home/user/.compiz[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]rm /home/user/.cache[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo dpkg-reconfigure lightdm[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]sudo apt install --reinstall lightdm[/FONT][/COLOR]

```
But no effect.
Please, help.
Sorry for my bad english.

---

### Post by rostres on 2020-06-08
Follow step one and two from [https://itsfoss.com/fix-ubuntu-freezing/](https://itsfoss.com/fix-ubuntu-freezing/)
And after go to Software & Updates/ Aditional Drivers and update to driver 440

---

### Post by darkxbunny on 2020-06-08
Done. Nothing changed. Still can’t load desktop environment

---

### Post by Bashing-om on 2020-06-08
darkxbunny; Hello

EFI system ? where disabling "secure boot" is needed as the proprietary driver is 3rd party.

Then what results:
```

sudo apt upddate
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```
here too the system will choose the driver it thinks best from what it has to choose from.

[INDENT]maybe Yes
[/INDENT]

---

### Post by darkxbunny on 2020-06-08
Legacy system. I was trying to do this, but problem still exist

---

### Post by Bashing-om on 2020-06-08
darkxbunny; Humm ..

Do you own your /home directory ?
What shows:
```

ls -al .Xauthority .ICEauthority

```

[INDENT]as a thought
[/INDENT]

---

### Post by darkxbunny on 2020-06-08
Yes, I’m own in my own /home folder.
```

-rw———- 1 darkbunny darkbunny 16244 Jan 15 00:04 .ICEauthority
-rw———- 1 darkbunny darkbunny 73 Jun 8 20:10 .Xauthority

```

---

### Post by Bashing-om on 2020-06-08
darkxbunny; Well -

Not that then, as you do have access,

So what is the graphic's situation ?
```

sudo lshw -C display
lspci -k | grep -iEA5 'vga|3d'

```

[INDENT]gots to be a reason
[/INDENT]

---

### Post by darkxbunny on 2020-06-08
```

*-display
description: VGA compatible controller 
product: GK107M [GeForce GT 640M]
-/- NVIDIA corporation
physical ID: 0
-/- : pci@0000:01:00.0
version: a1
-/- : 64 bits
frequency: 33MHz
-/- : pm msi pciexpress vga_controller bus_master cap_list rom
configuration: driver=nvidia latency=0
resources: IRQ:31 memory:f6000000-f6ffffff memory:e000000-effffff memory:f000000-f1fffff ioport:e000(size=128) memory:c0000-dffff

```

and

```

01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 640M] (rev a1)
  Subsystem: EeeTOP GK107M [GeForce GT 640M]
  Kernel driver in use: nvidia
  Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device NVIDIA Corporation GK107M [GeForce GT 640M] (rev a1)
  Subsystem: NVIDIA Corporation GK107 HDMI Audio Controller 

```

---

### Post by Bashing-om on 2020-06-08
darkxbunny; Well -

Does not appear to be a graphic's driver issue either.
Installed desktop conflicts ?
what shows:
```

ls /usr/share/xsessions

```
as there is:
> 
sudo apt install ubuntu-desktop ubuntu-unity-desktop unity


[INDENT]sometimes I wonder
[INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT]

---

### Post by darkxbunny on 2020-06-08
```

ubuntu.desktop unity.desktop

```

---

### Post by darkxbunny on 2020-06-08
Fixed.
In /var/log/syslog i found many errors about "too many open files". So, I'm increase some values:
```

sudo nano /proc/sys/fs/file-max

```
to 200000

and
```

ulimit -n 161759

```

and all starting normal

---

### Post by Bashing-om on 2020-06-08
darkxbunny - Wow !

Great find

I would have never thunk it :)

[INDENT]just goes to show
[INDENT][INDENT]never can tell
[INDENT][INDENT]'til it is over
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

