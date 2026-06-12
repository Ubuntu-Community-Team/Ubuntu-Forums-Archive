---
title: "screen resolution"
date: 2006-01-14
forum: General Help
---

### Post by matva on 2006-01-14
hi...
i have a 21" monitor that supports 1600x1200 resolution 75hz refresh rate.

i can't seem to select anything higher than 1024x768 60hz in ubuntu. This is with an mx440, after installing nvidia drivers. Could it be that the mx440 can't do 1600x1200 or is there something else wrong?

---

### Post by professor_chaos on 2006-01-14
and you modified /etc/X11/xorg.conf for appropriate resolutions??

---

### Post by 23meg on 2006-01-14
[QUOTE=professor_chaos]and you modified /etc/X11/xorg.conf for appropriate resolutions??[/QUOTE]
[Here]("http://www.ubuntuforums.org/showthread.php?t=83973") is how you can do that.

---

### Post by zappa86 on 2006-01-14
open up the file by going to a terminal and typing:
```
sudo gedit /etc/X11/xorg.conf
```
sudo=so you can be root user when doing it (the administrator)
gedit=a text editor
lastly is the file
If you scroll down you will see a bunch of resolutions there. look at the pattern and add your desired resolution in there. then you will need to restart x either by doing ctrl+alt+backspace
or by doing:
```
sudo /etc/init.d/gdm restart
```
See if that allows you to get your big resolution. let us know if that works.

---

### Post by handy on 2006-01-14
You should be able to google up the max res of the video card, if there is still trouble after you edit xorg.conf.

---

### Post by djgenesis on 2006-01-14
I found that helpful too, thanks

---

### Post by sroets on 2006-01-14
I have a silmilar problem with my Acer 12 inch notebook
1280*800 resolution is not in my list

but when I look in the file that you mention, the 1280*800 is all over the place
>> how do you get the resolution in the list ???

---

### Post by BathroomNinja on 2006-01-14
[QUOTE=sroets]I have a silmilar problem with my Acer 12 inch notebook
1280*800 resolution is not in my list

but when I look in the file that you mention, the 1280*800 is all over the place
>> how do you get the resolution in the list ???[/QUOTE]


Follow [**THESE INSTRUCTIONS**]("http://www.ubuntuforums.org/showthread.php?t=83973") that 23Meg posted in post#3.  That's how I had to do it a few months back.  They are very detailed.

---

### Post by matva on 2006-01-14
i tried the x autoconfig and now x wont start. How do i revert back to the backup config i made?

---

### Post by matva on 2006-01-15
anyone? I need to restore my old config so that i can use ubuntu again.

---

### Post by handy on 2006-01-16
Try this at the command prompt:

**sudo dpkg-reconfigure xserver-xorg**

---

