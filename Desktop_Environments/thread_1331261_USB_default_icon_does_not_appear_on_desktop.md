---
title: "USB default icon does not appear on desktop"
date: 2009-11-19
forum: Desktop Environments
---

### Post by krams915 on 2009-11-19
[B]Problem:
[/B]I have a 4GB Transcend USB drive. Ubuntu is able to mount and detect this USB drive. Whenever I insert the USB drive, it shows the USB icon on my desktop. Last night, for some unknown reason, when I inserted the USB drive, it's no longer showing the default USB icon. It's showing a different icon (I think it's blank document icon). The USB drive is still working fine. No problems with that. I've inserted another USB PQI drive. Same size. It mounts and shows the default USB icon. 

Why is this happening? I've searched Google and the closest answer that I've found is something to do with the autorun.inf which is missing on my Transcend drive. Here's the link: [http://brainstorm.ubuntu.com/idea/19721/](http://brainstorm.ubuntu.com/idea/19721/)

How do I restore the default USB icon for this drive? I would really appreciate some ideas or comments. Of course, I could reformat the drive, but I wanna know what's causing the problem. I will keep searching Google for answers. I hope someone can help. Thanks
[B]
Background:
[/B] I'm a new Ubuntu convert. I'm using Ubuntu 9.04 "Jaunty" for a month now. Everything seems to be running smooth although there are some bumps on the road. I'm really a former Windows power user since Windows 95 (I've handled Win 3.1, NT, 98, XP, 2000, Vista, 7 RTM). 

I'm a tech support for an anti-malware company. We support concerns about malware for Microsoft Windows Operating Systems.  Since last year, I'd been testing Ubuntu with VirtualBox for Windows XP. I'm also a PHP and Java/Spring programmer/web developer. I like overclocking and optimizing my hardware.

This month I've decided it's time to switch to Ubuntu as my main OS. Windows 7 is just too expensive for me. I've just realized that I like Windows mainly for DirectX gaming. But everything else that I do in Windows (programming, browsing the net, reading tech stuffs), I can do it in Ubuntu. Why pay $200 for a new Windows 7 when you can get Ubuntu for free?

---

### Post by emigrant on 2009-11-19
mount point for both the drives at /media?

---

### Post by krams915 on 2009-11-19
> **emigrant said:**
> mount point for both the drives at /media?

That I will check later. I'm at work now. We don't have Ubuntu here. Mostly are Windows OS.

Like I said I'm a new to Ubuntu. **How do I verify if the mount point is at /media**?

I'll search Google for that as well. But maybe you can answer it.

---

### Post by emigrant on 2009-11-19
go to terminal and past the output seperately for these two commands:

```

fdisk -l

```

```

gedit /etc/fstab

```

---

### Post by krams915 on 2009-11-19
> **emigrant said:**
> go to terminal and past the output seperately for these two commands:

```

fdisk -l

``````

gedit /etc/fstab

```

Here's a screenshot of **top**

[IMG]http://img685.imageshack.us/img685/2394/screenshotmarkmarkdeskt.jpg[/IMG]



Here's a screenshot of **fdisk -l**

[IMG]http://img515.imageshack.us/img515/2394/screenshotmarkmarkdeskt.jpg[/IMG]


Here's a screenshot of **gedit /etc/fstab**

[IMG]http://img40.imageshack.us/img40/1227/screenshotfstabetcgedit.jpg[/IMG]


[SIZE=4]HOWEVER, PROBLEM SEEMS TO BE RESOLVED.[/SIZE]

Here's the current screenshot of my drives:

[IMG]http://img40.imageshack.us/img40/8268/driveso.jpg[/IMG]

You can see in the screenshot that my Transcend flash drive has its default normal USB icon. Here's what I did. I inserted that drive to a Vista computer. I right-click on the drive and added a label "TRANSCEND".  I also added an **autorun.inf** (though I'm not sure if that made the difference). When I got home from work, I inserted the drive back to my UBUNTU and now the icon is showing.

Anyway, since you've requested the information above, maybe you can check if there's something wrong. Yes, those screenshots were taken after the problem has been resolved. 
[IMG]http://img685.imageshack.us/i/screenshotmarkmarkdeskt.png/][IMG]http://img685.imageshack.us/img685/3707/screenshotmarkmarkdeskt.th.png[/IMG]

---

### Post by krams915 on 2009-11-19
Any ideas people?

---

### Post by mechgt on 2010-06-18
I've got the exact same problem.  USB drive is there, I can read/write just fine, however the desktop icon looks like a blank document.  It does this for several (all?) of my USB drives.

Ubuntu 10.04

---

### Post by nasr_on_net on 2010-06-20
Same with me, but also my NTFS Drives doesn't appear at disktop and i can read and write to them normally !!
any idea how to restore them to the desktop again ??

---

