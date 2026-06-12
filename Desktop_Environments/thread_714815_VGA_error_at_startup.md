---
title: "VGA error at startup"
date: 2008-03-04
forum: Desktop Environments
---

### Post by jze_Dz on 2008-03-04
hi, i'm totally new to the linux environment.

the following problem occur.

I've sucessfully installed ubuntu on my duron 1.2 ghz. I installed with a normal monitor. then shifting to my 15" tft monitor i get this error at startup. Vga error. then i run the system from cd, in safe graphics mode and i get to the ubuntu desktop and all. it works fine. but without the installer cd, i can't get any graphics on the tft monitor. What should i do? Thanks in advance

---

### Post by taurus on 2008-03-04
You just need to reconfigure your X server again when you switch from one monitor to a difference monitor.

Boot into recovery mode from GRUB menu and run

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
dpkg-reconfigure -phigh xserver-xorg
shutdown -r now
```

---

### Post by jze_Dz on 2008-03-06
hi,

i've tried your method, typed everything in. but upon starting up again, the error still appears.

Vga mode error.

what else can i try?

thanks

---

### Post by taurus on 2008-03-06
You can either run that command again from a recovery mode except without the -phigh option.

```
dpkg-reconfigure xserver-xorg
```

Or you can boot with the LiveCD, mount the partition where / is, and then copy /etc/X11/xorg.conf from the LiveCD over to your harddrive. 

Which partition is your /?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jze_Dz on 2008-03-06
hi

i have also tried without the phigh option. this leads me to many different windows where i just enter along. it even 'detects' my vga. sometimes i can't enter but hit esc to carry on. starting from the livecd works fine.

i've got 3 partition, winxp, ubuntu and d drive. i think ubuntu is on e drive, because it doesn't pops up when i run winXP.

can you please write me the llines that i have to type in terminal. 

thanks!

p.s. i don't want to also reinstall ubuntu as i've downloaded some programms through internet. where the computer is, there's no internet.

---

### Post by taurus on 2008-03-06
I need to know which partition / is.  Drive e doesn't mean a thing in Linux.  So, run this command from the LiveCD and post the output here and I or somebody else will walk you through it.

Applications -> Accessories -> Terminal
```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```
That is a lower case letter L.

---

### Post by jze_Dz on 2008-03-06
ok will do. write again tomorrow.

---

