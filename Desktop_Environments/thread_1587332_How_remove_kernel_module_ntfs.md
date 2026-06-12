---
title: "How remove kernel module ntfs"
date: 2010-10-03
forum: Desktop Environments
---

### Post by cunning on 2010-10-03
Hi all:
 
I am fairly new to ubuntu and have a simple question on how to remove ubuntu kernel module: **NTFS**.
 
Basically I do not want to ubuntu to have any access to my NTFS partition, although this is very wired. 
 
I have to try following procedure
 
first unmount my ntfs partition
 
then
 
modprobe -r ntfs
 
however I still can read my NTFS partition from place browser.
 
Could anyone share a permant solution to disable access to NTFS partition?
 
Thanks a lot
 
cunning

---

### Post by coffeecat on 2010-10-03
> **cunning said:**
> how to remove ubuntu kernel module: **NTFS**.

There has not been an ntfs kernel module (at least in Ubuntu) for a very long time. If you found a reference on the internet to the ntfs kernel module, it must be an old one. Hence:

> **cunning said:**
> modprobe -r ntfs

.. will have no effect. Although I'm surprised that doesn't give an error message. (I've tried it.) If you need to be convinced try:

```
lsmod | grep ntfs
```No ntfs module. Nothing.
 
Ubuntu uses the userspace ntfs-3g driver so if you want to disable access to NTFS partitions the simplest thing would be to uninstall the ntfs-3g package using Synaptic, Software-Center or apt-get from the terminal. I should imagine your NTFS partition would still be visible in the Places menu, but you would get an error if you tried to mount it. Be aware that if you uninstall ntfs-3g you won't be able to mount external USB drives formatted NTFS.

Also - have you been mounting your NTFS partition from the Places menu or with a line in /etc/fstab? If the latter, you need to edit fstab before uninstalling ntfs-3g

---

### Post by cunning on 2010-10-03
Hi coffeecat:
 
Thanks a lot for your reply.
 
I check my /etc/fstab, which does not have any NTFS partition.
 
I already uninstall ntfs-3g and ntfsprogs by using apt-get.
 
However I can still have read access to my NTFS partition.
 
Finally I tried 
 
lsmod| grep -i ntfs
 
The only output is **ntfs**
 
After some search, I think it is **ntfs** that allow me to have read access to my NTFS partition. Currently there is not write access to NTFS partition. 
 
By the way, I am using ubuntu 10.04 LTS.
 
Thanks again
 
cunning.

---

### Post by coffeecat on 2010-10-03
> **cunning said:**
> Finally I tried 
 
lsmod| grep -i ntfs
 
The only output is **ntfs**
 
After some search, I think it is **ntfs** that allow me to have read access to my NTFS partition. Currently there is not write access to NTFS partition. 
 
By the way, I am using ubuntu 10.04 LTS.

Well, that's most interesting. I thought that the old ntfs kernel module had been deprecated years ago. I was/am posting from Maverick/10.10 and there's certainly no ntfs module in Maverick. I'll try Lucid/10.04 later. I'm curious about that.

**Edit:** No, I've just realised what I think is going on. I'm still in Maverick and looking in the /lib/modules folder I could indeed find the ntfs.ko kernel module. So I tried:

```
sudo modprobe ntfs
```Followed by:

```
lsmod | grep -i ntfs
```... and there it was. Interesting. I think what's happening is that if the ntfs-3g driver is present, the ntfs module is not loaded - which is what I found with my earlier lsmod. But if you uninstall the ntfs-3g driver, then perhaps the ntfs is auto-loaded. The ntfs-3g driver is the fuse read-write one. The ntfs driver is the older kernel module which is read-only. I thought it had been abandoned, but I was wrong - I've learnt something.

Anyway, uninstalling ntfs-3g seems to have achieved half your purpose because now you cannot write to the NTFS partition. If you want to have no access at all you'd need to blacklist the ntfs module. If you want to do that post back and I'll explain how. It's quite easy.

---

### Post by cunning on 2010-10-03
Hi coffeecat:
 
Appreciate your time and help for checking this thing out.
 
I have tried to blacklist ntfs using the followng method. However it does not work.
 
I added following line in the **/etc/modprobe.d/blacklist.conf**
 
**blacklist ntfs**
 
Please let me know whether you have better solution.
 
 
Regards
cunning

---

### Post by coffeecat on 2010-10-04
> **cunning said:**
> I have tried to blacklist ntfs using the followng method. However it does not work.
 
I added following line in the **/etc/modprobe.d/blacklist.conf**
 
**blacklist ntfs**
 
Please let me know whether you have better solution.

That was what I was going to suggest. I'm surprised it didn't work.

When you say it doesn't work, do you mean that you can still read the NTFS partition, or do you mean that you can still see it in Places but that you cannot mount it or read it? If you can still read the partition I suggest you double-check what you added to blacklist.conf. Make sure you didn't make a typo. Easily done. If there is no mistake in modprobe.conf there is a way of mounting the partition using fstab but making it non-readable and non-writable by everyone, and that should achieve your purpose.  Post back if you want that.

If, though, you cannot read the partition but it still appears in Places and you don't want to see it there, I don't know how you can stop that. Perhaps someone else knows.

Lastly, why do you want to deny access to the NTFS partition from Ubuntu?

---

### Post by cunning on 2010-10-04
Hi Coffeecat:

Again, really appreciate your time and help on this issue.

I will double check typing.

Right now, I can see the partition and read its content.

**If possible, could you let me know how to use modprobe.conf to do what you suggested?** I just do not want to have read/write access to NTFS partition.

Regarding the reasons, I think I have two.

1. I am not fully comfortable with Linux access windows partition. Because I am fairly new to linux, I may delete some critical file of window system by error.
2. I was always educated Linux is free of virus, although I do not truly believe so. Therefore I want a complete segregation of these two systems.

The reasons may not be valid at all. I just want to be comfortable with my system setup.

Regards
cunning

---

### Post by coffeecat on 2010-10-04
> **cunning said:**
> **If possible, could you let me know how to use modprobe.conf to do what you suggested?**

Post the contents of your /etc/modprobe.d/blacklist.conf file and we can double-check it.

> **cunning said:**
>  I just do not want to have read/write access to NTFS partition.

Regarding the reasons, I think I have two.

1. I am not fully comfortable with Linux access windows partition. Because I am fairly new to linux, I may delete some critical file of window system by error.

If you have read only access to your Windows partition, then there is no way you can delete a file by accident. I'm fairly sure that you cannot write to a NTFS partition with the old ntfs kernel module driver. The best way us to test this. If you are sure you have uninstalled the ntfs-3f driver, mount your Windows partition and navigate somewhere safe such as in your My Documents directory. Try to copy a file there. If you get an error, or if the system refuses to copy the file, you are safe. You have read-only access. You cannot delete or change a file from Ubuntu.

> **cunning said:**
> 2. I was always educated Linux is free of virus, although I do not truly believe so. Therefore I want a complete segregation of these two systems.

If there were Linux viruses in the wild (which I am certain there are not at this time) then your Windows system would be as immune from Linux viruses as Linux is from Windows viruses. Viruses are executables. Windows executables cannot run in Linux (except in wine which is a special case) and Linux executables cannot run in Windows.

> **cunning said:**
> The reasons may not be valid at all. I just want to be comfortable with my system setup.

Fair point. I think making your Windows partition safe from writes from Linux is a sensible precaution if that is what you want to do. People have made Windows unbootable with unguarded access to the Windows partition, but only by writing to the NTFS filesystem. If you have achieved a read-only situation I believe you have made your Windows system as safe as it can be.

---

### Post by cunning on 2010-10-04
Hi Coffeecat:

I will post the /etc/modprobe.d/blacklist.conf file later since I am away from my linux box.

I did not make myself clear. Probably virus is not what I mean.

Worm and Trojan Horses probably are the concern. Read only access does not give me privacy security.

Anyhow I seem to be oversensitive.

But just want to achieve my psychological comfort.

Regards
cunning.

---

### Post by cunning on 2010-10-11
Hi Coffeecat:

The following is my blacklist.conf file and I only copy the beginning part and my edit. When possible, please take a look.

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
blacklist ntfs

# evbug is a debug tool that should be loaded explicitly
blacklist evbug



Regards
cunning



> **coffeecat said:**
> Post the contents of your /etc/modprobe.d/blacklist.conf file and we can double-check it.



If you have read only access to your Windows partition, then there is no way you can delete a file by accident. I'm fairly sure that you cannot write to a NTFS partition with the old ntfs kernel module driver. The best way us to test this. If you are sure you have uninstalled the ntfs-3f driver, mount your Windows partition and navigate somewhere safe such as in your My Documents directory. Try to copy a file there. If you get an error, or if the system refuses to copy the file, you are safe. You have read-only access. You cannot delete or change a file from Ubuntu.



If there were Linux viruses in the wild (which I am certain there are not at this time) then your Windows system would be as immune from Linux viruses as Linux is from Windows viruses. Viruses are executables. Windows executables cannot run in Linux (except in wine which is a special case) and Linux executables cannot run in Windows.



Fair point. I think making your Windows partition safe from writes from Linux is a sensible precaution if that is what you want to do. People have made Windows unbootable with unguarded access to the Windows partition, but only by writing to the NTFS filesystem. If you have achieved a read-only situation I believe you have made your Windows system as safe as it can be.

---

### Post by coffeecat on 2010-10-11
This part of your blacklist.conf seems correct for blacklisting ntfs:

> **cunning said:**
> # This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
blacklist ntfs

But if lsmod still shows the ntfs module and if you can still mount and read your ntfs partition then I really have no idea what else you can do.

---

