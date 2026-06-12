---
title: "screen resolution not right"
date: 2008-02-22
forum: Desktop Effects &amp; Customization
---

### Post by Dillibag on 2008-02-22
When I started my computer the screen resolution was far to high, everything was just tiny. I reset the resolution to 1600x1200 and things were better. After I turned the computer on today,
the ikons and everything was far to big. I tried to set the resolution again and was asked to restart the computer which I did, and now I have just colours and lines and my keyboard which is German has reverted to en. US . How do I get out of that fix?? I am using Ubuntu on my 2nd HDD to write this. Can I work with a command line? and if so what do I write?
Your help here is very much appreciated.
Thank you

---

### Post by justleen on 2008-02-22
normally when ever you change anything in the GUI concerning your resoltution etc. a backup of your old xorg.conf will be made.

- boot your machine
- when at the color garbage pres CTRL-ALT-F2 to go to a terminal
- login with your user
- go to the X11 folder
```
cd /etc/X11
```
check the xorg.conf backups, specially the dates in this case. follow will list the files by date, newest at the bottom
```
ls -ltr 
```
- make a backup of your current xorg.conf
```
sudo cp xorg.conf xorg.conf_backup_notworking
```
- copy one of the older ones (of a date you think it till worked) over the xorg.conf
```
sudo  cp xorg.conf.0 xorg.conf
```
- restart X
```
 sudo /etc/init.d gdm restart
```

check if if works now... if not try another backup.


If this still doenst work, i'd re-setup the X setting by running
```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by Ampi on 2008-02-22
Ok, I'm having sort of the same problem I think, I am not sure so here it is.
When I started with Ubuntu I also put my resolution right. But still when I reboot my computer, it sort of switches between two different resolutions. So it's always a surprise for me what the resolution will be this time.
Can I fix this with the procedure as above?
And another question in order to do this procedure, do I really need to use the ctrl-alt-f2 for the terminal, can't I just open the terminal in the 'normal' way?
Thanks anyway!

---

### Post by Dillibag on 2008-02-22
Thank you (baie dankie) Justleen,
After the initial panic, I settled down and tried different things and found the <sudo dpkg-reconfigure xserver-xorg>, the way to go. After that,  I also did a <sudo gedit /etc/X11/xorg.config>. Which one did the trick I do not know, but when I re-started the computer the screen was here again, albeit with the old monster size. That was easy fixed 
<System><Preferences><Screen resolution> In the drop down window I adjusted to 1600x1200 and then clicked<keep preferences>. To you Ampi: when you get the options on your screen just type a "c" that will give you a command line. Depending on your system you might have to click "Escape" when it shows for a brief moment on your screen. Thanks again, to all the willing helpers at the "Ubuntu Forums" Totsiens

---

### Post by Ampi on 2008-02-23
I.m not still sure if it works. I did delete some xorg.conf that looked like it wasn't the one I wanted. But the command "sudo /etc/init.d gdm restart" didn't work because the command is not recognized as a command. 
How can I fix that?

---

