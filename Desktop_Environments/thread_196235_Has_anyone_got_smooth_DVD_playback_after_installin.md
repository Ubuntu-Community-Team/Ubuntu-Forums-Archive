---
title: "Has anyone got smooth DVD playback after installing XGL/Compiz?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by kpkeerthi on 2006-06-13
Mine is jerky (mostly tearing) after installing xgl/compiz. Anyone managed to get DVD playback as normal as it can be without xgl/compiz? Please point me to instructions. Thanks.

---

### Post by DarthMandeep on 2006-06-14
Video works fine here, once I used the right settings. If you're using the default Ubuntu install with Gnome, you'll need to add options to the XGL line in your GDM.conf file.

The old XGL thread has it: [http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+video](http://ubuntuforums.org/showthread.php?t=131267&highlight=xgl+video)

It looks like this:
[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true

If you happen to be using the symlink method to start XGL the old school way by typing startx at the command line then this might be of use:
[http://www.ubuntuforums.org/showthread.php?t=185020](http://www.ubuntuforums.org/showthread.php?t=185020)

---

### Post by kpkeerthi on 2006-06-14
I followed the instructions from [http://www.ubuntuforums.org/showthread.php?t=148351](http://www.ubuntuforums.org/showthread.php?t=148351) and differences are like night and day.

---

