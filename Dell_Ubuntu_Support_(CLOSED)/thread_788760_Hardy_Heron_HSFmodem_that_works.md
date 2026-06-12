---
title: "Hardy Heron HSFmodem that works"
date: 2008-05-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by showgun22 on 2008-05-10
After a lot of searching and trying I found something which seems to work just fine in  Ubuntu Hardy

I have not tested it but GnomePPP & KPPP does find the modem.

So hope the following will work for you if so post your comments.

 

The file I have found which made the difference is on linuxant

you will need this file

[http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.16.1-1_all.deb](http://www.linuxant.com/alsa-driver/alsa-driver-linuxant_1.0.16.1-1_all.deb)

It states

We provide a version of the alsa-driver package (from the ALSA project) with improved support for the HSF driver. This should be installed only if you have a HDA modem and the built-in ALSA HDA modules of the HSF driver either doesn't work or have a negative impact on your HDA sound device. It should be used with version 7.68.00.07 or later of the driver.

Before installing this package, make sure that you have the gcc and make packages installed. Additionally, the kernel headers are also needed, this is the linux-headers package in recent Debian and Ubuntu releases, kernel-devel in Fedora and Red Hat Enterprise Linux, kernel-source in Mandriva and SuSE

select reload

after which you reboot and install the Dell drivers

[http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb](http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem_7.68.00.09oem_i386.deb)

reload and reboot

In my case it did the trick

Good luck

---

### Post by Paul S on 2008-05-10
Thanks, Rick, it might just be the fix here.  I installed the new hsfmodem driver from Dell and it didn't work ("modem busy") and it killed my sound.  I have an E1505, that worked fine under gutsy.

So, I'll try this alsa driver update and see if it's the fix.

I'm thinking this would be a good bug item for launchpad?  What do you think?

---

### Post by showgun22 on 2008-05-10
It would be nice to have a couple feed back on this to confirm it is working for a couple more case.


What does puzzle me is why Dell has not picked up on this first.

I am not sure why it should be a bug since those drivers are for linuxant but if it should be they have the fix now...

Let me know how it turns out and you might have to do a complete remove of old HSF and then start the install of alsa first...
Good luck

---

### Post by Paul S on 2008-05-10
Yes it does work now with the alsa driver from linuxant.  And sound works too.

fwiw, I tried applying the patch from [http://www.linuxant.com/alsa-driver/alsa-driver-1.0.16-2.patch](http://www.linuxant.com/alsa-driver/alsa-driver-1.0.16-2.patch) to the alsa-source hardy package sources, but 3 hunks failed.  So I didn't try to compile it to make my own.  Would be nice if linuxant and alsa could work together better.  What will we do if an alsa secuity update comes out during the next 3 years .. it'll kill sound and the modem and we won't have a fix.

thanks,

---

### Post by showgun22 on 2008-05-10
Linuxant does it for the money
Alsa open source

AS far as I am concern I do not use the modem I am on high speed but it thicks me off to have hardware not working when it should be. I paid for it and believe it should work no matter what.

As far as buying Linuxant this is something I totally refuse to do. I believe I paid for that modem and there should be support no matter which OS I use.

Hopefully with in a few years there will be a little genius coming out of the closet with a Linux applet that will do an automatic recompile of programs on upgrade to ensure continuous  workability...<BG>

The important thing is that it now works...

I hope it will work for others

---

### Post by hasta2003 on 2008-05-11
It works for me!
I have an Acer Aspire 5920G with Ubuntu 8.04 64bit.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

thank you.. I'll report this thread in the "how-to linux on AS5920G" that I'm going to write. :lolflag:

---

### Post by Paul S on 2008-05-11
> **showgun22 said:**
> 
What does puzzle me is why Dell has not picked up on this first.


I just notice this repo by Dell for hardy:

[http://ppa.launchpad.net/dell-team/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/](http://ppa.launchpad.net/dell-team/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.24/)

and instructions how to use it at [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Update_Dell_PPA_Entry).

But, I'm already at linux 2.6.24-17, and they don't have a package for this kernel yet.  I downloaded and looked at the contents of the package for the 2.6.24-16 kernel and it does have an alsa module in it.  If you still have the 2.6.24-16 kernel installed, perhaps you can try it (uninstall hsfmodem, alsa-driver-linuxant, reboot, add dell PPA to sources.list, upgrade to install their modules package, reinstall hsfmodem and reboot).

regards,

---

### Post by showgun22 on 2008-05-11
Tried that first it did not work but the method I listed in the original post works great even in latest kernel linux 2.6.24-17

---

### Post by laszlo462 on 2008-05-15
What if I have already broken the sound using the modem driver?  I didn't use the deb package this time....so I can't remove it using synaptic...oops.  I used the tarball and ran 'make install'.  Is there a way to undo what 'hsfconfig' did to the sound?  I tried reinstalling alsa, as well as the linuxant alsa drivers but that did not seem to work.  I did get the logon sound while installing the linuxant version, but the volume control with the red x never changed, and there is no sound after that.

---

### Post by laszlo462 on 2008-05-15
Ok, so I got sound back.  So I got the linuxant-alsa driver installed.  I rebooted and the sound was still working.  After installing the hsfmodem package however, I still have no sound.  I rebooted after installing both.  Was this the correct order to install these?  Let me know, I would really love to get this working, since I live in the middle of nowhere with only dial-up access at home.

---

### Post by showgun22 on 2008-05-15
YOu might want to do the 3 known issue
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues](http://linux.dell.com/wiki/index.php/Ubuntu_8.04#Known_Issues) 

After which retry installing as suggested at the beginning...

---

### Post by laszlo462 on 2008-05-15
Retry the hsfmodem package?  Or both packages?

---

### Post by showgun22 on 2008-05-15
did you do the 3 steps on the link I posted?
If so redo the complete install
as in the post states at the beginning

---

### Post by laszlo462 on 2008-05-15
During the apt-get upgrade

Errors were encountered while processing:
 alsa-driver-linuxant
E: Sub-process /usr/bin/dpkg returned an error code (1)

EDIT: OK, I'll give it a try.

---

### Post by laszlo462 on 2008-05-15
Yea I wasn't sure what you meant my reinstall, if it was both or what.  But it worked!  Thanks for the assistance!

---

### Post by showgun22 on 2008-05-15
So the last bit did the trick..
I am glad to see it did work.
Pass the word along...

---

### Post by nutpants on 2008-05-18
great info..
worked for my dell 1210 modem


thank you

nutz

---

### Post by Repgahroll on 2008-09-11
**Thank you very much Rick!!**

Now we have another LTS working! :D

Nice info man! Thanks!

---

### Post by showgun22 on 2008-09-11
PS let us know on which laptop model it works just for ref....
Thanks

---

### Post by tjustleft on 2008-10-20
Hello everyone. First I'll say I am new to Ubuntu or any Linux os and have no clue what I am doing. I just installed Ubuntu 8.04.1 LTS from ShipIt. First off I am trying to get my conexant modem going so I can update.

I have come across info on this Dell driver a few times. Some post seem to say but never do that this driver may work on other machines. Is this the case? I am using an older compaq presario 5000. If not I have also downloaded the driver from the Linuant site for Hardy.

I read this: > Before installing this package, make sure that you have the gcc and make packages installed. Additionally, the kernel headers are also needed, this is the linux-headers package in recent Debian and Ubuntu releases, kernel-devel in Fedora and Red Hat Enterprise Linux, kernel-source in Mandriva and SuSE.

_I have no idea how to make sure I have gcc and make packages or how to get and install them if I don't._ If I need to download them I can boot to xp. After I get this somewhat figured out I have to do it all over. I am just testing it so I can put it on a machine for my daughter. Her's fried. I got a machine put together for her but can't afford to buy windows for her so I was hoping this to be a great or even better alternative.

Like I say I have no idea what I'm doing so anyone explaining it may have to break out the crayons. :) Thanks in advance just for reading all that.

---

