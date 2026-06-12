---
title: "A perfect Beryl (XGL) instalation stopped working without toutching anything"
date: 2006-10-16
forum: Desktop Environments
---

### Post by Moralez on 2006-10-16
I installed Beryl with ease, configured my ATI mobility x300 using fglrx "default" drivers (and they are still working, I checked fglrxinfo) and all was in peace.

Perfect performance and theme, did some test reboots... still 100% perfect.

And then... taram!I went to sleep, woke up, booted Ubuntu and BAM! No more XGL... I redid all the steps, nothing... I don't get it. what happened?

Did some1 had the same problem? A perfect instalation of Beryl that simply stopped working?

Thanks for all the help.

**Edit:**a simple "rm .beryl-managerrc" did the trick... 5 times Oo

There is something wrong with that file... it's not the config file, all my settings are working perfectly, what did I do wrong in order for that file to mess Beryl boot? huh... oh well... I guess I'll make a script to make that commang everytime I start a new session... (it works1).

---

### Post by zeekay on 2007-06-29
I got a similar issue. My OpenGL just simply got disabled or stopped working. Simple as that.

I don't have a clue on how did it happened, or why... but it did... :(
I tried to put the default xorg.conf that nvidia-settings creates, but it didn't got fixed.

_**Edit:**_
Finally, I got it working again. The REAL issue I suspect that were the update of those "linux restricted modules". The NVidia driver I had would not work under it. So, the solution was rather simple:
```
sudo apt-get install nvidia-glx-new
```

Everything's back on track. :)

---

### Post by Do0odz on 2007-07-06
I think I have the same problem .. Beryl stopped working .. it as working for 2 days I guess and then nothing :(.. 

I don't know whats wrong ..
I believe this is my vcard .. VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

can anyone help ?

---

### Post by M3edly on 2007-09-23
I have had the same problem, and like everyone has been saying, I believe it to be related to some time of update that Ubuntu is doing. Beryl will load, but will do nothing other than sit in the system tray (no pluggin, or opengl working) I can't seem to get it fixed, and have reformatted twice and have had the same problem happen.  If anyone knows how to fix this on an ATI 9600 please let me know.

---

