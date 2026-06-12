---
title: "Borked install trying to fix flash-no-audio issue"
date: 2009-05-06
forum: General Help
---

### Post by kulturloseramerikaner on 2009-05-06
I got a friend of mine set up with Kubuntu 9.04 this weekend, and we got everything running smooth except for the audio in Flash.  I went over yesterday to try to get that squared away and started running through a how-to for Ubuntu.  I didn't realize that it was specific to Ubuntu only because of PulseAudio. I installed all pulse packages, and after realizing it not only didn't fix the issue but caused problems in K after additional research, I uninstalled the packages with apt.  
Today he tried to fire it up, and couldn't launch X; after the bootup progress bar it dropped right into the command line with "enter login."  How should I get started sorting this one out please?  I'm not sure where to get started on this one, and I don't like eggs so having them on my face is pretty annoying, especially since I've been working on him for quite a while to give 'nix a go...

---

### Post by aparigraha on 2009-05-06
well.
you could try to reconfigure X to start with. 

from command line:

```
sudo dpkg-reconfigure xserver-xorg
```

then reboot:

```
sudo reboot now
```

after that you have to locate your audio in/out devices

---

### Post by kulturloseramerikaner on 2009-05-10
aparigraha-

Thank you. I'm in.

---

