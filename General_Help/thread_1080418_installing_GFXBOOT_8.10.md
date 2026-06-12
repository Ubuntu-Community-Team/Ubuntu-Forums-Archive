---
title: "installing GFXBOOT 8.10"
date: 2009-02-25
forum: General Help
---

### Post by wsonar on 2009-02-25
I have followed sevral sets of instructions and none of them work

I get to the point where I get into grub and it can't find stage1

but it is clearly in /boot/grub  works fine with old grub but when I try
gfxboot it cannot find stage1 or says it's not read correctly

has anybody installed gfxboot correctly with no problems on 8.10???

Have have xp,vista,ubuntu 8.10 latest kernal

want to get gfxboot working

any help greatly appreciated

so far everytime I follow the instructions it crashes my system and I have to reinstall old grub

---

### Post by wsonar on 2009-02-25
here is my grub tmp file

grub> dump (hd0,5)/boot/grub/stage1 /tmp/grubMEuS8O

Error 2: Bad file or directory type
grub> quit

---

### Post by zombaya01 on 2009-02-26
I bump this.  Would also love to see an updated tutorial which actually works.

---

### Post by wsonar on 2009-02-27
So if anybody has GFXBOOT on 8.10 can you please let me know so I know if it is possible?

---

### Post by zombaya01 on 2009-02-28
Well, i actually found a new thread a couple of days ago, after bumping this.  I managed to get it working with it, so I would advice you to try this one also.  The only thing I didn't follow was the gfxboot-link.  I had a newer version (grub-gfxboot_0.97-40_i386.deb) to make sure it would work with intrepid.

The url for the new thread: [http://guide.ubuntuforums.org/showthread.php?t=481957](http://guide.ubuntuforums.org/showthread.php?t=481957)
the url for new gfxboot: [http://sidux.com/debian/pool/main/g/grub-gfxboot/](http://sidux.com/debian/pool/main/g/grub-gfxboot/)

I hope you'll have as much success with it as I had.

---

### Post by wsonar on 2009-03-02
I got my gfxboot wroking

So I ended up just coping over the little data I had to the ntfs part this was a pretty fresh install of all os's it apears it was ext3 after all

I then booted to the ubuntu 8.04 cd deleted the linux and swap made the sawp 2 gig and the rest for the linux which was ext 3 and primary


after the install grub was back and booted into ubuntu 8.04

before getting any update

I followed the how to for the gfxboot here

[http://abhay-techzone.blogspot.com/2...on-ubuntu.html](http://abhay-techzone.blogspot.com/2...on-ubuntu.html)

rebooted and wolla I had my cool themed bootloader

I tested booting into each os

I then got all critical security updates

after testing was still good then got recomended updates

---

### Post by Malac on 2009-04-26
I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")
(There is a 64bit here : [grub-gfxboot_0.97-40_amd64.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_amd64.deb") )

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111189[/ATTACH]

Hope this helps

---

### Post by wsonar on 2009-05-20
> **Malac said:**
> I downloaded this deb file from sidux.com:
[grub-gfxboot_0.97-40_i386.deb]("http://sidux.com/debian/pool/main/g/grub-gfxboot/grub-gfxboot_0.97-40_i386.deb")

Uninstalled GRUB then installed the deb using GDebI (just double-clicked on it)
Then altered the gfxboot-theme-zen(installed via synaptic) using the jaunty GDM background and GIMP then compiled it to this one.
[ATTACH]111189[/ATTACH]

Hope this helps


Wow that is cool Thanks will save time in the future

---

