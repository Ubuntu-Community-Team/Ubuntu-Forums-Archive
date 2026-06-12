---
title: "Graphics Card/Driver Issue"
date: 2010-01-20
forum: Desktop Environments
---

### Post by FuzzWig on 2010-01-20
Hi, my ubuntu has just recently started to mess up in the graphics department.
Basically what happened was i tried to edit my xorg.conf so i could have 1280x1024 resolution which used to work fine and suddenly stopped then it turned out i couldn't edit it, eventually i fixed that with sudo gedit (i'm a noob btw) and after i saved it and rebooted my PC into ubuntu it forced me into low graphics mode because when i tried normal mode it went stange as if not all the screen will fit.
I have the reccommended nvidia drivers (185) and i'm using a GeForce 9500 gt.
It's very strange, it only started doing it today and it was working fine at the settings i wanted it at before
Any help would be highly appreciated.

---

### Post by M1GEO on 2010-01-20
try running
```
sudo nvidia-settings
```

Under the "X Server Display Configuration" section, you can graphically setup your displays, and then you have an option to write the xorg.conf file ("Save to X Configuration File").

Hope this Helped :)

---

### Post by FuzzWig on 2010-01-22
> **Compu-king said:**
> try running
```
sudo nvidia-settings
```Under the "X Server Display Configuration" section, you can graphically setup your displays, and then you have an option to write the xorg.conf file ("Save to X Configuration File").

Hope this Helped :)

No, unfortunatly it didn't, it said unable to parse xorg.conf or something along those lines

---

### Post by realzippy on 2010-01-22
..this parser error occurs when xorg.conf is not created by nvidia-settings.
Simply delete current file (no need to backup due to nvidia -) )

**sudo rm /etc/X11/xorg.conf**

Then make a new one:

**sudo nvidia-xconfig**

Now you can run

**gksudo nvidia-settings**,no more parser error....

---

### Post by FuzzWig on 2010-01-22
> **realzippy said:**
> ..this parser error occurs when xorg.conf is not created by nvidia-settings.
Simply delete current file (no need to backup due to nvidia -) )

**sudo rm /etc/X11/xorg.conf**

Then make a new one:

**sudo nvidia-xconfig**

Now you can run

**gksudo nvidia-settings**,no more parser error....

Well, it won't let me delete it for some reason, the delete button is greyed out.
Thanks for the help so far.

---

### Post by FuzzWig on 2010-01-22
Oh, nvm i didn't see the command in your post

Ah, now it says this:
But it doesn't appear to work when I do as it says
[IMG]http://img145.imageshack.us/img145/5519/hmmstrange.png[/IMG]

---

### Post by FuzzWig on 2010-01-22
Aha, i fixed it, i only needed to reboot my pc, thanks for the help!

---

### Post by FuzzWig on 2010-01-24
Ok, well now I have a slightly less urgent problem which is that every time I log on i have to change the resolution from 1024x768 back up to 1280x1024 again even after saving to x file.

---

### Post by realzippy on 2010-01-24
did you hit "apply" and "save to X configuration file" when running:

**gksudo nvidia-settings**

If so,post your xorg.conf file...


**gedit /etc/X11/xorg.conf**

---

### Post by mhgsys on 2010-01-24
@realzippy. 
Even if the xorg.conf is configured correctly; this problem will actually still appear.

@realzippy and @FuzzWig;

yep ;' I know that Problem../// And here's the solution,

 try setting it with :
System > Preferences > Display.

If you get;
It appears that your graphics driver does not support the necessary extensions to use this tool. Do you want to use your graphics driver vendor's tool instead?

Just click NO, and set the resolution.

I don't know why exactly, but it works for my GeForce4 Ti 4200.
Everytime I used nvidia-settings (even as root and saving the file to xorg.conf) my resolution kept changing back to 800 x 600 as well.
This way it keeps my display 1280x1024 all the time.

I even have this topic right here; 

[http://ubuntuforums.org/showthread.php?t=1192754](http://ubuntuforums.org/showthread.php?t=1192754)

:D

---

### Post by FuzzWig on 2010-01-24
Thank you! This appears to have fixed my problem.
Thanks for all the help everyone.

---

### Post by mhgsys on 2010-01-24
Your welcome, 

Please mark your thread as solved.

(it's under thread tools)

---

