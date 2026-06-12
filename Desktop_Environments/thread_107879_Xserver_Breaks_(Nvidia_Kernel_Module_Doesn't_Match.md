---
title: "Xserver Breaks (Nvidia Kernel Module Doesn't Match)"
date: 2005-12-24
forum: Desktop Environments
---

### Post by Evil Whisper on 2005-12-24
hi guys,

I need some help.  I installed the 8178 drivers off nvidia.com
I installed the kernel source & headers.  I hit control+alt+f2 and
I type:
```

 sudo /etc/init.d/gdm stop

```

Then I type:
```

cd ~/Desktop

```

Then:
```

sudo chmod +x NVIDIADRIVERS.bin

```

Then:
```

sudo sh NVIDIADRIVERS.bin

```

I go through the installer it says there are no precompiled kernel modules would you like to check the FTP.  I hit yes and it says there are none so it would have to compile one.  I press OK and it compiles one.  Then at the end I press Yes and allow it to set up my xorg.conf

Then after thats all done i type:
```

sudo /etc/init.d/gdm start

```

I log in and everything is fine.  That is until I shut down the PC or restart it.
Then I get the blue xserver error screen and under the details it says somthing
about the nvidia kernel module does not match the driver or somthing like that.

Thanks in advance for your help,
- Evil Whisper

---

### Post by nicodoggie on 2008-01-30
Mine breaks as well, but ny drivers are from the restricted repos, i'm not at home so I can't check, but it says something like: Nvidia version 100.blah is not compatible with the kernel modules... So I went and removed the nvidia-glx-new package and went on to install the drivers from the nvidia website

I can get gdm to work though when I type:

sudo dpkg-reconfigure -phigh xserver-xorg

But then, compiz-fusion wouldn't work, it says that I'm not using my nvidia driver

---

