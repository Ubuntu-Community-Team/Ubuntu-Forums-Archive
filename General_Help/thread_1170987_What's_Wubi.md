---
title: "What's Wubi?"
date: 2009-05-26
forum: General Help
---

### Post by mikeb1 on 2009-05-26
I can't figure out what Wubi is from its website ( [http://wubi-installer.org/](http://wubi-installer.org/) )

Will this enable me to run Ubuntu as an application from within windows or does this require me to reboot windows every time as if it's installed on a separate partition?

It's often very useful to be able to boot into ubuntu without logging out of windows and thus this would be very helpful.

Does anyone have any input/feedback on Wubi? Is it slow/fast? I would be running it on a dual core 2.53 ghz with 4 gigs of ram.

---

### Post by VMC on 2009-05-26
I've never installed Wubi, but I'll take stab at it. From that site you linked to:

Wubi is Safe

You keep Windows as it is, **Wubi only adds an extra option to boot** into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is free of spyware and malware, and being open source, anyone can verify that.


That would tell me that Ubuntu boots from Windows boot loader. If you want to have Ubuntu running along side or inside of Windows you need to look at a virtual machine - Virtualbox.

Someone will come along and straighten this out.

Edit: Now I see what your asking. Sorry I missed it. You will need a VM.

---

### Post by mikeb1 on 2009-05-26
Thanks!
The reason I was asking is because I recall running ubuntu from within Windows by putting the ubuntu CD in Windows and running setup.exe ...

If anyone has opinions about virtual box or alternatives -- send em this way :)

---

### Post by xXeHPiCXx on 2009-05-26
Wubi installs ubuntu like just another program in windows.You wont have to partition your drives.

---

### Post by cybrsaylr on 2009-05-27
I had problems installing WUBI with a flash drive on my sister's PC. It went on and all with the install but would not run Ubuntu. I still prefer going dual boot to get the most out of Ubuntu.

The flash drive ran Ubuntu live fine and installed well, just would not open after installed.

---

### Post by lisati on 2009-05-27
Long story short: Wubi lets you install Ubuntu on your system without messing around with partitions, by setting up a special folder on the Windows partition. It also lets you uninstall Ububuntu from the Windows Control Panel via "Add/Remove programs". The idea of doing things this way is to help make it easier for newcomers to Ubuntu to try things out.

---

### Post by Avidanis on 2009-05-27
Wubi is a fantastic way to get Linux distros installed  . Very easy you simply download an ISO and download Wubi.Sometimes Wubi is included in the download ISO.

Sometimes you have to download it seperately. I have used it both ways and you literally click on Wubi and it will install your distro.

No partitioning headaches .After the install is done,  when you  boot up you are given a menu to boot into your distro or whatever other OS you have.

---

### Post by 3rdalbum on 2009-05-27
You need to reboot in order to switch between Ubuntu and Windows. Wubi will install Ubuntu inside a file on your existing Windows partition, so there no repartitioning, but it's not any sort of virtualisation. The main two drawbacks are that you are limited to 30 gigabytes for Ubuntu, and if your Windows crashes it will leave its own partition in an inconsistent state that Ubuntu can't deal with - you'd need to boot into Windows again before being able to boot back into Ubuntu. Messy.

Virtualbox works well and it runs Ubuntu well. Admittedly I've only tried Ubuntu host, Ubuntu guest; not Windows host, Ubuntu guest. Performance is quite good. The limitation of "If Windows won't boot, neither will Ubuntu" still stands for running Ubuntu in a virtual machine on Windows. You also don't get direct hardware access on a virtualised Ubuntu.

What I'm saying is, for best results you should install Ubuntu into a partition of its own, but Wubi or Virtualbox will work fine if you're just trying it out.

---

### Post by armageddon08 on 2009-05-27
> **mikeb1 said:**
> I can't figure out what Wubi is from its website ( [http://wubi-installer.org/](http://wubi-installer.org/) )

Will this enable me to run Ubuntu as an application from within windows or does this require me to reboot windows every time as if it's installed on a separate partition?

It's often very useful to be able to boot into ubuntu without logging out of windows and thus this would be very helpful.

Does anyone have any input/feedback on Wubi? Is it slow/fast? I would be running it on a dual core 2.53 ghz with 4 gigs of ram.

Wubi enables you to install Ubuntu as an application in Windows. But it does not allow you to run Ubuntu as an app from Windows. To switch between OSes you would still need to reboot.

It'll be a bit slower than a stock Ubuntu install; but considering you've 4 gigs of RAM, I reckon it won't hurt much.

---

### Post by s.fox on 2009-05-27
Hi,

I installed WUBI very recently as a learning exercise.  Basically you run the setup file in windows and then it sorts out all the partitions and things like that.   At the end of the process you have another boot option available to you when you turn on your computer.  

Hope this clears things up a little.

-Ash R

---

