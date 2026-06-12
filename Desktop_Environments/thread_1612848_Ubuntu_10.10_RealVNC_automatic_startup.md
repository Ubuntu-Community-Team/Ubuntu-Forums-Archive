---
title: "Ubuntu 10.10 RealVNC automatic startup"
date: 2010-11-03
forum: Desktop Environments
---

### Post by Keamas on 2010-11-03
Hi I installed RealVNC Enterprise with the dep file. And It workes so far to start the VNC Server Manually. But now I want that the RealVNC Enterprise Server starts automatically at Startup.
I found this: [http://www.realvnc.com/products/enterprise/4.5/x0.html](http://www.realvnc.com/products/enterprise/4.5/x0.html)
but it is not working. I am a little bit confused with it and that there is no xorg.conf in Ubuntu 10.10.

So I created a file /etc/xorg.conf with the following lines:

```
  Subsection "vnc"
    Option "RSA_Private_Key_File" "/root/.vnc/private.key"
  EndSubSection

```

and so on and it did not work.
Can anyone help me or have some experience with this stuff ?

and after reboot the system comes up in texmode. I delete the /etc/xorg.conf and the system workes normal but without the vnc server

---

### Post by wipper on 2011-08-29
Hi Keamas...

Do you get this to work ???

I am trying to figure it out too....

it seem it should start manually. but for tightvnc there is a help out there...

let me know if you get this working...


Cheers


> **Keamas said:**
> Hi I installed RealVNC Enterprise with the dep file. And It workes so far to start the VNC Server Manually. But now I want that the RealVNC Enterprise Server starts automatically at Startup.
I found this: [http://www.realvnc.com/products/enterprise/4.5/x0.html](http://www.realvnc.com/products/enterprise/4.5/x0.html)
but it is not working. I am a little bit confused with it and that there is no xorg.conf in Ubuntu 10.10.

So I created a file /etc/xorg.conf with the following lines:

```
  Subsection "vnc"
    Option "RSA_Private_Key_File" "/root/.vnc/private.key"
  EndSubSection

```and so on and it did not work.
Can anyone help me or have some experience with this stuff ?

and after reboot the system comes up in texmode. I delete the /etc/xorg.conf and the system workes normal but without the vnc server

---

