---
title: "iPod nano (2G) won't automount"
date: 2006-09-30
forum: Desktop Environments
---

### Post by Flutterby on 2006-09-30
Hey all, I just got an iPod nano (2nd generation). I have one problem and that is that it will not automount or show up on the Desktop. I also have an iRiver H340 (an mp3 player) and several other USB devices that show up just fine.

I *am* able to mount the iPod "by hand" and then use it through gtkpod, but I would seriously like it to automount, just like my other gear.  Can anyone help me please?

---

### Post by deeptingler on 2006-09-30
I was having that prob too and I am currently having to do this by hand also, will subscribe to this thread incase anyone else has solved it.  Is the 2nd Generation different than the 1st for mounting?

---

### Post by test on 2006-10-06
My ipod nano 2G mounted fine with firmware 1.01.  It was sent back for repair and a new nano was returned with version 1.02.  Now it does not automount.  

It can, however, be manually mounted with a
mount /dev/sda2 /mnt/whatever

---

### Post by michael003 on 2006-10-12
I have this same problem, also with a 2G iPod Nano. I can mount it manually using pmount and everything else works fine, but it won't automount when I plug it in.

I am using Kubuntu Edgy. USB drives automount correctly when plugged in.

I have attached the relevant parts of lshal both before I mounted it and afterwards. I suspect that it has something to do with HAL, because the description of the volume is not the same as a volume of a USB flash drive (it isn't identified by the UUID, the filesystem type is not detected). So either HAL is messing up, or the partitioning/formatting of the 2G Nano is different from the 1G.

---

### Post by trauta on 2006-10-15
Has anyone worked on this problem.  I finally got all the kinks out of all my other devices and this is the only one left.

My wife's 1st Generation Nano works perfectly, but my 2nd Generation (Firmware 1.02) Nano only mounts manually.

Thanks.

---

### Post by smoothridersean on 2006-10-18
Same here!

(just posting to subscribe)

---

### Post by deeptingler on 2006-10-18
I have found a workaround in that I have to use dmesg in a terminal as each time I plug the nano in it seems to move from sdf2 to sdg2 etc - once I have edited the fstab to get this correct then all is ok

/dev/sdg2 /mnt/ipod vfat umask=000,uid=0,gid=0,noauto,rw,user 0 0

This is what I have in my /etc/fstab and I have to mount /mnt/ipod but the next time I boot the nano might be recognised by dmesg as /dev/sdf2 which means I have to edit the fstab and mount again

not sure of a way to stop this at present.

Also, today there has been a new HAL (18.1) which seems much better at recognising devices under Kubuntu 3.5.5 (which I use) - This still does not help with the 2G nano though.

All my other USB devices now show on the desktop but the 2G nano refuses to play unless coaxed into it by the above method for me..... [-(

---

### Post by igknighted on 2006-10-18
I wish I had that problem... mine automounts every time and it's very frustrating because I plug in to charge usually and would rather not have it mounted cause I don't change songs/files at all, but I have to click through windows that come up no matter what

---

### Post by brendon on 2006-10-25
I'm having the same problem with my nano.  I saw that there was a proposed fix for hal ([https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068](https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068)), but it doesn't look like they'll have edgy patched in time.

In the meantime I've been using fstab, but instead of checking dmesg each time the iPod is attached and changing /etc/fstab you can hard code it's by-id path.  Check the /dev/disk/by-id directory for usb-Apple_iPod_XXXXXXXXXXXXXXXX-part2 after you plug in your iPod and use that path instead of /dev/sd*2.  The line in /etc/fstab should look something like:

/dev/disk/by-id/usb-Apple_iPod_XXXXXXXXXXXXXXXX-part2 /media/ipod vfat umask=000,uid=0,gid=0,noauto,rw,user 0 0

---

### Post by deeptingler on 2006-10-25
Cool Brendon, Ive been looking at how things work on edgy beta lately and was noticing how some things were different but they seemed a little heavy going for me at the time, the way you explained it, it seems to not look so daunting....will give it a try as have 2 external drives which always change too...... now to get the pocket pc 5 smartphone recognised........hehehe

[http://ubuntuforums.org/showthread.php?t=168221](http://ubuntuforums.org/showthread.php?t=168221)

This is an interesting thread I came across on this too thx

---

### Post by deeptingler on 2006-10-25
Hey Brendon, have just tried that and worked FIRST time!  Much respect :p

---

### Post by chaosgeisterchen on 2006-11-06
Is there yet any fix for it?

---

### Post by strabes on 2006-11-15
My ipod auto mounted in dapper but I now have an install of edgy and it no longer auto mounts. How do I tell what the name of my 2nd partition on my ipod is so that I can fstab it?

---

### Post by chaosgeisterchen on 2006-11-19
This posting could help you out I assume.

> **brendon said:**
> I'm having the same problem with my nano.  I saw that there was a proposed fix for hal ([https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068](https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068)), but it doesn't look like they'll have edgy patched in time.

In the meantime I've been using fstab, but instead of checking dmesg each time the iPod is attached and changing /etc/fstab you can hard code it's by-id path.  Check the /dev/disk/by-id directory for usb-Apple_iPod_XXXXXXXXXXXXXXXX-part2 after you plug in your iPod and use that path instead of /dev/sd*2.  The line in /etc/fstab should look something like:

/dev/disk/by-id/usb-Apple_iPod_XXXXXXXXXXXXXXXX-part2 /media/ipod vfat umask=000,uid=0,gid=0,noauto,rw,user 0 0

---

### Post by Zhukov on 2006-11-22
I made some packages with a patched HAL, in case someone is interested...

---

### Post by Flutterby on 2006-11-23
> **Zhukov said:**
> I made some packages with a patched HAL, in case someone is interested...

I am!  Where can we find them? :)

And will it put a friggin ipod icon on my desktop?

---

### Post by Zhukov on 2006-11-23
Lol, yes it will put a friggin icon on your desktop :D
Let me just upload them somewhere and I'll let you guys know.

---

### Post by Flutterby on 2006-11-23
> **Zhukov said:**
> Lol, yes it will put a friggin icon on your desktop :D
Let me just upload them somewhere and I'll let you guys know.

Awesome, awaiting the upload. :)

---

### Post by Zhukov on 2006-11-23
Here are the packages!

Just a small warning, when I compiled I was dumb enough not to change the version number, so Synaptic tries to "update" the installed packages.

I changed a configuration file on apt-get or Synaptic and Update Manager no longer bugs me with it, but I cant recall exactly which file. I would appreciate if someone could (re-)point it to me.

[http://student.dei.uc.pt/~jpoa/PackagesHAL/hal_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/hal_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-device-manager_0.5.7.1-0ubuntu17_all.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-device-manager_0.5.7.1-0ubuntu17_all.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-doc_0.5.7.1-0ubuntu17_all.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-doc_0.5.7.1-0ubuntu17_all.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal1_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal1_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-dev_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-dev_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage1_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage1_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage-dev_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage-dev_0.5.7.1-0ubuntu17_i386.deb)

Feedback is welcome :)

---

### Post by Confuse on 2006-11-25
Thanks for the .debs! But how do you not make the package appear in update manager? Its the 'hal' package. I tried "lock version" and" force version" but it still wants to upgrade it.

---

### Post by Kingfield on 2006-11-27
> **Zhukov said:**
> Here are the packages!

Just a small warning, when I compiled I was dumb enough not to change the version number, so Synaptic tries to "update" the installed packages.

I changed a configuration file on apt-get or Synaptic and Update Manager no longer bugs me with it, but I cant recall exactly which file. I would appreciate if someone could (re-)point it to me.

[http://student.dei.uc.pt/~jpoa/PackagesHAL/hal_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/hal_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-device-manager_0.5.7.1-0ubuntu17_all.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-device-manager_0.5.7.1-0ubuntu17_all.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-doc_0.5.7.1-0ubuntu17_all.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/hal-doc_0.5.7.1-0ubuntu17_all.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal1_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal1_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-dev_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-dev_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage1_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage1_0.5.7.1-0ubuntu17_i386.deb)
[http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage-dev_0.5.7.1-0ubuntu17_i386.deb](http://student.dei.uc.pt/~jpoa/PackagesHAL/libhal-storage-dev_0.5.7.1-0ubuntu17_i386.deb)

Feedback is welcome :)

Well, when i tried it, it says dependency libc6 unsatisfiable...
(and obviously, i have it installed)

---

### Post by Zhukov on 2006-11-27
This is for Edgy, are you using this version?

---

### Post by Kingfield on 2006-11-28
> **Zhukov said:**
> This is for Edgy, are you using this version?
arrghh [insert profanity here].

dammmmmnnn...

---

### Post by Zhukov on 2006-11-29
You can always make your packages...

---

### Post by Kingfield on 2006-11-30
i got no idea how to use the .debdiff

---

### Post by strabes on 2006-12-03
brendon: you can stop the nautilus window from opening by going to system, preferences, Removable Drives and Media, and then on the Storage tab, uncheckking Browse removable media when inserted. Hope this helps.

---

### Post by Zhukov on 2006-12-03
> **Kingfield said:**
> i got no idea how to use the .debdiff

Ok, I'll help you.

Here:

[https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff](https://wiki.ubuntu.com/UbuntuPackagingGuide/BuildFromDebdiff)

And:

[https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068](https://launchpad.net/distros/ubuntu/+source/hal/+bug/66068)

Don't forget the package you want to patch is HAL, so replace PACKAGE with hal.

Good luck!

---

### Post by Kingfield on 2006-12-05
So troublesome...

---

### Post by Zhukov on 2006-12-05
> **Kingfield said:**
> So troublesome...

Not really.
I didn't even knew debdiff and following the tutorial I was able to get my patched packages within minutes.

What are the problem you're getting so far?

I'm sure we can sort it out :)

---

### Post by Kingfield on 2006-12-06
i dont understand this step

#

Apply the debdiff changes.

    *

      cd PACKAGE-* && patch -p1 < ../DEBDIFF 

#

well, actually i get some lamearse thing about unable to patch

kingfield@kingfield-desktop:~/Desktop/hal-0.5.7$ patch -p1 < ../via-raid-fix.debdiff
patching file debian/changelog
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file debian/changelog.rej
patching file debian/patches/23-fix-via-raid-detection.patch

---

### Post by Kingfield on 2006-12-06
output is :

patching file debian/changelog
Hunk #1 FAILED at 1.
patch: **** Can't rename file debian/changelog to debian/changelog.orig : Permission denied

---

### Post by Zhukov on 2006-12-06
Hmm, I remember having some similar problems.

Try two things:

- Run it as sudo, to make sure it is not a permissions issue

- Check the content of the file hal-0.5.7.1/volume_id/via_raid.c
for something like the text inside the debdiff.

Why? Because I got an error to, but the file was patched successfully, although an error file was created, something like via_raid.err, or alike.

After being sure the file was patched I removed this *.err file and I was able to compile.

Don't give up now, you're nearly there :)

---

### Post by Kingfield on 2006-12-07
oh realy, i got an error msg as well, about saving something to .rej file or something like that, ill try again now

---

### Post by Kingfield on 2006-12-07
yayyy it actually workd, but how come when i named my iPod - iPod, it comes out mounted like IPOD. its just a small mistake, but kinda annoying. is it like a known error, or just a problem with mines?

Thnx Zukovv on advice on deleting the error file. =)

---

### Post by Confuse on 2006-12-07
Does anyone know how to stop update notifier to show the hal package for update? The synaptic method is not working. Thanks.

---

### Post by Kingfield on 2006-12-10
what do you mean?

---

### Post by Zhukov on 2006-12-11
He is talking about configuring the system to ignore the newer packages available in the repos.
I had to change some configuration files (apt-get, aptitude or whatever) to ignore the repo versions, but I don't recall what.

Oh, and congratulations for your packages :D

I also have the IPOD issue.

---

### Post by Kingfield on 2006-12-14
i renamed it back in windows, and now when its back in linux, it just automatically went like that again... :mad:

---

### Post by Zhukov on 2006-12-14
Im not sure if my ipod was renamed... I just think that is the Gnome is giving to the device.

---

### Post by Kingfield on 2006-12-15
well on the contrary, i think it IS renaming it, cuz the windows computer detects it as IPOD as well.

---

### Post by Zhukov on 2006-12-15
Yes, you're right, it is renaming it.
Well, it doesn't bother me at all :D
But i'm sure that there is a solution somewhere...

---

### Post by Kingfield on 2006-12-15
yeah, well it isn't really a problem, oh welllz

---

