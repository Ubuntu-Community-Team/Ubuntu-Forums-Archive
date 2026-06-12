---
title: "2 GB Memory on Dell Mini 9"
date: 2008-12-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rneindorff on 2008-12-04
Does the latest version of Ubuntu Linux on the Dell Mini 9 support 2 GB of memory?  I have searched the threads and seem to find that the BIOS does but the first Mini 9's were shipped with a Ubuntu Remix that could only use the 1 GB that Dell supplied.
Using 2 GB would cut down or eliminate any swapping to the SSD, a desirable feature, and MS shouldn't care that Linux could use 2 GB. You can already get a 32 GB SSD on the Linux model.

---

### Post by notwen on 2008-12-04
The BIOS is not what is limiting the RAM. The LPIA kernel Dell used in the Mini 9's custom Ubuntu image is what limits the amount of RAM.  I personally re-installed a vanilla install of Ubuntu to get full usage of my 1GB of ram and plan on upgrading it to 2GB sometime after the holidays.  Hope this helps.  =]

---

### Post by Rallg on 2008-12-05
I have the mini 9, XP version but with Ubuntu 8.10 as dual boot from standard Ubuntu distro. Took out the 1G, put in 2G. Works great, both systems. My particular 2G was made by Crucial.

In Ubuntu, consider using /dev/shm as a virtual ramdisk for programs (such as GIMP) that use temporary storage. I don't know much about it; just trying it. If you also have the XP version, you can find a free ramdisk program somewhere, for the same purpose. I wouldn't do these things with only 1G memory.

---

### Post by 2damncommon on 2008-12-06
I am running the default Mini 9 Ubuntu and I finally recompiled the kernel to use my 2GB RAM.

---

### Post by runningdoc on 2008-12-06
> **2damncommon said:**
> I am running the default Mini 9 Ubuntu and I finally recompiled the kernel to use my 2GB RAM.
Wow, this is the first time as I have surfed all the threads on the mini9 that someone has mentioned they successsfully recompiled the kernel to utilize the full 2gb in the dell version of 8.04.  I am new to ubuntu and cannot do this myself, when will the fix become available to everyone?  On that note, I am noticing many complaining that the mini9 repository is not being updated with security patches, browser updates, ect.  Is this being addressed as I have not seen any new posts on it.  Thank you.  I am brand new to Ubuntu and have read many posts and decided to subscribe tonight.

---

### Post by rneindorff on 2008-12-07
> **2damncommon said:**
> I am running the default Mini 9 Ubuntu and I finally recompiled the kernel to use my 2GB RAM.

Is there a thread that lays out the steps required to remove the 1 GB limitation and then to recompile the kernel supplied by Dell? I have seen it can be done by downloading the "real Ubuntu" then trying to get the Dell drivers to fix what doesn't work.
Personal opinion: DELL SHOULD REALLY FIX THIS!  I guess I will just continue to use my D620 which I dual boot between XP and Ubuntu.

---

### Post by iggykoopa on 2008-12-07
you could look into kernelcheck, thats how I recompile kernels... the option your looking for is called highmem. On the dell version it's off, you wanna change it to 4.

---

### Post by kodemage on 2008-12-08
I'm trying to follow these instructions for re-compiling my kernel to use the 2gb memory chip I installed. 

<http://www.howtoforge.com/kernel_compilation_ubuntu_p2>

I'm at the step:

make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers 

and I get the error:

debian/ruleset/misc/checks.mk:36: *** Error. I do not know where the kernel image goes to [kimagedest undefined] The usual case for this is that I could not determine which arch or subarch this machine belongs to. Please specify a subarch, and try again..  Stop.

I tried googling to find what I need to add to the make-kpkg command. I tried -arch i386 but that resulted in different errors.

I'm subscribed to the thread via e-mail so I can respond if there's any information.

I'd also love an alternate method to simply replace the dell kernel with a stock ubuntu kernel, maybe via a package in synaptic package manager or something similar.

Regards,
-Benjamin

---

### Post by iggykoopa on 2008-12-08
heres the webpage of kernelcheck [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) thats what I use it's pretty simple. Also your architecture is going to be lpia (low power intel architecture)

---

### Post by kodemage on 2008-12-08
specifying the "--arch lpia" or "--arch=lpia" results in the same error. Dratz. 

The Kernelcheck .deb gives me an unresolvable dependency error which requires python 2.4. The default dell distro comes with python 2.5 so I'm at a loss what to do there. 

I'm going to try a couple more things and then give up. 

I'm looking into installing ubuntu from a flashdrive, which could be made easier, despite the hassle of the several significant known issues. I'd rather not re-install the OS, <sarcasm weight=light> I have it all set up the way I like it and it'll take me hours to get it back there when I re-install. </sarcasm>

Regards,
-Benjamin

---

### Post by runningdoc on 2008-12-08
> **iggykoopa said:**
> heres the webpage of kernelcheck [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/) thats what I use it's pretty simple. Also your architecture is going to be lpia (low power intel architecture)
Thanks for the information on recompiling.  My question is to where a newbie like myself might look for help. I don't gave any experience with building code for operating systems and could easily see this becoming a big mess.  Is it easy enough that I just download the kernelcheck software and change one line to the number 4?  I doubt it and hesitate to go down this road.  Should I just wait for Dell to release a fix (and will they as it seems it would violate the agreement with Microsoft)? 

Thanks

---

### Post by 2damncommon on 2008-12-08
> **rneindorff said:**
> Is there a thread that lays out the steps required to remove the 1 GB limitation and then to recompile the kernel supplied by Dell?
I got the same errors as you when trying the "correct Ubuntu method" of compiling the kernel.

[Check this thread.]("http://ubuntuforums.org/showthread.php?t=982983")

I was grateful for cmspider's reply. Also check my followup. You do need to run "depmod -a".

---

### Post by iggykoopa on 2008-12-09
kernelcheck handles most of it automatically for you. The only confusing part is the kernel config, but as long as your just changing the highmem support just don't change any other options and you'll be fine(it pulls the config from the currently running kernel). If you do something wrong you always have your old kernel to go back to, so it'll be a good learning experiance.

---

### Post by runningdoc on 2008-12-09
Thanks for the support.  I will try it and let you know.

---

### Post by ffreitas on 2008-12-19
This was based on the posts made by cmspider and 2damncommon on the threads [http://ubuntuforums.org/showthread.php?t=982983](http://ubuntuforums.org/showthread.php?t=982983) and [http://ohioloco.ubuntuforums.org/showthread.php?t=1001898](http://ohioloco.ubuntuforums.org/showthread.php?t=1001898), hopefully it will be useful for other new Mini 9 ubuntu users such as myself :-)

Mini 9 Kernel Re-compile for 2 GB ram:

- Open a terminal
- Enable root login using the command:
sudo passwd root

- Change to the root user and then execute the following commands:
su 
lsmod > /tmp/modules.old
apt-get install linux-source
apt-get install build-essential
apt-get install libncurses5-dev
cd /usr/src
tar -jxvf linux-source-2.6.24.tar.bz2
cd linux-source-2.6.24
cp /boot/config-2.6.24-19lpia .config
make oldconfig
make menuconfig 

- In the menu that opens, go to "Processor Type and Features", enter the option "High Memory Support (off)", select the option 4GB, exit and save.
- Execute the follwing commands:
make
make modules_install
cp arch/i386/boot/bzImage /boot/vmlinuz-2.6.24.3
cp .config /boot/config-2.6.24.3

cd /lib/modules
cp -r 2.6.24-19lpia/volatile 2.6.24.3
cp -r 2.6.24-19lpia/ubuntu 2.6.24.3
update-initramfs -u -k 2.6.24.3

- edit /boot/grub/menu.lst and at the very bottom add an entry for the new kernel. It is recommended that you also increase the delay time to something greater than 0 (like 10 seconds) so you leave the stock kernel as the default, but select the new one from the grub menu till you know it works.
- Reboot and select the entry you created for the Kernel 2.6.24.3
- Several modules won't have loaded after the reboot, You can identify which ones by doing a "lsmod > /tmp/modules.new" (without the double quotes) and comparing to the /tmp/modules.old generated previously. One that fails for sure is wireless, another one is the embedded webcam.
- To fix the wireless, just open a terminal and type the following commands:
su
depmod -a
modprobe wl

- at this point, perform a modprobe <module name> for the other modules listed in /tmp/modules.new that are missing from /tmp/modules.old . In my mini 9 the commands were:
modprobe michael_mic
modprobe arc4
modprobe ecb
modprobe blkcipher
modprobe unionfs

- At this point everything should be working normally in your Mini 9, and it should recognize all 2 GB of RAM. I did a last reboot before testing the camera and everything.
- If you are confortable that everything is working fine, edit /boot/grub/menu.lst again, change the delay back to 0 and make your new kernel entry the first one on the list of options.

---

### Post by 2damncommon on 2008-12-19
Great summary ffreitas.

---

### Post by schimschone on 2008-12-20
I'm not trying to stir the pot here but why go through all the trauma of recompiling the kernel for Dell's crappy version of Ubuntu, when a reinstall will take you less time and effort? Additionally the Dell version of Ubuntu ("Dumbutu") only allows you to access 4gb of your SSD, and has issues working with external optical drives. More importantly the Dell version is also installed with a SWAP partition, which only serves to limit the life of your SSD.

I've been running a Mini 9 with 8.10 (Netbook Remix) now for over a month, and I love it. It's stable, and the menu system of Remix rocks! Additionally it remains actively supported through the community, to which I've heard Dells version has not been. I've included a few screen shots if that convinces you.

Also here's an amazing guide for installing and maintaining your Mini 9, and additionally there's also a Google group on the subject created by the same guy.

[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

schim

---

### Post by kodemage on 2008-12-20
Thanks for the detailed instructions. I'll try them a little later today. (At work now, can't take the time.)

I'll let you know how it goes later. 

Thanks for the help.

Regards,
-Benjamin

---

### Post by kodemage on 2008-12-20
schimschone, 

A fair question, not just stirring the pot. 

*Installing Ubuntu from a USB key is not nearly as easy as it should be. I've yet to find a good step by step guide. I could do it, but recompiling the kernel seemed like more fun, and I've recompiled kernels before, never installed an os from USB.
 
*I'm sure that the Ubuntu remix looks good to you, but I don't like it at all.(In fairness your screen shots are the first I've seen it and if it's as customizable as most linux programs are I could probably tweak it to something good looking.) I use Avant Window Navigator for the maybe 4 programs I actually run on my mini. (Firefox, Amarok, Miro, and Notepad)

*"I've got it just how I like it." Me answering the same question when my friend asked it offline. I spent several hours installing programs, Yakuake, AWN, Amarok, and removing other chafe like the games and "edutainment".

*Finally, just installing a fresh OS was my original plan but then I saw the list of known problems and I figured one kernel recompile beats half a dozen smaller fixes. 

I didn't know about the only having access to 4gb of the SSD, I'm pretty sure that my comp lets me have all 8gb and there is no swap. Although, I'm ok with it using a swap, despite the fact that it wears out the drive. It should also make the whole thing faster and Linux is pretty damn good at the whole memory management thing. 

Regards,
-Benjamin

> **schimschone said:**
> I'm not trying to stir the pot here but why go through all the trauma of recompiling the kernel for Dell's crappy version of Ubuntu, when a reinstall will take you less time and effort? Additionally the Dell version of Ubuntu ("Dumbutu") only allows you to access 4gb of your SSD, and has issues working with external optical drives. More importantly the Dell version is also installed with a SWAP partition, which only serves to limit the life of your SSD.

I've been running a Mini 9 with 8.10 (Netbook Remix) now for over a month, and I love it. It's stable, and the menu system of Remix rocks! Additionally it remains actively supported through the community, to which I've heard Dells version has not been. I've included a few screen shots if that convinces you.

Also here's an amazing guide for installing and maintaining your Mini 9, and additionally there's also a Google group on the subject created by the same guy.

[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

schim

---

### Post by yakker.yak on 2008-12-20
> **kodemage said:**
> schimschone, 
I didn't know about the only having access to 4gb of the SSD, I'm pretty sure that my comp lets me have all 8gb and there is no swap. Although, I'm ok with it using a swap, despite the fact that it wears out the drive. It should also make the whole thing faster and Linux is pretty damn good at the whole memory management thing. 


Yup, there's no swap on the Dell Ubuntu and the 4 GB SSD limitation bug has since been fixed. I think some of the earliest of the Mini 9's shipped with this problem.

Other users have also indicated that the Dell Ubuntu compiled for the LPIA architecture seemed a little bit faster than a default i386 Ubuntu install, but I haven't compared myself.

---

### Post by shiningkenmonster on 2008-12-20
schimschone, you don't have your facts straight. Previously, Dell had their workers in Taiwan reused the same 4GB SSD format of Ubuntu on all their SSDs on the Dell mini 9 model. which were a 4GB, 8GB, 16GB at that time. 

However, you can fix this by doing the following:
1, This could be fixed by doing a system restore on which came with the CD/DVD. or use a USB flash drive.
2, use gpart
3, other online partition sources to fix this.

However, the 4GB SSD partition error is fixed since mid of October 2008.

Also, the SWAP Partition is off by default which is the factory settings from Dell's Ubuntu.

Even the author whom you citied on the website said it too!

You said a statement that is true in the past. But you apply that the error still exists. It doesn't! Please, do not mislead the newbies on this board.

as of the 883.2 MB of RAM (supposedly 1GB of RAM). yes, the problem still exist. You can fix it, if you want to rebuild your linux kernel. It'll fix the problem. But I don't see the need that I need to use up all my RAM at once.  I had opened about 50 applications to get my system to slow down/max out my ram. but to the majority of people, they don't open that much applications at once.

and btw, the Dell's custom version of Ubuntu 8.04 is running on the LPIA (Low Power on Intel Architecture) is build for optimize speed for the Dell Mini 9.

---

### Post by schimschone on 2008-12-20
Well thank you for setting my facts straight shiningkenmonster.. kodemage did mention much of that in answering my post, before you.. but I appreciate that your passion for your Mini made you want to say something. I like mine quite a bit too. 

I don't think that my intention was to purposely mislead 'the newbies' but maybe to offer another option, and learn something myself. I was unaware of the fixes in the last few weeks.. but it's not like I was bringing up stuff from last year.

I believe the general point of the forum is to facilitate discussion, which this has.. however if you expect people not to ask questions lest they confuse other people, a forum setting may perpetually shake your expectations.

Sorry if the Dumbuntu comment got your goat though.. I was being flippant, not so much insulting.

schim

---

### Post by shiningkenmonster on 2008-12-22
it was on the same day. not sooo last week. you did confuse some of the other people on your post.

i just don't like it how the truth is twisted and mislead people. that is all. :-({|=

---

### Post by iggykoopa on 2008-12-23
I have a question for anyone that has recompiled the kernel. I used kernelcheck and made a new kernel, I'm running a default intrepid install, but before I wiped the machine I took the kernel config from the dell version. Everything works fine on the new kernel except wireless, I've tried compiling the wl driver and can't get it to compile, I've tried ndiswrapper but after I install ndiswrapper-utils it still says module ndiswrapper not found when I try to modprobe it, do I need to compile the module from source?  Or should I just hand compile the kernel and kernelcheck is missing an option I need? Is there any way to use the restricted modules package from the repo with a different kernel if it's the same version (i.e. 2.6.27-9). I've tried everything I can think of and am about to give up on having a custom kernel, so any help you can give me would be appreciated.

---

### Post by hackel on 2008-12-23
People, you don't need to compile your own kernel just to get HIGHMEM support.  Just add the dell netbook remix repository to your sources.list:

deb [http://dell-mini.archive.canonical.com/ubuntu](http://dell-mini.archive.canonical.com/ubuntu) hardy-netbook-remix main universe multiverse restricted

After update and dist-upgrade, and you should get the latest kernel that does support HIGHMEM.  Here's a direct link:
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb)

Much easier. :)

---

### Post by iggykoopa on 2008-12-23
this isn't for highmem support, I have a stock 8.10 install and want the lpia kernel optimizations, ext4, and pcie aspm support so I'm compiling my own for that, I just can't get the wireless to work right.

---

### Post by hackel on 2008-12-23
> **iggykoopa said:**
> this isn't for highmem support, I have a stock 8.10 install and want the lpia kernel optimizations, ext4, and pcie aspm support so I'm compiling my own for that, I just can't get the wireless to work right.

Check the topic...none of that other stuff has anything to do with it.  If you want to compile your own kernel for those other reasons then you certainly should do so.  This topic is specifically about HIGHMEM support.

FYI--you don't need ndiswrapper or anything else, the standard non-free broadcom driver will work fine.  In System>Preferences>Hardware Drivers, make sure "Broadcom STA wireless driver" is used.

---

### Post by anjilslaire on 2008-12-24
Good to know they've released a properly fixed kernel, thanks. My mini 9 should be arriving any day now.

---

### Post by ArKay on 2008-12-25
> **hackel said:**
> People, you don't need to compile your own kernel just to get HIGHMEM support.  Just add the dell netbook remix repository to your sources.list:

deb [http://dell-mini.archive.canonical.com/ubuntu](http://dell-mini.archive.canonical.com/ubuntu) hardy-netbook-remix main universe multiverse restricted

After update and dist-upgrade, and you should get the latest kernel that does support HIGHMEM.  Here's a direct link:
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb)

Much easier. :)
I tried adding the repository line you quoted - and got this response :
Failed to fetch [http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/Packages.gz](http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/universe/binary-lpia/Packages.gz](http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/multiverse/binary-lpia/Packages.gz](http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/multiverse/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/restricted/binary-lpia/Packages.gz](http://dell-mini.archive.conical.com/ubuntu/dists/hardy-netbook-remix/restricted/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Mind you, I was connected, the other sources loaded as well, just not those you referenced.

Am I missing something or did you find something and they yanked iot away ?


Having a Dell mini it would be soooo nice to have a repository of software that is supposed to run on it with the full support the hardware can give...

(ooops) And this is where he looks back at what he typed and realizes that when you misspell canonical as conical you won't have any success no matter how hard you try...

It's pulling the 125 updates down as we speak... (ooops)

---

### Post by joepp00 on 2008-12-27
> **hackel said:**
> People, you don't need to compile your own kernel just to get HIGHMEM support.  Just add the dell netbook remix repository to your sources.list:

deb [http://dell-mini.archive.canonical.com/ubuntu](http://dell-mini.archive.canonical.com/ubuntu) hardy-netbook-remix main universe multiverse restricted

After update and dist-upgrade, and you should get the latest kernel that does support HIGHMEM.  Here's a direct link:
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb)

Much easier. :)

Tried this, works great with full 2gb now showing...but no sound and wireless!
HELP

---

### Post by anjilslaire on 2008-12-27
[http://ubuntuforums.org/showpost.php?p=5770666&postcount=1]("http://ubuntuforums.org/showpost.php?p=5770666&postcount=1")

---

### Post by rneindorff on 2008-12-28
> **hackel said:**
> People, you don't need to compile your own kernel just to get HIGHMEM support.  Just add the dell netbook remix repository to your sources.list:

deb [http://dell-mini.archive.canonical.com/ubuntu](http://dell-mini.archive.canonical.com/ubuntu) hardy-netbook-remix main universe multiverse restricted

After update and dist-upgrade, and you should get the latest kernel that does support HIGHMEM.  Here's a direct link:
[http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb](http://dell-mini.archive.canonical.com/ubuntu/dists/hardy-netbook-remix/main/binary-lpia/linux-image-2.6.24-19-lpia_2.6.24-19.41netbook11_lpia.deb)

Much easier. :)

This method does seem much simpler than most but if I read the above instructions correctly, after you do the dist-upgrade you have actually replaced the Dell supplied OS with a true Ubuntu Netbook Remix.  This would be like going from one version of Ubuntu to the next.  That would be why some additional steps are required to get all of the hardware to function properly - ie. sound and WiFi.  Has anyone noticed any other side effects?

---

### Post by sanubie on 2008-12-28
I found this tutorial here too 

[http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html](http://www.ubuntumini.com/2008/10/installing-ubuntu-on-dell-inspiron-mini.html)

Has anybody used this successfully? I'm thinking about trying it when I get mine in the mail. It should remove the 1 GB RAM limit because you'd be overwriting the original Kernel. Can anybody confirm?

---

### Post by Mig Daddy on 2009-01-05
I checked the Dell website earlier today.  There is now an option for 2GB RAM (for $50 more than 1GB) as well as for a 64GB SSD (also $50 more than 32GB) for the Ubuntu version of the Mini 9.  Does this mean the kernel for the Dell Mini OS has been updated?  Is it worth asking Dell for the updated version of their flavor of Ubuntu Hardy (which I believe is free of charge) or is installing Intrepid w/ Netbook Remix a better solution?

I just came up on a Mini 9 from their outlet store for $380 including tax and shipping (1.3MP Webcam, Bluetooth, 1GB RAM, 32GB SSD, Previously Ordered New).  Not sure which Bios version or Ubuntu version (if there is more than one) it is, but it seemed like a great deal.  I know it's not related to the thread but any opinions?

---

### Post by Mig Daddy on 2009-01-07
Hey all.  I have been doing some searching on the net and have come across an email dialogue between a Mini 9 Ubuntu user and a Dell Linux expert.  It seems legit, but I have no way of verifying this.  Apparently the 1GB limitation is a bug in the kernel and has since been fixed.  I have no idea when this occurred or what other fixes are included in the currently shipping versions.

[http://lists.us.dell.com/pipermail/linux-desktops/2008-October/002131.html](http://lists.us.dell.com/pipermail/linux-desktops/2008-October/002131.html)

---

### Post by jbelmonte on 2009-01-07
> **Mig Daddy said:**
> ...  Apparently the 1GB limitation is a bug in the kernel and has since been fixed.

[http://lists.us.dell.com/pipermail/linux-desktops/2008-October/002131.html](http://lists.us.dell.com/pipermail/linux-desktops/2008-October/002131.html)

The link you provided does not indicate that the bug has been fixed. The Launch Pad link [https://bugs.edge.launchpad.net/dell-mini/+bug/286258](https://bugs.edge.launchpad.net/dell-mini/+bug/286258) for the bug indicates a status of Pending.

In general, the Dell Mini Project has not been keeping up with updates and patches that are available in the standard versions of Ubuntu. I don't remember getting any updates since I got my Mini 9 in October. My standard desktop install of Hardy has had dozens of updates during that time frame.

---

### Post by rneindorff on 2009-01-07
> **Mig Daddy said:**
> I checked the Dell website earlier today.  There is now an option for 2GB RAM (for $50 more than 1GB) as well as for a 64GB SSD (also $50 more than 32GB) for the Ubuntu version of the Mini 9.  Does this mean the kernel for the Dell Mini OS has been updated? 
One could hope that this solves the problem that originally started this thread.  Perhaps Dell is listening after all.  With 2GB of RAM, a 16GB SSD and a Ubuntu Linux OS this is a great device for staying in touch on the road with including video conferencing.  With the 64GB SSD you can carry extra customer files or store your digital photos from your camera or camcorder for uploading.  Now if they just keep up with the updates! :)

---

### Post by Ancalagon82 on 2009-01-07
This will probably sound like a *really* dumb question, but if we wanted to upgrade a Mini9 to 2GB is there any special kind you need?

---

### Post by Mig Daddy on 2009-01-07
jbelmonte:
No.  The provided link does not indicate the bug has been fixed.  It is merely an assessment I made on the situation given the dialogue and current configuration options of the system.  It has likely been fixed on their side and is just pending release (again, I have no way of verifying this).  It seems to me that it will be fixed for any system currently being built and that it will be available to the rest of us in the near future.  Now, I know that the standard warranty does not technically cover the operating system, but I have received additional copies of WinXP for my E1505 free of charge.  I expect it to be the same for Mini OS on the Mini 9.  Now if only Dell would package the software into a thumb drive.  Does anyone know if the Mini OS is considered to be proprietary software?  My gut says no, but anything is possible in this world of ours.

Ancalagon82:
The type of RAM used is of the DDR2 SODIMM (PC-6400) variety.  I believe it is also compatible with PC-5300 and PC-4200.  Please correct me if I am wrong.

---

### Post by anjilslaire on 2009-01-08
Correct. i just added 2gigs  of DDR2 PC-6400 on my 8.10 install. Works great.

---

### Post by yakker.yak on 2009-01-10
The Dell Ubuntu (8.04) has now also been updated with the latest packages and fixes from the vanilla 8.04 and the kernel RAM limitation bug has also been fixed so that 2 GB of RAM is detected correctly.

---

### Post by Mig Daddy on 2009-01-10
My Dell Mini OS underwent an automatic update yesterday.  It took about a half hour including the ~200MB download.  Does anyone know if this is the update to the latest version of their OS, or is it just a bunch of miscellaneous packages?

---

### Post by anjilslaire on 2009-01-10
Just updates to 8.04, not a dist-upgrade to 8.10

---

### Post by jheaton5 on 2009-01-11
I installed the general upgrade this morning and discovered my web browser bookmarks had been erased.  Or, perhaps the bookmark file has been renamed in favor of a new one.  Any ideas?

---

### Post by ugm6hr on 2009-01-11
> **jheaton5 said:**
> I installed the general upgrade this morning and discovered my web browser bookmarks had been erased.  Or, perhaps the bookmark file has been renamed in favor of a new one.  Any ideas?

[http://ubuntuforums.org/showthread.php?t=1036290](http://ubuntuforums.org/showthread.php?t=1036290)

---

### Post by jheaton5 on 2009-01-11
That did it.  Thank you.

---

### Post by starcannon on 2009-01-11
I did the automatic update this afternoon, my mini9 now recognizes the 2g ram chip I put in it right after I bought it. Thanks for the bookmark fix, I was gonna work on that.

---

### Post by Ancalagon82 on 2009-01-19
^ My Mini9 updated itself when I first booted it up Weds before last.  Is that the update you are all talking about.


How can I find out if it will read my 2gig?

---

### Post by ugm6hr on 2009-01-20
> **Ancalagon82 said:**
> ^ My Mini9 updated itself when I first booted it up Weds before last.  Is that the update you are all talking about
Yes.
> How can I find out if it will read my 2gig?
```
free -m
```
The total should be 2000(ish) if you have 2GB

---

### Post by Ancalagon82 on 2009-01-20
> **Mig Daddy said:**
> 
Ancalagon82:
The type of RAM used is of the DDR2 SODIMM (PC-6400) variety.  I believe it is also compatible with PC-5300 and PC-4200.  Please correct me if I am wrong.

What's the difference between PC6400 and PC5300.

The 2Gig I bought is 5300, but when I opened my Dell the 1gig I was replacing said 6400.   Should I go back to Fry's and try an get a 2gig 6400 or does it not really matter?

---

### Post by Ancalagon82 on 2009-01-20
> **ugm6hr said:**
> Yes.

```
free -m
```
The total should be 2000(ish) if you have 2GB


Sweet!  







Thanks!

---

### Post by Mig Daddy on 2009-01-20
> **Ancalagon82 said:**
> What's the difference between PC6400 and PC5300.

The 2Gig I bought is 5300, but when I opened my Dell the 1gig I was replacing said 6400.   Should I go back to Fry's and try an get a 2gig 6400 or does it not really matter?

5300 is capable of running up to 667MHz.  6400 is capable of 800MHz.  But either can be limited by the chipset, like in the case of my 3 year old laptop.  The chipset limits the speed to 533MHz (4200).  I'm assuming that the Mini's chipset supports 800MHz and if this is the case the 5300 chip is certainly going to be slower.

---

### Post by yakker.yak on 2009-01-21
> **Mig Daddy said:**
> 5300 is capable of running up to 667MHz.  6400 is capable of 800MHz.  But either can be limited by the chipset, like in the case of my 3 year old laptop.  The chipset limits the speed to 533MHz (4200).  I'm assuming that the Mini's chipset supports 800MHz and if this is the case the 5300 chip is certainly going to be slower.

The Mini's chipset is actuall limited to 533 MHz so there's no difference b/w 5300 and 6400 as far as the Mini's concerned. Both will be stepped down to 533 MHz.

---

### Post by Ancalagon82 on 2009-01-21
Then why does Dell waste the money to put in 6400?

---

### Post by yakker.yak on 2009-01-21
> **Ancalagon82 said:**
> Then why does Dell waste the money to put in 6400?

The short answer is that it's cheaper for Dell to get 6400 or faster when compared to 4200. The longer answer has to do with production cycles of RAM manufacturers: way more of the 6400+ memory was produced recently compared to slower RAM.

---

### Post by dragonmojo on 2009-01-22
Besides, at the rate all things technological gets superceded (meaning by the time you're ready to ditch your Mini9 for the next big thing), you can probably still use the 6400 memory in a newer system.

Is it me, or is the life-cycle for the netbooks a lot shorter than other tech? That's the downside of a hot market... every manufacturer scrambling to up their product line to get or stay ahead of the competition.

Good for tech-heads; not so good as a consumer, esp in this economy.

---

### Post by sandalgod on 2009-04-11
thanks to everyone for the info.  i just put a 2gig stick in week old mini 9 and i checked it with the terminal and the free -m and it recognizes the new memory.  i got patriot model PSD22G8002S.

---

