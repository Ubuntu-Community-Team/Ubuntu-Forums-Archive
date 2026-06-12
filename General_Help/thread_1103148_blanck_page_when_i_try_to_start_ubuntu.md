---
title: "blanck page when i try to start ubuntu"
date: 2009-03-22
forum: General Help
---

### Post by urd on 2009-03-22
hi, today i try to start my and first he answer mi user and password in a blank page(the login image doesn't appear), so i put mi user a pass but the system  doesn't change and in the same page try to open but apears that the system can't start and open a text, just like the console 

what can i do?? i try to start in recovering mode i think, i check everithing, and try to fix dpkg for that way, but ubuntu doesn't start :S

the huge problem is that i have really important information on mi ubuntu sesion whitout copy in sticky notes and text files

i also try 
```
sudo apt-get install -- reinstall ubuntu desktop
```


but the code doesn't work for any reason :S ... i don't know what to do for start my ubuntu and don't lose that important information :S 

thanks

by the way, i have a toshiba a2 series, with 2gb ram, ati x1200, 50 gb on disk for ubuntu, and turionx2 of 1.9 ghz each one :S

edit:
 i try 
```
startx
```

but the code doesn't start the OS ... looks like the problem is a video card drivers what can i do?

---

### Post by NT4usB on 2009-03-22
Can you Ctrl+Alt+F1 to a terminal?
Try:```
dmesg | less
``` and page down through it. See if anything jumps out at you as might be a problem. Also:```
 cat /var/log/Xorg.0.log | less
``` and look down that. Otherwise:```
sudo /etc/init.d/gdm restart
``` If that doesn't work, rebuild the x:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
If that doesn't work, try it without the -phigh. Step through and change the video driver to vesa. or if you're handy with vi or other non graphical editor, you can also edit xorg.conf:```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.bkup
sudo vi xorg.conf
``` under device, (add or) change the driver to vesa```
Section "Device"
        Driver          "vesa"
EndSection
```

If that goes completely wrong, cp your bkup to xorg.conf to put it back the way it was.

---

