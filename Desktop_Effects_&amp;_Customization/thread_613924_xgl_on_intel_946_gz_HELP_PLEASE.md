---
title: "xgl on intel 946 gz HELP PLEASE"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by akshaysub18 on 2007-11-15
I don't get even NORMAL effects on my Ubuntu 7.10 .ALL what comes is "Desktop effects could not be enabled." .Why is it so ?? When i try out compiz , i get:

Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

Where do i get the required drivers ,,, or am i "blacklisted" ?? is it compatible with integrated drivers ?? 
Somebody help me please ....

---

### Post by bingoUV on 2007-11-15
Try this [http://ubuntuforums.org/showthread.php?t=594605](http://ubuntuforums.org/showthread.php?t=594605)

---

### Post by Jiks on 2007-11-15
Same Porblem with me .... please help ... :( .... no desktop effects at all !!! ..... all i get is "desktop effects could not be enabled" .... i am on Core 2 duo, 1 GB RAM, on 946GZ board, and my monitor is SyncMaster 740n [i mentioned it as, i cant get 1280x 1024 @ 75 Hz !!! so i am on a lower resolution as it flckers in higher resolutions ]

---

### Post by bingoUV on 2007-11-16
> **Jiks said:**
> Same Porblem with me .... please help ... :( .... no desktop effects at all !!! ..... all i get is "desktop effects could not be enabled" .... i am on Core 2 duo, 1 GB RAM, on 946GZ board, and my monitor is SyncMaster 740n [i mentioned it as, i cant get 1280x 1024 @ 75 Hz !!! so i am on a lower resolution as it flckers in higher resolutions ]

did you try this [http://ubuntuforums.org/showthread.php?t=594605](http://ubuntuforums.org/showthread.php?t=594605) ?

---

### Post by akshaysub18 on 2007-11-16
Yes i tried that ...i have installed that xserver-xgl thru synaptic, . .  but still desktop effects cant be enabled ... and i cant find the compiz folder you told in the code : no directory exists as such . . what do i do next ..??   [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)  [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by bingoUV on 2007-11-16
> **akshaysub18 said:**
> Yes i tried that ...i have installed that xserver-xgl thru synaptic, . .  but still desktop effects cant be enabled ... and i cant find the compiz folder you told in the code : no directory exists as such . . what do i do next ..??   [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)  [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

I was asking Jiks whether or not he tried it, but anyway.

Create the folder if it does not exist. For me, the file did not exist but the folder did. I am not sure if it will work. It worked for me in G965, whereas you have 946. But the problem was so strikingly similar to mine that I thought it might just work. 

Also, uninstall xgl if it does not help.

---

### Post by akshaysub18 on 2007-11-22
Thank you people  . . . and i migrated to fedora .... it's way cooler  . . . try it

---

