---
title: "Razer Deathadder Mouse"
date: 2014-10-17
forum: Gaming &amp; Leisure
---

### Post by kyoopid on 2014-10-17
I owned a razor deathadder mouse and was using the Razer  device configuration tool to run it (v0.21) found here ([http://bues.ch/cms/hacking/razercfg.html](http://bues.ch/cms/hacking/razercfg.html)). 

I bought a new razer  deathadder 2013 version and discovered v0.21 does not support the  deathadder 2013 version. So i downloaded the latest version (0.30) and i  went through the setup process in the README. Everything installed ok  (i think) but when i went to run qrazercfg i get this error....

qrazercfg
Traceback (most recent call last):
  File "/usr/local/bin/qrazercfg", line 20, in <module>
    from pyrazer import *
  File "/usr/local/bin/pyrazer.py", line 60
    except (ValueError), e:
                       ^
SyntaxError: invalid syntax

kyoopid@kyoopid:~$ razerd
Razer device service daemon
librazer: No config file /etc/razer.conf present. Ignoring.
Failed to bind socket to /var/run/razerd/socket: Address already in use


When  i was running version 0.21 all i had to do was type qrazercfg and it  would load the GUI, but now it doesn't and i get this error. What am i  doing wrong? Please keep in mind i am a linux noob. Do i have to  uninstall the old version? If so how?

Or if somoene could give me a command step by step process to follow how to fix this error, would be appreciated.

---

### Post by R33D3M33R on 2014-10-18
Open /usr/local/bin/pyrazer.py in text editor and find line with RAZER_VERSION, what does it say?

---

### Post by kyoopid on 2014-10-18
RAZER_VERSION    = "0.21" i dont understand why this is. i have installed 0.30

---

### Post by R33D3M33R on 2014-10-18
I suggest that you run uninstall.sh first on version 0.30 which you installed now, and then download 0.21 and run uninstall.sh from that version. After all is removed, reinstall 0.30.

---

### Post by kyoopid on 2014-10-18
there was no uninstall with v0.21 and the uninstall for v0.30 seems to do nothing

---

### Post by R33D3M33R on 2014-10-18
You should read the readme. You must give the script the install path and probably run it with sudo.

---

### Post by kyoopid on 2014-10-18
i got it to work, dont know how. i deleted the /var/run/razerd/socket aND it seemed to work

---

### Post by dannyboy79 on 2014-10-18
that just means the old socket was still around from when you were running the older version. smart thinking to delete it and try again, it's not advisable to normally just delete a pid file but in this case since it's just mouse software it's no big deal.

---

