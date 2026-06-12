---
title: "No internet connection on Dell M1530"
date: 2010-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by myrtle001 on 2010-07-29
After using the LiveCD twice now to compare Windows Vista versus Ubuntu 10.04, I am really impressed with Ubuntu.

The only thing I can't figure out is that my internet won't work. I've tried turning my WiFi off and then back on but then it just says something like "Loading" and doesn't change.

My wireless card is a Dell Wireless 1395 WLAN Mini-Card and I am running a 2008 Dell XPS M1530 using Ubuntu 10.04 32-bit off a LiveCD.

---

### Post by mansourk on 2010-07-30
Hi,
per haps you need wireless dirver. go to System -> Administration ->Hardware Drivers . the needed drivers for your system are listed there. you can download your wireless driver with a cabled internet right from here and then use your wireless.

---

### Post by myrtle001 on 2010-07-30
Ok, so now I'm thinking on actually installing Ubuntu 10.04 on my computer using Wubi but I have a few things to clarify before I go and completely install a new OS:
**1)**This will dual-boot Windows Vista and Ubuntu, right?
**2)**Has anyone ever heard of the installation process not working, or does it usually work?
**3)**Is there any way to expand the partition it creates? Example: I have 144GB free space on my hard drive. I'm planning to give Ubuntu about 15GB. If I like Ubuntu, I might want to give it a little more. Is it possible to do this?
**Last but not least 4)**Is the "wubi.exe" that is on the LiveCD the same Wubi that you can download from like [www.wubi-installer.org?](www.wubi-installer.org?)

I have been very impressed by Ubuntu on the LiveCD, but I would like to now even install it. I found that Wubi can be unistalled if you don't like it, so I've chose to go that route.

As far as the internet connection goes, I will install Ubuntu via Wubi first and then I will look for drivers as you said.

Thanks in advance!

**EDIT**:My computer has the Media Center button that Dell puts on laptops now. I've read that this can completely screw up computers. Will Wubi do this??

---

### Post by ptn107 on 2010-07-30
You should try to get native Ubuntu working before Wubi.  Your wireless will work.  It's just a matter of using either the STA driver (bcmwl-kernel-source) or the B43 driver (b43-fwcutter).

If you can post the results of the following terminal commands it would be very helpful.

lspci -nn | egrep Network
lspci -v

---

### Post by myrtle001 on 2010-07-30
> You should try to get native Ubuntu working before Wubi.

Do you mean use the LiveCD (I'm new to most of this)?

> If you can post the results of the following terminal commands it would be very helpful.

So all I have to do type the commands into the terminal?

Thanks again!:)

---

### Post by ptn107 on 2010-07-30
Yeah from the Live CD (if your not planning on installing Ubuntu to the hard disk at least).  Just go to Applications -> Accessories -> Terminal, type the first command and press enter.  Paste the results.  Repeat for the second command.

first command:
lspci -nn | egrep Network

second command:
lspci -v

---

### Post by myrtle001 on 2010-07-30
> Paste the results.
Okay, I had the results but since I had no internet I could not post them here. I tried connecting to the DSL modem but had no success there.

I would have saved the results as a ".doc" file in OpenOffice to my hard drive, but I didn't know if that would completely screw up my hard drive or not.

Thanks!:)

---

### Post by myrtle001 on 2010-07-31
Okay, after figuring out how to get the results over to windows, I've been able to get the results!:)

Sorry it took so long, I'm new to all of this:

For the [FONT="Courier New"]lspci -nn | egrep network[/FONT] I got nothing. No results at all.

For the [FONT="Courier New"]lscpi -v[/FONT], this is what I got:
```

0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 
	Subsystem: Dell Device 000b 
	Flags: bus master, fast devsel, latency 0, IRQ 17 
	Memory at f1efc000 (64-bit, non-prefetchable) [size=16K] 
	Capabilities: <access denied> 
	Kernel driver in use: b43-pci-bridge 
	Kernel modules: ssb 

```
To make the post shorter, I just kinda guessed you wanted the one with "Network controller:" on it. If you need more, I got all of the results.

Any help is very much apprieciated!:D

Thanks!

---

### Post by ptn107 on 2010-07-31
Ok lets try this B43 driver.

First pop open a terminal again (Applications -> Accessories -> Terminal) and type this:
```
sudo touch /etc/modprobe.d/blacklist-bcm43.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-bcm43.conf
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist-bcm43.conf
```

Now you need to download these files any way you can and get them onto your Ubuntu Desktop (a flash drive will be handy):
[_b43-fwcutter_012-1build1_i386.deb_]("http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb")
[_wl_apsta-3.130.20.0.o_]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")
[_broadcom-wl-4.150.10.5.tar.bz2_]("http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2")

Go back to the terminal:
```
cd ~/Desktop/
sudo dpkg -i b43-fwcutter_012-1build1_i386.deb
```
When it asks you to extract and install firmware say NO!

Now at a terminal you can type this:
```
b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo modprobe -r ssb
sudo modprobe -r bcm43xx
sudo modprobe -i b43
sudo modprobe -i b43legacy
```

This really should be done from an installed system.  Never did this from a live CD before since it usually requires a restart after.

---

### Post by myrtle001 on 2010-07-31
> This really should be done from an installed system.
Should I just install Ubuntu from Wubi now so it is an installed version? I was planning on doing that anyway once I got internet working. If I do, I'll probably give it 20GB to 25GB.

> ```

sudo touch /etc/modprobe.d/blacklist-bcm43.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-bcm43.conf
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist-bcm43.conf

```
This will probably make me sound more like one, but I guess I'm what people call a "noob" to Linux. Is each line in the code a separate command, or do I just copy & paste this whole thing into the terminal? I ask the same thing about the rest of the codes.

And I also just need to make sure of this: If I never ever again press my Windows MediaCenter button, will everything be okay (I've read that the MediaCenter can screw up computers)?

Thanks for the help! I appreciate it very much!:D

---

### Post by ptn107 on 2010-08-01
I would just install Ubuntu even if you're going to Wubi install it.  Just go for it.  Each of those commands in the terminal is separate so you must type each line and press enter to execute it.  Then go on to the next command.  I would not worry about your mediacenter button.  Sorry for the delay, but I work night shifts sometimes.

---

### Post by myrtle001 on 2010-08-01
Okay, I'm having a slight issue with Wubi. It gets done "extracting" files from the E: drive (CD) and then shoots near done and says "An error occured" and something like "Access denied", and then "see (a file location) for details" which I go to and it doesn't exist. Right now I just went and uninstalled it. Not sure, maybe it was just a false error thing?

> Sorry for the delay, but I work night shifts sometimes.
I don't mind. I appreciate all the help I get at the forums here!

I'll be gone for a week starting at 12:15PM Eastern time, but I hope to have my computer with so I think I'll download the driver files before I leave.

Thanks so much for the help ptn107, I really helps noobs like me get Ubuntu installed and ready.:D

---

### Post by ptn107 on 2010-08-02
Make sure you right-click wubi and choose 'Run as administrator'.

---

### Post by myrtle001 on 2010-08-06
Ok, I'm back.

I've tried to install Ubuntu via Wubi several times now with and without the CD. I tried "Run as administrator" and this is what eventually happened:
[ATTACH]165688[/ATTACH]
Of course it said something after c:/users/ but I edited that out. I think I'm going to have to make a new LiveCD, but I just wanted to make sure that was the right thing to do.

I've got the drivers on a USB drive so they're ready to go once I get Ubuntu going.

Thanks for the help!

**EDIT:** I've tried downloading Wubi from [www.wubi-installer.org](www.wubi-installer.org) but that one keeps telling me that there is no disk in the computer and to insert a disk.

---

### Post by ptn107 on 2010-08-07
Personally I would just install Ubuntu side-by-side with Windows in your situation.  Download[1] the Ubuntu 10.04 CD and when it comes to partitioning choose 'Install them side-by-side choosing between them each startup'.  Then adjust the slider bar to change the amount of space you give to Ubuntu.

[1] [_32-bit Live CD_]("http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-i386.iso"), [_64-bit Live CD_]("http://releases.ubuntu.com/lucid/ubuntu-10.04-desktop-amd64.iso")

---

### Post by myrtle001 on 2010-08-07
Okay. Now if I do this, will it screw up Windows? I have a 285GB hard drive with 143GB free.
[ATTACH]165749[/ATTACH]
Now, if I give Ubuntu 10.04 about 20-40GB of that, will this screw up Windows and all this boot record stuff and etc.?

Next, will I be able to uninstall Ubuntu if I decide I do not like Ubuntu? I know I'll probably have to uninstall it from Ubuntu and it will be somewhat confusing.

Sorry if I'm getting kinda hard to give help to, I'm just being careful with my computer and I'm defiantly a noob.

I appreciate all the help!

---

### Post by ugm6hr on 2010-08-07
Couple of things to remember:
1. Installing any new OS can potentially "screw up" any existing OS. I would recommend making a complete backup before proceeding.
2. Resizing existing partitions (the hard drive space that Windows exists on) is more likely to screw things up. Hence, take heed of above advice.
3. I have never tried Wubi, but my understanding is that it significantly reduces (or maybe completely removes) the above hazards, but trades them for others that are more likely to be problematic in the long term. If you like the LiveCD experience, I'd suggest a proper installation - true "dual-booting" (unlike Wubi).
4. A true dual-boot cannot be "uninstalled" with a few clicks, but it can be removed. Just make sure you find the correct instructions on how to do it before experimenting, since it can be trickier than the original installation.
5. Windows will run just fine with a smaller space on the HD.
6. The boot record will be (correctly) over-written when you install Ubuntu. You will still be able to boot into Windows, provided you do it correctly.

In summary, it's easy to install Ubuntu, but it is prudent to backup data before doing so.

What version of Windows are you running? Vista can resize its own HD partition, which simplifies things.

---

### Post by myrtle001 on 2010-08-07
This is the version of Windows that I use, straight from the Control Panel:
[ATTACH]165763[/ATTACH]

I've made a new LiveCD with the download link ptn107 gave to me. I tried Wubi again, but I guess its a lost cause. It does, though, show up in the "Uninstall a program" area of the Control Panel but I delete it immediately because I'm not sure if it's safe to restart the computer with a faulty installation of an OS.

I just need very detailed instructions (but *too* detailed, I am a noob) how to dual-boot Ubuntu 10.04 LTS alongside Windows Vista. I also take it that I'm supposed to use a 32-bit OS since my Control Panel says "32-bit Operating System".

I ***really, really, really*** want to get this to work, but I **do not** want to mess up my computer!

I really do apprieciate all of this help I get on the Ubuntu Forums!:D

---

### Post by ugm6hr on 2010-08-07
Use the Vista partition resizing tool to about 390GB, **after** backing up your files.
Then install ubuntu using the Manual process into the "unallocated" space.

If you really are very inexperienced, and have never installed an OS at all, I would suggest you find someone who can help you in person. While the forums are great for trouble-shooting, they are not live help, and it may be very tempting to progress through the installation without knowing what you are doing.

Equally, it is almost impossible for someone else to write personalized step-by=step instructions.

Anyway - yes - just use 32-bit if you are not sure.

---

### Post by myrtle001 on 2010-08-07
I'll kinda just think over which route I want to go here to get Ubuntu on my computer and get back to the forums with my decision.

I have some experience in technology and am not able to get a tech person out here. 

I guess I'm just a little surprised it wasn't as easy as I thought it would be to dual-boot Ubuntu for people who have never done this before.

I'll get back eventually with my decision how to get Ubuntu to dual-boot with Windows.

I must say though that I am very surprised at how much good help I have got so far here on the Ubuntu Forums. I defiantly know where to go whenever I have a question about Ubuntu. I really, **really** appreciate the support I've got here. **Thank you very much**!:D:D

---

### Post by ugm6hr on 2010-08-08
> **myrtle001 said:**
> I guess I'm just a little surprised it wasn't as easy as I thought it would be to dual-boot Ubuntu for people who have never done this before.

It is very easy, in fact. It can be done by just a few clicks. But installing an OS is never going to be 100% easy.

However, data corruption or user error *can* occur, which is where all the complaints come from.

As mentioned, if you shrink the partition from within Vista - you should then be able to use the "Guided - use largest unallocated space" installation" option to install without being confronted with too many options.

---

### Post by myrtle001 on 2010-08-08
[ATTACH]165849[/ATTACH]
Ok, so say I want to create a new 30GB partition for Ubuntu from the OS "C:" partition. Would I do this by doing the "Shrink Volume" option to about 30,720MB (30GB)? I just want to be able to use Ubuntu in its full form with internet (which I will install the drivers for once I get Ubuntu installed) and speed **without** any risk of corrupting the 145GB of files on Windows Vista. Due to the fact I live hundreds of miles away from any somewhat "big" city, I can't get any live help. I feel capable enough to install Ubuntu on my own.

Defiantly when I get a new computer, I will run Ubuntu on its own. Let's face it, Ubuntu is just better.

Thanks to ptn107 and ugm6hr for your great support helping me to install Ubuntu 10.04 and get it up and running to its full force!:D:D

---

### Post by ugm6hr on 2010-08-08
You have 4 partitions at present, it appears

The first is likely related to the recovery / hardware testing, the second is the recovery partition itself, and the third is "C" (or Vista).
The final in the diagram, "Healthy, Primary Partition" looks like it is completely empty and unformatted at 2.5GB.

Hence, I would suggest deleting that 4th partition completely, and reducing the size of C to 30GB less than its current size.

After this, you can install into the largest unallocated space.

Remember, there is no 100% guarantee that resizing will not cause file corruption, in the same way that defragmenting can also cause problems. Hence, backups are vital.

---

### Post by myrtle001 on 2010-08-08
I have another question now: under which partition is the MediaDirect or MediaCenter thing located (I'm just worried it is the 2.5GB partition)? I hear it somewhat acts as an operating system that formats the hard drive when you start it up.

And to delete the healthy 2.5GB of space, I just click "delete volume", or is there a catch?

I guess I'm just gunna throw an idea out there: Is there a way to install Ubuntu onto my 2GB USB zip-drive and then copy the files onto a new partition? It probably won't work, but I'm just coming up with ideas.

We do have a backup hard drive, but I think there might already be files saved onto it from our old computer (which my mind should run Xubuntu, since it runs *so* slow).

I guess I could say I'm slowly making the change from Windows to Linux, just looking for the **safest** way to get Ubuntu onto my computer. I saw Wubi as the safest and easiest way, but these errors showed up (click the links):  [Annoying pyrun.exe]("https://bugs.launchpad.net/ubuntu/+bug/365881") and [Permission denied]("https://bugs.launchpad.net/wubi/+bug/371264") even running as admin and I tried from two LiveCDs.

Thanks for all the help!:D

---

### Post by ugm6hr on 2010-08-08
In turn:
1. I don't know where the Media Center software is installed. If it is in a separate partition, it could be the 2.5GB one. It might be worth checking what Partition Manager on Ubuntu LiveCD labels it as.
2. Yes, you can just delete it.
3. No, you can't copy from USB to HD. In any case, how would that help? You can install it on to a USB drive, but subsequently copying to HD will be harder than installing directly.
4. Can't help with Wubi - I never used it. It should be the safest way, but isn't really a proper Ubuntu installation.

---

### Post by myrtle001 on 2010-08-08
[attach]165867[/attach]
Looks like the 2.5GB space was MediaDirect/"Extended".

So, can I make a 30GB partition out of the OS partition without backing up, or is this the part where it gets risky?

And if I do, are these the correct steps?
[LIST=1]
[*]Click Shrink Volume
[*]Set amount of space to be shrunk to 30,720MB and click shrink.
[*]That's it.
[/LIST]

Sorry if I'm being somewhat hard to help, just making sure I know what I'm doing.

Thanks for the help!:D

**EDIT: I edited out the Serial Number and Worldwide Name**

---

### Post by ugm6hr on 2010-08-08
Any partition management is *always* risky. Degree of risk is greater if resizing / moving, less if deleting or creating.

Given the way your HD is configured, you will have to shrink Vista, extend the "Extended partition" to include the newly created empty space, and then install into the empty part of the Extended partition.

This is because, only 4 primary partitions are permitted, and you already have 4.

---

### Post by myrtle001 on 2010-08-08
How about I try doing it this way: I'll install Ubuntu on a 2GB USB zip drive and save files into a specific folder on the C: drive (something like C:\Ubuntu\Username\Documents). This *sounds* like it would be risk free and an easy installation of Ubuntu. I take it it would be as fast as it would be on the hard drive, but I want to make sure about that.

Thanks everyone for the great support and helping me install Ubuntu for the first time! I really do appreciate all this help!:D

---

### Post by ugm6hr on 2010-08-08
That won't work.
1. 2GB is too small for Ubuntu. Realistically, you will need 8GB as a minimum.
2. It is not risk free. It is possible to accidentally over-write the MBR on your HD, which will then mean you won't be able to boot the computer without the USB plugged in. IF you go down this route, make sure you know how to manually change the location of the bootloader.

PS: I presume you mean USB Flash, rather than USB zip drive.
Also, writing files to the Vista NTFS formatted C drive will require installation of NTFS-config (don't worry, this is easy to do).

---

### Post by myrtle001 on 2010-08-08
Alright. Next time I get a chance I'll buy probably a 16GB "flash" drive (I just call them "zip drives") to install Ubuntu on. I'll get back to this thread when that happens to take the next step.

Thank you very much! I'm getting excited now to finally get Ubuntu! I apprieciate the help!:D:D:D

NOTE: I'm not going to list mark this thread as "solved" since Ubuntu is not up and running yet on my computer.

---

### Post by myrtle001 on 2010-08-09
Hallelujah!

Today I received my Ubuntu 10.04 LTS LiveCD in the mail and Wubi worked on the first try! I guess the two CDs I made are corrupted in some way. I've booted into both Ubuntu and Windows Vista and each work properly (except for the fact I still haven't installed the wireless drivers yet, so internet doesn't work (which was the whole point of this thread ;)haha)).

I'm both glad and very relieved I don't have to do a risky full install of Ubuntu. I logged into Ubuntu and it all seems to work just fine.

I must also say that it only took 2 weeks for my LiveCD to get from the Netherlands to Midwestern US, way less than the advertised 6-10 weeks!

So, I guess my question is should I be doing this:
> **ptn107 said:**
> Ok lets try this B43 driver.

First pop open a terminal again (Applications -> Accessories -> Terminal) and type this:
```
sudo touch /etc/modprobe.d/blacklist-bcm43.conf
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-bcm43.conf
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist-bcm43.conf
```

Now you need to download these files any way you can and get them onto your Ubuntu Desktop (a flash drive will be handy):
[_b43-fwcutter_012-1build1_i386.deb_]("http://mirrors.kernel.org/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb")
[_wl_apsta-3.130.20.0.o_]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o")
[_broadcom-wl-4.150.10.5.tar.bz2_]("http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2")

Go back to the terminal:
```
cd ~/Desktop/
sudo dpkg -i b43-fwcutter_012-1build1_i386.deb
```
When it asks you to extract and install firmware say NO!

Now at a terminal you can type this:
```
b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo modprobe -r ssb
sudo modprobe -r bcm43xx
sudo modprobe -i b43
sudo modprobe -i b43legacy
```

This really should be done from an installed system.  Never did this from a live CD before since it usually requires a restart after.

I thank everyone for the great support, I appreciate it very, very much!:D:D:D

---

### Post by Wilbefast on 2010-08-10
> **mansourk said:**
> Hi,
per haps you need wireless dirver. go to System -> Administration ->Hardware Drivers . the needed drivers for your system are listed there. you can download your wireless driver with a cabled internet right from here and then use your wireless.

I have a similar problem with my Dell Vostro 1510. Most of the time I have the wireless physically switched off. Now when I need to use it (when I don't have a wired connection) I click the physical switch on but all it says under wireless network is "disconnected" or "not available".

I remember that with 9.04 I would get a list of available networks, but 10.02 seems to want me to set up a network, enter all this information, stuff about DNS, VPN, WLAN and so on. I'm far too much of a noob to know exactly which IP I want to connect to, and even if I wasn't it's a bit of a Catch22 situation. Can't I just select a network from a list? Long story short I'm using my Windows partition to write to you now, because on Ubuntu I can't connect :(

 I think the problem may stem from the fact that I installed Ubuntu without turning the wireless on (hence  no hardware was detected, hence no drivers were installed). But is there any way I can get hold of the drivers other than the automatic update? I hate using Windows online because I have no antivirus :o

Dell Vostro 1510
Ubuntu 10.02 (Lucid Lynx) 64bit

Thanks,

William

---

### Post by ugm6hr on 2010-08-10
This should be a simpler solution: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

---

### Post by myrtle001 on 2010-08-10
I'm not able to get an ethernet cable at the moment, so I'm not able to get a wired connection from my router to my computer.

I was just wondering would those commands do what I need?

Thanks in advance!:D:D:D

---

### Post by ugm6hr on 2010-08-10
This is how I achieved it:
[http://ubuntuforums.org/showthread.php?t=1477215](http://ubuntuforums.org/showthread.php?t=1477215)

---

### Post by Wilbefast on 2010-08-10
> **ugm6hr said:**
> This should be a simpler solution: [http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)
Cool-o I did a quick search for the specific package ([COLOR=#000099]bcmwl-kernel-source[/COLOR]) and got a deb from the first hit that came up. Now I'm talking to you from Ubuntu - thanks ;)

---

### Post by myrtle001 on 2010-08-11
Hey there, just thought I'd let you guys know I got my internet up and running (I'm posting this from Chrome on Ubuntu)!

I found a ethernet cable as I was just going through some stuff and used it to download the [FONT="Courier New"]bcmwl-kernel-source[/FONT] package, which gave me the B43 driver I needed to connect to my network.

Thanks everyone for helping me, I couldn't have done it without you guys!:D:D:D

myrtle001

---

