---
title: "Ubuntu / Debian installed on the PlayStation 3 (PS3)"
date: 2006-12-05
forum: Gaming &amp; Leisure
---

### Post by candell on 2006-12-05
hi, i was able to install Ubuntu 6.10 on the PS3.

here are some pictures of the install:

  *  [http://www.louiscandell.com/ps3/](http://www.louiscandell.com/ps3/)

is anyone else interested in installing ubuntu / debian on the ps3, or am i the only one?

let me know.

thanks.

---

### Post by kerry_s on 2006-12-05
Does everything work?
What kind of performance are you getting? 
How good is it with resources,heavy on memory,uses lots of cpu?

---

### Post by candell on 2006-12-05
thats one of the main reasons i would like other people to install ubuntu on the ps3.  

i installed it @ like 5am on monday morning and work starts at 9:30am.  i have not had much time to really dig deep as i'm at work for 10-12 hours a day. ](*,)  this means my updates wouldnt be until the weekend when i have time, but i know a lot of other people have different schedules so its a call for help! :p 

i installed xubuntu 6.10 on the ps3 as i'm mainly a CLI guy, but it would be nice to have others help out on the ps3 as i dont have much time during the week to really tinker with my new toy.

---

### Post by tworkemon on 2006-12-05
If you can post a HOWTO would be great. MANY people are trying and are not able to do what you have accomplished.

---

### Post by slimdog360 on 2006-12-06
I hope you can fix that resolution. Good job anyways.

---

### Post by Yogarine on 2006-12-06
> **candell said:**
> is anyone else interested in installing ubuntu / debian on the ps3, or am i the only one?

let me know.
You bet ya we're interested:

[http://wiki.ubuntu.com/PS3Compatibility](http://wiki.ubuntu.com/PS3Compatibility)
[http://ubuntuforums.org/showthread.php?t=298256](http://ubuntuforums.org/showthread.php?t=298256)

---

### Post by Shin_Gouki2501 on 2006-12-06
Hello if anyone has details please contribute here:
[http://ubuntuforums.org/showthread.php?t=298256&page=11](http://ubuntuforums.org/showthread.php?t=298256&page=11)
wbr Shin Gouki

---

### Post by undeadsoldier on 2006-12-07
errr.. then why does it say fedora core then...

[http://www.louiscandell.com/ps3/00060.jpg](http://www.louiscandell.com/ps3/00060.jpg)

---

### Post by tomei on 2006-12-08
Did you even click the last 3 pictures? :-k 
[http://www.louiscandell.com/ps3/00072.jpg](http://www.louiscandell.com/ps3/00072.jpg)

---

### Post by madmetal on 2006-12-08
good news..
thanx for the pictures.
a how-to will be just great!

---

### Post by candell on 2006-12-10
[FONT="Tahoma"]Here is a quick HOWTO on installing Ubuntu / Xubuntu / Kubuntu / Debian Unstable on the PlayStation 3:

 [SIZE="3"] *  [http://www.louiscandell.com/ps3/](http://www.louiscandell.com/ps3/)[/SIZE]

If you are attempting to do the install tonight continue refreshing the page as I'll attempt to finish it up within the next couple of hours.

I was able to resolve the xorg.conf situation check out the new pics - total difference story now:

[SIZE="3"]  *  [http://www.louiscandell.com/ps3/images/](http://www.louiscandell.com/ps3/images/)[/SIZE]

My IRC nickname is:

  * lcandell

In case you have questions while installing.

Late!

[/FONT]

---

### Post by Shin_Gouki2501 on 2006-12-10
wow thanks thats very nice!
wbr Shin  Gouki

---

### Post by Boreras on 2006-12-10
Maybe you want to try and install kernel 2.6.20, Sony gave Linus & friends some patches, which will improve compatibility with the linux Kernel greatly,  by allowing SMP and DMA (being the most important of features / compatibility added).

[http://www.linuxdevices.com/news/NS6521115697.html](http://www.linuxdevices.com/news/NS6521115697.html)
and [kernel.org's patch from sony]("http://git.kernel.org/git/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=f58a9d171a346afb1b09190427e6c28c6118703e")

I think it's really great Sony is doing this, too bad Sony / nVidia will probably never release a driver for the RSX, though [ nouveau might be interesting]("http://nouveau.freedesktop.org/wiki/) but it's far from being even usefull at this moment, but it probably could work on the RSX, because it's not a x86 binary blob.

congratulation on getting ubuntu to run on the PS3, but I'll probably would run gentoo for the fun of it.

---

### Post by JurB on 2006-12-10
:-D \\:D/ =P~ =D> :biggrin: AWE-SOME!

---

### Post by Ciego on 2006-12-10
Can you please let us know how you can delete the Fedora installation after you have Ubuntu installed?

---

### Post by haxer on 2006-12-10
May I say this ... How is blue ray going to work? ;) And do you got an link to the screen lcd? Where did you buy it looks good :) Im currently looking for an nice lcd screen 26" minimum how big are your tv?

---

### Post by Ciego on 2006-12-10
Is there a way to do this installation without burning a Fedora DVD?  I do not currently have access to a DVD burner.

---

### Post by Dpdk on 2006-12-13
If f.c. is on a separate partition, you could just nuke the partion and either add it some how to the ubuntu one or use it as a seperate drive for something such as linux games, or music/video.

---

### Post by Ciego on 2006-12-15
For those interested, I created a thread for sharing PS3 aliases for the Playstation network.

[http://ubuntuforums.org/showthread.php?t=319528](http://ubuntuforums.org/showthread.php?t=319528)

---

### Post by inee on 2007-01-08
hi,

its been maybe ten years since i've gone on a red hat terminal, so treat me as a noob.

im trying to install ubuntu onto the ps3. i got fedora and yellow dog running; but my ultimate goal is to get ubuntu and darwin on the machine. im running into several roadblocks and hope the more experienced members here can lead the way.

a guide for ubuntu on ps3 was written here:

[http://louiscandell.com/ps3/](http://louiscandell.com/ps3/)

but it goes through several steps and requirements that i think we can skip. it requires that you install ubuntu on a usb hdd where you can partition it, PLUS, it also requires fedora as a base install, then cross-installing onto debian and then upgrading to ubuntu.

i want a simpler way where i can install ubuntu from kboot prompt with a dvd-rom installer ready.

keep in mind there are a few things that make the ps3 installation different:

1. the ps3 boots into kboot only. cannot boot from hdd and cannot boot from cdrom or usbdrive.

2. only 1 partition available: /dev/sda (i imagine parted can fix this)

3. ppc architecture



okay, some issues i want cleared. 

1. can i modify kboot to load the cdrom such that i can install from the cdrom? if this is possible then i can just plug in the installer cd (whether ubuntu, osx, or darwin) and let it run its course.

2. can i do without partitioning the hdd? id imagine just making a /ubuntu folder and installing everything there. the guide above requires partitioning of the hdd which the ps3 does not allow by default (although yellow dog's druid was able to do it). 

3. can kboot boot ubuntu instead of yaboot? in that case, can kboot boot darwin/osx too (darwin/osx requires bootx)?

4. i get this error:

w: failure trying to run: chroot /mnt/ubuntu mount -t proc proc /proc

after typing this:

/usr/sbin/debootstrap --arch powerpc edgy /mnt/ubuntu [http://archive.ubuntulinux.org/ubuntu](http://archive.ubuntulinux.org/ubuntu)

specifically after "i: validating libatu1" step. what does that mean and how do i fix it? 


this error happens after i chose "minimal fedora install". i dont get it when i choose the full install (2.5hrs wait); but the guide above states to use the minimal install.



all the help is greatly appreciated. hope i can get ubuntu running NATIVELY on the ps3 without an external usb hdd.

---

