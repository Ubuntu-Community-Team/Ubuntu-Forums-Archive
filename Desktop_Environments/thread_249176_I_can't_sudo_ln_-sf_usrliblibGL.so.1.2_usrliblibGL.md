---
title: "I can't sudo ln -sf /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1"
date: 2006-09-02
forum: Desktop Environments
---

### Post by lukew on 2006-09-02
Hi,

I have been trying to install ATI drivers with GL support from [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide). Everything went ok (3d desktop worked etc and fglrxinfo reported everything was ok) though xmess.x11 repoted that libGL could not be opened. I downloaded the file which they stated to download. I backed up the copy before copying over the new file.

My problem is, as you can see the symlink to the backjup file is present on 
libGL.so.1 which needs to go into the new file i copied over.

I have run the commands below, which seem to work, reboot but on restart the symlink remains to my .old file.

I am using the -f command to force it and running as sudo.

Thanks in advanced for anyone who can help me with this one.

Luke


foomin@foobuntu:~$ sudo ldconfig -v|grep GL
ldconfig: Can't open configuration file /etc/ld.so.conf: No such file or directory
ldconfig: Can't stat /lib64: No such file or directory
ldconfig: Can't stat /usr/lib64: No such file or directory
        libGLEW.so.1.3 -> libGLEW.so.1.3.1
        libGLU.so.1 -> libGLU.so.1.3.060401
        libGL.so.1 -> libGL.so.1.2.old
foomin@foobuntu:~$ sudo ln -sf /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1
foomin@foobuntu:~$ sudo ldconfig -v|grep GL
ldconfig: Can't open configuration file /etc/ld.so.conf: No such file or directory
ldconfig: Can't stat /lib64: No such file or directory
ldconfig: Can't stat /usr/lib64: No such file or directory
        libGLEW.so.1.3 -> libGLEW.so.1.3.1
        libGLU.so.1 -> libGLU.so.1.3.060401
        libGL.so.1 -> libGL.so.1.2.old (changed)
foomin@foobuntu:~$

---

### Post by lukew on 2006-09-02
Hi,

Not to worry I deleted both files and then recreated the link again. Everything is hunky-dory and fglrxinfo reports that everything is working fine, including after a restart.

Thanks

Luke

---

