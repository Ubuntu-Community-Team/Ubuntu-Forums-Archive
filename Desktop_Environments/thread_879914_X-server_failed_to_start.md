---
title: "X-server failed to start"
date: 2008-08-04
forum: Desktop Environments
---

### Post by Polo82 on 2008-08-04
hi 

i use ubuntu dapper LTS, but there's something wrong with the X-server.
I receive this error:
```

(EE) Failed to load /usr/lib/xord/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)

```

Can anyone help?

thanks in advance

P.

---

### Post by tuxxy on 2008-08-04
This amybe of use,

[http://ubuntuforums.org/showthread.php?t=186468](http://ubuntuforums.org/showthread.php?t=186468)

---

### Post by Polo82 on 2008-08-04
I read the message before, but the solution refers to the nivida driver error not loaded. I haven't this error. 
Anyway I have intel graphical card.

Any solution?

thanks

P.

---

### Post by tuxxy on 2008-08-04
COuld be your video card drivers...did you make any changes to them recently?

If you cannot boot into GNOME you could try reconfigure xorg

```
sudo dpkg-reconfigure xserver-xorg
``` 

and change the video drivers back

---

### Post by Polo82 on 2008-08-04
the xorg configuration is right becouse i used it for another ubuntu installation in a new partition.

I'm looking for install again video driver but i'n not able to do that. 
I use an intel and driver should be i810.
 how i can install again it?

thanks
P.

---

### Post by tuxxy on 2008-08-04
Is it listed in system > admin > hardware drivers

---

### Post by Polo82 on 2008-08-04
But i can't open the display manager.

i've tried to do

```

apt-get install xserver-xorg-video-i810

```
but doesn't work.
i'd like to find a way to install the intel driver i810.

thx

P.

---

