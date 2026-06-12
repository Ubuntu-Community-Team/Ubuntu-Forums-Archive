---
title: "Using arandr for dual monitors, how do I make changes persistent?"
date: 2013-01-27
forum: Desktop Environments
---

### Post by sambarnett on 2013-01-27
I want my monitors to be extended onto each other, not mirrored.  By default it always mirrors them and then I have to go into arandr to set them to be extended.  How can I make this change permanent?

I'm using Xubuntu 12.10.

Thanks,
Sam

---

### Post by Elfy on 2013-01-27
set it up in arandr

save the file - should then be there in .screenlayout/whateveryoucallthefile

add that to startup applications, you might need to type the path in there - from memory searching doesn't see hidden files

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=230702&d=1359307780[/IMG]

---

### Post by sambarnett on 2013-01-28
I tried this but it did not work.  Any other suggestions?

---

### Post by Elfy on 2013-01-29
How about some idea of what didn't work?

---

### Post by sambarnett on 2013-01-29
When I log or reboot the monitors still mirror each other.  I then have to still manually separate then monitors in arandr each time I start up in order to use extended screens.

---

### Post by Elfy on 2013-01-29
Couple of things to check 

is the script in .screenlayouts set to run in Startup apps in system settings

is the script allowed to run - check it's permissions, right click on the file in thunar - permissions tab - you might need to ctrl+h to see hidden files

---

### Post by sambarnett on 2013-01-29
Yes, the script is set to run.

What do the permissions need to be in order for it to run?

---

### Post by Elfy on 2013-01-30
You can either set it to Allow to run in thunar or with a terminal

chmod +x /path/to/the/script

For me, from my terminal that's

```
chmod -x .screenlayout/good.sh
```

Make sure that it is called from autostart

```
ls /home/yourusername/.config/autostart
```

You should see the name of the item you've called this there.

Mine is called screens

```
ls /home/hob/.config/autostart
blueman.desktop               devilspie.desktop     screens.desktop
broken windows again.desktop  print-applet.desktop  xscreensaver.desktop
```

---

### Post by sambarnett on 2013-01-30
It was already set as "allowed to run" and it still doesn't work.

---

### Post by Elfy on 2013-01-30
Can you open a terminal and then run this please

```
ls .screenlayout/ && ls .config/autostart/
```

paste the complete output.

---

### Post by sambarnett on 2013-01-30
sbarnett@sbarnett-Satellite-L755:~$ ls .screenlayout/ && ls .config/autostart/
default.sh
AF4C043927B5E6AC71FCF2B33F18A482A1AF95D5.chromium-service.desktop
blueman.desktop
dropbox.desktop
Screen.desktop
xfce4-settings-helper-autostart.desktop
sbarnett@sbarnett-Satellite-L755:~$

---

### Post by Elfy on 2013-01-30
Ok - now 

```
cat .config/autostart/Screen.desktop && cat .screenlayout/default.sh
```

Let's make sure the files look like they should. 

It all 'looks' right as far as files being where they should.

You can also see if the script is working from a terminal

```
./.screenlayout/default.sh
```

One other thing - what graphics card are you using and driver for it. 

I used to use nvidia driver with a card - had to set it up with nvidia-settings in that case.

---

### Post by sambarnett on 2013-01-31
sbarnett@sbarnett-Satellite-L755:~$ cat .config/autostart/Screen.desktop && cat .screenlayout/default.sh
[Desktop Entry]
Encoding=UTF-8
Version=0.9.4
Type=Application
Name=Screen
Comment=
Exec=/home/sbarnett/.screenlayout/default.sh
OnlyShowIn=XFCE;
StartupNotify=false
Terminal=false
Hidden=false

#!/bin/sh
xrandr --output HDMI1 --off --output LVDS1 --mode 1366x768 --pos 0x0 --rotate normal --output DP1 --off --output VGA1 --mode 1360x768 --pos 1366x0 --rotate normal
sbarnett@sbarnett-Satellite-L755:~$ 


-------

I don't know what video card I'm using.  It's a Toshiba laptop.

---

### Post by sambarnett on 2013-01-31
By the way I checked and it DOES work from a terminal.

---

### Post by Elfy on 2013-02-02
Moved to Desktop Environments

Not sure what's going wrong to be honest, all seems ok to me - especially if running the script from a terminal does the job.

Moved it here to get some different people looking.

---

### Post by Toz on 2013-02-02
> Exec=/home/sbarnett/.screenlayout/default.sh
Does this file exist and is it executable?

---

### Post by sambarnett on 2013-04-13
Yes that file exists.  As a matter of fact I can even make a shortcut to that on the desktop and click on it right after I boot up and it will immediately change the screen settings to the correct settings.

Any other ideas?

---

### Post by cinq on 2013-05-21
I solved it (it worked for me at least)!
that's my script
```
#!/bin/bash
sleep 5

sh ./startdual.sh 
exit
```

***startdual.sh*** is the saved configuration copy-pasted on m home folder and excecutable.

---

