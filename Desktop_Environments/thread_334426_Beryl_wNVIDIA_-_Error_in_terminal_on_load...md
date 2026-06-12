---
title: "Beryl w/NVIDIA - Error in terminal on load.."
date: 2007-01-08
forum: Desktop Environments
---

### Post by Kilk on 2007-01-08
Hello,

I just got Beryl all installed and installed the NVIDIA drivers without errors though when I try to load beryl and beryl-manager in the terminal I get the following error-

```
carsen@Carsen-Linux:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
carsen@Carsen-Linux:~$ 
```

And then all the bars on my programs like the box that has the minimize, maximize, and close buttons disappear.. Help?

---

### Post by kd7swh on 2007-01-09
It looks like you don't have GLX installed follow the Nvidia HowTo: in the Beryl Wiki:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

---

### Post by Kilk on 2007-01-09
> **kd7swh said:**
> It looks like you don't have GLX installed follow the Nvidia HowTo: in the Beryl Wiki:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)


I know I already did that, I did that exact tutorial and these are the errors from it above after I try to run beryl and beryl-manager.

---

### Post by jbayone on 2007-01-23
Have you gotten this fixed yet?  I have this same problem.  I didn't add beryl-manager to startup because the last time I tried installing beryl, I couldn't even login.  After I get the message saying "missing glx..." x restarts.

---

