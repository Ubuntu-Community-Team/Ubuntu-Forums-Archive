---
title: "Screen Resolution"
date: 2005-04-11
forum: Desktop Environments
---

### Post by RevJack on 2005-04-11
When I was using Warty, I had several options for screen resolution available, but with Kubuntu (Hoary 5.04) I am stuck with 600x800 screen resolution as that is the only one offered in the dsiplay settings. This is unacceptable! how do I get 1024x768 screen resolution?

---

### Post by erkki70 on 2005-04-11
Hi Rev,
If "acceptable" you could try to reconfigure your X server. :grin: 
```
sudo dpkg-reconfigure xserver-xorg
```

Hope this helps.
Cheers,
Erkki

---

### Post by RevJack on 2005-04-11
Thanks! I'll give that a try.

---

### Post by maruchan on 2005-04-11
I just tried running this configurator. It wrote to a file at the end. Then I rebooted. Then everything was the same. It seemed to identify my graphics card and monitor, and let me choose new screen resolutions. So close!

Anybody know what else I can try? Surfing at 640x480 is like using Google Maps to view webpages :)

Thanks!

Edit: I *did* try to use KDE's configuration tool but it still shows 640 as the highest it will go. Interesting to see 320x200 on there.

---

### Post by maruchan on 2005-04-11
Nevermind, had a look around the forum and fixed the problem by running these:

```
apt-get install nvidia-glx
 apt-get install nvidia-settings
 nvidia-glx-config enable
```

I have an nVidia graphics card so I hope this helps someone.

---

### Post by audscott on 2005-04-11
Or you could use Kynaptic to load nvidia-glx and the nvidia control center....but that's just me.  :D

---

### Post by cmikepee on 2005-04-12
i'm having the same problem as well.  tried both reconfiguring X server and installing nvidia driver (have nvidia video card) and neither fixed the problem.  I previously had hoary installed and there was no problem with the display resolution.  now it seems to "max" at 600x800.

---

### Post by Lachlan on 2005-04-12
You could try using vi to change your horiz. and vert. settings in /etc/X11/xorg.conf to what is in the manual for your monitor.

---

