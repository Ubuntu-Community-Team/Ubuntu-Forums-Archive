---
title: "WMD (Wiimote for Linux) Help"
date: 2007-08-24
forum: Desktop Environments
---

### Post by nystud162 on 2007-08-24
I have followed all the instructions from the original WMD website and from the wiili wiki:

[http://www.wiili.org/index.php/WMD](http://www.wiili.org/index.php/WMD)

Whenever I run ```
sudo python WMD.py
```

i get 
```
root@evan-laptop:/home/evan/Desktop/wmd-0.1.2# python WMD.py
Traceback (most recent call last):
  File "WMD.py", line 15, in <module>
    from wmd.Config import CFG
  File "/home/evan/Desktop/wmd-0.1.2/wmd/Config.py", line 38
    'UINPUT_DEV: "/dev/input/uinput",  ##ubuntu - you need to modprobe uinput first
                                                                                  ^
SyntaxError: EOL while scanning single-quoted string

```


Anyone? I feel like I've tried everything.

---

### Post by christhemonkey on 2007-08-24
Have you done what it says?
```
sudo modprobe uinput 
```

Also, you should edit that file and add a ' to the end of that line. Then this error will not happen.

---

### Post by jdfreshwater on 2007-10-15
Try these instructions found for adding WMD.  I had used this before and it should help.

> Make sure that the uinput module is loaded on system startup and your mythtv user has read access to the created device /dev/input/uinput. I added the following lines to /etc/rc.local

 modprobe uinput
 chmod a+r /dev/input/uinput

found at

[http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote]("http://www.mythtv.org/wiki/index.php/Controlling_MythTV_using_a_Wii_remote")

hope this helps.

---

