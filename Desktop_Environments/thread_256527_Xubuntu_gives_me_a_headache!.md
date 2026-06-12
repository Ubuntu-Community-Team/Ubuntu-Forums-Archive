---
title: "Xubuntu gives me a headache!"
date: 2006-09-13
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-13
After using Ubuntu for two years and being... quite happy with it, I switched to Xubuntu for several reasons, and all of a sudden nothing really works. Is it just that I have become a computer-bourgeoise, or are the default configurations in Xubuntu *actually *designed to make a person commit suicide?

Well... after having that out of my system.

Here's what I got now: I'm trying to mount (and if possible automount) my USB port to which I want to connect both different USB sticks and a Canon camera. Made me feel retarded. Here's how my fstab looks:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hds	/media/USB	auto	rw,user		0	0
```

What's wrong?
](*,) 
Gabriel

---

### Post by orb9220 on 2006-09-13
Try this link as my understanding usb devices do not require fstab entries and are handled automatically.

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

---

### Post by GabrielWolff on 2006-09-13
Hey thanx for that reply, but the link you referred my to look slike I gotta study math for it. How about something as easy as: ```
sudo apt-get install some-darn-application-that-autoconfigures-automount-for-all-my-ports
```???

In Ubuntu it was so easy.

Gabriel

P.S.: Normally I'm a bit more enthusiastic to learn, right now I just wanna have it done. In Ubuntu it just came along with the OS installation (I think...)

---

### Post by carontis on 2006-09-13
You should know you can use also Ubuntu's application if needed, 'cause Xubuntu is the same to Ubuntu, and the only change is the GUI, so if you have installed Synaptic, try to input an Ubuntu's CD and let add all to it, after this you will be able to install all you want / need. Xubuntu is used on old time machine, but the base system is Ubuntu (Debian).

---

### Post by Psquared on 2006-09-13
Just click Settings > Sessions and Startup Settings > Advanced and click "use Ubuntu-Gnome applications" (says something like that) and it will make those apps available to you. Or, you can just download and install them. I don't like mixing QT and GTK, but Xubuntu uses GTK so you are Ok with those.

---

