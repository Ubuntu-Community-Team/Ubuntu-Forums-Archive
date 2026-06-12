---
title: "System hangs on start up!"
date: 2009-03-30
forum: General Help
---

### Post by hellarough on 2009-03-30
I am still pretty much a linux noob but recently I updated and now my system hangs on the start up. It used to hang on the start up and shutdown/restart but I did a little reading and found a fix for the shutdown problem. 

Here is how it happens:
1. turn on / restart computer
2. select operating system from grub
3. linux gives first message something about ignoring 4gb beyond aperture
4. ubuntu loading screen w/ the bar that moves back and forth freezes until I press and hold any button
5. ubuntu loading screen  w/ bar that fills up from left to right fills up normally and I get the log in screen

Basics about my system:
hp laptop dv6815nr
dual boot with vista and linux


Please Help, I'd be happy to post any other details necessary

Thanks,
Ryan

---

### Post by spiderbatdad on 2009-03-30
Check diagnostic message from the kernel:
```
dmesg > ~/Desktop/dmesg.txt
```

Copy and paste the file to ubuntu pastebin:
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)
after you select paste, a new url will appear. Please copy that link to your next post for more help. Or...right click the file and select "create an archive." You can then upload the archived package here with the "manage attachment tool" below.

---

### Post by hellarough on 2009-03-31
> **spiderbatdad said:**
> Check diagnostic message from the kernel:
```
dmesg > ~/Desktop/dmesg.txt
```

Copy and paste the file to ubuntu pastebin:
[http://paste.ubuntu.com/](http://paste.ubuntu.com/)
after you select paste, a new url will appear. Please copy that link to your next post for more help. Or...right click the file and select "create an archive." You can then upload the archived package here with the "manage attachment tool" below.


Link = [http://paste.ubuntu.com/141375/]("http://paste.ubuntu.com/141375/")

---

### Post by spiderbatdad on 2009-03-31
Unfortunately I don't see any of the classic solutions to slow boot suggested by the kernel. I have noticed HP's can be troublesome in terms of hardware for linux kernel.

It looks like this boot was a resume from hibernate or suspend...maybe part of the problem. I also noticed some type of warning near the end...mind you, I am not an expert:

"2.226849] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after"

Then an ehci driver gets loaded...maybe for usb boradband? or some other usb device. You might try hot plugging your usb device after boot.

Sorry I havent been much help. I would recommend booting without the quiet splash option, so that you can see where your boot hangs more precisely, possibly. Also an old option like "irqpoll" or "pci=acpi" might handle assigning irqs better than acpi.

There are also links available for bootcharts and speeding up boot greatly.

This will show you how to apply boot options like pci=routeirq, or irqpoll, or just removing quiet splash, if you have never tried before:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
It's very easy to do, if you read the instructions, and you dont need the cd, as you have already installed.

If you search Ubuntu slow boot on google you should find hundreds of discussions for installing bootchart, disabling unused startup services, etc. Sorry you are having the issue, it isnt the norm, but not uncommon either. From what I have seen HP's take a little tweaking. Search ubuntu on HP also, you should find a lot.

---

### Post by hellarough on 2009-04-01
> **spiderbatdad said:**
> Unfortunately I don't see any of the classic solutions to slow boot suggested by the kernel. I have noticed HP's can be troublesome in terms of hardware for linux kernel.

It looks like this boot was a resume from hibernate or suspend...maybe part of the problem. I also noticed some type of warning near the end...mind you, I am not an expert:

"2.226849] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after"

Then an ehci driver gets loaded...maybe for usb boradband? or some other usb device. You might try hot plugging your usb device after boot.

Sorry I havent been much help. I would recommend booting without the quiet splash option, so that you can see where your boot hangs more precisely, possibly. Also an old option like "irqpoll" or "pci=acpi" might handle assigning irqs better than acpi.

There are also links available for bootcharts and speeding up boot greatly.

This will show you how to apply boot options like pci=routeirq, or irqpoll, or just removing quiet splash, if you have never tried before:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
It's very easy to do, if you read the instructions, and you dont need the cd, as you have already installed.

If you search Ubuntu slow boot on google you should find hundreds of discussions for installing bootchart, disabling unused startup services, etc. Sorry you are having the issue, it isnt the norm, but not uncommon either. From what I have seen HP's take a little tweaking. Search ubuntu on HP also, you should find a lot.


Sweet, thanks much for giving me something to go on, I will report back to let you know how it goes.

---

### Post by IceBadger on 2009-04-01
I have see this happen on a friends laptop (a compaq something) and on an old G3 Apple PowerBook I have.  The way that I got around this was disabling the boot splash in the boot loader.

It does not look pretty, but it boots without having to hold down keys, and it will print any errors to the screen.

So far we have not found any errors that printed, so our guess is that it is the splash that is not playing nice.

To disable the splash, in a terminal:
```

sudo gedit /boot/grub/menu.lst

```

Locate your kernel that you boot into (usually the first entry near the bottom half of the file) which looks something like this:
```

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3a98d41-1df1-47f9-b680-cbfc7d06674c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

```

You will notice on the third line, the last word is *splash*.  Change it so it says *#splash*.  Save and reboot, and see if you can find a error on startup.

---

### Post by hellarough on 2009-04-01
Okay so I took you suggestion and ended up in this thread [http://ubuntuforums.org/showthread.php?t=512059]("http://ubuntuforums.org/showthread.php?t=512059"). I tried adding a few options to the boot but it didnt seem to help although during shutdown I did get a message about an unusual/failed shut-down of NetworkManager. 

At first I was guessing that my system could be hanging on services related to my wireless card since wireless cards seem to be a big issue with the HP laptops and I am using the madwifi drivers (also because it seems that I usually have to change any references from eth0 to ath0). But after I checked the new dmesg I am begining to think that it is much more than that. 

Here is the new dmesg [http://paste.ubuntu.com/141894/]("http://paste.ubuntu.com/141894/"), I inserted break lines below the 'hang ups' so you can see where my system is stalling and requires a key entry.

---

### Post by hellarough on 2009-04-04
> **IceBadger said:**
> I have see this happen on a friends laptop (a compaq something) and on an old G3 Apple PowerBook I have.  The way that I got around this was disabling the boot splash in the boot loader.

It does not look pretty, but it boots without having to hold down keys, and it will print any errors to the screen.

So far we have not found any errors that printed, so our guess is that it is the splash that is not playing nice.

To disable the splash, in a terminal:
```

sudo gedit /boot/grub/menu.lst

```

Locate your kernel that you boot into (usually the first entry near the bottom half of the file) which looks something like this:
```

title		Ubuntu jaunty (development branch), kernel 2.6.28-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=b3a98d41-1df1-47f9-b680-cbfc7d06674c ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

```

You will notice on the third line, the last word is *splash*.  Change it so it says *#splash*.  Save and reboot, and see if you can find a error on startup.

Doesn't commenting it out like that have the same effect as just deleting "quiet splash"?  
In my previous post I had found where it hangs but I have no idea where to go from there because it happens in so many places and this problem only occurred after I upgraded to 8.10 (the documentation seemed to be useless for this problem too)

---

### Post by IceBadger on 2009-04-09
It is the same, but I try to never delete things when troubleshooting.  It is easier to restore the file to normal by removing the comments then to try and remember what you deleted.

---

### Post by hellarough on 2009-04-10
> **IceBadger said:**
> It is the same, but I try to never delete things when troubleshooting.  It is easier to restore the file to normal by removing the comments then to try and remember what you deleted.


Yeah I can understand that, its actually a good practice.

---

