---
title: "update breaks my machine again! kernel update + nvidia(this is for help only please )"
date: 2006-09-14
forum: Desktop Environments
---

### Post by robert114 on 2006-09-14
I've updated my machine and the relevant packages that received an upgrade are:
linux-headers-2.6.15-26 (2.6.15-26.46) to 2.6.15-26.47
linux-headers-2.6.15-26-k7 (2.6.15-26.46) to 2.6.15-26.47
linux-image-2.6.15-26-386 (2.6.15-26.46) to 2.6.15-26.47
linux-image-2.6.15-26-k7 (2.6.15-26.46) to 2.6.15-26.47

But the restricted arnt updated and now Nvida won't load!!!

This is the second X failure due to an update I realy hate to say this but in my opinion Ubuntu is NOT ready for the desktop. If updates keeps breaking down my system how can I tell people that Ubuntu is the Windows replacement!

I am very annoyed right now and i will just install the official Nvidia drivers.

I love Ubuntu and the community but things like this make me doubt and it is very very likely that i'm switching distros very soon!!!

my apologizes for my English

---

### Post by Jussi Kukkonen on 2006-09-14
If you ask me, NVidia isn't ready for the desktop :) (not to mention that I don't think Ubuntu is a Windows replacement)

---

### Post by brucevangeorge on 2006-09-14
Haven't you read the Wiki?

It says that anytime you update the kernel, you have to reinstall the drivers. That's why you make sure you got the newest kernel first, THEN you install Nvidia. On TOP.

And why do you have both k7 and 386?

---

### Post by brucevangeorge on 2006-09-14
> **Jussi Kukkonen said:**
> If you ask me, NVidia isn't ready for the desktop :) (not to mention that I don't think Ubuntu is a Windows replacement)

It is for me. And for the average Joe Bob it is not a windows replacement. Not yet... but its ALOT better than the linux distros a few years ago.

---

### Post by robert114 on 2006-09-14
Well, i'm sorry for my language... but, I reeaaly do love linux and i'm a happier man right now because i managed to get the official nvidia driver running but this is really an Ubuntu issue people should really be more carefull when they upgrade the kernel!
All the kernel related packages should be upgraded at the same time.

For an other example take a look at the vmware player modules these aren't updated as well so if somebody installs the vmware player he will find out that after an upgrade vmware doesn't work anymore!
These things are really not acceptable voor a noob linux newby just like my parents... and some friends. How can i defend Linux, and especially Ubuntu when these things happen, i just can't!!! and i really want to distribute Linux and I love the Ubuntu spirit, but this is just unacceptable!

---

### Post by Tom Tiger on 2006-09-14
To me it is the perfect replacement. I run it at work (as one of the few) and I have a lot less problems than my coworkers. I run it at home aswell, for my mail, movies ect...  I do admit I still have one W2K left... but that one is purely for my games.... But wine has taken care of some of those too...

---

### Post by brucevangeorge on 2006-09-14
> **robert114 said:**
> Well, i'm sorry for my language... but, I reeaaly do love linux and i'm a happier man right now because i managed to get the official nvidia driver running but this is really an Ubuntu issue people should really be more carefull when they upgrade the kernel!
All the kernel related packages should be upgraded at the same time.

For an other example take a look at the vmware player modules these aren't updated as well so if somebody installs the vmware player he will find out that after an upgrade vmware doesn't work anymore!
These things are really not acceptable voor a noob linux newby just like my parents... and some friends. How can i defend Linux, and especially Ubuntu when these things happen, i just can't!!! and i really want to distribute Linux and I love the Ubuntu spirit, but this is just unacceptable!

Relax. I'm sure the developers know about this. It will get fixed in time. After all, its only been around for a few years. There will be a new version coming out in October. (Edgy.)

And read the wikis!

---

### Post by robert114 on 2006-09-14
> **brucevangeorge said:**
> Haven't you read the Wiki?

It says that anytime you update the kernel, you have to reinstall the drivers. That's why you make sure you got the newest kernel first, THEN you install Nvidia. On TOP.

And why do you have both k7 and 386?

Well i used the restricted module wich have got the nvidia drivers in it! so no need to reinstall Nvidia the restricted module has got to be updated to the correct version in order to load the restricted Nvidia drivers and more!

Now i should reinstall the Nvidia drivers because i installed the originals from Nvidia.com

the question about my kernels.... the i383 are installed by default and there is no need to remove them! BTW it is allways a good ID to have more than one kernel installed on your system!

---

### Post by neymac on 2006-09-14
The same hapens to me right now.

---

### Post by robert114 on 2006-09-14
Well, you've got 2 options wait for the update of the restricted modules or install the official nvidia drivers ive ignored a few warnings but the official nvidia driver works!

---

### Post by stefan1975 on 2006-09-14
i have the exact same problem. the kernel update broke my system! I have an ATI mobility with the fglrx drivers installed. After the .26 k7 kernel update the drivers aren't running anymore so no more compiz for me :-(

and yes i have uninstalled the old fglrx drivers and after the kernel update installed the latest .26 fglrx drivers AND rebooted the system (again).

any help would be really appreciated, i just love my Compiz and want it back.

---

### Post by Jussi Kukkonen on 2006-09-14
> It is for me. And for the average Joe Bob it is not a windows replacement.

My point was that Ubuntu does not (AFAIK) even try to be a 100% drop-in replacement for Windows, and it could never be one -- there's always that newest word-format, last winAPI change, the latest DRM-music-format or whatever, that isn't supported. Ubuntu and other linux distributions are competitors of Windows, in some areas worse and in some areas superior compared to Windows. Still, it is not a drop-in replacement and will never be one, and telling computer-illiterate people that it is, is just not smart.

robert114, sorry for taking your thread off-topic -- got a little carried away.

---

### Post by neymac on 2006-09-14
> **robert114 said:**
> Well, you've got 2 options wait for the update of the restricted modules or install the official nvidia drivers ive ignored a few warnings but the official nvidia driver works!

How do I install the official nvidia drivers?

---

### Post by robert114 on 2006-09-14
well i suggest you seek an howto it's a pretty nifty job!

you could use this howto:
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

**It depends on your Linux knowledge but i suggest you cross your fingers and hope Ubuntu will fix the kernel modules very soon!**

this way you won't f**k up your system after a new kernel update (when it happens properly)

My problem with a new kernel is that I do have got to reinstall the official 
Nvidia driver!

---

### Post by tofuconfetti on 2006-09-14
Okay, so we don't have to sit on our thumbs waiting for the developers to fix the packaged kernel module, I'll go ahead and install the "official" nvidia module.  I have a few questions.  I've done this oodles of other times on Gentoo and before that Slackware and Mandrake.  However, Ubuntu doesn't install the necessary programs to compile the module.  So which gcc do we need?  I have the "base" for 3.3 and 4.0 installed, but I've had the wrong gcc installed before on other distros and I DO NOT want to screw up this Ubuntu install.  

I've already installed the binutils, does someone know the other exact packages I need to install before I try the official drivers?

Thanks.  BTW, this type of mistake, especially in light of the recent xorg foul up, doesn't do much for the image of Ubuntu.  I still like it a lot, but I really hate having this happen right in the middle of a busy day.

---

### Post by tofuconfetti on 2006-09-14
Scratch that ... the post that hit just seconds before mine answered the question for me.  Thanks.

---

### Post by robert114 on 2006-09-14
to compile the Nvidia drivers just install this package: build-essential
After you've installed it make sure your running kernel headers has been installed as well, i thougt it came with the build-essential package but im not sure!

After you have the build-essential and the kernel headers you've got it all to compile the Nvidia stuff!

**But keep in mind after another kernel upgrade you'll have to reinstall the Official nvidia drivers!!**

anyway you can also take a look at this howto:
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

---

### Post by towsonu2003 on 2006-09-14
here is my take on the issue: 
the kernel we were using was this:  2.6.15-26.46
the kernel update is this:  2.6.15-26.47

now my understanding is that as long as the 2.6.15-26 does not change (i.e. regardless of the number after the period(.) ), restricted modules are not needed to be updated. but everytime you change the kernel version (this time not disregarding the number after the period), you need to recompile kernel modules that you got from a 3rd party (nvidia site, vmware etc). 

in any case, if your restricted modules are not working (the ones you got from our repositories), you need to report a bug so that devels can fix the issue...

---

### Post by jdong on 2006-09-14
This problem is getting fixed and uploaded right now.


As I understand it, the kernel developers decided to skip bumping the ABI of the kernel, assuming that the changes they made do not affect any modules, so they can save the users from the possible inconvenience of rebuilding kernel modules.

However, for some odd reason nvidia.ko was affected, so an updated linux-restricted-modules package needs to be uploaded.



Needless to say, Matt Zimmerman is not at all happy about the way the kernel update was issued....

---

### Post by towsonu2003 on 2006-09-14
here is alink to the bug report, so you can track down what's going on...

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/60433](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/60433)

---

### Post by trakz on 2006-09-14
The sooner the better :) 

Ubuntu rocks, but breaking of X is a very serious issue for most users.

---

### Post by zooperman on 2006-09-14
Happened to me too. The kernel was upgraded to 2.6.15-26 during a routine run of Update Manager and Nvidia wouldn't load afterwards. I fixed fairly quickly by down-revving back to 2.6.15-23. 

The only problem is if this affects the DOZENS of people I have converted to Ubuntu... I really don't want to spend the next few days with my phone ringing off the hook, traveling to repair kernels and doing damage control. #-o

---

### Post by marqs on 2006-09-14
I guess we should be more conservative when new upgrades for the xserver and kernel appear. I've been convincing a lot of people to switch to ubuntu, but this kind of breakdowns are really horrible for those people who can't use linux without X. I hope that the new updates that fix it come soon, until then I'll be using the 386 kernel whihch works for me. I love ubuntu, but these kind of failures make that you have to spend a lot of time fixing things and I need the computer to work.

---

### Post by jdong on 2006-09-14
We are all frustrated by what's happened and all hope it doesn't happen again.... Apparently the new QA measures Mark Shuttleworth has been talking about are not in place yet :-/.... It does not look like anyone outside the kernel team reviewed that update before it was posted.

---

### Post by eledu81 on 2006-09-14
The error I got was:

```

nvidia: disagrees about version of symbol boot_cpu_data
nvidia: Unknown symbol boot_cpu_data
```

Please don't forget to upgrade amd64-k8,

---

### Post by lokimon on 2006-09-14
ok, so i guess at this point we're just waiting for the developers to update the glx module?

my dvr box won't start x-windows with either the 386 or 686 kernel, so i guess i'm stuck either compiling the nvidia driver (i don't want to deal with this) or waiting.

anyone have any idea about how long things like this will take? a day? a month? a week? cause i can live without tv for a day, but my fiancee will be pissed if she gets home tonight and i hosed the dvr cause i was trying to run a standard update.

---

### Post by jdong on 2006-09-14
It should be ready in a few hours.

You could try downgrading the kernel with **sudo apt-get install linux-image-`uname -r`/dapper**.

---

### Post by towsonu2003 on 2006-09-14
> **lokimon said:**
> 
anyone have any idea about how long things like this will take?
the bug report response says it's gonna take at most 24 hours. it usually takes a few hours. less if this is published somewhere (as a news item such as "ubuntu breaks X yet again").

---

### Post by abelthorne on 2006-09-14
> **lokimon said:**
> my dvr box won't start x-windows with either the 386 or 686 kernel, so i guess i'm stuck either compiling the nvidia driver (i don't want to deal with this) or waiting.

anyone have any idea about how long things like this will take? a day? a month? a week? cause i can live without tv for a day, but my fiancee will be pissed if she gets home tonight and i hosed the dvr cause i was trying to run a standard update.

You can try to edit xorg.conf and replace the "nvidia" driver with the "nv" one, although I don't know if it can handle whatever is needed to watch TV on your dvr box (ie functions that are only available with the closed-source nVidia driver).

On the Launchpad page, it's said that a fix will be available in "less than 24 hours"... #-o

---

### Post by pwhite on 2006-09-14
I'm not sure if it's a problem on my end or the servers, but I tried following the directions in the NvidiaManual and was unable to install the linux headers:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.47_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.47_i386.deb)  403 Forbidden

---

### Post by lokimon on 2006-09-14
wow, that sure didn't work... no more error message but the screen is only displaying a bunch of purple noise video

---

### Post by tophfisher on 2006-09-14
This bit me too... MAN THIS SUCKS.. This is my work system... DANG IT.

Its an easy fix to go change the driver from nvidia to nv and fix the issue, but the Windows people in the office laugh at me when they see what looks like a "Linux Crash".

Bummer.. ](*,) 
-Chris

---

### Post by hajk on 2006-09-14
> **robert114 said:**
> I've updated my machine and the relevant packages that received an upgrade are:
linux-headers-2.6.15-26 (2.6.15-26.46) to 2.6.15-26.47
linux-headers-2.6.15-26-k7 (2.6.15-26.46) to 2.6.15-26.47
linux-image-2.6.15-26-386 (2.6.15-26.46) to 2.6.15-26.47
linux-image-2.6.15-26-k7 (2.6.15-26.46) to 2.6.15-26.47

But the restricted arnt updated and now Nvida won't load!!!

This is the second X failure due to an update I realy hate to say this but in my opinion Ubuntu is NOT ready for the desktop. If updates keeps breaking down my system how can I tell people that Ubuntu is the Windows replacement!

I am very annoyed right now and i will just install the official Nvidia drivers.

I love Ubuntu and the community but things like this make me doubt and it is very very likely that i'm switching distros very soon!!!

my apologizes for my English

This is just a common timing problem when a kernel security update is released: what should be sent to the mirrors first, the updated image (with the regular modules), or the restricted-modules? Either way, there is the risk that people upgrade one and don't wait to upgrade the other. I think it makes sense to upload the image to the mirrors first, since there are fewer users of the restricted-modules.
People who don't understand this simple process and start griping right-away about Ubuntu not being ready for the desktop are just not being helpful in the community effort that Ubuntu is. I think that the Ubuntu community would be better off without them... And, yes, pardon my English too (just in case I didn't make myself crystal clear).

Signed: been using Linux from the early days of Slackware (that's about 13 years now).

---

### Post by jdong on 2006-09-14
> **hajk said:**
> This is just a common timing problem when a kernel security update is released: what should be sent to the mirrors first, the updated image (with the regular modules), or the restricted-modules? Either way, there is the risk that people upgrade one and don't wait to upgrade the other. I think it makes sense to upload the image to the mirrors first, since there are fewer users of the restricted-modules.

No, it's not a problem with timing. I explained it earlier. The developers assumed that they did not need to upload a new restricted modules package because the kernel update didn't affect binary compatibility with modules. Unfortunately, they forgot to check the restricted modules, and nvidia happened to be broken by the kernel ABI change.

---

### Post by zooperman on 2006-09-14
> **lokimon said:**
> ok, so i guess at this point we're just waiting for the developers to update the glx module?

my dvr box won't start x-windows with either the 386 or 686 kernel, so i guess i'm stuck either compiling the nvidia driver (i don't want to deal with this) or waiting.

anyone have any idea about how long things like this will take? a day? a month? a week? cause i can live without tv for a day, but my fiancee will be pissed if she gets home tonight and i hosed the dvr cause i was trying to run a standard update.

1) use Synaptic or apt-get to install the old kernel (I down-revved to .23)
2) reboot and select the old kernel from the grub boot screen
3) Optional: use Synaptic or apt-get to remove the .26 kernel but only AFTER you've rebooted into the old kernel

---

### Post by jdong on 2006-09-14
It seems like the archive admins are marking the broken packages as 403/forbidden to block users from getting them until the restricted modules land on the archives.

---

### Post by hajk on 2006-09-14
> **jdong said:**
> This problem is getting fixed and uploaded right now.


As I understand it, the kernel developers decided to skip bumping the ABI of the kernel, assuming that the changes they made do not affect any modules, so they can save the users from the possible inconvenience of rebuilding kernel modules.

However, for some odd reason nvidia.ko was affected, so an updated linux-restricted-modules package needs to be uploaded.



Needless to say, Matt Zimmerman is not at all happy about the way the kernel update was issued....

There are limits to the amount of groveling that I'm willing to accept on this -- there is absolutely no reason for Ubuntu devs to apologize on this. Ubuntu (and all distros since early Slackware) are using a "real-time" updating service, where one upgrade hits the servers after another in serial fashion. Of course, if one happens to upgrade half-way such a chain, then things may get broken once in a while -- it's inherent in the process. It can be avoided by doing it the M$ way, with ServicePacks, do we in Ubuntu want that? I think not, so stop apologizing where there is no reason to, please!

---

### Post by zooperman on 2006-09-14
> **hajk said:**
> This is just a common timing problem when a kernel security update is released: what should be sent to the mirrors first, the updated image (with the regular modules), or the restricted-modules? Either way, there is the risk that people upgrade one and don't wait to upgrade the other. I think it makes sense to upload the image to the mirrors first, since there are fewer users of the restricted-modules.
People who don't understand this simple process and start griping right-away about Ubuntu not being ready for the desktop are just not being helpful in the community effort that Ubuntu is. I think that the Ubuntu community would be better off without them... And, yes, pardon my English too (just in case I didn't make myself crystal clear).

Signed: been using Linux from the early days of Slackware (that's about 13 years now).

I'm not 100% sure of the exact point you are making but for me the kernel update came through the Update Manager.. practically the only method through which most all non-technical users of Ubuntu receive updates. The Ubuntu community would be better off without non-technical users? :-s 

I support dozens of non-technical Ubuntu users whom I've converted. This is a SERIOUS issue for both myself when I have to repair installs and do damage control and for the confidence of non-technical Ubuntu users in the product. Update Manager should NEVER install ANYTHING with dependency issues that break needed applications.

---

### Post by jdong on 2006-09-14
hajk, reread my posts carefully... :)

The problem is not the typical mis-sync of l-r-m and l-i packages, as you are assuming. The problem is that the kernel devs purposely suppressed the building of l-r-m on a faulty assumption that it was not necessary.


I appreciate your forgiving nature, but there is an underlying concern that needs to be addressed, that it seems like once again a QA procedure was not in place or followed when this update was pushed out.

---

### Post by lokimon on 2006-09-14
> **zooperman said:**
> 1) use Synaptic or apt-get to install the old kernel (I down-revved to .23)
2) reboot and select the old kernel from the grub boot screen
3) Optional: use Synaptic or apt-get to remove the .26 kernel but only AFTER you've rebooted into the old kernel

ok i did this, and downgraded the kernel, but that didn't help either

here's the end of my Xorg log file:

```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "ConnectedMonitor" "TV"
(**) NVIDIA(0): Option "TVStandard" "NTSC"
(**) NVIDIA(0): Option "TVOutFormat" "SVIDEO"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Forcing SVIDEO output
(**) NVIDIA(0): TV Standard string: "NTSC"
(WW) NVIDIA(0): Unknown TV Standard "NTSC"; defaulting to "NTSC-M"
(**) NVIDIA(0): ConnectedMonitor string: "TV"
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

also thought this might be relevant from earlier in the log:

```
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.8762
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX

```

as well as this:

```
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.8762
        Module class: X.Org Video Driver

```

---

### Post by hajk on 2006-09-14
> **jdong said:**
> hajk, reread my posts carefully... :)

The problem is not the typical mis-sync of l-r-m and l-i packages, as you are assuming. The problem is that the kernel devs purposely suppressed the building of l-r-m on a faulty assumption that it was not necessary.


I appreciate your forgiving nature, but there is an underlying concern that needs to be addressed, that it seems like once again a QA procedure was not in place or followed when this update was pushed out.

OK, not a simple timing problem then, but I stand by the tenor of my remarks (also made in another thread) that the "real-time" updating service virtually invites this kind of thing happening once in a while. It has since the early days of Debian, and I don't expect it to be much better with a stronger QA effort. The only way to avoid it is to issue a ServicePak every half year or so, like M$, I don't think we want that in Ubuntu. And no, I don't consider myself particularly forgiving, how could you get that idea?;)

---

### Post by zooperman on 2006-09-14
> **lokimon said:**
> ok i did this, and downgraded the kernel, but that didn't help either


hmmm :-k 

One other thing I did was removed/reinstalled nvidia-glx and the restricted modules and oddly, when I went to reinstall it insisted on only installing the 386 modules despite the fact I only have a k7 kernel.

I remedied this by removing nvidia-glx (which also removes restricted modules), installing the k7 restricted modules, then reinstalling nvidia-glx.

Hope that works. :)

---

### Post by hajk on 2006-09-14
> **zooperman said:**
> I'm not 100% sure of the exact point you are making but for me the kernel update came through the Update Manager.. practically the only method through which most all non-technical users of Ubuntu receive updates. The Ubuntu community would be better off without non-technical users? :-s 

I support dozens of non-technical Ubuntu users whom I've converted. This is a SERIOUS issue for both myself when I have to repair installs and do damage control and for the confidence of non-technical Ubuntu users in the product. Update Manager should NEVER install ANYTHING with dependency issues that break needed applications.

I see your problem and don't wish to belittle it. At the same time, I think people should realize that any Linux distro requires a certain amount of care (often using the command line) that is not required by M$ and Apple OSes. And that part of that means repairing some system breakage as a result of an upgrade. This is inherent in the process, in my view, and should not lead to a stream of abuse about Ubuntu not being ready for the desktop and of going to switch to M$.
There are some good words on this in a sticky of the beginners forum (no offence meant).

---

### Post by robert114 on 2006-09-14
> **hajk said:**
> This is just a common timing problem when a kernel security update is released: what should be sent to the mirrors first, the updated image (with the regular modules), or the restricted-modules? Either way, there is the risk that people upgrade one and don't wait to upgrade the other. I think it makes sense to upload the image to the mirrors first, since there are fewer users of the restricted-modules.
People who don't understand this simple process and start griping right-away about Ubuntu not being ready for the desktop are just not being helpful in the community effort that Ubuntu is. I think that the Ubuntu community would be better off without them... And, yes, pardon my English too (just in case I didn't make myself crystal clear).

Signed: been using Linux from the early days of Slackware (that's about 13 years now).

I'm sorry but I'm not a Linux expert but i'm using it for almost three years... I started with Fedora Core (I used it for almost one year). On a distrobution like Fedora Core you could expect these flaws because it is the testing distrobution of red hat. Anyway I never experienced a problem like I have done so in four weeks on Ubuntu... to be more specific Ubuntu 6.06 Long Term Support... (please, make no mistake, I'm not really angry anymore) but it just hurts to me as well that a distrobution which has got Long Term Support and therefore can be considered as stable has got “stability” issues like the one I and many other people do have today.
Ubuntu really needs to test their updates before it hits the repo's. And I'm really looking foolish to my friends to who I've just told how wonderfull Ubuntu is. Not all of my friends are IT-guys and have the knowledge to fix a problem like this when they see a command prompt after they reboot their beloved Ubuntu system!

Edit: I never ment to be offending to anybody! but I really want to make my point clear! I do love Ubuntu that and I do love it that much that I want a lot of other people to experience Ubuntu as well. but at this point I just can't recommend them Ubuntu! I really hope this discussion is being mentioned by a highly placed member of Canonical so it triggers some kind of change in the way Ubuntu releases updates
If Ubuntu wants to take a portion of the marked share of Microsoft (and i hope they still do) and if they want to keep their leadership of the Linux markted they really have to change the way they update the packages!

---

### Post by jdong on 2006-09-14
Alright guys, please try to keep your calm -- I understand it's frustrating, but yelling at each other isn't gonna solve this.


I have posted a front-page forum announcement regarding this issue and also the officially recommended instructions to resolve this issue.

[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by zooperman on 2006-09-14
> **hajk said:**
> I see your problem and don't wish to belittle it. At the same time, I think people should realize that any Linux distro requires a certain amount of care (often using the command line) that is not required by M$ and Apple OSes. And that part of that means repairing some system breakage as a result of an upgrade. This is inherent in the process, in my view, and should not lead to a stream of abuse about Ubuntu not being ready for the desktop and of going to switch to M$.
There are some good words on this in a sticky of the beginners forum (no offence meant).

I think the original "not ready for the desktop" comment really meant "this kind of thing will really freak out a non-technical user and scare them away"

With regards to inevitable breakage of an automatic update system, both of the two big recent breakages were 100% preventable. Outside of the two recent instances the Ubuntu automatic update feature has been very very solid.

---

### Post by lokimon on 2006-09-14
> **zooperman said:**
> hmmm :-k 

One other thing I did was removed/reinstalled nvidia-glx and the restricted modules and oddly, when I went to reinstall it insisted on only installing the 386 modules despite the fact I only have a k7 kernel.

I remedied this by removing nvidia-glx (which also removes restricted modules), installing the k7 restricted modules, then reinstalling nvidia-glx.

Hope that works. :)

nope, no change

---

### Post by robert114 on 2006-09-14
> **zooperman said:**
> I think the original "not ready for the desktop" comment really meant "this kind of thing will really freak out a non-technical user and scare them away"

With regards to inevitable breakage of an automatic update system, both of the two big recent breakages were 100% preventable. Outside of the two recent instances the Ubuntu automatic update feature has been very very solid.

You are totaly right on my part!

---

### Post by lokimon on 2006-09-14
> **jdong said:**
> Alright guys, please try to keep your calm -- I understand it's frustrating, but yelling at each other isn't gonna solve this.


I have posted a front-page forum announcement regarding this issue and also the officially recommended instructions to resolve this issue.

[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

thanks much... it worked, back in business.

thanks for the fast turnaround on the patch.

---

### Post by robert114 on 2006-09-14
Ok I've updated my system and installed the latest kernel stuff!

But as expected my screen didn't work because I installed the Official Nvidia driver. I solved it as described below:

**How to remove the binary Nvidia driver**
For those who have installed the Nvidia binary from Nvidia.com just do the following:
```
sudo /path to nvidia installer /NVIDIA-Linux-x86-1.0-8774-pkg1.run --uninstall
```
Update your system and check weather the kernel stuff and Nvidia GLX is updated
```
sudo apt-get update
sudo apt-get dist-upgrade

```

---

### Post by mdz on 2006-09-14
The vmware player drivers were not available in time to be properly integrated in Dapper, so they may occasionally be out of sync.  In Edgy and beyond, the drivers are now included with the kernel and released in sync.

---

### Post by mdz on 2006-09-14
> **hajk said:**
> This is just a common timing problem when a kernel security update is released: what should be sent to the mirrors first, the updated image (with the regular modules), or the restricted-modules? Either way, there is the risk that people upgrade one and don't wait to upgrade the other. I think it makes sense to upload the image to the mirrors first, since there are fewer users of the restricted-modules.

This was not a timing issue at all, but a bug in the update.  Whenever the module interface changes incompatibly, a new set of packages are generated (e.g., 2.6.15-25 to 2.6.15-26) which do not interfere with the old, and the metapackages (linux, linux-generic, etc.) are updated accordingly so that the packages are upgraded in sync.

---

### Post by mdz on 2006-09-14
> **hajk said:**
> There are limits to the amount of groveling that I'm willing to accept on this -- there is absolutely no reason for Ubuntu devs to apologize on this. Ubuntu (and all distros since early Slackware) are using a "real-time" updating service, where one upgrade hits the servers after another in serial fashion. Of course, if one happens to upgrade half-way such a chain, then things may get broken once in a while -- it's inherent in the process. It can be avoided by doing it the M$ way, with ServicePacks, do we in Ubuntu want that? I think not, so stop apologizing where there is no reason to, please!

I absolutely do apologize on behalf of the development team.  This was human error, plain and simple, and should not have happened regardless of when the update was released.

---

### Post by orb9220 on 2006-09-14
Thank mdz and jdong for your efforts and ubuntu is always timely and fast to resolve these issue's.

Now if this had been OHhhh Let's see another OS Let's pick winXP for instance. Then it would been hours and hourse to define the problem and verify it. Then a statement from microsoft 1 to 7 days to release a  statement verify that there is indeed a problem and they are working on it.

A fix or update when?

You get my drift. So people in the future if you want to get around this. Wait 24hrs before clicking on the little orange star thingy, I do and have missed both of these major mistakes.

And for anyone who wants to complain and whine about this not being ready for masses. Well they are right I find that all the time when a customer calls me a month later and says "I saved a document where is it?". This after I explain to them that they need to spend time learning to get around.

But since this is a FREE OS with FREE apps please be kind in a way of understanding and patience.

For people that are trying to convert others that are not computer savy then please advise them to wait 24hrs before clicking on the "Orange Star Thingy". That is what I tell them and have not had an issue with them so far.

Thanks again for all the Great people here in the forums and The Ubuntu Team.

---

### Post by etotehpii on 2006-09-14
I'm glad I waited and searched the forums about this update.  Whenever I see kernel, xserver, or nvidia I search the forums before saying yes to the update.  I learned my lesson when xserver broke last month.  I'm new to linux and I don't know a lot of the commands and whatnot so its safer to wait certain updates out before appling them.

Perhaps to those like myself who are linux noobs, it would be prudent to wait a couple of days and do a little research before appling upgrades to the kernel or affect the GUI.

---

### Post by robert114 on 2006-09-14
in reply of orb9220:
I do not fully agree with you (no offense of course). Well, first of all a mistake is easily made as a beginning programmer I can fully agree with it and of course it can even go wrong with software after it has been tested... well that is just, shit happens. But this is for me the second time I see a terminal instead of the GUI after I've upgraded Ubuntu Dapper Drake. So this situation doesn't give me the full confidence that the updates are properly tested. And to be honest to you, this situation isn't a real big issue for me because i was able to fix it for my self. But I just love the concept of free software and that is what keeps me coming back!

Now, my point is that I've got the feeling that the software needs to be tested better before it enters the main repos so everybody can update when the packages are available. In my opinion just waiting before updating is proberbly not enough because the still can download the wrong or not all the packages at that time, or did I misunderstood you?

This is just a silly proposal, but maybe there is a need for some kind of  test repositorie on which some users can subscribe to with a wide variety of configuration so that they get a few hours of testing the updates and eventually complaining about faulty updates. This way the normal user hopefully doesn't get confronted with problems as we have seen today.

---

### Post by jdong on 2006-09-14
Ben Collins was expressing frustration that at least for some parts of this kernel update (namely the sky2/sk98lin regression) that a testing package was made available, and has been in Edgy for some time, but nobody seems to care to test it -- not even the ones who originally made the bug report.

---

### Post by tofuconfetti on 2006-09-14
Is this fixed??  I just uninstalled the "official" nvidia module by using the --uninstall parameter after the run script.  Then I reinstalled the nvidia-kernel-common, nvidia-settings, and nvidia-glx.  Xorg still won't start.  What was the fix supposed to be?

I did the above on the recommendation of an earlier post, but on lsmod, I have no nvidia driver present?!?  'modprove nvidia' gives me zilch other than an error message telling me it's not there.

---

### Post by mdz on 2006-09-14
> **tofuconfetti said:**
> Is this fixed??  I just uninstalled the "official" nvidia module by using the --uninstall parameter after the run script.  Then I reinstalled the nvidia-kernel-common, nvidia-settings, and nvidia-glx.  Xorg still won't start.  What was the fix supposed to be?

I did the above on the recommendation of an earlier post, but on lsmod, I have no nvidia driver present?!?  'modprove nvidia' gives me zilch other than an error message telling me it's not there.

The fix was a new version of the linux-restricted-modules package, version 2.6.15-11.4.  See [http://launchpad.net/bugs/60433](http://launchpad.net/bugs/60433) for details.

---

### Post by christxr on 2006-09-14
I recently have been waiting to see if any complaints come up in here for at least a week before updating. I don't see the need to update right away anyway.

---

### Post by robert114 on 2006-09-15
> **tofuconfetti said:**
> Is this fixed??  


Did you allready fixed it? please be sure youre system is completely up to date! all kernel headers and restricted modules check weather they are upgraded
I've updated the following packages to the correct version!
Upgraded the following packages:
linux-restricted-modules-2.6.15-26-386 (2.6.15.11-3) to 2.6.15.11-4 // i don't use this one
linux-restricted-modules-2.6.15-26-k7 (2.6.15.11-3) to 2.6.15.11-4 // AMD k7 only
linux-restricted-modules-common (2.6.15.11-3) to 2.6.15.11-4
nvidia-glx (1.0.8762+2.6.15.11-3) to 1.0.8762+2.6.15.11-4

---

### Post by dr_d on 2006-09-15
oh shite... as i write this im in the middle of updating to the new kernel... i have the proprietary nvidia drivers... are these the ones which are causing problems?

oh well i guess i'll soon find out.

*crosses fingers*

---

### Post by robert114 on 2006-09-15
Everything should be fine by now!

I've updated my system and all works fine now

---

### Post by Bigglez on 2006-09-15
I am confused and the latest update ( 5 minutes ago ) did not result in a working nvidia + X situation.

I have been booting: linux-image-386 2.6.15-**23**.39 for  weeks now because no nvidia drivers work on anything else.

Same today.

So now I am on kernel 2.6.15-23 and nvidia-glx 2.6.15.11-4

I *think*

It's pretty confusing to find those version numbers in the first place.

So, I dunno. I'm so lost it's not funny. I just boot an old kernel and get on with my day. 

:(

---

### Post by The Pinny Parlour on 2006-09-15
Here I go.

I learned my leason with ubuntu updates after the infamous X update/crash ealier this month.  I saw my update light come on this morning and saw what was to be upgraded and thought, 'no way'.  "I will wait".  I'm glad I did.

I have 10 updates sitting in my updates awaiting to be installed.  I'm to afraid to install them.  I have hit the 'check' button several times, but am unable to determined what is the good and what is the bad.  The numbers on the updates seem double dutch to me.

I am deeply sadened that something like this has happened again.  How could it?  How could it after the last major balls-up just several weeks ago?  I really don't want to say it, but ubuntu is lossing face.  Some heads need to roll, it's just not aceptable.  What ever was discussed in the deep, dark bowels of the ubuntu hierachy recently (after the X crash), appears wasted.  I'm trying to hold in my frustration.  I enjoy ubuntu, even though I had a most horrible experience recently with it and curse and screamed every expletive under the sun.   I dearly hope the head-honchos at ubuntu are taking it in turns to kick each others ***.

---

### Post by Bigglez on 2006-09-15
Pinny,
I feel your confusion, but you should keep some perspective. I had the same hassles on Fedora Core with Nvidia vs Kernel updates.

Yeah, I'm confused by this situation, but I also know that Nvidia is a proprietary driver and that we had to  use the Universe (was it?) repo to install it at all - this puts us on the 'unusual' list and stuff breaks when you are out on a limb!

it's not something to rant and scream about. I do hope someone helps me to understand the problem, but I'm not going to panic.

I would let your updates happen, and then make sure you know how to edit your /etc/X11/xorg.conf file so that you can remove the 'nvidia' (replace with 'nv') driver and still boot X. 

OR

Press ESC when rebooting and choose an earlier kernel that way the nvidia driver may still work. That's what I'm doing now.

Good luck.
HTH
:)

---

### Post by Dinerty on 2006-09-15
Right guys is it safe to upgrade to these packages now?

>linux-image-2.6.15026-386
>linux-restricted-modules-2.6.15-26-386
>linux-restricted-modules-common
>nvidia-glx

Will I have to re-install my xgl/compiz set up with these new kernel upgrades?

EDIT: Installed all and booted fine

---

### Post by Bigglez on 2006-09-15
Well, I don't know why I can't get mine working. I have done the update and rebooted, but there is no X. I have had to select the 2.6.15-23 Linux kernel again.

What am I missing here?

---

### Post by godefroy on 2006-09-15
Same here...! Can anyone explain me what im doing wrong?

---

### Post by The Pinny Parlour on 2006-09-15
I just did mine and thankfully, all good.  (I deserved it after the wretched time I had with X crash/update.

You guys might need to do the whole:
sudo apt-get update
sudo apt-get upgrade

[http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459)

---

### Post by zooperman on 2006-09-15
I use the K7 kernel and when I did update/upgrade it only update the linux-restricted-modules with the 386 version... even though I don't have a 386 kernel installed. 

I had to manually install the k7 l-r-m's and manually uninstall the 386 l-r-m's and suffer through a couple reboots before it synced.

Hope this helps somebody :)

---

### Post by Bigglez on 2006-09-15
Well, I have done update and upgrade. 0 New packages installed. As I related earlier - no effect.
I can't reboot right now, so I'll see what the next few days brings. 

A UPS + Linux = never rebooting. I forget what rebooting is. :D

---

### Post by jdong on 2006-09-15
zooperman, that usually means you installed the k7 kernel wrong. Make sure you installed **linux-k7**, and not just **linux-image-k7**.

---

### Post by zooperman on 2006-09-15
> **jdong said:**
> zooperman, that usually means you installed the k7 kernel wrong. Make sure you installed **linux-k7**, and not just **linux-image-k7**.

hmm @ jdong :-k 

let me try that out... thanks for the tip :cool:

---

### Post by zooperman on 2006-09-15
> **jdong said:**
> zooperman, that usually means you installed the k7 kernel wrong. Make sure you installed **linux-k7**, and not just **linux-image-k7**.

UPDATE: installed linux-k7 instead of just the image, rebooted just for giggles and everything looks good.

I feel more existentially pure and clean in a "packaging" kind of way already and am looking forward to a future free of kernel/l-r-m/nvidia unsynchronicity.

Thanks jdong! :)

---

### Post by jdong on 2006-09-15
No problem :). It's quite a common mistake, actually. Personally I'll be glad come Edgy, when there will no longer be the need to install all these k7 and 686 kernel flavors (and hence no chance to make such mistakes!)

---

### Post by tofuconfetti on 2006-09-15
Yep, worked here too.  What was wrong is that I had an incompatible kernel and restricted modules.  When I got the right ones installed, I uninstalled the "official" Nvidia drivers (./NVIDIA*.run --uninstall) and then installed the correct restricted modules, nvidia-glx.  

At first, I killed gdm, loaded what I thought was the correct module (rmmod nvidia, modprobe nvidia) but gdm wouldn't restart.  I rebooted and it worked just fine.  I don't understand that one, but who cares.  Now everything is back up to speed.

Thanks to all on the forum.

---

### Post by statue on 2006-09-15
Second big mistake in a matter of weeks...any distro that gears itself towards those with little linux knowledge should always try to ensure their updates don't break their users X....

---

### Post by karamba_kid on 2006-09-15
I still don't have a desktop with all the latest stuff installed, are fixes still being worked on, or am I going to need to install Debian?  The problem is with nvidia still complaining about au unknown symbol, boot_cpu_data.  Help please!

---

### Post by CaveRat on 2006-09-15
Well this is why I wait to update. The one that broke xorg was the educator for me. Now when I see updates, I come to the Wiki to see if there are any problems from updating. The updates are still sitting there waiting for me to jump. My machine works, so I'm in no hurry. Thank you Devels for the updates and the fixes for those that occasionally break things.

---

### Post by jdong on 2006-09-15
Alright folks,

1) Please stop the complaints about the updates. It's really getting old now -- I think every possible complaint and argument has already been given at least once. We all understand the frustration and let-down this incident has caused.

2) Let's all work towards recovering from this incident. Help each other get our systems back up-and-running, instead of cluttering this thread with more complaining.

---

### Post by statue on 2006-09-15
> **CaveRat said:**
> Now when I see updates, I come to the Wiki to see if there are any problems from updating.

I do the same thing and, like you, the updates are still waiting for me...after xorg I will never install an update until I vist the forums. I just don't think this should be a necessary step though...If you can't trust updates, well, you can't exactly use the argument that ubuntu is more stable than windows...perhaps *as* stable...but certainly not more. I'm thinking about switching distros.

---

### Post by jdong on 2006-09-15
> **karamba_kid said:**
> I still don't have a desktop with all the latest stuff installed, are fixes still being worked on, or am I going to need to install Debian?  The problem is with nvidia still complaining about au unknown symbol, boot_cpu_data.  Help please!

The fix was released and on the mirrors more than 28 hours ago. Have you tried the instructions here: [http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459) ?

---

### Post by CaveRat on 2006-09-15
> **jdong said:**
> The fix was released and on the mirrors more than 28 hours ago. Have you tried the instructions here: [http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459) ?

Jdong please, a question. Would I be better off upgrading the Linux-image-K7, Linux-restricted modules-K7, and Linux-restricted modules-common before I update nvidia-glx? Or do you feel I will be ok to just do all the updates at once?

---

### Post by ~LoKe on 2006-09-15
Not entirely sure what to do here.  I believe I installed the bad kernel yesterday, or whenever, but haven't rebooted since.  However, an hour ago I was updating some things, and decided to reboot.  Now my X Server won't start, and I've tried a few things to get it working.

First of all, I followed the instructions in the sticky for the update (which I probably already have).  I've also tried sudo dpkg-reconfigure xserver-xorg.  I've also tried installing the linux-restricted-modules, as well as linux-386.  I've tried reinstalling the latest drivers using "Envy", but I still can't get the XServer to start.

Any suggestions on where I should go from here?  Also, is it possible to burn an ISO via the terminal?  I've got the Edgy Knot release ISO, and I figure now's the best time to try it out.

**EDIT:** Oops, fixed.

---

### Post by jdong on 2006-09-15
> **CaveRat said:**
> Jdong please, a question. Would I be better off upgrading the Linux-image-K7, Linux-restricted modules-K7, and Linux-restricted modules-common before I update nvidia-glx? Or do you feel I will be ok to just do all the updates at once?

All at once should be just fine.

---

### Post by Jado on 2006-09-15
Hi, I'm running from the Live CD. I guess I installed some of the bad updates from earlier today. I'm not sure. But when I was asked to restart, and did so, my computer is now at a screen with "grub>" where the command-line remedies I've seen in sticky won't even work. What do I do to fix this? Any help would be appreciated.

---

### Post by OffHand on 2006-09-15
I really cannot under stand how the hell this could happen after the Xorg disaster. They really should go sit around the table and take some serious precautions. Very unprofessional... second time within a month or something.


P.S. It didn't not affect me.

---

### Post by karamba_kid on 2006-09-15
> **jdong said:**
> The fix was released and on the mirrors more than 28 hours ago. Have you tried the instructions here: [http://ubuntuforums.org/showthread.php?t=257459](http://ubuntuforums.org/showthread.php?t=257459) ?

Yeah I have applied all those updates.  Nvidia is still complaining about an unknown symbol boot_cpu_data.  I believe there are still problems with the latest linux-restricted-modules. 
"sudo apt-get update; sudo apt-get dist-upgrade" shows no more updates avalible.  I'm considering moving to Debian but would really just like to have this issue resolved seeing that I just installed dapper a month ago.  I'm all out of ideas I have run the reconfigure scripts for xserver and looked over my xorg.conf file but still no go.  I need a fix, please.

---

### Post by jdong on 2006-09-15
Are you sure you have the right kernel package installed then? Sounds like an incomplete update still.

For each kernel flavor installed, make sure linux-flavor is installed.

For example, if you only have the 386 kernel, install linux-386. If you have 686, install linux-686 also, and so on.

---

### Post by karamba_kid on 2006-09-15
> **jdong said:**
> Are you sure you have the right kernel package installed then? Sounds like an incomplete update still.

For each kernel flavor installed, make sure linux-flavor is installed.

For example, if you only have the 386 kernel, install linux-386. If you have 686, install linux-686 also, and so on.

Yes I do, "linux-686 is already the newest version"

---

### Post by OffHand on 2006-09-15
Where did my post go?

---

### Post by jdong on 2006-09-15
Hmm, that is quite strange. Does the 386 kernel boot up for you?

---

### Post by karamba_kid on 2006-09-15
> **jdong said:**
> Hmm, that is quite strange. Does the 386 kernel boot up for you?

Well i should try to boot the 386 kernel up again, but I think when i tried it last night it didn't show up in my grub menu even though it is not commented out. I was able to get the 2.6.15-23-686 kernel to boot and the nvidia-glx modual worked there, however I think the restricted drivers for that kernel didn't work with my wifi card as well as the latest kernel does.  With the latest update sudo modprobe nvidia returns and error message and I think that is where my problem is coming from.

---

### Post by The Pinny Parlour on 2006-09-15
> **jdong said:**
> Alright folks,

1) Please stop the complaints about the updates. It's really getting old now -- I think every possible complaint and argument has already been given at least once. We all understand the frustration and let-down this incident has caused.

2) Let's all work towards recovering from this incident. Help each other get our systems back up-and-running, instead of cluttering this thread with more complaining.

jdong I agree, but don't take offence when I say that everyone has a right to express their opinion on this matter.  Many people may well be tiring of ubuntu's errors.  There is nothing old about complaining constructively about something which really should not happen.   If I want to express my dissapointment at something I will.

---

### Post by jdong on 2006-09-15
> **The Pinny Parlour said:**
> jdong I agree, but don't take offence when I say that everyone has a right to express their opinion on this matter.  Many people may well be tiring of ubuntu's errors.  There is nothing old about complaining constructively about something which really should not happen.   If I want to express my dissapointment at something I will.

Certainly you are free to express your your opinions and frustration -- just not in this thread, please. There are still people who have broken systems, and the complaints are just cluttering up the thread and creating more havoc.


If you want to start a new thread in the lounge to discuss what happened with regards to the broken updates, that's perfectly fine with me. Let's stay strictly on helping get broken systems back online in this thread.


Thanks!

---

### Post by Jado on 2006-09-15
So no one knows anything about this grub> thing? My computer stays there and nothing loads up, not even Linux sans X GUI. Only a message saying that pressing TAB will bring up a list of limited BASH-like commands.

---

### Post by artinla on 2006-09-15
I would suggest that it is wise to lock your kernel version in synaptic until you are sure that the update isn't going to break anything.

---

### Post by zooperman on 2006-09-15
> **Jado said:**
> So no one knows anything about this grub> thing? My computer stays there and nothing loads up, not even Linux sans X GUI. Only a message saying that pressing TAB will bring up a list of limited BASH-like commands.

Jado, you are the first i've heard of related to the kernel update with a boot stuck at the grub prompt.

Being stuck at the grub prompt sounds more like the kernel is missing or not linked promptly... or.. at least something different than the kernel/restricted-modules/nvidia update thing.

Not sure. Wish I could help.

---

### Post by Zyzzyx on 2006-09-15
> **artinla said:**
> I would suggest that it is wise to lock your kernel version in synaptic until you are sure that the update isn't going to break anything.
Hmm, like this idea.

Is the *linux-image-2.6.15-26-386* the only package that I should be locking? Or some of the other libraries too?  Maybe the Nvidia GLX package too?

---

### Post by zooperman on 2006-09-15
> **Zyzzyx said:**
> Hmm, like this idea.

Is the *linux-image-2.6.15-26-386* the only package that I should be locking? Or some of the other libraries too?  Maybe the Nvidia GLX package too?

In this instance the problem was the kernel got upgraded while the restricted  modules weren't. A variable/symbol name in the kernel that was referenced in  the nvidia restricted module changed and an updated restricted module package was not released along with the kernel update. 

So, in this particular case locking the kernel would have prevented the loss of X. 

No guarantees (or probably even the likelihood) that any future update snafu's will involve a kernel/restricted-module dependency.

---

### Post by houstonbofh on 2006-09-16
> **jdong said:**
> If you want to start a new thread in the lounge to discuss what happened with regards to the broken updates, that's perfectly fine with me. Let's stay strictly on helping get broken systems back online in this thread.
One could argue that the update process is the broken system.  And the bug fix...  After all, to find the solution you need to access the forum that requires a graphical web browser.  For many of us supporting Ubuntu with non-technical users, this was a loss of face for us as well.  As to the suggestion of waiting 24 hrs to "hit the star thing..."  Consider an update to a font on Tuesday, and an update that shatters the system on Wednesday.  There is no way to tell in the update GUI how old an update is.

And to address the grub lock, you may need to boot to a console from the CD and chroot to your system.  The find out if you have a kernel at all.  As already stated, that is usually grub pointing to empty space.

---

### Post by karamba_kid on 2006-09-16
Jdong- I was able to boot into the 386 kernel with nvidia-glx support.  Thanks for the suggestion.  There must still be some issues with the 686 kernel and nvidia-glx.  Has anyone been successfull with booting those two together? I sure couldn't get it working.

EDIT: Oh wow the ubuntu gods must have heard me :) new linux-restricted-modules-2.6.15-26-686 and nvidia-glx packages just showed up in the repos.  I'm about to go try these out now. Thank you very much ubuntu developers.

---

### Post by Jado on 2006-09-16
Sorry, I don't understand a few things you said, houstonbofh. Boot to a console from the CD? Chroot my system? The rest I get, I suspected Grub was pointing to nothing from what I've gathered reading around. If I do find that I have no kernel, would there be a way to restore it without doing a reinstall of Ubuntu?

---

### Post by karamba_kid on 2006-09-16
> **karamba_kid said:**
> Jdong- I was able to boot into the 386 kernel with nvidia-glx support.  Thanks for the suggestion.  There must still be some issues with the 686 kernel and nvidia-glx.  Has anyone been successfull with booting those two together? I sure couldn't get it working.

EDIT: Oh wow the ubuntu gods must have heard me :) new linux-restricted-modules-2.6.15-26-686 and nvidia-glx packages just showed up in the repos.  I'm about to go try these out now. Thank you very much ubuntu developers.

Quoting myself, but just wanted to meantion that the very newest updates I just mentioned sill didn't let xserver start with the 686 kernel.

---

### Post by CaveRat on 2006-09-16
> **jdong said:**
> All at once should be just fine.

Cool beans. Did what you suggested, crossed my fingers, rebooted, and whalla. I have a normal running system. Seems like getting around on the net is a little more responsive now too. Thanks again to the Devels and to you Jdong for your patients and calm demure over this issue. Now to see what kind of offerings the Automatix update brings. Chow!

---

### Post by houstonbofh on 2006-09-21
> **Jado said:**
> Sorry, I don't understand a few things you said, houstonbofh. Boot to a console from the CD? Chroot my system? The rest I get, I suspected Grub was pointing to nothing from what I've gathered reading around. If I do find that I have no kernel, would there be a way to restore it without doing a reinstall of Ubuntu?

I hope you actually solved this by now, but I thought I would answer for the search function.  If you can use grub to get to an older kernel, and bring up a gui, Synaptic can be used to remove and reinstall your kernel of choice.
If you have no kernel on the system, use apt-get from a rescue console to install a 386 kernel.  Then grub into it, and do the step above.

PS:  Saw a kernel patch today.  I was nervous. :-o I did reboot without incident. :)

---

### Post by Rodneyck on 2006-12-13
Well, this just happened to me. I updated to the latest kernel modules without actually thinking or really knowing what would happen. I think the latest udates are for the 2.6.17-1 or something like that found in the update manager. They do not work with the latest nvidia drivers. Had to uninstall beryl, then the nvidia drivers to get into x server.

I am now using the "nv" drivers. I will read through this thread, just scanned it for now, so hopefully there are some answers or help for me. 

I must say, this is not something that will win over a Windows or other OS user. Nothing like getting a black screen and not knowing what to do.

---

### Post by jdong on 2006-12-13
```

linux-restricted-modules-2.6.17-10-generic | 2.6.17.5-11 | edgy/restricted | i386
linux-restricted-modules-2.6.17-10-generic | 2.6.17.5-11 | feisty/restricted | i386
linux-restricted-modules-2.6.17-10-generic | 2.6.17.6-1 | edgy-security/restricted | i386

```
The repositories show that the new linux-restricted-modules is indeed available.

Do you have the metapackage **linux-generic** installed?
If you run **apt-cache policy linux-restricted-modules-2.6.17-10-generic**, does it show the last version I posted above?

---

### Post by Rodneyck on 2006-12-13
this is what i get...

linux-restricted-modules-2.6.17-10-generic:
  Installed: 2.6.17.7-1
  Candidate: 2.6.17.7-1
  Version table:
 *** 2.6.17.7-1 0
        500 [http://albertomilone.com](http://albertomilone.com) binary/ Packages
        100 /var/lib/dpkg/status
     2.6.17.6-1 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
     2.6.17.5-11 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages

---

### Post by jdong on 2006-12-13
Can you please post output to
```

apt-cache policy nvidia-glx

```

Also, post any errors you get when trying to start nvidia drivers, such as

modprobe nvidia
(post dmesg output too)


When GDM fails and tells you where it saved its xorg.log, please post a copy of that too.

thanks in advance!

Trying to get to the bottom of this.

---

### Post by Rodneyck on 2006-12-13
Well as I said, I (think) the beta or latest nvidia drivers are now uninstalled, using "nv" in the xorg.conf.

here is the output..

nvidia-glx:
  Installed: 1.0.9629+2.6.17.7-1
  Candidate: 1.0.9629+2.6.17.7-1
  Version table:
 *** 1.0.9629+2.6.17.7-1 0
        500 [http://albertomilone.com](http://albertomilone.com) binary/ Packages
        100 /var/lib/dpkg/status
     1.0.8776+2.6.17.6-1 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages
     1.0.8774+2.6.17.5-11 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
rodney@rodney-desktop:~$

---

### Post by jdong on 2006-12-13
Thanks for your help.

Can you try:
```

sudo rmmod nvidia
sudo modprobe nvidia
find /lib/modules/`uname -r` -name nvidia.ko

```

and post the output(s)

---

### Post by Rodneyck on 2006-12-13
Here is my xorg error log file.. see attachment.

---

### Post by jdong on 2006-12-13
Try running **sudo depmod -ae** and reboot, see if that fixes your problems.

---

### Post by Rodneyck on 2006-12-13
> **jdong said:**
> Thanks for your help.

Can you try:
```

sudo rmmod nvidia
sudo modprobe nvidia
find /lib/modules/`uname -r` -name nvidia.ko

```

and post the output(s)

Here you go...

ERROR: Module nvidia does not exist in /proc/modules
rodney@rodney-desktop:~$ sudo modprobe nvidia
Not loading nvidia module; not used in /etc/X11/xorg.conf
rodney@rodney-desktop:~$ find /lib/modules/`uname -r` -name nvidia.ko
/lib/modules/2.6.17-10-386/volatile/nvidia.ko
rodney@rodney-desktop:~$

---

### Post by jdong on 2006-12-13
Can you please try those commands again with nvidia set in xorg.conf ?

---

### Post by Rodneyck on 2006-12-13
> **jdong said:**
> Can you please try those commands again with nvidia set in xorg.conf ?

Ok, well I could not boot into x server, so I had to boot in with the "generic" setting. It gave me the same thing...

ERROR: Module nvidia is in use
rodney@rodney-desktop:~$ sudo modprobe nvidia
rodney@rodney-desktop:~$ find /lib/modules/`uname -r` -name nvidia.ko
/lib/modules/2.6.17-10-generic/volatile/nvidia.ko

---

### Post by jdong on 2006-12-13
Please post "dmesg | grep NVIDIA" output

Also, "ls -al /usr/lib/libGL.so.1"



I realize you can't start xorg with nvidia, but nvidia.ko won't show its error messages without having xorg.conf read nvidia.

---

### Post by Rodneyck on 2006-12-13
> **jdong said:**
> Please post "dmesg | grep NVIDIA" output

Also, "ls -al /usr/lib/libGL.so.1"



I realize you can't start xorg with nvidia, but nvidia.ko won't show its error messages without having xorg.conf read nvidia.

Odd, neither one of these typed into Terminal returns anything.

---

### Post by Roque on 2006-12-13
Rodney:

I think you must edit your xorg.conf, enable the "nvidia" driver  
(comment out the "nv" thing) and reboot. Then issue all these commands in the tty console (ie. not with gdm, which won't run anyways).

---

### Post by Rodneyck on 2006-12-13
> **Roque said:**
> Rodney:

I think you must edit your xorg.conf, enable the "nvidia" driver  
(comment out the "nv" thing) and reboot. Then issue all these commands in the tty console (ie. not with gdm, which won't run anyways).

Thanks.  That is exactly what I did.  Although when I reboot, it will not start up x server (black screen) so then I rebooted and got the grub option for "generic" and it boots into x server.  I ran the lines again in Terminal and got nothing in return.

---

### Post by Roque on 2006-12-13
Once you get that black screen, you should be able to start a tty console by pressing ctrl-alt-f1 to ctrl-alt-f4. I'll try this later and post the results.

---

### Post by Roque on 2006-12-13
> **jdong said:**
> Thanks for your help.

Can you try:
```

sudo rmmod nvidia
sudo modprobe nvidia
find /lib/modules/`uname -r` -name nvidia.ko

```

and post the output(s)
```

sudo modprobe nvidia

```
Said the module couldn't be loaded (or something akin).
```

find /lib/modules/`uname -r` -name nvidia.ko

```
/lib/modules/2.6.15-27-386/kernel/drivers/video/nvidia
(I am not using 2.6.17 because it claims it doesn't support PPPoE (?!)

I followed your advice and did:
```

depmod -ae

```
and now I have full hardware acceleration again.

---

### Post by infoseeker on 2006-12-15
I must note that I had the same problem when updating the kernel. Previously I had the generic kernel installed (off the alternate edgy CD), and I simply could not get the X server configured correctly using the following instructions ---->

[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

Issuing ```
depmod -ae
``` at the command prompt finally fixed my problem. Thanks.
PS.  The upgrade installed kernel ```
2.6.17-10-386
```

---

