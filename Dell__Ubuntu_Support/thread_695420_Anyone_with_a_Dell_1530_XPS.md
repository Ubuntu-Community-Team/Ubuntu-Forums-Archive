---
title: "Anyone with a Dell 1530 XPS?"
date: 2008-02-13
forum: Dell  Ubuntu Support
---

### Post by putz3000 on 2008-02-13
I am shopping a Dell XPS 1530 and one of the reasons I am looking at it is for what I hope to be better Ubuntu support than my previous two HP laptops (which fried right after the 1 year warranty's were up).  Anyhow, I digress.  Here are the main system specs, I am especially curious / concerned about the wireless adapter:

XPS M1530, Intel Core 2 Duo Processor T7500 (2.2GHz/800MhzFSB, 4M L2 Cache) 	

2GB, DDR2, 667MHz 2 Dimm, for XPS M1530 	

15.4 inch Wide Screen WXGA+ TrueLife LCD with 2.0 MO Camera for XPS M1530 	

256MB NVIDIA GeForce 8600M GT 	

120G 7200RPM SATA Hard Drive Free Fall Sensor 	
	
8X DVD+/-RW Slot Load Drive for XPSM1530 	

Integrated High Definition Audio 2.0 	

Intel 4965AGN Wireless-N Mini-card

Any comments regarding experiences installing and using Ubuntu 7.10 or 6 out of the box would be nice to know.

Thanks!

---

### Post by lexxonnet on 2008-02-13
Hello... 

Interesting Coincidence! I just got my XPS m1530 around 6 hours ago, and I've been playing around with it for a while.

I've installed kubuntu gutsy on it. Everything is working quite well. 

What works:
[LIST]
[*]Wireless works out of the box(I haven't tried n, but g works)
[*]The display drivers are initially vesa, but running restricted manager gets them to the non-free nvidia ones.
[*]Sound card and remote work fine
[*]Suspend and Hibernate work sometimes but are flaky
[/LIST]
What doesn't work:
[LIST]
[*]Brightness control keys don't work as of now. But the power manager in kubuntu allows me to control them.
[/LIST]
Others:
[LIST]
[*]Fingerprint Reader: I haven't put much effort into figuring out how this works yet :) 
[*]Camera: Same as above!
[/LIST]

---

### Post by BluePlum on 2008-02-13
Fingerprint reader? mad..... i have a dell xps ( lastest version laptop) but i dont think mine has a finger reader :P

---

### Post by sgtbug on 2008-02-13
err.. even mine has a fingerprint reader, but it sucks so i dont use it.. lol..

what does not work:
webcam

rest everything works perfect on 32 bit.. 64 bit not recommended!!

---

### Post by lexxonnet on 2008-02-17
Hehe... indeed. I couldn't get the bootup splash screen working in 64-bit. Everything else seemed fine, but graphics were a bit slow. Could be bad nvidia drivers.

My brightness controls didn't work in gutsy, but they do in hardy. Camera doesn't work on either after a few attempts, and I haven't really bothered about the fingerprint reader.

There is a weird issue with volume though, it seems too exponential! I cant hear anything until around 70% and then it increases raipdly till 100%

---

### Post by LK_gandalf_ on 2008-02-19
I have an xps 1530 (T7250, 8600gt, 2gbram), and I'd like to format and install Vista (in Italy we can't buy a dell with ubuntu so we have only Vista) + Kubuntu.

If I install the 64bit version, all the devices are ok?

---

### Post by Floi on 2008-02-19
Did you also get the integrated microphone to run?
I've been trying different things on my xps 1530 - without any success...

Floi

---

### Post by jespdj on 2008-02-19
I have an XPS M1330, see the specs in my signature. It's almost the same as the 1530.

Everything works on my 1330, also the webcam. The only thing that didn't work was the internal microphone, but that was easily fixed with a patch, see [this page](http://www.nervous.it/2007/11/linux-dell-xps-m1330/). Maybe it will work on the 1530 as well.

---

### Post by gecko113 on 2008-02-19
I have one and everything works on Ubuntu almost everything execpt i haven't tried the webcam or mic but it seems flaky on everything such as when i switch desktops but other than that it works perfectly fine

---

### Post by LK_gandalf_ on 2008-02-19
and what about the 64bit version?

---

### Post by jsc1959 on 2008-02-20
I tried the 64 bit hardy and it was flaky... 32 bit work great.

---

### Post by LK_gandalf_ on 2008-02-20
flaky...means? Sorry I don't know :)

Doesn't DELL install 64bit version of ubuntu in the country where it sells the laptop with ubuntu? (USA, etc...) Only 32bit?

---

### Post by nine7six on 2008-02-21
> **lexxonnet said:**
> Hello... 

What doesn't work:
[LIST]
[*]Brightness control keys don't work as of now. But the power manager in kubuntu allows me to control them.
[/LIST]


I had this problem in Kubuntu as well but after a format and a fresh install of Ubuntu they worked fine..

---

### Post by dragonx on 2008-02-28
I have XPS M1530 and I have running the mic
view the solution here [http://weblogs.inf.udp.cl/nboettcher/28/02/2008/configurar-microfono-en-ubuntu-gnome-en-equipo-dell-xps-m1330-m1530/]("http://weblogs.inf.udp.cl/nboettcher/28/02/2008/configurar-microfono-en-ubuntu-gnome-en-equipo-dell-xps-m1330-m1530/")

---

### Post by Vaun on 2008-03-11
I just purchased a Dell XPS m1530 and running Ubuntu Hardy 8.04 latest updates.  Everything seems to be working except the trackpad scrolling and the wireless card is not recognized.  I have not messed with the fingerprint reader yet, but everything is working great.  Most importantly, Compiz fusion works great after forcing the Powermizer always to run the GPU at full speed.  Any solutions on the wireless please let me know.

I was able to get trackpad scrolling working by editing xorg.conf.  No luck yet on the wireless as I think I've tried everything with ndiswrapper.  I may have to purchase and Intel wireless card to ensure it will work/

---

### Post by koby on 2008-03-23
I tried to make the built-in webcam according to Saitoh in
[https://answers.launchpad.net/ubuntu/+source/hal/+question/14286](https://answers.launchpad.net/ubuntu/+source/hal/+question/14286)
but couldn't.

---

### Post by koby on 2008-03-24
I installed cheese through Synaptic package manager.  The built-in webcam blue LED came on and webcam started to work even for Skype.  Does this mean webcam drivers were installed with cheese?  I'm not sure.

---

### Post by chocon on 2008-04-18
Hello, mine is 1530, although I installed the driver from NVIDIA website, but still I just got 800x600 screen, any ideas to get over this, thanks.

---

### Post by MikeyMike01 on 2008-04-19
> **chocon said:**
> Hello, mine is 1530, although I installed the driver from NVIDIA website, but still I just got 800x600 screen, any ideas to get over this, thanks.

System > Preferences > Screen Resolution

If that doesn't work, uninstall that driver, and then enable Desktop Effects and it will install the Nvidia Driver for you.

And BTW, everything on my M1530 worked out of box, except mic:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=702642](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=702642)

---

### Post by chocon on 2008-04-19
Hi, actually the problem is I can't find the driver in the list to choose for "Graphics card", it's still the default vesa - generic VESA, and browsing to NVIDIA just give me 8 series, but the card is 8600M GT.
Anybody experiencing this, pls help.

---

### Post by mrojas73 on 2008-04-19
I got mine last night...everything works out of the box including webcam, sound, brightness, wireless...everything.

Running 8.04 downloaded this morning though.

This thing is sweet!

---

### Post by lexxonnet on 2008-04-25
I've finally got everything working with Kubuntu Hardy :) I've got the fingerprint reader working with gdm, using thinkfinger (cos kdm crashes).

The webcam works in 32-bit flawlessly, I haven't tried 64-bit hardy yet. Mic took some working, but the main issue seems to be to set the mic to Digital Input in alsamixer. 

Sound still is a bit exponential however. And I usually cant hear anything below 50%. 

And the touchpad, I calibrated myself, after some trial and error. This makes scrolling and such work very nicely indeed.

```

Section "InputDevice"
 Identifier "Mouse0"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "on"
 Option "SHMConfig" "on"
 Option "VertEdgeScroll" "on"
 Option "VertTwoFingerScroll" "on"
 Option "LeftEdge" "85"
 Option "RightEdge" "910"
 Option "TopEdge" "85"
 Option "BottomEdge" "715"
 Option "FingerLow" "25"
 Option "FingerHigh" "30"
 Option "MaxTapTime" "180"
 Option "MaxTapMove" "220"
 EndSection


```

---

### Post by SewardsDiary on 2008-04-27
I bought my XPS 1530 also very recently and had to face some major problems so far with any Linux Distribution I tried (which is openSuse 10.3 and Hardy Heron, both 64 bit).
It seems there is actually no way to get the 3D support running with the right proprietary drivers.

The whole issue is discussed here [http://ubuntuforums.org/showthread.php?t=615215&page=13]("http://ubuntuforums.org/showthread.php?t=615215&page=13") at length.

I'm going to try the 32bit version now, and just hope that everything will be fine.


Note: There is a BIOS Update available (REV A08) on the DELL Homepage which claims to improve the touchpad performance.

---

### Post by bongomatic on 2008-05-03
> **SewardsDiary said:**
> 
Note: There is a BIOS Update available (REV A08) on the DELL Homepage which claims to improve the touchpad performance.

I have a Dell XPS m1530 that I installed Hardy Heron 8.04 on that was running bios version A07. Since bios A08 offers the ability to enable VT I installed bios A08, and now the touchpad is unusable. Symptoms are erratic movements in the opposite direction and random clicks. Also, somehow my mouse preferences were switched to left-handed! Anyone else experience this or have any suggestions for how to fix please?

---

### Post by damis648 on 2008-05-03
I have revision A08 and no erotic movements and clicks as you have mentioned... maybe try flashing the firmware again.. maybe something went wrong

---

### Post by ruffEdgz on 2008-05-04
> **damis648 said:**
> I have revision A08 and no erotic movements and clicks as you have mentioned... maybe try flashing the firmware again.. maybe something went wrong

I'm also having this problem when I installed Hardy this past Friday and I got this Dell XPS 1530 with the new BIOS A08 already installed on Friday as well (it had windows on it first). 

I will try flashing the BIOS and then installing the new BIOS again and see what I get. 

Hope it works :P

---

### Post by blekos on 2008-05-05
I have the xps1530.
If you upgrade the Bios to A008 for VT (i've done so) then you come up with your touchpad. The problem is solved easily if you do this:
add the bold letters to your menu.lst

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **i8042.nomux=1**

the original post is here [http://ubuntuforums.org/showthread.php?t=737060&page=2](http://ubuntuforums.org/showthread.php?t=737060&page=2)

I am looking for suggestions for the following:
1. Volume up/down/mute does not work from remote control
2. Webcam does not work
3. sound works great but is it as good as in vista? (are the "same" drivers? or just compatibles)
4. finger rec. doesnot work (dont care really)
5. nvidia drivers are installed. How can i test the 3d acceleration etc?
6. card reader not yet tested

I am using Kubuntu 8.04

Thank you for your time

---

### Post by ruffEdgz on 2008-05-05
I tried to flash my BIOS but the application I wanted to use (uniflash = [http://www.uniflash.org/](http://www.uniflash.org/)) couldn't recognize the chip I was using and because of that, I didn't want to risk the flashing process (I have lost a lot of Motherboards flashing the BIOS before).

blekos suggestion about placing **i8042.nomux=1** at the end of **defoptions=quiet splash** is a new one that I will try since my BIOS is already up to speed with A8. I have tried placing that next to the: 

kopt=root=**** ro **i8042.nomux=1**

which works after I place my computer to sleep and wake it back up again.

---

I was surprised by the problems with the webcam since I downloaded an application called 'Cheese' and it worked without any problems. 
I don't know much about Kubuntu but I would hope it would be close to the same thing.

Thanks again for the update blekos about the touchpad issue :D

---

### Post by ruffEdgz on 2008-05-05
> **bongomatic said:**
> I have a Dell XPS m1530 that I installed Hardy Heron 8.04 on that was running bios version A07. Since bios A08 offers the ability to enable VT I installed bios A08, and now the touchpad is unusable. Symptoms are erratic movements in the opposite direction and random clicks. Also, somehow my mouse preferences were switched to left-handed! Anyone else experience this or have any suggestions for how to fix please?

Sorry for the double post but I thought I would help out **bongomatic** with his problem since I was having the same one.

After reading the post: [http://ubuntuforums.org/showthread.php?t=737060&page=2](http://ubuntuforums.org/showthread.php?t=737060&page=2)

I noticed that **smazero** placed the *i8042.nomux=1* in a different place to get the touchpad to work when you start up your Ubuntu. He placed it in the /boot/grub/menu.lst entry:

```

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=4d1f9d83-796c-4618-bcfe-6125202bf4f4 ro quiet splash **i8042.nomux=1**
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

```

After doing that, you will need to place another in the menu.lst:

```

# kopt=root=UUID***************** ro **i8042.nomux=1**

```

The code above will help if the lid closes on your laptop and the touchpad will still work.

Mine works wonderful with these minor changes in the menu.lst file. 
The suggestion that blekos showed from the post is correct as well but I did it by just typing it in but I did place one more part in the menu.lst that isn't necessary:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **i8042.nomux=1**

```

---

### Post by blekos on 2008-05-06
Hi,
could i hear it worked. I'll try it also with my screen closed :)
Could you please confirm if the volume up/down works from the remote control?

thank you

---

### Post by pablopancho on 2008-05-07
Hi, I got my XPSm1530 on 6th of May. 
Configuration: Dual Core 2.00GHz, 2GB RAM, Nvidia GF 8600M GT 256MB, 250GB disk, BIOS v. A08, Intel Wireless WiFi Link4965AGN

I was able to boot Live CD of Hardy (32bit) without any problems except touchpad (but I fixed it by adding a magic spell ;) at the end of kernel line). Everything seems ok, even wireless (although I didn't test it for long).

Now I'm wondering how to partition my disk. Vista in Disk Management shows 4 primary partitions. The first is EISA Configuration 118 MB, then recovery partition 10GB (drive d), os 220GB (drive c) and empty 2.50GB partition.

Gparted however sees it differently. Fourth partition is extended (sda4) and contains 1 MB unallocated space and a FAT32 volume of 2.50 GB (as sda5).

I would like to keep Vista & recovery partition, just shrink them to make room for Hardy. Is it safe to delete sda4? I think it contains MediaDirect. Will getting rid of this partition save me from "Self-destruct-direct" button? Does this void my warranty (base 1 year)?

And what should I choose: 32 or 64 bit?

Thanks in advance for any replies.

---

### Post by ruffEdgz on 2008-05-07
I know there is a way to do it with something like Parted Magic but I also hear that you can extend/shrink partitions within Vista. 

I know for a fact that extending a partition with exsisting information on it (aka Operating Systems) have a better success rate then trying to shrink. I personally know for experience that shrinking a partition can almost be fatal as it could damage the OS all together using Parted Magic (it isn't Parted Magics fault but Windows fault).

If Windows Vista has an option to extend/shrink partitions, I would use that because if the shrinking is for the Vista partition, it might warn you and maybe help with any file moves and such for it happens (I would hope Vista would be smart enough but then again, we do put a lot of trust in these machines/OS's). 

I really don't know for a fact how it will work for Vista since I'm trying to stay away from Windows OS's as much as I can :D

----

Also, blekos - I will check out if my remote works later tonight and update this thread if I find anything.

---

### Post by pablopancho on 2008-05-07
I'm not so much worried about Vista. When resizing partition you always have to be prepared for failure. The worst case scenario is reinstalling Vista with a CD provided by Dell. Besides I trust more Gparted than Partition Magic or anything else that runs on Windows. :P

For me the big X in equation is MediaDirect partition. You see the problem is if you don't want this software, you should be able to uninstall it. But all I could do is to uninstall the Media Direct program residing in Program Files. If I push the MD button while computer is off it will run the Media Direct from the partition. 

I read that sometimes MD is on a totally hidden partition, sometimes not. I think my case is the latter but who knows. That causes my uncertainty. What will happen if I mess up with that last partition? Will the MD button still pose a threat to my MBR?

---

### Post by pablopancho on 2008-05-08
I was impatient so I installed Hardy 32bit on my brand new Dell M1530. That's how it worked:

First I deleted Media Direct partition in Vista's Disk Management. Reboot. I pushed MD button and it loaded normal Windows. Good.

I booted live cd of ubuntu with i8042.nomux=1 at the end of kernel line. I lauched Gparted and got rid of sda4, resized sda3 (Vista partition) from 220 GB to about 60 GB, created extended partition from the whole unallocated space after sda3, created big ntfs volume, smaller ext3 volume and left about 3 GB for swap. It took ages to shrink sda3 (I think about 2 hours). Reboot, launch Vista.

Vista was very unhappy with the new partitions, but after several disk checks decided it is ok and started normally. Reboot to live CD.
I see that Gparted left 5 MB unallocated space before sda3 but no matter.
I installed Ubuntu successfully. I enabled Nvidia drivers without any problems. Wireless works. No complaints. Shutdown - test of MD button. Media Direct screen and then GRUB menu. Success! :)

Now I'm going to test for any problems but the most important things work for me. If I find anything wrong I'll let you know. The only thing that worries me is the temperature of the laptop. It seems quite hot, average processor temp. is 56C and nvidia GPU is 65C. Is it me or that's a bit too hot?

---

### Post by ruffEdgz on 2008-05-08
Sorry for the late post **pablopancho** but I tried out my remote and it wasn't working for a small amount of time so I searched for a solution. I found the thread below and read somethings about current problems with XPS 1530:

[http://ubuntuforums.org/archive/index.php/t-652364.html](http://ubuntuforums.org/archive/index.php/t-652364.html)

After reading it, **vbabiy** talked about "fixing the position of the battery" so I played with the battery and NOW it works when I point it directly at the computer (like I point it down towards the keyboard on an angle and it works). 

I don't know if it just needed to 'sync' with the remote to make it work or the battery is picky so I made the battery + sign face the other + sign on the dell remote when placing the battery in it.

I hope that helps but it just seems that the remote is picky and just needs to be pointed at it in a different way or needs some kind of syncing/communication set (by the computer) to make it work.

In that link above, it also said to look up in google about 'lirc + dell remote' which could help understand the process more.

---

### Post by pablopancho on 2008-05-10
Yeah, thanks ruffEdgz, I have the same observations about the remote. But I'm not too worried about it - I'm not going to use this remote too often. Its nice to know it works, though (maybe not perfectly but still).

I tested hibernation - it worked, some errors were displayed during the process but the result was ok I guess. I also rarely use it.

Next to test is webcam, I'll do it in my free time. I hope it works. I won't bother with the fingerprint reader, I'm not going to use it at all. Never. :P

I'm still worried about the temperature (especially graphics card). Has anyone noticed similar problem? Or am I overreacting?

---

### Post by arioch_yu on 2008-05-10
What are the ways to monitor, and more importantly to control, temperature of various components on XPS 1530 running Hardy? Please share your impressions. Does i8k fan control work for this laptop?

---

### Post by semiconductor on 2008-05-10
I decided to go for the full ubuntu install as I was just running off the ubuntu live cd which worked fine apart from the erratic mouse error which others seemed to have fixed. 
Dell XPS 1530 320GB HD

I followed others explanations on how to install dual boot. Dell xps 1530 comes with 4 partitions so I deleted the restore partition which was 2nd. I then moved my OS partition along to 2nd so that I could add a larger one after it. After trying this which took more than 10 hours!!! Vista was totally lost. So I erased all the OS and media direct partitions and started to reinstall windows and media direct from scratch.
This worked for a while but then I started getting read / write errors. I went back to vista install again and formatted the HD again. Each time the HD got worse and now it doesn't work at all.

It was fine until I used Gparted. I have no confidence in trying any NTFS modification again with Gparted or ubuntu for that matter. I was very excited about using it and now I have a dead brand new laptop that Im going to have to beg to Dell to fix.

---

### Post by rossmoore on 2008-05-10
I have a brand new Dell M1530 in the UK, and almost killed my own laptop too. I'm now writing this on a triple booting m1530. Hold in there, I'll talk you through it. It's great - video, compiz, the works. Having said that, I still can't get the eject button working in Ubuntu (you can eject, you just have to use the mouse), and I'm not convinced by the smoothness of DVD playback yet, I'm still working on that...

I've got to pop out for a couple of hours, but don't send it back to Dell yet. It took me a couple of hours to do the whole thing, from a nuked laptop with nothing but MediaDirect CD, Vista CD, Ubuntu Hardy live CD (I used 32 bit, which I gather is less problematic). I'll dig out the link, and I'm happy to help you through it.

---

### Post by rossmoore on 2008-05-10
Here's the link:
[http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/](http://www.daryl.mu/2008/03/05/howto-triple-boot-dell-xps-m1330-with-vistaubuntu-and-media-direct/)

I followed this, carefully, on my M1530 and it worked perfectly. I also followed it incorrectly, by forgetting to shutdown the laptop and pressing home correctly as it says in step 5.2 - which meant I had to start from the beginning again...

If you have any questions while you're doing it (presuming you've got another computer) I'm happy to help.

---

### Post by pablopancho on 2008-05-11
**To arioch_yu:**
I'm not a big expert in linux so I don't know too many good programs to manage temperature. I'm using sensors-applet (you can find it in Synaptic) which I put on my panel so that I can monitor CPU & GPU temp. in real time. Simply right-click on a panel and choose *Add to panel* and find that applet. You can also configure it. That's all I can help you with, I'm afraid. I hope it helps.

**To semiconductor:**
It is possible that Gparted messed up your disk, but in that case it should be reversible. However, it's also possible that your disk was defective from the start (10 hours for moving partition? strange - it took me about 2 hours), in that case you'll need to send it back to Dell. In my opinion, if you wanted dual boot you should have left recovery partition intact (it's only 10GB). All you should do is to shrink big OS partition (in my case sda3) and use the free space for Ubuntu. But remember that on a disk there can be maximum 4 primary partitions or for example 3 primary partitions + one extended (in extended you can create many volumes that work like partitions). It is a good idea to defragment the disk before shrinking. Are you going to use Media Direct? In my opinion it is a waste of disk space. I got rid of it as well. 

And don't give up. If I ever learned anything about computers, I learned it by repairing my mistakes :)

---

### Post by ruffEdgz on 2008-05-11
**To arioch_yu:**
It is hard to actually control the temprature of a computer and to really control it would be to understand how many programs your computer can run before it reaches a high temprature. I think that is why [laptop coolers]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2030260319+1276817102&name=Cooler") still exist because there really is no sure way to keep temprature down. **pablopancho** is correct though to use [sensor-applet]("https://help.ubuntu.com/community/SynapticHowto"). Try it out and just understand how hot your computer can get before it gets dangerous.

**To semiconductor:**
Personally, I would call Dell and tell them your situation since this could be more about the hardware then the software. If you want to, keep at the uninstall and reinstall of the Windows OS. If you want to clear everything from the disk and see if it might be the hardware, use a [DBan cd]("http://dban.sourceforge.net/") which can be created for free. This DBan will clean more then a Windows format can do. After this, try installing the Windows OS or Ubuntu OS and see if that helps. If it doesn't, I would call Dell and see if they have any suggestions to resolving this problem if it keeps reaccuring.

**To rossmoore:**
That is an interesting tutorial and I'm happy it worked :D To bad, I never wanted to keep my Windows OS on this computer but it's nice to know ;)

---

### Post by arioch_yu on 2008-05-15
Thanks guys for the tip about sensors for temperature, that's surely a good thing to have. But my question is really about controlling the fans since XPS 1530 default settings (with Ubuntu) make CPU run between 50 and 60 degrees most of the time (GPU is 60 and above) and I find this a little high value, so I am concerned, not sure whether I should be or not?

---

### Post by arioch_yu on 2008-05-15
I have another question, not sure how sensible it is but I am curious: is there a noticeable difference in how much your XPS 1530 heats up depending on whether it's running Gnome or KDE (Hardy)?

---

### Post by jackobean on 2008-05-15
Hi folks

I've had my 1530 for a couple of months now, and i love it. Hardy is running like a gem! The only thing i have been struggling with is resuming from standby and hibernate. The problem is that on resume the screen comes up blank white. There is a mouse cursor but that's it! Could it have something to do with having set automatic login?

Thanks in advance :)

---

### Post by rossmoore on 2008-05-15
To arioch_yu:
I got similar temps of CPU and GPU around 50-60 degrees C in Ubuntu Hardy on an M1530. I've now switched to Kubuntu, so I'll download sensors-applet, keep an eye on the temp and get back to you tonight.

---

### Post by arioch_yu on 2008-05-16
thanks rossmoore, any update regarding temperatures in ubuntu/kubuntu?

---

### Post by rossmoore on 2008-05-16
Sorry, no chance to boot up last night - I spent most of the evening stuck on a train out of London. I'll try again tonight.

---

### Post by rossmoore on 2008-05-21
I was getting temperatures more in the high 40s typically with Kubuntu. I've decided I prefer Gnome, so I've gone back. Temps typically in the low 50s now, with GPU mostly hotter than CPU (I'm using Compiz, laptop 8600GT graphics and restricted drivers straight from the distro).

It's interesting, each time I reinstall it gets smoother - graphics are less jerky, it scrolls better, looks slicker. I guess each time I remember and understand more, but I have no idea what I'm doing differently each time. I've only been using Linux since March, and have yet to persuade the wife it's a step up... there are some annoyances in it, and it's difficult to remind yourself all the time of the annoyances in other OS; and of course it's something new to learn. She didn't like the slideshow in F-Spot last night, so I need to find another program now!

---

### Post by darinmiller@cableone.net on 2008-05-31
> **jackobean said:**
> Hi folks

I've had my 1530 for a couple of months now, and i love it. Hardy is running like a gem! The only thing i have been struggling with is resuming from standby and hibernate. The problem is that on resume the screen comes up blank white. There is a mouse cursor but that's it! Could it have something to do with having set automatic login?

Thanks in advance :)

I've seen the blank screen behavior on several Ubuntu machines.  Seems Ubuntu fails to correctly display the password prompt window.  At the blank screen, type your password and hit enter (even though auto login is enabled) and your desktop should appear.

---

### Post by ruffEdgz on 2008-05-31
> **darinmiller@cableone.net said:**
> I've seen the blank screen behavior on several Ubuntu machines.  Seems Ubuntu fails to correctly display the password prompt window.  At the blank screen, type your password and hit enter (even though auto login is enabled) and your desktop should appear.

This is true and the blank screen problem doesn't happen to me a lot but on occasion when I close my screen or have the screen saver on for a long period of time causes this problem.

I did what darinmiller suggested when it happened to me some weeks ago and it works. If you try it and nothing happens, just try it again. Typing in the password incorrect will just shack to the screen and ask you to type it in again.
------
The only problem I'm facing is the webcam not working the way I want it to (recording both video and voice at the same time). The application [Cheese]("http://www.youtube.com/watch?v=zUCrzVmmzsM") is a wonderful to use but I wanted to try and record (with sound) videos for places like Youtube and others out there. I will live until something else is done with that application :D

Hope everyone else is enjoying their Ubuntu on the XPS M1530 :D

---

### Post by stevieP on 2008-06-07
> **ruffEdgz said:**
> This is true and the blank screen problem doesn't happen to me a lot but on occasion when I close my screen or have the screen saver on for a long period of time causes this problem.

I did what darinmiller suggested when it happened to me some weeks ago and it works. If you try it and nothing happens, just try it again. Typing in the password incorrect will just shack to the screen and ask you to type it in again.
...

Hope everyone else is enjoying their Ubuntu on the XPS M1530 :D

I'm using a Dell XPS 1530, I wish I could say I was enjoying Ubuntu on it. 

I have found tthatt the hibernation problem is more serious than this. When I close my laptop it simply does not hibernate. It keeps runnning and when I open the lid again all the windows are open and in plain view. When I go to: System -> Quit -> Hibernate I get a page full of text about usbb devicces, and eventually the computer goes into hibbernation. It does not come out of hibernation unless I hit the power button. 

When I hit the power button all I get is a dark screen. I type my password, hit enter, and wait 10 seconds. I do this again. and again. Eventually I have to hit Ctrl-Alt-delete to restart the computer. I went through this whole process including restarting the computer twice. 

There is a thread on the hhibernation problem in these forums:
[http://ubuntuforums.org/showthread.php?t=579781&highlight=trouble+hibernate&page=36](http://ubuntuforums.org/showthread.php?t=579781&highlight=trouble+hibernate&page=36)
but at 36 pages, it's not very useful if you're just looking for a solution.  It would be nice if there was a section onn these forumms that just contained solutions to commmon problems.

I should mmention that I am also having a problem with the keyboard on my wonderful Dell XPS1530. Several of the keys seem to stick intermmittently. I've just left it as is in this post. NNormally I'm backspacinng every few words to correct the double letters due to the sticky keys.

---

### Post by Clockswork on 2008-06-19
Is there a way to control your fans in the XPS 1530? My fans doesnt seem to be moving at all :S CPU temp gets above 50C and they still dont move. How can I change this? Please help

---

### Post by damis648 on 2008-06-19
Interesting... my fans control automatically. I think they start after the computer gets above 60 though, but i am not positive.

---

### Post by Agrajag27 on 2008-06-24
How did you guys get the touchpad to work? I've tried everything listed here without success. When I say, "work" I mean scrolling. Everything else is fine. gsynaptics tells me it can't init because I need to add a setting to xorg.conf that is already in there. It worked for ONE boot and that was it. It hasn't worked before or since.

Aside from this things are going well with the 1530 and Ubuntu (I'm new to both). Once I solve this I'll look into getting the fingerprint thing working.

---

### Post by rossmoore on 2008-06-24
With i8042.numux=1 option on the kernel in grub I find the touchpad works fine, and I can scroll this page using the side of the touchpad fine. Having said that, I have found scrolling ability to be a hit and miss. In case it helps, here's the relevant bit from my xorg.conf:

```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection
```

If you get the fingerprint thing working I'd be interesting to hear how. I haven't tried it in Vista or Linux, but would be hanndy sometimes I guess - perhaps for gksudo instead of the password?

---

### Post by Agrajag27 on 2008-06-24
Well, I got it working. Not sure entirely how. I found one line that had a lot of blank spaces after it and I removed them, rebooted and, presto, it's working now. I still can't get some things going like circular scrolling but this is a huge improvement.

The fingerprint reader is okay but I find it to be very sensitive and I often have to swipe my finger several times to get it to match.

---

### Post by rossmoore on 2008-06-24
what program do you use to use the fingerprint reader?

---

### Post by Agrajag27 on 2008-06-24
Nothing in Ubuntu yet. It's working in Vista on the laptop which is what I'm attempting to replace. I see references to several solutions on the Ubuntu side. I'll be delving into that soon.

---

### Post by titimoi on 2008-06-26
> **rossmoore said:**
> With i8042.numux=1 option on the kernel in grub I find the touchpad works fine, and I can scroll this page using the side of the touchpad fine. Having said that, I have found scrolling ability to be a hit and miss. In case it helps, here's the relevant bit from my xorg.conf:

```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection
```



I used exactly this and it worked just for one boot.. the next one, I couldn't scroll anymore.. :(

---

### Post by rossmoore on 2008-06-27
Sorry it didn't help. If I find it doesn't work one time for me I'll try and dig into it and figure out why - as I say, it does seem to be a bit hit and miss implying it might be something to do with one program or daemon starting up before another.

One other possibility that could be confusing things is that I (and perhaps you?) have set up the touchpad to ignore input if I have typed a key in the last 0.5 seconds - some people set it up for 2s, the default. You can do this by starting a program called syndaemon at startup. This link explains what it's doing:
[http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/](http://ubuntu.wordpress.com/2006/09/20/disable-touchpad-temporarily-when-typing/)

I thought I had touchpad problems until I realised that I hadn't waited long enough between pressing a key and using the touchpad. Drove me mad for a few hours while I was trying to Ctrl+Click things until I figured out what was going and reduced the "idle-time"...

On the fingerpring reader, I've found a program called thinkfinger (open source) that you can install from the repositories. Unfortunately I found it couldn't really recognise my finger (my swipes would fail 90% of the time) so I haven't found a solution yet.
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Hardy](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger#Hardy)

There's a binary-only alternative that I haven't tried yet, and I'm not sure if it works with the Dell laptop - I think it shares the same fingerprint device at the T43:
[http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader](http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader)

---

### Post by titimoi on 2008-06-27
Thank you for your answer. Well I haven't modified anything for this working delay, and I only changed some parameter in xorg.conf. Those problems seems to come from the new kernel.. I don't really know why.. as you said it must be a daemon problem.. as I am quite new on ubuntu.. I don't really know which one we are speaking about..

---

### Post by rossmoore on 2008-06-27
Me neither I'm afraid... Just a guess. I first touched linux 2 months ago. If I find anything I'll make another post.

---

### Post by titimoi on 2008-06-27
can you just tell me what kind of Touchpad you have, giving me the result of those command : > sudo cat /proc/bus/input/devices | grep GlidePoint just to verify if have the same

---

### Post by rossmoore on 2008-06-27
N: Name="AlpsPS/2 ALPS GlidePoint"

---

### Post by titimoi on 2008-06-28
ok cool we are speaking about the same !.. hope it will be fix for the next kernel !

---

### Post by Agrajag27 on 2008-07-04
Well, mine has been working great until THIS boot and now, no more scrolling. It worked every boot for the last two weeks (that's about 5 sessions as I mainly computer on my PC). I wish I knew enough about Ubuntu to troubleshoot it but this is yet another of the annoyances that makes me think it's really not worth the hassle.

I'm at an age now where I don't need to be a rebel. I just want stuff to work. Ubuntu was put forth as an OS that just works and then when you get into it you find that's a bit of a stretch. 

I still like what I see and I can still be functional with it but it's got to get to a point where this sort of thing is rarely heard of if any real progress is going to be made with market share. Bad catch-22 but that's the way it is.

---

### Post by pablopancho on 2008-07-05
Well, frankly speaking this  touchpad doesn't work perfectly even under Vista, maybe a little better but far from perfect. Compared to my previous laptop (Sony Vaio FS-315M) the experience of using the touchpad on Dell is poor. Strangely enough, in both cases they are Alps touchpads, but what a difference!

---

### Post by searayman on 2008-07-11
> **blekos said:**
> I have the xps1530.
If you upgrade the Bios to A008 for VT (i've done so) then you come up with your touchpad. The problem is solved easily if you do this:
add the bold letters to your menu.lst

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash **i8042.nomux=1**

the original post is here [http://ubuntuforums.org/showthread.php?t=737060&page=2](http://ubuntuforums.org/showthread.php?t=737060&page=2)

I am looking for suggestions for the following:
1. Volume up/down/mute does not work from remote control
2. Webcam does not work
3. sound works great but is it as good as in vista? (are the "same" drivers? or just compatibles)
4. finger rec. doesnot work (dont care really)
5. nvidia drivers are installed. How can i test the 3d acceleration etc?
6. card reader not yet tested

I am using Kubuntu 8.04

Thank you for your time

Ok I tried this the restarted my computer and it didnt fix my touch pad. 

Also I ma having problems with wireless not working.. has anyone goten a fix for that yet?

My bios is A08

when my mouse isnt spazzing out it takes a million swipes to move it, do i just need to configure it soem how?

---

### Post by pablopancho on 2008-07-12
I think you also need to add this "i8042.nomux=1" to the end of kernel line, like this:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2459ad2d-f94e-4023-9879-056482d69817 ro quiet splash vga=789 **i8042.nomux=1**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

And if there's an update of the kernel and touchpad misbehaves again, you may need to add this to the most recent kernel line as well, again (in case the file menu.lst was overwritten). 

If you've already done that, then I'm afraid I have no idea what to do next. Sorry :(

About wireless: what card do you have? My Intel PRO/Wireless 4965 AGN Network Connection worked out of the box, but sometimes you get Broadcom cards, which require ndiswrapper.

---

### Post by Agrajag27 on 2008-07-12
There is also absolutely an intermittent issue going on. I'm averaging success on about half my boots. Something with regard to boot order is hosing this. I don't have the understanding to troubleshoot it unfortunately.

---

### Post by searayman on 2008-07-12
> **pablopancho said:**
> I think you also need to add this "i8042.nomux=1" to the end of kernel line, like this:
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2459ad2d-f94e-4023-9879-056482d69817 ro quiet splash vga=789 **i8042.nomux=1**
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

And if there's an update of the kernel and touchpad misbehaves again, you may need to add this to the most recent kernel line as well, again (in case the file menu.lst was overwritten). 

If you've already done that, then I'm afraid I have no idea what to do next. Sorry :(

About wireless: what card do you have? My Intel PRO/Wireless 4965 AGN Network Connection worked out of the box, but sometimes you get Broadcom cards, which require ndiswrapper.

than you soo much!! that worked!!

I now have mouse but no wifi. I am not sure of my wireless card. If you give me a command to plug into terminal I can get it for you.

Also is there a way to get two finger scrollign to work for the touchpad?

thanks

---

### Post by pablopancho on 2008-07-12
I'm glad it helped. However I'm not an expert and I don't know how to customize touchpad behaviour any further, frankly speaking this touchpad isn't really perfect and scrolling feature is sometimes frustrating.

Wireless:
There probably is an easy way of finding the card in terminal but I don't know much of command line. But you could use a gui program called gnome-device-manager that will list all your hardware.

---

### Post by searayman on 2008-07-14
> **pablopancho said:**
> I'm glad it helped. However I'm not an expert and I don't know how to customize touchpad behaviour any further, frankly speaking this touchpad isn't really perfect and scrolling feature is sometimes frustrating.

Wireless:
There probably is an easy way of finding the card in terminal but I don't know much of command line. But you could use a gui program called gnome-device-manager that will list all your hardware.

OK Found it out. My wireless card is:

Dell Wireless 1505 Wireless-N Mini-card

Now how can I get that to work?

THanks!

---

### Post by unknownzlt on 2008-07-14
Make Additional money online [http://bux.to/?r=unknownzlt](http://bux.to/?r=unknownzlt) It's not a lie, but you won't earn millions of dollars. Its just additional pocket money for you.

---

### Post by pablopancho on 2008-07-14
Oops, if I'm not mistaken this is a Broadcom card which brings headache to ubuntu users. What you will need to use is ndiswrapper. Unfortunately I have no idea how to do it, I am a lucky user of Intel card.

Check forum for posts about your card and ndiswrapper, I'm sure someone solved this problem, you can't be the only one...

Sorry I can't help you any further :(

---

### Post by Lumpy da Moose on 2008-07-17
[FONT="Comic Sans MS"][SIZE="2"]
Hi--

For wireless support of the wonky Broadcom cards, check these links:

[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+hardy)

also:

[http://ubuntuforums.org/showthread.php?t=706034](http://ubuntuforums.org/showthread.php?t=706034)

You don't even really have to know what you're doing to do the install, if you follow the instructions **to the letter**.  There's links to the XP drivers for ndiswrapper and everything.

I'm living testament that it can be done without knowing much about the inner workings of Linux.  Writing this on an M1530 laptop and the only not-functioning item is the fingerprint reader; it is stubborn in XP, and it takes less time to type a password.  I have some of the touchpad issues as well, but I think as someone pointed out here, it's a matter of things either loading ahead or behind it that causes the problem.  When I'm at a desk, I just use a wireless mouse.[/SIZE][/FONT]

---

