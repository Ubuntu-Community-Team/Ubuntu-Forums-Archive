---
title: "XPS 15z Fail"
date: 2011-06-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by redoubt33 on 2011-06-05
Dear Community,

I recently bought an XPS 15z hoping to install Ubuntu.  However, I have had nothing but trouble with this hardware.  Most USB and CD/DVD Live sessions fail with either blank screen or initramfs failures.

Finally, I was able to get 10.04 and 11.04 to install but with major issues.  For 10.04, my screen is at a much lower resolution, wired/wireless interfaces are not recognized, and trackpad is not recognized.  For 11.04, my screen's native resolution (1080p) is recognized, and the wireless interface is recognized, but my trackpad (trackpad!) still is not recognized.  To make matters worse, allowing the update manager to update all available packages makes the machine unbootable with a blank screen after the initial splash.

My questions:
1) Is it unrealistic to expect new hardware like this to be supported?
2) Do I report these as launchpad bugs?  What output will I need?  (dmesg shows no obvious errors)

Thanks.

---

### Post by Toz on 2011-06-05
I believe this system has the optimus graphic system. Have a look at this thread: [http://ubuntuforums.org/showthread.php?t=1618801](http://ubuntuforums.org/showthread.php?t=1618801)

---

### Post by redoubt33 on 2011-06-06
Thanks for the link.  Any thoughts on how I begin to troubleshoot the unrecognized trackpad?

---

### Post by Toz on 2011-06-06
Try the boot option **i8024.nomux**. For instructions, see:[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions"). Try first and if it works, then make it permanent.

---

### Post by jwhirl06 on 2011-06-07
> **Toz said:**
> Try the boot option **i8024.nomux**. For instructions, see:[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions"). Try first and if it works, then make it permanent.

Did not fix the issue for me. It's Cypress Semiconductor trackpad, I added that command to the kernel just before boot with no luck. Thanks though... wonder what it could be...

---

### Post by Toz on 2011-06-07
> **jwhirl06 said:**
> Did not fix the issue for me. It's Cypress Semiconductor trackpad, I added that command to the kernel just before boot with no luck. Thanks though... wonder what it could be...

@jwhirl06 - do you have the same system? 

Other options that are good for troublesome trackpads are:```
i8024.reset
i8024.nopnp
i8024.noloop=1
irqpoll
```

Perhaps you can try those. Otherwise, post back the contents of /var/log/Xorg.0.log/

---

### Post by zobbo on 2011-06-08
I ordered my XPS 15z yesterday and will be installing Ubuntu onto it when it arrives so will be following this thread with interest. If you make any further progress please report it here!

---

### Post by xxjoshxx on 2011-06-08
> **zobbo said:**
> I ordered my XPS 15z yesterday and will be installing Ubuntu onto it when it arrives so will be following this thread with interest. If you make any further progress please report it here!

Me too. Any help would appreciated.

---

### Post by Toz on 2011-06-08
Other links of interest:

- [https://launchpad.net/~dell-14z-15z](https://launchpad.net/~dell-14z-15z)

- [http://en.community.dell.com/support-forums/laptop/f/3518/t/19382036.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/t/19382036.aspx)
- [https://answers.launchpad.net/ubuntu/+question/160465](https://answers.launchpad.net/ubuntu/+question/160465)
-

---

### Post by mattold7 on 2011-06-08
I also have a XPS 15z and desperately trying to get everything to work!

---

### Post by redoubt33 on 2011-06-10
So it appears that the boot options have worked for no one?  

Are there any other ideas?  Isn't this the same (or similar) trackpad that the Macbook Pro uses, which purportedly works "out-of-the-box" with Natty?  Am I missing something here?

[https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad)

Thanks for the help.

---

### Post by jwhirl06 on 2011-06-14
> **redoubt33 said:**
> So it appears that the boot options have worked for no one?  

Are there any other ideas?  Isn't this the same (or similar) trackpad that the Macbook Pro uses, which purportedly works "out-of-the-box" with Natty?  Am I missing something here?

[https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad](https://help.ubuntu.com/community/MacBookPro8-1/Natty#Touchpad)

Thanks for the help.

I have a 2nd gen  XPS15Z as well and my trackpad doesnt work either. help!!

---

### Post by markbl on 2011-06-14
I ordered an xps 15z 3 weeks ago and have been waiting patiently for it to arrive. It was due tomorrow but after discovering the problems reported here and elsewhere with linux compatability, particularly with the graphics and touchpad I have just cancelled the order. :(

---

### Post by jwhirl06 on 2011-06-15
> **markbl said:**
> I ordered an xps 15z 3 weeks ago and have been waiting patiently for it to arrive. It was due tomorrow but after discovering the problems reported here and elsewhere with linux compatability, particularly with the graphics and touchpad I have just cancelled the order. :(

I wouldn't have canceled it. It's a great laptop and I am sure support will be here in the near future. I'd re-order it. It's a beast. Just be patient.

---

### Post by jwhirl06 on 2011-06-15
> **Toz said:**
> @jwhirl06 - do you have the same system? 

Other options that are good for troublesome trackpads are:```
i8024.reset
i8024.nopnp
i8024.noloop=1
irqpoll
```

Perhaps you can try those. Otherwise, post back the contents of /var/log/Xorg.0.log/

Thanks, I will give those a try now.

---

### Post by jwhirl06 on 2011-06-15
yeah no dice on those kernel commands... I'm looking at XInput and it says that I havea  PS/2 Generic Mouse as slave pointer (2) with the ID of 13...

---

### Post by markbl on 2011-06-15
> **jwhirl06 said:**
> I wouldn't have canceled it. It's a great laptop and I am sure support will be here in the near future. I'd re-order it. It's a beast. Just be patient.

I may reorder later. Without a working touchpad it is not really a usable portable device atm. Also, it will be a long while before optimus graphics are supported properly in linux, if ever. I think it makes more sense to look for a notebook with non-hybrid graphics.

---

### Post by jwhirl06 on 2011-06-15
> **markbl said:**
> I may reorder later. Without a working touchpad it is not really a usable portable device atm. Also, it will be a long while before optimus graphics are supported properly in linux, if ever. I think it makes more sense to look for a notebook with non-hybrid graphics.

Eh, try bumblebee. Worked good for me. I think our problem here is the lack of a driver for the Cypress trackpad. Hmmmm...

---

### Post by verwilst on 2011-06-16
In order to facilitate our efforts to get Ubuntu running on the XPS 15z, I created a new wiki page dedicated to this laptop.

I hope you guys join in and add useful information to this page, it will surely help a lot of people.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z]("https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z")

I've only received mine for a couple of hours, just finished installed Ubuntu 11.04 on it, and currently rebooting. Therefor the page only has my very rudimentary findings.

Thanks!

Bart

---

### Post by jwhirl06 on 2011-06-16
> **verwilst said:**
> In order to facilitate our efforts to get Ubuntu running on the XPS 15z, I created a new wiki page dedicated to this laptop.

I hope you guys join in and add useful information to this page, it will surely help a lot of people.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z]("https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z")

I've only received mine for a couple of hours, just finished installed Ubuntu 11.04 on it, and currently rebooting. Therefor the page only has my very rudimentary findings.

Thanks!

Bart

Thanks Bart. I will contribute what I can just let me know what you need.

---

### Post by verwilst on 2011-06-16
> **jwhirl06 said:**
> Thanks Bart. I will contribute what I can just let me know what you need.

I don't need anything :) Feel free to add whatever you think is relevant :) Go crazy ;)

---

### Post by jwhirl06 on 2011-06-16
> **verwilst said:**
> I don't need anything :) Feel free to add whatever you think is relevant :) Go crazy ;)

How do we install the driver file for the cypress trackpad?

---

### Post by verwilst on 2011-06-16
> **jwhirl06 said:**
> How do we install the driver file for the cypress trackpad?

You can't. It was just an initial patch that the Cypress dev posted to get some feedback. I've mailed him to ask for a status update.. :)

---

### Post by verwilst on 2011-06-16
About fan noise.. The 15z seems a lot louder fan-wise than for example my Latitude E6500. The latter has no audible fan noise, while I can clearly hear my 15z blow its fans. Anyone here used the 15z with Windows, and noticed that it was a lot quieter there?

---

### Post by jwhirl06 on 2011-06-16
> **verwilst said:**
> You can't. It was just an initial patch that the Cypress dev posted to get some feedback. I've mailed him to ask for a status update.. :)

Thank you, glad to see we're making progress!! Also, is anyone here using bumblebee to manage optimus

---

### Post by jwhirl06 on 2011-06-16
> **verwilst said:**
> About fan noise.. The 15z seems a lot louder fan-wise than for example my Latitude E6500. The latter has no audible fan noise, while I can clearly hear my 15z blow its fans. Anyone here used the 15z with Windows, and noticed that it was a lot quieter there?

Ya, but I think it probably has something to do with windows having all of the necessary drivers to sense temperatures & maintain fan control.

---

### Post by jwhirl06 on 2011-06-17
any updates

---

### Post by doughnuts64 on 2011-06-21
I have read through a number of threads and discussions on the 'Net about this topic, and almost did not consider buying the 15z, as it seemed as though getting Ubuntu working is virtually impossible.

I am pleased, however, to say that I have managed to get Ubuntu installed, using the CD. The trackpad does not work, as everyone else has found, but other than that, my limited use of my machine has not suggested any areas which are not functioning correctly.

I selected the Nvidia restricted driver, and installed it, and rebooted, and all graphics seem to be working fine (however, I cannot use the NVidia settings application).

Other than the trackpad, is there anything else I should check to see whether it is not working?

---

### Post by ChoneZone on 2011-06-21
> **doughnuts64 said:**
> Other than the trackpad, is there anything else I should check to see whether it is not working?

How is the webcam functionality?

---

### Post by spjakob on 2011-06-21
> **doughnuts64 said:**
> I have read through a number of threads and discussions on the 'Net about this topic, and almost did not consider buying the 15z, as it seemed as though getting Ubuntu working is virtually impossible.

I am pleased, however, to say that I have managed to get Ubuntu installed, using the CD. The trackpad does not work, as everyone else has found, but other than that, my limited use of my machine has not suggested any areas which are not functioning correctly.

I selected the Nvidia restricted driver, and installed it, and rebooted, and all graphics seem to be working fine (however, I cannot use the NVidia settings application).

Other than the trackpad, is there anything else I should check to see whether it is not working?

There are more problems; 

Battery is consumed very fast.
Laptop is hot even during idle
Fan is very loud.
external SATA port and USB is not working as install media (when I tried, has to be confirmed).

but the most annoying problem right now is the nonworking trackpad.

Personally, I do not care about nvidia, gfx, I just want a silent, cool laptop with long battery life. I heard from a friend that there existed trackpad drivers that has not yet been merged into official kernel (and distro), has anyone tried these?

---

### Post by doughnuts64 on 2011-06-21
> **spjakob said:**
> There are more problems; 

Battery is consumed very fast.
Laptop is hot even during idle
Fan is very loud.
external SATA port and USB is not working as install media (when I tried, has to be confirmed).

but the most annoying problem right now is the nonworking trackpad.

Personally, I do not care about nvidia, gfx, I just want a silent, cool laptop with long battery life. I heard from a friend that there existed trackpad drivers that has not yet been merged into official kernel (and distro), has anyone tried these?

I have not tried it on battery, I have to confess, but I don't think the fan is particularly loud, and the laptop did not get very hot while I was using it. In fact, after it had been on in Ubuntu for a number of hours, I was very surprised how cool it felt when I finally turned it off, when compared against my Dell XPS M1330, which gets so hot on the outside, it nearly burns.

I had read that there were problems with installing from USB, so did so from CD, and it seemed to freeze at certain points, but did install Ok.

---

### Post by doughnuts64 on 2011-06-21
> **ChoneZone said:**
> How is the webcam functionality?

Webcam seems to work fine. I have tested it using 'Cheese', as well as the 'Test' button in Skype (I've not yet had a video conversation on Skype with anyone).

> **spjakob said:**
> There are more problems; 

Battery is consumed very fast.
I am going to leave my laptop running off battery to see how long it lasts. The time Ubuntu is quoting is about 3 hours. I'll leave it for a while, and see what it says afterwards.

---

### Post by doughnuts64 on 2011-06-21
On the subject of battery life, having left the laptop running on battery power, with processes running (Dropbox downloading a few GB) the whole time, including 20 minutes full-screen video calling (yes, the webcam does work with Skype calls), my battery time after over an hour is saying 1hour 45 minutes left. Is that poor battery life?

Further, the fan is working normally - nice and quiet. It's not spun up high once while I have been using the laptop, despite the 20 minutes full-screen video.

The laptop is also surprisingly cool.

---

### Post by zobbo on 2011-06-21
There's a new page up to support the hardware at [https://wiki.edubuntu.org/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.edubuntu.org/HardwareSupport/Machines/Laptops/Dell/XPS/15z) - trackpad seems to be unsolvable at the moment.

For myself, I'm finding the machine so powerful and it has so much RAM, that running Ubuntu in a 3GB of RAM VM is good enough for me at the moment. With VMWare Workstation it's pretty seamless.

Edit - OK, I'm an idiot - that page was put up by somebody here :).

---

### Post by kaaloo on 2011-06-23
I just got mine, the only way to avoid 

drm:intel_dsm_platform_mux_info: *error* mux info call failed

and freezing at boot is to add acpi=off but then it only sees one core and I also miss unity very much :(

I have tried all of the 3.0 kernels up to rc4 (on 11.04) without seeing a change in this behavior.

Luis

---

### Post by doughnuts64 on 2011-06-23
> **kaaloo said:**
> I just got mine, the only way to avoid 

drm:intel_dsm_platform_mux_info: *error* mux info call failed

and freezing at boot is to add acpi=off but then it only sees one core and I also miss unity very much :(

I have tried all of the 3.0 kernels up to rc4 (on 11.04) without seeing a change in this behavior.

Luis

This confuses me. I'm no expert at configuring Ubuntu, but I have my laptop up and running, and Ubuntu can see all four cores (two cores with two threads each), and it reports their usage. I've never seen that error that you are quoting. I'm using the standard Ubuntu 11.04, installed from CD (not USB stick). I connected it to the wireless network before starting the install, and checked the box to download updates while installing.

As soon as I was in (logging into 'Ubuntu Classic' as Unity sucks IMHO), I performed a
```
sudo apt-get upgrade
```
after which I rebooted, and selected the NVidia restricted driver.

Prior to selecting the NVidia driver, there were performance lags every-so-often, which were pretty annoying, but since installing the NVidia drivers, I have had no issues at all.

The only thing which still does not work is the trackpad.

---

### Post by kaaloo on 2011-06-23
More experimentation: Another way to boot is to use nosplash (no need to put acpi=off in this case) but then the keyboard doesn't work.

---

### Post by abys on 2011-06-23
Hi all,

I think the best way to boot for the moment is with acpi=noirq

You'll get the 4 cores and keyboard working.

For the grafic card, i've install bumble bee that way :

```
sudo apt-get install git
# type password
git clone https://github.com/MrMEEE/bumblebee.git
cd bumblebee/
sudo ./install.sh
optirun glxgears
# check the speed and compare to running:
glxgears
```
[http://linux-hybrid-graphics.blogspot.com/2011/05/testers-needed-intelnvidia-bumblebee.html](http://linux-hybrid-graphics.blogspot.com/2011/05/testers-needed-intelnvidia-bumblebee.html)

It found that I had a xps 15z and works great. Something need to be installed for glxgears but don't remember what.

Trackpad is still not working even with kernel 3.0 rc4 but I don't mind as I use a USB Mouse. My Ipod touch and  phone are not detected.

Hope it help.

---

### Post by pmartrenchar on 2011-06-23
I installed bumblebee from git too, It recognized my dell 15z, but the files bumblebee-enableCard and disableCard are not set so I have the error:

optirun cd
 * Starting Bumblebee X server bumblebee                                       
 /usr/local/bin/bumblebee-enablecard: 1: &#65533;: not found
                                                                         [ OK ]
exec: 301: cd: not found
 * Stopping Bumblebee X server bumblebee                                         * 
/usr/local/bin/bumblebee-disablecard: 1: &#65533;: not found
                                                                         [ OK ]

What script are you using?

Thanks

---

### Post by kaaloo on 2011-06-24
abys:  acpi=noirq is working great, thanks!

pmartrenchar: I'm getting the same output as you :(  However I do see the speed increase with optirun.

Now, what I have not been able to do is to use the nvidia drivers with gdm, x never starts complaining about a missing screen (after running nvidia-xconfig).  I'm using the 270.41.06 drivers from oneiric and running the 3.0rc4 kenel.

[    11.670] (II) LoadModule: "nvidia"
[    11.670] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    11.744] (II) Module nvidia: vendor="NVIDIA Corporation"
[    11.745] 	compiled for 4.0.2, module version = 1.0.0
[    11.745] 	Module class: X.Org Video Driver
[    11.758] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    11.758] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    11.759] (++) using VT number 7

[    11.759] (EE) No devices detected.
[    11.759] 
Fatal server error:
[    11.759] no screens found

---

### Post by kaaloo on 2011-06-24
Oops strike that!  I'm actually on 2.6.38-8 generic

---

### Post by abys on 2011-06-24
I don't use any script, I just test the optirun which gave me a much better glxgear FPS reseult. I think 600 or 700 FPS.

And longer battery run, from arround 2h to 3h30 which mean the nvidia is probably disable now when I'm on batterie. I don't know if it switch directly on the nvidia when I'm plugged in, how could I test that?

Cheers

---

### Post by alidrus2000 on 2011-06-24
> **pmartrenchar said:**
> I installed bumblebee from git too, It recognized my dell 15z, but the files bumblebee-enableCard and disableCard are not set so I have the error:

optirun cd
 * Starting Bumblebee X server bumblebee                                       
 /usr/local/bin/bumblebee-enablecard: 1: &#65533;: not found
                                                                         [ OK ]
exec: 301: cd: not found
 * Stopping Bumblebee X server bumblebee                                         * 
/usr/local/bin/bumblebee-disablecard: 1: &#65533;: not found
                                                                         [ OK ]

What script are you using?

Thanks

After much digging around, I managed to find a way to get bumblebee-enablecard and bumblebee-disablecard to work.

You need to use the examples from /usr/share/doc/bumblebee and replace the two scripts. The acpi calls are also different from anything included by default in the bumblebee installations. For more info look here for step by step instructions:

[https://github.com/MrMEEE/bumblebee/issues/258](https://github.com/MrMEEE/bumblebee/issues/258)

---

### Post by kaaloo on 2011-06-24
Ok I finally got unity to run with my current config, just had to run "unity &" then logout and back in again.  So I'm a happy Dell XPS 15z user except for the trackpad which I don't use that much anyway.

---

### Post by morefeo on 2011-06-27
So the only thing that doesn't work with it is the trackpad?

---

### Post by spjakob on 2011-06-27
> **morefeo said:**
> So the only thing that doesn't work with it is the trackpad?


There are more problems (except not working trackpad); 

Battery is consumed very fast.
Laptop is hot even during idle
Fan is very loud.
external SATA port and USB is not working as install media (when I tried, has to be confirmed).
....and possibly some gfx issues(???!)


I have just turned off nvidia (just removing the noveau module), but laptop stills seems very hot and I guess that battery time is still the same (low). Has someone done any battery measurements with or without nividia module loaded??

---

### Post by morefeo on 2011-06-27
The low battery time is a power regression present in kernels 2.6.38 and forwards.

Try adding "pcie_aspm=force" to the boot command line as said here [http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_aspm&num=1)

---

### Post by alidrus2000 on 2011-06-28
Anyone got the trackpad working yet?

---

### Post by jwhirl06 on 2011-06-28
> **alidrus2000 said:**
> Anyone got the trackpad working yet?

Nah, not yet. Cypress needs to release a driver for it which may take some time... unfortunately it's just a game of patience at this point... X.x

---

### Post by alidrus2000 on 2011-06-30
Didn't someone get it to work on gentoo? That probably means there's a kernel module out there or something. At least in one of the more recent kernels. I really hope that it somehow makes its way back into Natty.

---

### Post by morefeo on 2011-06-30
I've installed nvidia drivers, they're installed but ubuntu says it's not in use. What should I do? Install bumbeblee?

Edit: Nevermind, I installed bumblebee and now I can use nvidia.

---

### Post by pmartrenchar on 2011-06-30
I tried to use a sd card today, I put it in the slot next to the USB ports and nothing happended. Can someone test it too?

In an other topic, there is a button on the left side of the laptop, what is it for?

Thanks

---

### Post by spjakob on 2011-06-30
> **pmartrenchar said:**
> I tried to use a sd card today, I put it in the slot next to the USB ports and nothing happended. Can someone test it too?

In an other topic, there is a button on the left side of the laptop, what is it for?

Thanks

SD card reader does not seem to work at all with 10.10 (have not tried anything else).

I think the button is to check status of battery, when I press mine, several diodes lites up to indicate battery level (i think)

---

### Post by im.brian on 2011-07-01
Hi guys, here's how my 11.04 install went on my XPS 15z, maybe some of this will help:

To install, you must use acpi=off or you will encounter a black screen.

Once installed, go and download bumblebee and use the installer, it will install everything it needs.

You can boot the machine without acpi=off now, but, you're keyboard won't work. Swap out acpi=off for acpi=noirq, this will enable the other core, show your battery monitor, and make your keyboard work again. It also, most importantly, allows bumblebee to function.

Things working:
WebCam + Microphone
Speakers
Video (with bumblebee)
Keyboard
USB Ports
eSATA Port (used for USB, don't have a device to test eSATA)

Things that were working and then stopped working:
Headphone Jack

Things still not working:
HDMI (because it's attached to the big card)
Mini Displayport (at least on mine, but my adapter may have been bad)
Card Reader
Trackpad

Me personally, the machine is wonderful even with some of the things not working. I dual boot with Winblows for games that don't run under Wine.

Another observation was that with bumbleebee, if you did "optirun firefox", you don't get accelerated Flash. So things like Facebook games made in Flash will run horrible as will YouTube in full screen mode.

Maybe some of this helped, maybe it didn't, and maybe somebody can help me with the rest of my problems :)

---

### Post by morefeo on 2011-07-01
> **im.brian said:**
> 
Another observation was that with bumbleebee, if you did "optirun firefox", you don't get accelerated Flash. So things like Facebook games made in Flash will run horrible as will YouTube in full screen mode.

I've done "optirun chromium-browser" with it closed, and then I got accelerated flash (I watched a 1080p video on youtube in full screen with no slowness).

Now, sometimes I get some screen issues with chromium, while scrolling some polygons appears of different parts of the page I'm viewing. Testing with Firefox right now. Take a look:

[http://i.imgur.com/FhSeW.png](http://i.imgur.com/FhSeW.png)

Also: how do I press ImprPant? I've tested ctrl, Fn, Shift, Super key and alt + [Insert], none presses it.

---

### Post by morefeo on 2011-07-05
Ok, Fn+Insert did the trick (I just didn't realize).

Now, anyone has that screen corruption? It's terrible, I've updated mesa and Intel drivers to a more recent release and it's the same.

---

### Post by minni on 2011-07-05
The Trackpad seems to be working by adding a parameter to the psmouse kernel module:
> sudo rmmod psmouse; sudo modprobe psmouse proto=imps


Originally noticed that at the hardware support site: 
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)


Has anyone got an external Monitor to work?

---

### Post by morefeo on 2011-07-05
> **minni said:**
> sudo rmmod psmouse; sudo modprobe psmouse proto=imps

This works.

> To make this persistent, add the following line at the bottom of /etc/modules:

echo "psmouse proto=imps" | sudo tee -a /etc/modules


This doesn't. I can't make it work at all. I need to remove the module everytime before load it again with proto=imps

# Solved: I added the command to the startup with this method [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

---

### Post by jwhirl06 on 2011-07-05
> **morefeo said:**
> This works.



This doesn't. I can't make it work at all. I need to remove the module everytime before load it again with proto=imps

# Solved: I added the command to the startup with this method [http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)

I am having trouble understanding it... what did your executable look like?

---

### Post by morefeo on 2011-07-05
As root, run:

echo "rmmod psmouse; modprobe psmouse proto=imps" > /etc/init.d/trackpad
chmod 755 /etc/init.d/trackpad
update-rc.d trackpad defaults

---

### Post by jwhirl06 on 2011-07-06
ty for that.

---

### Post by pmartrenchar on 2011-07-06
Thanks for the trackpad fix :)

My problem now is that my USB port seem to stop randomly: I have a mic and a external hard drive on them and suddenly they just stop working. I can still use the usb ports to charge my phone, but if I restart the external hard drive, it is not recognized by Ubuntu. I have to reboot the system to get them work again.

I am using apci=noirq.

Anyone have a similar problem?

---

### Post by morefeo on 2011-07-07
I'm not experiencing those issues, maybe due to I don't need to use acpi=noirq -my laptop hasn't got issues with acpi, at least I see the 4 virtual cores. Also, that acpi command makes my wifi very slow.

Still nobody with screen corruption like me?

---

### Post by tyl77 on 2011-07-08
> **morefeo said:**
> I'm not experiencing those issues, maybe due to I don't need to use acpi=noirq -my laptop hasn't got issues with acpi, at least I see the 4 virtual cores. Also, that acpi command makes my wifi very slow.

Still nobody with screen corruption like me?

my first post on these forums...

I seem to have some graphical issues from time to time as well.

Anyway, I thought I'd just give some input of my own so others can see what's working. Keep in mind that I am an absolute novice when it comes to linux, I only installed ubuntu 4 days ago for the first time and I don't even know the absolute basics, but I managed to get it working at a reasonably good level.

Here's what's working for me:
-Trackpad is working fine, no multi touch but all the basic functionality working including page scrolling.
-USB ports work no problem, haven't tried the other things
-no problems with wireless
-bluetooth works fine
-no problems with sound
-keyboard works fine

some issues:
-battery seems to be drained faster then it does on windows, though i've read elsewhere that this is a more broad problem affecting all linux  laptops to an extent, though I don't know for sure.
-seems to run hotter then when running windows and the fans are noticeably more audible, but they are not loud by any means.
-as mentioned above, some graphics corruption now and again, other times it seems to work fine. I'll try and get a screenshot of it. 

I'll add more as I think of it.

---

### Post by tyl77 on 2011-07-08
Also, OP should change the thread title to something more appropriate like Dell xps15z issues...fail isn't exactly the most encouraging word to use ;)

---

### Post by morefeo on 2011-07-09
> **tyl77 said:**
> 

Your trackpad is working out of the box or did you make the fix?

---

### Post by kaaloo on 2011-07-09
I had been suffering from the system freezing every 1-3 days with the current 2.6.38 Natty kernel but I seem to  be getting much more stability from the 2.6.39.2 oneiric kenel on [http://kernel.ubuntu.com/~kernel-ppa/mainline](http://kernel.ubuntu.com/~kernel-ppa/mainline).  A 2.6.39.3 kernel was published today but I haven't tried it yet.

---

### Post by SmokeyTheBear on 2011-07-10
morefeo's trackpad fix works like a charm. TY. What about the headphone jack though? Mine doesn't seem to be operational. Nor have I gotten the HDMI out working yet. Anyone get the headphone jack working yet? its killing me.

UPDATE: By installing the nvidia drivers my headphone jack now works however i cannot boot into unity any longer and must use "classic mode"

---

### Post by morefeo on 2011-07-11
I installed bumblebee from git, it worked.

Now I tried from ppa: it doesn't want to run glxgears.

---

### Post by jwhirl06 on 2011-07-13
> **SmokeyTheBear said:**
> morefeo's trackpad fix works like a charm. TY. What about the headphone jack though? Mine doesn't seem to be operational. Nor have I gotten the HDMI out working yet. Anyone get the headphone jack working yet? its killing me.

UPDATE: By installing the nvidia drivers my headphone jack now works however i cannot boot into unity any longer and must use "classic mode"

I'd use the bumblebee optimus manager to enable the gfx switching, after doing this my unity UI came back

---

### Post by doughnuts64 on 2011-07-17
I have just performed the most recent update provided by Ubuntu, and the new kernel version seems to have completely broken Ubuntu on this machine. If I select the original kernel, then I can boot in without any difficulty, but with the new one, I end up with a blank screen and flashing 'Caps Lock' light.

Has anyone had any experience similar to this?

---

### Post by jwhirl06 on 2011-07-17
That's called a kernel panic its similar to a bsod. Definately bad news

---

### Post by tyl77 on 2011-07-17
> **doughnuts64 said:**
> I have just performed the most recent update provided by Ubuntu, and the new kernel version seems to have completely broken Ubuntu on this machine. If I select the original kernel, then I can boot in without any difficulty, but with the new one, I end up with a blank screen and flashing 'Caps Lock' light.

Has anyone had any experience similar to this?

Yep, exact same thing happened to me as well, updated the laptop, won't boot AT ALL, just a black screen and flashing caps lock. I have to boot previous version of linux. 
 
Before updating everything was working OK. Computer still ran a lot hotter than it does under windows and as such the fan spins faster+louder too. Battery drains faster as well, I squeezed about 2 and a half hours of it with moderate use. When running windows I can easily get 4 and a half or more and 6/7 hrs easily with very light use and reduced screen brightness.

:cry:

---

### Post by morefeo on 2011-07-17
Kernel update didn't broke my system, however, my headphone don't work, when it did before.

And I don't know how to fix something that wasn't supose to broken without touching it.

---

### Post by tyl77 on 2011-07-22
How did you go about updating to 2.6.38-10 without breaking the system?  

So has anyone found fixes for the graphical/heat/battery issues?

---

### Post by abys on 2011-07-22
I install the 2.6.39 kernel and just after the install I run the update for bumblebee and I don't have any issue.

Don't forget to check that if you didn't went there already. [https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

Good luck

---

### Post by pmartrenchar on 2011-07-25
Is the card reader and the HDMI port working with the 2.6.39 kernel?

Is there a ppa to install this kernel?

Thanks

---

### Post by spjakob on 2011-07-26
Anyone who could help me on how to disable "tap to click", "scroolwheel emulation" and similar features on trackpad after using the fix to enable trackpad? 
In the GUI, the trackpad appears to be a very basic PS2 mouse with no settings...

---

### Post by kaaloo on 2011-07-31
> **pmartrenchar said:**
> Is the card reader and the HDMI port working with the 2.6.39 kernel?

Is there a ppa to install this kernel?

Thanks

You can install the different kernel versions here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by marcoli on 2011-08-03
Hello,
I am also a XPS 15z owner. It looks good and hopefully soon everything works with Ubuntu :D
As pmartrenchar for me a very importend point is the HDMI output as I use the Laptop for work and my big screen is useless at the moment :(

I didn't see anyone in this forum saying I got the hdmi port working so I suppose it is not working at the moment even with newer kernels?

Cheers
Marco

---

### Post by pmartrenchar on 2011-08-04
I saw somewhere you can use a mini-displayport to HDMI adaptater to display on your screen.
The mini displayport is next to the HDMI port and it is connected to the intel card.

---

### Post by marcoli on 2011-08-10
Thanks, I bought an Adapter and it worked, so I can confirm that an external monitor can be connected to the mini Display port.

---

### Post by marcoli on 2011-08-10
I get also freezes, unfortunately there is nothing in the log files after a reboot

---

### Post by marcoli on 2011-08-10
Wlan Interface when in battery mode disconnects after some time.
Has anybody seen this as well:
ping 192.168.222.3
PING 192.168.222.3 (192.168.222.3) 56(84) bytes of data.
.
.
.
64 bytes from 192.168.222.3: icmp_req=232 ttl=64 time=93.1 ms
64 bytes from 192.168.222.3: icmp_req=233 ttl=64 time=116 ms
64 bytes from 192.168.222.3: icmp_req=235 ttl=64 time=1082 ms
64 bytes from 192.168.222.3: icmp_req=236 ttl=64 time=180 ms
64 bytes from 192.168.222.3: icmp_req=237 ttl=64 time=105 ms
64 bytes from 192.168.222.3: icmp_req=238 ttl=64 time=26.4 ms
64 bytes from 192.168.222.3: icmp_req=239 ttl=64 time=48.8 ms
64 bytes from 192.168.222.3: icmp_req=240 ttl=64 time=71.9 ms
64 bytes from 192.168.222.3: icmp_req=241 ttl=64 time=95.0 ms
64 bytes from 192.168.222.3: icmp_req=242 ttl=64 time=629 ms
64 bytes from 192.168.222.3: icmp_req=243 ttl=64 time=39.7 ms
64 bytes from 192.168.222.3: icmp_req=244 ttl=64 time=60.9 ms
64 bytes from 192.168.222.3: icmp_req=245 ttl=64 time=2029 ms
64 bytes from 192.168.222.3: icmp_req=246 ttl=64 time=2053 ms
64 bytes from 192.168.222.3: icmp_req=247 ttl=64 time=1258 ms
64 bytes from 192.168.222.3: icmp_req=248 ttl=64 time=461 ms
64 bytes from 192.168.222.3: icmp_req=249 ttl=64 time=177 ms
64 bytes from 192.168.222.3: icmp_req=250 ttl=64 time=151 ms
64 bytes from 192.168.222.3: icmp_req=251 ttl=64 time=3090 ms
64 bytes from 192.168.222.3: icmp_req=252 ttl=64 time=3109 ms
64 bytes from 192.168.222.3: icmp_req=253 ttl=64 time=3030 ms
64 bytes from 192.168.222.3: icmp_req=254 ttl=64 time=4079 ms
64 bytes from 192.168.222.3: icmp_req=255 ttl=64 time=3078 ms
64 bytes from 192.168.222.3: icmp_req=256 ttl=64 time=2280 ms
64 bytes from 192.168.222.3: icmp_req=257 ttl=64 time=2097 ms
64 bytes from 192.168.222.3: icmp_req=258 ttl=64 time=2117 ms
64 bytes from 192.168.222.3: icmp_req=259 ttl=64 time=2344 ms
64 bytes from 192.168.222.3: icmp_req=260 ttl=64 time=1343 ms
64 bytes from 192.168.222.3: icmp_req=261 ttl=64 time=395 ms
64 bytes from 192.168.222.3: icmp_req=262 ttl=64 time=7429 ms
64 bytes from 192.168.222.3: icmp_req=263 ttl=64 time=7039 ms
64 bytes from 192.168.222.3: icmp_req=264 ttl=64 time=7063 ms
64 bytes from 192.168.222.3: icmp_req=265 ttl=64 time=9033 ms
64 bytes from 192.168.222.3: icmp_req=266 ttl=64 time=8135 ms
64 bytes from 192.168.222.3: icmp_req=267 ttl=64 time=8057 ms
64 bytes from 192.168.222.3: icmp_req=268 ttl=64 time=9105 ms
64 bytes from 192.168.222.3: icmp_req=269 ttl=64 time=8320 ms
64 bytes from 192.168.222.3: icmp_req=270 ttl=64 time=10176 ms
64 bytes from 192.168.222.3: icmp_req=271 ttl=64 time=9584 ms
64 bytes from 192.168.222.3: icmp_req=272 ttl=64 time=9094 ms
64 bytes from 192.168.222.3: icmp_req=273 ttl=64 time=9112 ms
64 bytes from 192.168.222.3: icmp_req=274 ttl=64 time=9137 ms
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable
ping: sendmsg: Network is unreachable

---

### Post by abys on 2011-08-10
Yeah, I've notice wlan slowness when I unplugged the battery.. But I keep it always plugged =)

---

### Post by morefeo on 2011-08-14
> Optimus / Graphics cards
Switch off NVIDIA card

# echo OFF > /sys/kernel/debug/vgaswitcheroo/switch

I can't run this command even as root. The file does not exist and I can't create it.

---

### Post by jamboarder on 2011-08-15
Everything appears to be working on my Dell XPS 15z (after reading the wiki and this thread).  However, my battery life is never above 3 hours.  When booted to Windows 7 I get consistently get between 6 and 7 hours.

The nvidia card is disabled per the wiki and I've tried the 3.0 kernel with very little improvement.  Anyone else seeing better than 3 hours of battery life?

---

### Post by morefeo on 2011-08-17
> **jamboarder said:**
> Everything appears to be working on my Dell XPS 15z (after reading the wiki and this thread).  However, my battery life is never above 3 hours.  When booted to Windows 7 I get consistently get between 6 and 7 hours.

The nvidia card is disabled per the wiki and I've tried the 3.0 kernel with very little improvement.  Anyone else seeing better than 3 hours of battery life?

[http://i.imgur.com/auIzS.png](http://i.imgur.com/auIzS.png)

Have you tried this?

> Add pcie_aspm=force acpi=noirq i915.semaphores=1 to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub.

---

### Post by spjakob on 2011-08-17
> **morefeo said:**
> [http://i.imgur.com/auIzS.png](http://i.imgur.com/auIzS.png)

Have you tried this?

I also have battery problem (and a very hot laptop), I use these option to grub and also has just 3h laptops....

---

### Post by feri_crosby on 2011-08-18
hi guys, i have already installed ubuntu 11.04 but booting is still with bugs, ubuntu does not starts normally, my keyboard doesnt work, trackpad too, nVidia is upgraded but still this bugs, ..i dont know, what to do...please help
actually, when is ubuntu loading (4 point changin color from red to white) its small, not optimised for resolusion...when is ubuntu ready, im logged in (without password, while my keyboard doesnt work) ..after loggin it shows in 10seconds intervals few errors and my screeen is blank, i just see ubuntu standard background, ...i dont know ...please help me

---

### Post by darkhoros on 2011-08-18
Hi all,
This is my first post so I will make it short.
I like to start by saying that my laptopn dell xps l15z I am using to write these words, is using ubuntu 11.04 with all functionalities exept the gesture but the touch pad is working so fine as a normal mouse, this is to make you all looking to gt ubuntu to work on this wonderful laptop have a pace of mind.

I will write my experiance here:

1- When booting with setp CD must click f6 and select acpi=off or you will get black screen.

2- the wireless will be auto detected on the first page of the setup so you can select to download updates.

3- to get mouse and keyboard works to work you have to
#sudo pico /etc/default/grub

and add this line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force acpi=noirq i915.semaphores=1"

 right after

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`

Then run the following command:

# update-grub

and restart

4- to get touch pad to work
# sudo rmmod psmouse; sudo modprobe psmouse proto=imps

( Or use proto=bare or proto=exps ).

To make this persistent, add the following line to a file in /etc/modprobe.d/ (/etc/modprobe.d/options.conf could be an option, but modprobe parses all the files in that directory):
so you can do
#sudo pico /etc/modprobe.d/options.conf
and only put the following line in to it

options psmouse proto=imps 

5- to get the optimus to work use this links
[http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/](http://www.omgubuntu.co.uk/2011/05/bumbleebee-brings-nvidia-optimus-gpu-switching-to-linux-users/)
and
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)

6- I dont remember me doing anything more.
hope it works for you, and any questions are welcome.

Thank you all.

---

### Post by feri_crosby on 2011-08-18
hi, thanks for that, im gonna to try it, but i dont understand step 4. and 5. ...
in step 4., i have to do just this? 

# sudo rmmod psmouse; sudo modprobe psmouse proto=imps

or the following too?

and step 5., i dont understand this steps, its chaotic....please help me.

---

### Post by web-e on 2011-08-19
[FONT=Lucida Sans Unicode][SIZE=2]@@^^
step 5 is all about a way to enable nvidia 540m for specific application.Since the nvidia refuses to support optimus system in linux.

Now this project got one ppa in launchpad, for installation..
run the following
```

sudo apt-add-repository ppa:mj-casalogic/bumblebee 
sudo apt-get update 
sudo apt-get install bumblebee

```It will install all the necessary components,after installation it will search internet for already working configuration, if available select one.

Now you can run a program using [/SIZE][/FONT][FONT=Lucida Sans Unicode][SIZE=2]"optirun32 <application>" or "optirun64 <application>"

Or you can install bumblebee ui from synaptic. 

[ I have tested it in my xps15 with nvidia 540m and intel HD 3000]
[/SIZE][/FONT]

---

### Post by darkhoros on 2011-08-19
Hi,
Just use these
#sudo pico /etc/modprobe.d/options.conf
and only put the following line in to it

options psmouse proto=imps 

then save and exit with ctrl+x

---

### Post by morefeo on 2011-08-20
Everything is in the hardware support page [https://wiki.edubuntu.org/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.edubuntu.org/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

### Post by beudbeud on 2011-08-21
hi

the card reader work in natty with acpi=off but it doens't works with pcie_aspm=force acpi=noirq i915.semaphores=1

why?

---

### Post by morefeo on 2011-08-21
Try with pcie_aspm=force acpi=off i915.semaphores=1 or acpi=noirq i915.semaphores=1

Then we could discover what's wrong.

---

### Post by warp10 on 2011-08-24
Just wrote this report:

[http://blog.andreacolangelo.com/2011/08/25/nvidia-optimus-on-dell-xps-15z-performance-and-battery-consumption-comparison/](http://blog.andreacolangelo.com/2011/08/25/nvidia-optimus-on-dell-xps-15z-performance-and-battery-consumption-comparison/)

Thought it might be of help and worth of being linked here.

JM2C :)

---

### Post by morefeo on 2011-09-12
My headphones continue no not work at all with current Ubuntu (fully updated). Anyone with this problem too?

---

### Post by themicon on 2011-09-13
I'm having the same problem with the headphones. The internal speakers work fine, but no sound plays through the headphones when I plug them in.

---

### Post by abys on 2011-09-19
Hi All,

For the headphone, I've just installed windows 7 on a dual boot and it appear to make my headphone not working anymore after reboot. However on my case, if I fully shutdown my computer and start straight on ubuntu, the headphone is back.

Don't know if that help to find a way to fix this bug, but still.

After reboot my clock is also set up to GMT+1 instead of GMT.

Maybe a restore default setting on the BIOS could help for people with headphone issue (Simple test I would make)

Also does anyone having issue with the computer freezing randomly? Appends often to me, the computer stop responding, even CTRL + ALT + Backspace is useless, have to force power it down.

I'm hoping new kernel on Oneiric will fix that!

Good luck

---

### Post by themicon on 2011-09-19
Thanks abys

The headphones work for me too when I boot straight into Ubuntu. This is really strange. I checked the BIOS and there doesn't seem to be any option for fixing the issue. Here's hoping Oneiric fixes it too ;)

---

### Post by Stephen Lilley on 2011-09-25
I'm thinking about purchasing an XPS 15z with the following specifications. Please tell me if your machine has the same specifications and you were able to get it running with what has been advised so far on this thread

My specs if I purchase from Dell this week

1. 2nd generation Intel® Core i7-2640M processor 2.80 GHz with Turbo Boost 2.0 up to 3.50 
2. 15.6" (39.6cm) FHD Widescreen, 300-nit (typical) (1920x1080) 1080p
3. High Definition Audio with Waves MaxxAudio® 3
4. 8GB 1333MHz DDR3 SDRAM(2x4GB) 
5. 750GB 7200RPM Hard Drive 
6. 9.5mm SATA Slot Load DVD+/-RW
7. NVIDIA® GeForce® GT 525M 2GB graphics 
9. Intel® Centrino® Advanced-N 6230 with Bluetooth v3.0+HS

---

### Post by themicon on 2011-09-25
I have exactly the same the computer as the one you listed.

I managed to install Ubuntu 11.04 on my machine with the help of this thread. The only thing that still doesn't work right is the headphone thing. When I boot into Windows 7 and restart my computer, the headphone jack doesn't work in Ubuntu. But if I boot straight into Ubuntu first, the headphones work fine. This problem does not affect the built in speakers though, they work just fine.

Other than that I see no reason not to buy this computer. I'm loving mine so far.

Hope that helps.

---

### Post by morefeo on 2011-09-25
Everything works except HDMI and Optimus, but the last one has partial support under linux thanks to Bumblebee.

I really hope Wayland will be the key to have Optimus in linux.

---

### Post by Otto Nascarella on 2011-09-29
Guys...

I've tried everything.

the "pcie_aspm=force acpi=noirq i915.semaphores=1" trick sometimes work, but sometimes does not.

Weirdly enough, I managed to install it from DVD with apci=off.
Keyboard, trackpad, wifi and sound were FINE!

Now I try booting and most of times it just gets black screen with the CPU fan going BANANAS. When, sometimes, it boots, I get not trackpad or keyboard.


Could anyone enlighten me on WHAT TO DO!?


cheers

---

### Post by Otto Nascarella on 2011-09-30
OK.

Re-installed it, and after installation was finished,
I changed root to the HD, and changed grub to what was
recommended on the Wiki page. Also blacklisted "nouveau" and changed the mouse modules.

After reboot, machine booted normally,
Sound, trackpad with OK functionalities and etc...but I still haven't managed to make nVidia GT 525 M work.
When I tried installing the propriety drivers, gdm would not start.
On 

Xorg.0.log I had: No devices detected, no screens found.


Anyone has a clue of what I should do???

---

### Post by morefeo on 2011-10-04
Didn't you written you blacklisted the nouveau driver? Whitelist it and let bumblebee install normally.

---

### Post by Chilly_Willy on 2011-10-13
Anyone on the new Ubuntu 11.10, did things inprove?

---

### Post by damianpeterson on 2011-10-13
I'm waiting and watching this thread for other people's experiences before updating to 11.10. :)
I've got it working really nicely with 11.04 64bit on my XPS 15z at the moment but it took a long time to get it like this and I don't really want to go through all that again if I don't have to.

---

### Post by ChadeFarseer on 2011-10-19
I just installed 11.10 on my 15z. It actually ran pretty smoothly, there's no need to add any arguments to the boot parameters any more.

Interesting to note, it's stuck running unity 2D and I can't seem to switch it over to unity 3D. Running Gnome Shell always drops back to fallback mode as well.

Apart from that it's fine. The only hack I've had to use so far is the trackpad fix discussed in the wiki. I haven't tried installing nvidia drivers yet though, and it does seem to run a little hot.

---

### Post by abys on 2011-10-19
Hey,

sudo apt-add-repository ppa:mj-casalogic/bumblebee
sudo apt-get update && sudo apt-get install bumblebee

That should fix your unity 2d issue.

If I remove acpi=noirq I'm still getting the black screen on boot.

Otherwise, works fine.

It's an upgrade from 11.04, not a new installation.

---

### Post by welfare on 2011-10-24
I installed Ubuntu 11.10 (64bit) on my XPS 15z last weekend. I followed the steps in the [ XPS wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z") and got the OS working after some while, partitioning of the HDD was a bit tricky.

The grub settings I use are:

pcie_aspm=force acpi=noirq i915.semaphores=1 i915.i915_enable_rc6=1

I installed bumblebee and it works like a charm when starting programs with optirun. WiFi and soundcard is working as well and I have full keyboard functionality.

My number one concern right now is the problem with heating, the fans run on full speed and the computer is burning hot. I don't experience this problem when I boot Windows 7, so this is clearly a linux issue. Anyone got a solution for this?

There are other issues aswell, I can only get basic mouse functionality of the trackpad. The battery is drained quite fast and it seems as I can't use 803.11n, only b or g. 

I haven't tested HDMI yet.

But in the long run I can't use ubuntu on the laptop if the heating issue remains unsolved. :(

---

### Post by morefeo on 2011-10-25
> **welfare said:**
> i915.semaphores=1 i915.i915_enable_rc6=1


Having RC6 enabled may cause GPU hangs on some devices, disable it and try if it fixes something. Also, semaphores were needed for 11.04 due to the poor state in which the intel SB driver (and its support on the 2.38 kernel) was, try disabling it too.

About the trackpad, as long as I know, cypress has not released any driver for linux, so we'll need to wait for it.

The battery draining issue may be related to the nvidia card, and installing Bumblebee could fix it -as the heat and fan noise produced in consequence. BUT: the bumblebee project mentioned above is discontinued, it has been double forked, one is maintained by the bumblebee original author and is called Ironhide: [http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/](http://www.martin-juhl.dk/2011/08/ironhide-reporting-for-duty/) The other one is called Bumblebee-project [https://github.com/Bumblebee-Project](https://github.com/Bumblebee-Project) and is maintained by a small group of developers. Both projects have problems with ACPI calls and are resolving it, until then we'll need to wait.

---

### Post by amjad1074 on 2011-10-27
hi,

I want to install Ubuntu 10.11 64bit, but afraid of the lack of compatibility with my laptop Dell xps 15z
 Do you advise me in this version?
 Or what do you advise me?
 Please advise

 Thank you

---

### Post by morefeo on 2011-10-28
11.10 works better than 11.04. Better out of the box performance, no errors like no headphones/microphone while rebooting from windows. No graphical issues with the Intel graphics chip.

But lowered battery duration.

---

### Post by ChadeFarseer on 2011-10-30
Has anyone else found that WiFi is shockingly slow when running Ubuntu on their 15z?

---

### Post by morefeo on 2011-10-31
[IMG]http://i.imgur.com/TBMJO.png[/IMG]

I have my laptop with almost 6 hours of battery life, this is what I've done:

**1) Add pcie_aspm=force to the grub command:**

Open the grub config file

```
sudo gedit /etc/default/grub
```

Change this:

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash"
```

To this:

```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash pcie_aspm=force&#8221;
```

Make sure you update grub after that
```
sudo update-grub
```


**2) Stop nvidia to suck power like a wh*re**

Install Bumblebee:
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee
```

After the initial bumblebee installation, you need to add yourself to the 'bumblebee' group:
```
sudo usermod -a -G bumblebee YOURUSERNAME
```

Make it to turn on/off your nvidia chip. Read this and follow the steps mentioned [https://github.com/Bumblebee-Project/Bumblebee/issues/100](https://github.com/Bumblebee-Project/Bumblebee/issues/100)

(Note: You'll need to install acpi-tools as mentioned here: [https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee))
```
sudo apt-get install acpi-call-tools
```


**3) Play a bit with boot commands for the Intel device**

Open your grub config file:
```
sudo gedit /etc/default/grub
```

And try these commands one by one and make sure it doesn't make any conflicts (like flickering or screen artefacts) or returns you black screens. Follow the step 1 to add them to the boot command line.

> i915.i915_enable_rc6=1 # This is the most decisive, but causes permanent tearing
i915.i915_enable_fbc=1
i915.lvds_downclock=1 # may cause freezes

After every attemp, update grub
```
update-grub
```

Source of this Intel commands: [http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)


Run this before and after this instructions to see a huge drop in battery usage (from 1800mA to 640mA in my laptop).
```
watch grep rate /proc/acpi/battery/BAT0/state
```

Hope it helps.

---

### Post by ronnystickshift on 2011-11-01
hi all, newb here.  lots of great information in this thread, which is why i signed for the forum.  i have a "small" problem though.  i'd love to try any and all of these suggestions, but i can't even boot into ubuntu to try them.  

here's my situation at the moment:
1) dell xps 15z, ubuntu 11.04 just installed, appeared to be successful without any problems, and i rebooted to complete the installation when it prompted me too.  the whole time during the install the trackpad and mouse were working fine
2) upon reboot, the grub menu is there, and i can boot into windows with no problems
3) i can't boot into the normal mode of ubuntu at all, i just get a black screen
4) when trying to boot into ubuntu using recovery mode, i get to the menu but i can't scroll through it - i guess it isn't taking the keyboard input

please help!

---

### Post by morefeo on 2011-11-01
You need to add "acpi=noirq" to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, if you can't select recovery mode try with the live cd as you will do restoring the grub.

---

### Post by ronnystickshift on 2011-11-01
morefeo, thank you so much for replying!  i ended up doing a fresh install of 11.10.  the first reboot went fine, ubuntu loaded right up, but the keyboard and trackpad still didn't work.  however, i coincidentally had a USB keyboard and mouse and those worked immediately after plugging in, and i was able to use them to log in and make the changes suggested by you (and others).  now, the keyboard and trackpad are working perfectly.

Cheers!

---

### Post by SavageCHRIS on 2011-11-02
Hey morefeo are you using 11.10 ?

I followed your instructions but I'm having trouble getting my nvidia card to switch off.

---

### Post by morefeo on 2011-11-02
> **SavageCHRIS said:**
> Hey morefeo are you using 11.10 ?

I followed your instructions but I'm having trouble getting my nvidia card to switch off.

Yes, 11.10, what problem have you got?

---

### Post by SavageCHRIS on 2011-11-02
> **morefeo said:**
> Yes, 11.10, what problem have you got?
I followed the steps in the link you posted to switch off the nvidia chip, but it doesn't appear to have done anything because my battery still lasts about an hour.

---

### Post by morefeo on 2011-11-02
I missed a part, you need to install acpi-tools in order to make the acpi calls work.

```
sudo apt-get install acpi-call-tools
```

---

### Post by SavageCHRIS on 2011-11-02
I have already installed the acpi tools but it still doesn't seem to be switching off, what nvidia card have you got ? mines the GT540m.

thank you for trying to help me :P

---

### Post by morefeo on 2011-11-02
525m, ACPI calls are different between cards, that's why it doesn't work. You'll need to find the right calls for yours.

Try with these calls:

[http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls](http://hybrid-graphics-linux.tuxfamily.org/index.php?title=ACPI_calls) With models XPS L502X and M11xR3 A01

---

### Post by SavageCHRIS on 2011-11-02
I have managed to get the card switched off but it is still using a lot of power, my fans are loud and I read someone else on here with the same problem. Thanks for the help.

---

### Post by ronnystickshift on 2011-11-06
> **spjakob said:**
> Anyone who could help me on how to disable "tap to click", "scroolwheel emulation" and similar features on trackpad after using the fix to enable trackpad? 
In the GUI, the trackpad appears to be a very basic PS2 mouse with no settings...

hi all, i read through the whole thread but never found a response for this.  following the advice in this thread has worked great for me so far with this laptop but i haven't been able to disable tap-to-click either.  i have the same problem in the GUI as jakob describes

i saw in another thread to try "synclient MaxTapTime=0" but when i do that i get an error message: "Couldn't find synaptics properties.  No synaptics driver loaded?"  which i guess means it doesn't realize there's a trackpad, even though the trackpad has full functionality.

---

### Post by SavageCHRIS on 2011-11-06
There is a good write up here on how to get Bumblebee working properly on 11.10, including power management. [http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

---

### Post by morefeo on 2011-11-06
> **SavageCHRIS said:**
> There is a good write up here on how to get Bumblebee working properly on 11.10, including power management. [http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)

It's just a rip off of what I've written on the last page. Even it has the same order (aspm_pcie, bumblebee and Intel tweaks). At least you could mention that you based your guide in another user's guide.

If you try to get more visits to your blog, don't rip other people's work without giving credit.

---

### Post by verwilst on 2011-11-07
root@xps:~# cat /proc/acpi/battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          discharging
present rate:            2111 mW
remaining capacity:      4067 mWh
present voltage:         16057 mV

Battery draining fast :(

Tried some acpi_call echo's, but none seem to work.. installed ironhide, etc.. anyone here has some more pointers?

---

### Post by SavageCHRIS on 2011-11-07
> **morefeo said:**
> It's just a rip off of what I've written on the last page. Even it has the same order (aspm_pcie, bumblebee and Intel tweaks). At least you could mention that you based your guide in another user's guide.

If you try to get more visits to your blog, don't rip other people's work without giving credit.

If you look at the site there is another bumblebee post that was written on the 1st of September 2011 and the one I linked is just an updated version of that. No one is trying to steal your work, that's just how you install bumblebee, you can't do it any other way.

---

### Post by morefeo on 2011-11-07
> **SavageCHRIS said:**
> If you look at the site there is another bumblebee post that was written on the 1st of September 2011 and the one I linked is just an updated version of that. No one is trying to steal your work, that's just how you install bumblebee, you can't do it any other way.

The other bumblebee post is another way of turning off the nvidia card, that's all. On the last post you just ripped my entire comment, you follow the same order even if it does not matter what you do first.

It's easy to see because you have no idea of what you are talking about on the post. Pcie_aspm and the Intel tweaks have nothing to do with bumblebee, just for longer battery life.

It's just a copy/paste of my post, phoronix page, the links I posted where a user tells everybody how to make acpi calls work in dell xps 15 z and the last comment I said to you.

At least you should give credit to who wrote all that, the bumblebee user and the phoronix owner.

---

### Post by SavageCHRIS on 2011-11-07
Its clearly stated that them tweaks are nothing to do with bumblebee, "These tweaks are not necessary in getting &#8216;Optimus&#8217; working but can give you a significant boost in battery life." - quoted from the blog, so you obviously haven't read it.

I'm not using this thread to argue with you, this is a place to help people, not get upset because you think you should get credit for something (that you shouldn't).

Has your post been copied and pasted ? NO, did you create bumblebee ? NO, so whats your problem ? because I don't see why you have one.

---

### Post by morefeo on 2011-11-07
Have you create that post copying on mine? Yes. Have you give credit to other people work and textual words (like Phoronix)? No. Have you post that guide without research, stealing other people words and posting in every related thread here to get more visits? Oh, hell yeah.

That's all. Help is good, but hey, your post is exactly what I wrote few comments ago so it's not necessary to write that URL everywhere.

---

### Post by ronnystickshift on 2011-11-07
so am i to understand that installing bumblebee will fix the tap-to-click trackpad issue?

---

### Post by morefeo on 2011-11-07
> **ronnystickshift said:**
> so am i to understand that installing bumblebee will fix the tap-to-click trackpad issue?

You cannot fix it because cypress has no drivers for linux. You'll need to wait for them to make ones or reverse engineering from any other people.

---

### Post by AvalonSpirit on 2012-06-10
I know this thread has been inactive for some time, I cant get my XPS 15z to boot Precise, even following the wiki ([https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z]("https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z")) I get issues. It either hangs in the boot process or once it gets going it dumps me back on my regular grub boot menu. Has anyone had the same issue?

And I thought we were done with these issues for a new LTS release...
Anybody else still using natty?

---

### Post by doughnuts64 on 2012-06-11
I have managed to install 12.04 on my XPS 15z. I initially wanted to do a fresh install (from CD of USB thumb drive) as every kernel update that had been installed since 11.04 had caused a kernel panic when I tried to boot with it, so I was unsure that I would be able to get the new kernels working.

In the end, I could not manage to install either from CD or USB thumb drive - I don't know what was going wrong. I updated via the Internet, going from 11.04 -> 11.10 -> 12.04. Interestingly (and worryingly at the time), I still saw the kernel panic after the first upgrade and it wasn't until upgrading to 12.04 that I could use the newest installed kernel (which was a real relief).

Since then, everything has been going fine with the only noticable issues being startup and shut-down, both of which take an absolute age - the speed of these is something Ubuntu has previously been proud of!

I know I have not managed to resolve your issue - but at least you can see that there are people out there who have managed to get Ubuntu working properly.

---

### Post by AvalonSpirit on 2012-06-18
Well, at least its encouraging to know people have managed to update to precise. I've always expected to have to solve some problems when updating ubuntu, but doing so on this laptop has been a pain. How come it gets worse with every update??

---

### Post by rrohde on 2012-07-02
I recently got a Dell XPS 15z (coming from a MacBook Pro) and installed the current Alpha 2 of Quantal (12.10), and nvidia-current (302.17-0ubuntu1) is not installable (I assume that's because of an xserver-xorg issue at this time).

The mouse and touchpad worked right away, however, there's no Touchpad tab within the System Settings > Mouse and Touchpad configuration. Thus, multitouch does not work at this time. 

Dual-monitor support via mini HMI port using the built-in Intel video card works great. 

I am looking forward to seeing the Nvidia Optimus issues solved that everyone here is talking about. It's shame that there's no driver for the touchpad yet that allows multitouch. I never thought I'd say that, but my MacBook Pro was better supported than this Dell. :)

---

### Post by rrohde on 2012-07-02
There seems to be a kernel patch available: [http://kernel.ubuntu.com/git?p=kamal/ubuntu-precise.git;a=patch;h=8591b1a6356aa4d4db9557ba2b86f7bacabec376](http://kernel.ubuntu.com/git?p=kamal/ubuntu-precise.git;a=patch;h=8591b1a6356aa4d4db9557ba2b86f7bacabec376)

Any ideas when this will become available for us mere mortals? :)

---

### Post by darkhoros on 2012-08-27
Hi all,

This is to continue my post in page 10, read it if you need help

I managed to get the sd card to work. on ubuntu 12.04 kernel 3.2.0-29-generic

First to start, I like to let you know that if you insert the sd card before system bootup it will work as expected even eject and insert new and will be read/write.

The tricky part is to get it working if you insert the sd card after system boot up :D

I took my time of reading, googling and experimenting and other people efforts must be thanked for that.

ok, first of all we will have to load the modules needed by the sdcard "sdhci" manually to do so 
# sudo pico /etc/modules

then add after last line
acpiphp
mmc_block
sdhci_pci
sdhci
nls_iso8859_1
nls_cp437
vfat
fat
snd_seq

then save and close

now modify grub to get around an error "Refusing to bind to secondary interface"
to do so 
# sudo pico /etc/default/grub

and add pci=usepirqmask to the GRUB_CMDLINE_LINUX_DEFAULT
mine looks something like that
GRUB_CMDLINE_LINUX_DEFAULT="pci=usepirqmask acpi=noirq quiet splash"

then
# sudo update-grub

then restart pc

once logged in again after restart
insert sd card don't panic as it will not work yet :P

now type in terminal
# sudo -s
# echo 1 > /sys/bus/pci/rescan  -don't try # sudo echo 1 > /sys/bus/pci/rescan  you will get permission denied -

then vola :D
It will pop up, you will NOT need to retype these commands after every /eject/insert, and it will be also read/write

I know that you don't like typing in commands to get it working after every boot, I will be working on script to automate this task, or if any one can help about this would be perfect.

I hope some one may find this useful.

---

### Post by jwhirl06 on 2012-10-10
Just letting you all know there is a custom BIOS available for us, I updated to it yesterday.

[http://www.bios-mods.com/forum/Thread-UEFI-Dell-XPS-15z-L511z-modded-BIOS-and-HOWTO](http://www.bios-mods.com/forum/Thread-UEFI-Dell-XPS-15z-L511z-modded-BIOS-and-HOWTO)

This unlocks ALL of the advanced menus with more options than you could hope for to tinker with. This makes Hackintosh as well as other features we've been struggling with possible. Be warned, this is a risky procedure but I went through it just fine. One word of caution, when you update it, make sure you have a NEW version of Phoenix WINFLASH UEFI. Use the command prompt to execute the command. I did this with a LOW BATTERY on purpose, the end of the flash came up with an error for me, the flashing procedure shuts down leaving the laptop on with a blank screen. Simply pull the charger end out and let it power down. Then reconnect and reboot.

---

### Post by jwhirl06 on 2012-10-19
XPS 15z Owners rejoice. 

[http://hwe.ubuntu.com/uds-q/dellxps/amd64/sputnik-precise-amd64.iso](http://hwe.ubuntu.com/uds-q/dellxps/amd64/sputnik-precise-amd64.iso)

That's an ISO that works almost perfectly with our laptops, multitouch works, everything except Nvidia Optimus is working. To get Optimus working follow the instructions here:

Ubuntu linux

Currently, you need to open your terminal and enter the commands below.

sudo add-apt-repository ppa:bumblebee/stable
If you are on Ubuntu 11.04 or older and want newer drivers (recommended) than the ones available in the official repos, run:
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
To install Bumblebee using the proprietary nvidia driver:
sudo apt-get install bumblebee bumblebee-nvidia
Reboot or re-login. More help and information for Ubuntu can be found here.

(source: [http://bumblebee-project.org/install.html](http://bumblebee-project.org/install.html) )

---

### Post by jwhirl06 on 2012-10-23
Those of you upgrading to a 12.10 distro, the trackpad works fine out of the box on the 3.5 kernel. What doesn't work via traditional install is bumblebee. Follow these instructions.

[http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10](http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10)

---

### Post by armita on 2013-04-12
hello
I have a 15z and installed Ubuntu 12.10 gnome remix. I finally managed to install that with [COLOR=#333333][FONT=Ubuntu Mono]acpi_backlight=[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]dell_laptop.[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]backlight=[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]0[/FONT][/COLOR], keyboard and touch pad are working fine.
but i have a very important problem :( laptop shutdowns with no warning! it seems to be overheating problem. just after install ubuntu, fans didnt work at all! then i add acpi_osi=Linux in grub and now they are working, but very very slow. what should i do?

---

### Post by soberjack on 2013-04-13
After several tries I managed to install Ubuntu 12.04 in EFI mode (GPT partition table) on my DELL Inspiron 15z. What worked for me is what is in this post [http://askubuntu.com/a/224332/149034](http://askubuntu.com/a/224332/149034), i.e. I set the BIOS in legacy mode and then choose to boot (F12 at stuart-up) the 12.04 Live CD in EFI mode. In this way I get Ubuntu installed in a GPT partition table , with EFI boot loader.

The problem is that now, to start Ubuntu, I have to repeat these steps everytime:

    The boot is set in legacy mode from BIOS.

    I press F12 at start-up to choose to boot Ubuntu in UEFI mode.

If I set UEFI mode directly in BIOS, after grub, I get a blank (purple) screen, and Ubuntu does not start.

Secure boot is disabled, and I tried fixing it with boot-repair but did not succeed.

Does anyone have a clue of what is the problem?

---

### Post by oldfred on 2013-04-13
BIOS mode and UEFI mode are not compatible although you can dual boot, but only by going into UEFI/BIOS and changing boot mode to match install. 
UEFI writes data for system differently to hard drive than does BIOS.

Boot repair should be able to convert a BIOS install to UEFI install. And if your system only boots with secure boot on convert again by installing the signed versions of grub & kernel and renaming files. Some only boot the Windows efi file, so renaming to really boot grub secure boot file is a work around.

Is this an UltraBook with Intel SRT. The RAID used by Intel often causes issues. 
       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
Dell 14z used Dell Recovery and Refind
[http://ubuntuforums.org/showthread.php?t=2125397](http://ubuntuforums.org/showthread.php?t=2125397)

    
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

---

