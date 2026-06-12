---
title: "How to disable boot to gnome?"
date: 2007-02-06
forum: Desktop Environments
---

### Post by explorer1979 on 2007-02-06
Hi all,

I am using Server version, and installed the GNOME, but after reboot the system, it is auto come to the GNOME login screen.

I want to back to the command line login screen, and want I need GNOME, then press startx to go to the GNOME,

How to do like it in 6.10 Server version?

Thank you.

---

### Post by taurus on 2007-02-06
```
sudo aptitude remove gdm
```

---

### Post by teckfatt on 2007-03-01
how to do it on ubuntu 6.10 desktop version??

i have tried 
```
sudo aptitude remove gdm
```

after i reboot it automatic reinstall the gdm

---

### Post by AlcoJaguar on 2007-03-01
Or you could use:
```
sudo apt-get remove gdm
```

---

### Post by teckfatt on 2007-03-11
I have found an alternative to disable to boot gnome on startup.

System -> Administration -> Services -> unclick the Graphical Logic Manager (gdm)

---

