---
title: "fedora 9 X server problem"
date: 2008-06-17
forum: Fedora/RedHat and derivatives
---

### Post by shawnansasio on 2008-06-17
Okay, So I just upgraded my dual boot system from windows 2000 to vista and FC6 to F9.

Windows works very good so does grub.  But when I boot into fedora the X server won't start!!

Please,

HELP ME!!!!!

---

### Post by John.Michael.Kane on 2008-06-17
More info is required.

What video card is in the system in question?

What is the error Xorg reports upon final boot?

Are there any other errors reported during the booting phase?

---

### Post by shawnansasio on 2008-06-17
My Graphics card is an Intel Extreme Graphics2 3D

And when i boot up i get:

Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.
 Would you like to view the server output to diagnose the problem?

(Tell me if if you need that)


And there are no problems booting up except, that it boots up like an old version of linux not in that gui thing.

---

### Post by John.Michael.Kane on 2008-06-17
If I remember correctly, nearly all Intel Graphic chips work without issue.

What you can try doing is reseting your xorg.conf.

After booting, and receiving the error etc, you should be drop at a command prompt. Being you are running fedora you would have to su - to get full root privileges.

Next you can try editing the xorg file to use vesa, if it is not using it already, and see, if this allows you to reach a login screen.
```
nano /etc/X11/xorg.conf
```

The other option is trying to reset xorg trying one of the below commands.

```
system-config-display --reconfig --noui && reboot
```

```
/usr/bin/system-config-display --reconfig
```

```
system-config-display --reconfig
```

Note: If you are not drop to a command prompt you can access tty 1 or tty 2 with ALT+F and the number of your choosing. This will leave you at a terminal prompt.

Hope this helps.

---

### Post by shawnansasio on 2008-06-18
F.Y.I i read the server output and it said something like no divice found.

ps. I am at work so i will try your advice when i get home.

---

### Post by shawnansasio on 2008-06-18
Sorry but when i try all the commands i end up with the same error:

Traceback (most recent call list):
File "/usr/share/system-config-display/xconf.py" ,  Line 32, in <module>
  import rhpxl.monitor
ImportError: No module named rhpxl.monitor

PLEASE HELP!!!!!!!!


Ps. my driver was vesa.

---

### Post by Kingsley on 2008-06-19
This could be a bug that's been fixed since the release of Fedora 9. Try doing an upgrade (as root) and restart you computer.

```
yum -y upgrade
```

---

### Post by shawnansasio on 2008-06-19
Thanks it works but now the only resolutions that i can switch between are:

1024 x 768 , 800 x 600 , 640 x 480.

Please help!!

---

### Post by djhyland on 2008-06-26
If you're still using the vesa drivers, I imagine you might try switching your driver to one of the intel ones and see if that fixes your resolution issue.  I'm not sure which one your card requires, but System->Admin->Display Settings->Hardware has like six intel drivers in its list.  I'm sure with some research you can find which one corresponds to your card.  Good luck!

---

### Post by igknighted on 2008-06-27
Fedora 9 shouldn't be using an xorg.conf (for any real configuration at least)

Have you tried the fedora forums?  Dollars to donuts you will get better answers there...

---

### Post by shawnansasio on 2008-07-01
YAY!!! It works like a charm!!!!!

Thanks

________________________________________

I am 9 years old!!!!

---

