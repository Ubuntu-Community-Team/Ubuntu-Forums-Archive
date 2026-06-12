---
title: "Worth upgrading to 9.04?"
date: 2009-05-21
forum: General Help
---

### Post by orchidfire on 2009-05-21
Hi all,

I'm currently using 8.10, and pretty much everything is working well for me, except for my built-in microphone.  I have a Dell Inspiron 1525, and this microphone problem has been reported with other Inspiron 1525 users.

I was wondering about whether or not it would be worthwhile to upgrade to 9.04.  I would really only be interested if the microphone bug is fixed; I don't want to risk breaking the programs that I use frequently (Skype, Firefox, Songbird/Amarok, and LaTeX), as I'll be out of the country soon and don't want to deal with the problems.

So, is it worth it for me to upgrade to 9.04?  What are the big bugs to note in my decision?  (Additionally, my boyfriend recently upgraded to 9.04, but it malfunctioned and he had to reinstall Ubuntu.  I wouldn't want that to happen to me.)

Thanks in advance!

---

### Post by Yellow Pasque on 2009-05-21
You may be able to get your mic working without upgrading:
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Add or edit this model= line to read:
```
options snd-hda-intel model=dell-bios
```

At this point, restarting your system may be required.

> To activate the microphone you have to enable all Capture and Mux channels (left and right) and also set Input Source to Digital Mic. -- [http://en.gentoo-wiki.com/wiki/Dell_Inspiron_1525](http://en.gentoo-wiki.com/wiki/Dell_Inspiron_1525)

---

