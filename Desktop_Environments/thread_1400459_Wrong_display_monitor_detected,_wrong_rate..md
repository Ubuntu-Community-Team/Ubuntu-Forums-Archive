---
title: "Wrong display monitor detected, wrong rate."
date: 2010-02-06
forum: Desktop Environments
---

### Post by Locaj on 2010-02-06
Hi.

Got Ubuntu 9.10 for 2 days now.

Got problem with my monitor. When I go to System > Preferences > Display it shows Eizo 19" (crt). I got Eizo 21".

Second thing is I cant set refresh rate. I can choose between 75 and 85 only. I need to set it to 100Hz.

How do I change my monitor as device? How do I force refresh rate?

Thanks.

/edit: Is there some advanced display settings application?

---

### Post by warp99 on 2010-02-06
You monitor is giving the wrong EDID information. Which display drivers are you using, IE: Nvidia, ATI, or open source version?

---

### Post by Locaj on 2010-02-06
I got Radeon x800xl and I use open source coz ati drivers dont work for my card in 9.10.

---

### Post by warp99 on 2010-02-07
Since you using the open source drivers you can use xrandr to test and change for non-detected resolutions and refresh rates:

[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions)

To keep the changes persistent I suggest that you use the .xprofile method since it's the easiest to set up. If you feel comfortable editing the xorg.conf file use that method instead replacing the example information with yours.

Edit: There are some GUI packages such as gnome-randr-applet, arandr, or grandr but if you don't need to change the resolution frequently then an .xprofile file is most likely the way to go.

---

### Post by Locaj on 2010-02-07
Thanks for reply.
```
:~$ xrandr --newmode "1280x1024_100.00"  189.50  1280 1376 1512 1744  1024 1027 1034 1087 -hsync +vsync
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  23
  Current serial number in output stream:  23
```I used cvt to get info about 1280x1024 and put as it was shown on wiki u posted. First time i run command it just ran and nothing happened. I cant set to 100hz. This error message i got when i tried to run the command again.

Thanks !

/edit: I cant find .xprofile in my /Home/[me]/ folder

---

### Post by warp99 on 2010-02-07
The first time you run it looks like nothing happened, but the screen will flicker and if you run the command "xrandr" by itself you'll see the modeline was added. You need to then associate the mode to the display and switch to that mode with some commands like this:

```
:~$xrandr --addmode VGA 1280x1024_100.00

:~$xrandr --output VGA --mode 1280x1024_100.00
```

Of course the addmode and output is whatever output your monitor is listed under xrandr. Also you need to create the .xprofile file in your home directory and make it executable. So something like this should work:

First create the file:
```
:~$gedit ~/.xprofile
```

Add your working commands to the file and save:
```
xrandr --newmode "1280x1024_100.00"  189.50  1280 1376 1512 1744  1024 1027 1034 1087 -hsync +vsync
xrandr --addmode VGA 1280x1024_100.00
xrandr --output VGA --mode 1280x1024_100.00
```

Make the file executable:
```
chmod +x ~/.xprofile
```

If you're still having problems you can download one of the GUI programs I mentioned and try those instead.

---

### Post by Locaj on 2010-02-07
Thanks ! ! !

Thank you so much. I got 100Hz now. Just need to make it to be forever =-D



[IMG]http://http://img94.imageshack.us/img94/4536/xrandr.png[/IMG]

---

### Post by warp99 on 2010-02-07
That should be "xrandr --addmode VGA-0 1280x1024_100.00" and not "1280_1024_100.00". I checked my previous post and noticed I made this error. Sorry about that. I'll change it right away. 

Once you change this on your end everything should be OK.

---

### Post by warp99 on 2010-02-07
> **Locaj said:**
> Thanks ! ! !

Thank you so much. I got 100Hz now. Just need to make it to be forever =-D

Glad I could help. If you could please mark the thread as "solved" by going into Thread Tools and clicking that option. Thanks!!

---

### Post by jenaniston on 2010-02-07
> **Locaj said:**
> Hi.
. . .
Second thing is I cant set refresh rate. I can choose between 75 and 85 only. I need to set it to 100Hz.

. . . How do I **force refresh rate**?

Is there some advanced display settings application?

Although I am waiting for Xubuntu live iso to try lighter weight Xfce desktop . . .
all I ***may*** need for gnome desktop is to reset refresh rate from the recovery mode root terminal -[I]
 maybe[/I] more X config though too.

Gnome desktop lasts about 1 minute before freezing up . . . the refresh rate can ***not*** be set by
 System > Preferences > Display (Refresh rate has even said **0 Hz** with no other choices).

Very good to know for my troubleshooting -
Thanks for the thread and reply with a possibly valuable lead about forcing a refresh rate with **xrandr**.

---

