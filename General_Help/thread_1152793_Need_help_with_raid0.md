---
title: "Need help with raid0"
date: 2009-05-08
forum: General Help
---

### Post by randomg on 2009-05-08
OK, here is a problem I have a winxp machine, and it got some kind of start up error, and doesnt start anymore, it just goes to blue screen. I need to get some important files off that machine before I plan to reinstall it to fix the errors, or attempt to fix them. I was told on other forums, that unbutu would help me to do that, because I can just go into linux from a cd, and copy all the important stuff into flash drive while in linux, or go on the internet and save the stuff there. So, I got the ubuntu cd, and loaded up my pc into linux. Problem is, I cant see my hard drives. I suspect its because they are in raid0, and its not recognizing them because of that? How do I turn on raid0 in ubuntu? Or could it be something else that is preventing linux from recognizing my HDs? Thanks/

---

### Post by indytim on 2009-05-08
I can't speak to the raid0 issue if that is, in fact impacting you.  What I would offer is to just mount the ntfs partition and pull off your files.

Either boot to a LiveCD or an installed Linux ops.
Bring up the terminal:
```

$ sudo mkdir /media/NTFS
$ sudo mount /dev/sda1 /media/NTFS

```
Assuming your Windows partition is sda1 (adjust accordingly).  Of course you can name the mount partition (NTFS) anything you want.

Once mounted, use the file manager of choice to explore the NTFS partition and copy files to wherever.

Hope this is of some help.

Best,

IndyTim

---

### Post by dandnsmith on 2009-05-08
Initially there is a need to establish what sort of raid system is in use - whether it be a hardware controller mastering it, or a software provided control. Until that is known it won't be possible to work out how to mount the multiple disks so they can be seen as one filesystem.

This, unfortunately, is where my knowledge stops. I've avoided using any raid system, being aware of pitfalls like these, and how difficult it can be to recover from certain types of problem. RAID 0 is particularly bad, having no redundancy built in to aid recovery.

---

### Post by dandnsmith on 2009-05-08
> I think there is no such thing as a RAID that is set up in the BIOS

I think there are a number of companies which would disagree with you, since they provide an extension BIOS with the controller card in which it all done. Sometimes this is seen as part of the original motherboard BIOS, as it is integrated in. Where this is in use, you need a controller which dupes the original setup to even get started on recovery.

BTW OP is working with an NTFS on RAID0 created under Windows, not linux.

---

