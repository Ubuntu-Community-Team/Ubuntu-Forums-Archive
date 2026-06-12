---
title: "How to install two buntus via Wubi ?"
date: 2008-12-20
forum: General Help
---

### Post by rams123 on 2008-12-20
I have ubuntu now I want to install kubuntu install same pc with cd (WUBI) . But it says only one buntu is allowed to install through WUBI.

I know we can install kubuntu using **kubuntu-desktop** command in ubuntu . But I have slow connection , so I want to install it through CD (WUBI)

Is there any way to install kubuntu and ubuntu in the same pc using cd's (WUBI installation) ?
[I]BTW,
Does anyone understand my problem :confused:[/I]

---

### Post by lovelyvik293 on 2008-12-20
You can get the installer from [http://wubi-installer.org/](http://wubi-installer.org/)
and you can choise your option of ubuntu/kubuntu from there.
Put the iso image of chosed OS in the same folder as the wubi.And it install the OS without downloading it from net.

---

### Post by rams123 on 2008-12-20
I downloaded Wubi.exe . When I open that here is what I'm getting ..

[CENTER][IMG]http://fumpr.com/images/few229pmtga1k4g12qp6.png[/IMG][/CENTER]

I don't want to uninstall ubuntu. I want to install both kubuntu and ubuntu.

---

### Post by lovelyvik293 on 2008-12-20
Sorry but according to wiki support(ubuntu)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20multiple%20distros?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20multiple%20distros?) 
You can install one os and then install other desktop managers as the packages.

---

### Post by abn91c on 2008-12-20
> **lovelyvik293 said:**
> Sorry but according to wiki support(ubuntu)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20multiple%20distros?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20multiple%20distros?) 
You can install one os and then install other desktop managers as the packages.
No need to do all that, just do the [COLOR="Blue"]**sudo apt-get install kubuntu-desktop**[/COLOR], when it finished running it will be under [COLOR="Blue"]sessions[/COLOR] in the log in screen, as for you slow connection you can add the kubuntu live cd to the repositories and try it that way.make sure the cd is clean and scratch free

---

### Post by rams123 on 2008-12-22
Can you please tell me how to  add cd to repositories ? I need only cd or cd image ?

---

### Post by brandon88tube on 2008-12-22
There is no need to do that. Just rename your ubuntu folder located on your hard drive to something like ubuntu8.10. Then go to /host/ubuntu/disks/boot/grub/menu.lst. Open that file in a text editor and scroll down to these lines ```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin
```

replace ()/ubuntu/disks with what you named your folder. Example ```
title		Ubuntu 8.10, kernel 2.6.27-9-generic
root		()/ubuntu8.10/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root		()/ubuntu8.10/disks
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
root		()/ubuntu8.10/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root		()/ubuntu8.10/disks
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=1674B1EF74B1D1AB loop=/ubuntu/disks/root.disk ro ROOTFLAGS=syncio  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu8.10/disks
kernel		/boot/memtest86+.bin
```

I changed it to ()/ubuntu8.10/disks

When you are done with that you should be able to run wubi.exe again and install another version of Ubuntu.

---

### Post by rams123 on 2009-04-06
@brandon88tube: I've done the same thing as you said, but in win bootloader I can only see kubuntu option. There's no Ubuntu option! 

My previous boot menu: > Windows
Uubuntu

I expected like this after doing above things:
> Windows
Ubuntu
Kubuntu

But now it's showing like this:
> Windows
Kubuntu
So any ideas on what to do now? 
==[I]
Reply if you've not understood my problem..[/I]

---

### Post by 3rdalbum on 2009-04-06
The file he got you to edit is the GRUB bootloader file. So select Kubuntu at the Windows bootloader screen, then press Escape when you see the GRUB countdown. You should then see another boot menu with entries for "Ubuntu" or "Kubuntu".

---

### Post by rams123 on 2009-04-06
Thanks a ton 3rdalbum! 

One small silly doubt here(not very imp): Is there any way to show ubuntu in GRUB menu by default, without pressing Escape ?

---

### Post by rams123 on 2009-04-07
3rdalbum, I've done that but no luck. There's no ubuntu option in Grub menu!

When I press the "Esc" I'm getting like this:
> 
Kubuntu
Recovery mode
memtest
**Other OS**
Windows


No ubuntu, any ideas?

==
*I'd logged into ubuntu, changed folder name from "ubuntu" to "ubuntuG", opened menu.lst and changed "ubuntu" to "ubuntuG", then logged into windows, installed kubuntu via wubi.*

---

