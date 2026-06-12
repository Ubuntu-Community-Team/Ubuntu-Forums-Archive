---
title: "NVidia not working on kubuntu"
date: 2005-08-24
forum: Desktop Environments
---

### Post by t0m4s3 on 2005-08-24
Hello,
i have downloaded and installed kubuntu i386 version on AMD64, because i thought there is some bug in 64bit edition. But recently i've heard that i should install nvidia drivers to run Xserver on my card (nv gf6600). So i've followed this

[http://home.comcast.net/~andrex/Debian-nVidia/installation.html](http://home.comcast.net/~andrex/Debian-nVidia/installation.html)

but still Xserver isnt working right. Only correct that i see is mouse, everything else is  green and distorred. Any opinions and advices? I will be very happy to pass through this problem to start using ubuntu. Thx

---

### Post by Lord Illidan on 2005-08-24
No, man, no...

That is how to install NVIDIA on Debian...but you want NVIDIA on Ubuntu..

You can install NVIDIA via synaptic, just have a look at the Ubuntu Guide in my sig!

---

### Post by t0m4s3 on 2005-08-26
i have done everything just like in guide but i have no '/usr/share/applications/NVIDIA-Settings.desktop' file. Any ideas?

Also i try to run official driver for Nvidia (64bit edition), the .run file, but it told me i have no kernel-source installed. Also there is no hoary-2.6.8 kernel-source (and also kernel-tree) package on official ubuntu packages site.

Any ideas? I really like to run ubuntu, but it's still not working  ](*,)  :| 

PS. i have 64bit machine ;)
PS2. i've install fresh new ubuntu on formatted ext3 partition

---

### Post by Takis on 2005-08-26
Did you read Lord Illidan's post? Follow the link in his signature, you'll find everything you need to know. It's very easy.

---

### Post by t0m4s3 on 2005-08-29
i have done everything just like in guide, but i haven't got file 'NVIDIA...' in /usr/share/application.

yesterday i tried to start kubuntu, and on my surprise, it works... i have patched kernel by 2.6.7 patch, so maybe that helped.  :???:

---

### Post by Takis on 2005-08-29
Hang on I just noticed something.

You downloaded/installed the i386 version of Kubuntu but are trying to use 64-bit versions of the NVidia drivers? If you're going to run i386 on your 64-bit (that's fine, I'm doing that too), you can only use i386 (32-bit) drivers.

---

### Post by mrowth on 2005-08-30
[QUOTE=t0m4s3]i have done everything just like in guide, but i haven't got file 'NVIDIA...' in /usr/share/application.[/QUOTE]
I think the guide asks you to create it, not modify it. It only contains the lines:

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

Of course if you're running Kubuntu you may not have gedit. Try nano or vim -- or (possibly less frustrating) KDE's kate:

kdesu kate /usr/share/applications/NVIDIA-Settings.desktop

---

### Post by tseliot on 2005-08-30
[QUOTE=t0m4s3]Hello,
i have downloaded and installed kubuntu i386 version on AMD64, because i thought there is some bug in 64bit edition. But recently i've heard that i should install nvidia drivers to run Xserver on my card (nv gf6600). So i've followed this

[http://home.comcast.net/~andrex/Debian-nVidia/installation.html](http://home.comcast.net/~andrex/Debian-nVidia/installation.html)

but still Xserver isnt working right. Only correct that i see is mouse, everything else is  green and distorred. Any opinions and advices? I will be very happy to pass through this problem to start using ubuntu. Thx[/QUOTE]
You can try my guide, it's easy and it's meant for ubuntu

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

If you have any questions about the guide please ask them in that link

---

### Post by t0m4s3 on 2005-08-30
[QUOTE=Takis]Hang on I just noticed something.
You downloaded/installed the i386 version of Kubuntu but are trying to use 64-bit versions of the NVidia drivers? If you're going to run i386 on your 64-bit (that's fine, I'm doing that too), you can only use i386 (32-bit) drivers.[/QUOTE]

no no no. i have installed i386 version and try tu run, drivers as written in guid (glx and so.) But i was told to try original drivers from nvidia website, so i reinstalled system (x86_64) and try them, but there was some mistakes during installation of them. But as i sad, one morning i have run the computer, and everything is going well, so no problem now  :smile: 

Ubuntu is great! I like it very much! \\:D/

---

