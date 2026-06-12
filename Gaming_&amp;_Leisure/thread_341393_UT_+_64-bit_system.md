---
title: "UT + 64-bit system"
date: 2007-01-18
forum: Gaming &amp; Leisure
---

### Post by tommyonthenet on 2007-01-18
I've managed to install UT99 GOTY with the installer from lifli.org and installed the extra maps, however when I try to run "ut" I get the following output:

```
tommyonthenet@devastator:~/Gaming/Installers$ ut
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  18
  Current serial number in output stream:  19
Signal: SIGSEGV [segmentation fault]
Aborting.
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  4 (X_GLXDestroyContext)
  Serial number of failed request:  22
  Current serial number in output stream:  25
```

Any ideas? I have 32bit wine, etc installed, however this was a "native" ut install... All the maps, etc unpacked just fine (which never happened when I had a 32-bit lappy!)

Any help will be greatly appreciated!

---

### Post by handy on 2007-01-18
I'm not too sure about UTgoty, but ut2k4 installs a 64bit version nativily if it deems that your system will run it.

If utgoty is only available in 32bit, then it won't run under 64bit, without chroot or force or whatever, I haven't had to do it, so I'm running on memory here.

If you search for chroot, you will become more informed.

By the way I ran ut244 on the same machine using both 64bit & 32bit Ubuntu, & couldn't see any difference in performance?

Looking at the error's you posted, do you have a 3D graphics card installed & have you installed the latest proprietary drivers for nVidia or ATI?

I hope you have an nVidia card, life will be easier for you...

All the best :)

---

### Post by tommyonthenet on 2007-01-19
Unfortunately my graphics card is an Intel 945GM 128mb shared graphics card (built into this lappy)... Life will not be so easy :(

glxgears runs beautifully on it though...

---

### Post by tommyonthenet on 2007-01-19
I figure the problem is something to do with wine maybe?

I have install KOTOR with the installer from liflg.org and that returns a similar error: 

```
tommyonthenet@devastator:/usr/local/games/kotor$ linux32 wine swkotor.exe
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
```

When just running winecfg:

```
tommyonthenet@devastator:/usr/local/games/kotor$ linux32 winecfg
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  17
  Current serial number in output stream:  18
```

UT GOTY is supposed to be native yet returns the same error... So could it possibly be there is an OpenGL error?  glxgears shows the 3 gears rotating VERY smoothly... I'm soo confused :(

---

### Post by handy on 2007-01-19
You don't need Wine if you are doing a native install.

What you need to know is whether your utgoty knows about 64bit OS's?

If it does, then you will need to find the ***linux_Installer.sh***, or something similar on your disk & run that.

If utgoty is only 32bit, then I believe you need to go the ***chroot*** path.  Which is probably what you will have to do, but I don't know for sure.

The other thing, is that 64bit linux, is not really suitable for beginners, you may be best of to reinstall 32bit & have an easier more friendly future.

You see there are next to no 64bit windoze games around, so Wine has to be run a special way, to make it run in 32bit... & on it goes.

I highly recommend 32bit Ubuntu to newish users, & especially gamers.

That's not only my opinion...

---

### Post by tommyonthenet on 2007-01-20
I'm not a newish user to ubuntu - I'm new to 64-bit certainly, but I've used ubuntu for quite a while now (nearly a year and a half I'd say... I used to use slackware, gentoo, etc before that) :)

---

### Post by handy on 2007-01-21
> **tommyonthenet said:**
> I'm not a newish user to ubuntu - I'm new to 64-bit certainly, but I've used ubuntu for quite a while now (nearly a year and a half I'd say... I used to use slackware, gentoo, etc before that) :)

?

---

