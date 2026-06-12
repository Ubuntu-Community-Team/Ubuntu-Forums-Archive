---
title: "Dell Inspiron 1545 with Ubuntu 10.10 not reading Wireless Card"
date: 2011-01-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drkPu1se on 2011-01-29
Hello. I just install Ubuntu 10.10 with the Macbuntu UI. I have everything working completely swell except for the fact that my laptop does not read my wireless card. I have used ndiswrapper and even downloaded a few other apps to see if I can get it to go. 

When I type this command:

lshw -C network

it shows this:


*-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff



What does it mean UNCLAIMED? And is there a way to "claim" it?

thank you in advance.

---

### Post by the.scarecrow on 2011-01-29
Try System>Administration>Additional Drivers

Select Broadcom STA wireless driver

Then press the Activate button

and hopefully your problem will be solved. Make sure wireless is turned on by the keyboard switch which is shared with the F2 key on my laptop.

---

### Post by drkPu1se on 2011-01-29
> **the.scarecrow said:**
> Try System>Administration>Additional Drivers

Select Broadcom STA wireless driver

Then press the Activate button

and hopefully your problem will be solved. Make sure wireless is turned on by the keyboard switch which is shared with the F2 key on my laptop.


yeah i did that as well. i tried again and it says that its activated but not in use.

still nothing. i also tried reinstalling resticted for ubuntu and that  didnt work as well.

---

### Post by Jimtheplanner on 2011-01-30
Hi Folks,

I've had this with my 1545 before, generally when I change set-up etc. Try shutting down then remove the battery for a minute or so. Put it back in then restart and all should be well.

I guess the wireless set-up gets confused and this should re-set it for you....

Jim

---

### Post by drkPu1se on 2011-01-30
Thank you. lemmme go try it out.

---

### Post by drkPu1se on 2011-01-30
> **Jimtheplanner said:**
> Hi Folks,

I've had this with my 1545 before, generally when I change set-up etc. Try shutting down then remove the battery for a minute or so. Put it back in then restart and all should be well.

I guess the wireless set-up gets confused and this should re-set it for you....

Jim



yeah nothing. thanks anyways

---

### Post by Megaptera on 2011-01-30
I've used this fix on my Dell Inspiron, similar to the re-boot suggested above but without battery removal. I know it says Dell Mini - ignore that but do the re-boot.
Hope this helps?

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by the.scarecrow on 2011-01-30
> **drkPu1se said:**
> yeah i did that as well. i tried again and it says that its activated but not in use.

still nothing. i also tried reinstalling resticted for ubuntu and that  didnt work as well.

I have the same BCM4312 working fine with the STA driver from a fresh install. It can be fiendishly difficult to completely remove drivers once the wrong ones are installed, although it can be done I don't know how.

I just got the WiFi working on a live Puppy Linux USB 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
If you look at the READme.txt by Broadcom, it has a thorough description of what to do. (not Puppy specific).

However, if it were me, I would:
1 Boot into a Live session from USB or CD
2 Connect to the router with a cable to access the internet 
3 Try and install the STA driver and get WiFi working in the live session
4 If you get it working, do a fresh install straight from the working live session.

I hope this works for you, at least be confident that your Broadcom WiFi will work when you hit the right combination.

---

### Post by drkPu1se on 2011-01-30
> **the.scarecrow said:**
> I have the same BCM4312 working fine with the STA driver from a fresh install. It can be fiendishly difficult to completely remove drivers once the wrong ones are installed, although it can be done I don't know how.

I just got the WiFi working on a live Puppy Linux USB 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
If you look at the READme.txt by Broadcom, it has a thorough description of what to do. (not Puppy specific).

However, if it were me, I would:
1 Boot into a Live session from USB or CD
2 Connect to the router with a cable to access the internet 
3 Try and install the STA driver and get WiFi working in the live session
4 If you get it working, do a fresh install straight from the working live session.

I hope this works for you, at least be confident that your Broadcom WiFi will work when you hit the right combination.

So you are telling me i should uninstall Ubuntu and use this method?

---

### Post by TBABill on 2011-01-30
Keep the STA activated and restart. Then ```
sudo rfkill list
``` and if soft or hard blocked states YES, then ```
sudo rfkill unblock all
```

---

### Post by drkPu1se on 2011-01-30
> **TBABill said:**
> Keep the STA activated and restart. Then ```
sudo rfkill list
``` and if soft or hard blocked states YES, then ```
sudo rfkill unblock all
```

yea this didnt work cuz they both were NO.

---

### Post by TBABill on 2011-01-31
What happens if you ```
sudo apt-get install bcmwl-kernel-source
``` and then ```
sudo modprobe -r b43 ssb wl

``` and then ```
sudo modprobe wl
``` If this starts the wireless up (for this session only probably), then it may be a matter of straightening out what could be blacklisted in /etc/modprobe.d/blacklist.conf and what modules may be missing from your startup configuration in /etc/modules

---

### Post by the.scarecrow on 2011-01-31
> **drkPu1se said:**
> So you are telling me i should uninstall Ubuntu and use this method?

No, I suggest you try getting STA drivers to work in a Live Session by booting from your Ubuntu CD. This will bypass any mess-up with the installation on your Hard Drive. Steps 1-3 will not harm your installation.

However, if it were me, I would:
1 Boot into a Live session from USB or CD
2 Connect to the router with a cable to access the internet
3 Try and install the STA driver and get WiFi working in the live session
Then if you want,
4 If you get it working, do a fresh install straight from the working live session.

Or TBABill seems to be offering you good advice so try that.

In your first post you said that you have tried using ndiswrapper and other apps, this leaves your current drivers installation in a very uncertain state. You must decide if you want to try and fix it or start over again with a fresh install.

---

### Post by drkPu1se on 2011-01-31
> **TBABill said:**
> What happens if you ```
sudo apt-get install bcmwl-kernel-source
``` and then ```
sudo modprobe -r b43 ssb wl

``` and then ```
sudo modprobe wl
``` If this starts the wireless up (for this session only probably), then it may be a matter of straightening out what could be blacklisted in /etc/modprobe.d/blacklist.conf and what modules may be missing from your startup configuration in /etc/modules

yeah i tried this and i didnt get anywhere with it. this is what i got this

```
drkpu1se@drkpu1se-Inspiron-1545:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for drkpu1se: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
drkpu1se@drkpu1se-Inspiron-1545:~$ sudo  modprobe-r b43 ssb wl
sudo: modprobe-r: command not found
drkpu1se@drkpu1se-Inspiron-1545:~$ sudo modprobe - r b43 ssb wl
FATAL: Module _ not found.
drkpu1se@drkpu1se-Inspiron-1545:~$ sudo modprobe -r b43 ssb wl
drkpu1se@drkpu1se-Inspiron-1545:~$ sudo modprobe wl
FATAL: Error inserting wl (/lib/modules/2.6.35-25-generic/updates/dkms/wl.ko): Invalid argument
FATAL: Error running install command for wl

```

i may had to try it a few times but i think i did it right. sooo.... yeah.

---

### Post by drkPu1se on 2011-01-31
> **the.scarecrow said:**
> No, I suggest you try getting STA drivers to work in a Live Session by booting from your Ubuntu CD. This will bypass any mess-up with the installation on your Hard Drive. Steps 1-3 will not harm your installation.

However, if it were me, I would:
1 Boot into a Live session from USB or CD
2 Connect to the router with a cable to access the internet
3 Try and install the STA driver and get WiFi working in the live session
Then if you want,
4 If you get it working, do a fresh install straight from the working live session.

Or TBABill seems to be offering you good advice so try that.

In your first post you said that you have tried using ndiswrapper and other apps, this leaves your current drivers installation in a very uncertain state. You must decide if you want to try and fix it or start over again with a fresh install.

oh. i didnt understand the first time lol. i will have to try this later. thank you.

---

### Post by TBABill on 2011-01-31
Looks like you just need to go into Synaptic and search for B43, then remove anything referencing it. You could have a conflict between b43 and wl drivers. I'd remove the b43 stuff, then try the steps for the STA again.

---

### Post by drkPu1se on 2011-01-31
> **TBABill said:**
> Looks like you just need to go into Synaptic and search for B43, then remove anything referencing it. You could have a conflict between b43 and wl drivers. I'd remove the b43 stuff, then try the steps for the STA again.

should uninstall the wl drivers as well? cuz i just tried it and it still doesnt make it work. or even better yet should i just attempt to reinstall ubuntu and set the drivers up *before* i update?

one of my buddies who is an ubuntu freak says that if the restricted drivers didnt work then my laptop just plain hates ubuntu. i got it to run once soo i know it works

---

### Post by TBABill on 2011-02-01
I'd say your buddy is fairly unfamiliar with Ubuntu to make a comment like that. You have the same card as many users on Ubuntu who get it to work every time. 
 
Since you are so new to Ubuntu and you have no files to backup on this install it'll only take about 20-30 min to get it reinstalled and start over. What I recommend is...
 
1. Plug the ethernet cord into your machine
2. Run the LiveCD or LiveDVD and install fresh
3. If this is 10.10, check the box to have the system install all the updates, extras, proprietary drivers, etc. If it's 10.04 or earlier, just install, then immediately do an update. Do the update FIRST...meaning do it before you try to install any proprietary drivers. The drivers do get updated as well as other parts of the system, including the kernel, so it's best to have an up to date system before you add drivers just as a precaution. I've done it beforehand successfully, but as a new user it's better safe than sorry.
4. Once fully updated and restarted after the updates, then go to System>>Administration>>Hardware (10.04 or earlier versions) and select the STA driver when prompted. Let it do its thing, restart and enjoy.
 
NOTE: If you install 10.10 it should care for lots of things for you if you select the right boxes at each prompt. This is a wonderful improvement and may solve your issues for you.
 
Since this is a Broadcom, if the wireless does not immediately allow you to connect, next do ```
sudo rfkill unblock all
``` and see if it works. Most likely it'll just work but on early installs of 10.10 I had to do this for mine. Last time I installed it I did not. YMMV.
 
Reinstalling is the easy way out but it teaches you nothing other than how to install again. But to get up and running this is the fastest way without running you through more terminal commands, uninstalls of the b43, etc. Once you get the hang of it this will seem very simple for you on later installs.

---

### Post by drkPu1se on 2011-02-02
> **TBABill said:**
> I'd say your buddy is fairly unfamiliar with Ubuntu to make a comment like that. You have the same card as many users on Ubuntu who get it to work every time. 
 
Since you are so new to Ubuntu and you have no files to backup on this install it'll only take about 20-30 min to get it reinstalled and start over. What I recommend is...
 
1. Plug the ethernet cord into your machine
2. Run the LiveCD or LiveDVD and install fresh
3. If this is 10.10, check the box to have the system install all the updates, extras, proprietary drivers, etc. If it's 10.04 or earlier, just install, then immediately do an update. Do the update FIRST...meaning do it before you try to install any proprietary drivers. The drivers do get updated as well as other parts of the system, including the kernel, so it's best to have an up to date system before you add drivers just as a precaution. I've done it beforehand successfully, but as a new user it's better safe than sorry.
4. Once fully updated and restarted after the updates, then go to System>>Administration>>Hardware (10.04 or earlier versions) and select the STA driver when prompted. Let it do its thing, restart and enjoy.
 
NOTE: If you install 10.10 it should care for lots of things for you if you select the right boxes at each prompt. This is a wonderful improvement and may solve your issues for you.
 
Since this is a Broadcom, if the wireless does not immediately allow you to connect, next do ```
sudo rfkill unblock all
``` and see if it works. Most likely it'll just work but on early installs of 10.10 I had to do this for mine. Last time I installed it I did not. YMMV.
 
Reinstalling is the easy way out but it teaches you nothing other than how to install again. But to get up and running this is the fastest way without running you through more terminal commands, uninstalls of the b43, etc. Once you get the hang of it this will seem very simple for you on later installs.

im gonna try that now. and i just thought of something as well. is it possible that its cuz im trying to install the amd64 version? i have a dual core 2.0 processor 64x so yeah... andon the site it sez its recommended to use the 32x version

---

### Post by vvojciech on 2011-02-02
I knew the way to fix wirless card problem in dell 

1. run your ubuntu (normal boot from hard disk) 
2. get liveCD or LiveUSB,
3. find on them folder-> pool
3. then find pool>main>b
4. install b43-fwcutter 
5. install patch in pool>main>p
6.  On a computer with Internet access, download the required firmware files from [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o) and [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)  
 7. on ubuntu copy the downloaded files to your home folder and execute the following commands consecutively in a terminal to extract and install the firmware:  
 
~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
~$ sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o


thats all, work for my dell studio with 1397 wireless card 
I found this solution on: [http://wireless.kernel.org](http://wireless.kernel.org) when looking for driver (becouse this is the problem)

---

### Post by drkPu1se on 2011-02-02
so i did a fresh install. when i try to connect wirelessly under wireless networks it says device not ready (firmware missing)

am i not doing something right?

when i do the rfkill thing it says that none of my things are blocked.

---

### Post by the.scarecrow on 2011-02-02
> **the.scarecrow said:**
> Try System>Administration>Additional Drivers

Select Broadcom STA wireless driver

Then press the Activate button

and hopefully your problem will be solved. Make sure wireless is turned on by the keyboard switch which is shared with the F2 key on my laptop.

Do this.

---

### Post by drkPu1se on 2011-02-03
> **the.scarecrow said:**
> Do this.

ive tried quite a few times.

---

### Post by drkPu1se on 2011-02-03
well i have i ubuntu install on a seperate partition from windows 7 ultimate 64x. could be possible that i dont have the drivers installed for windows? cuz i dont cuz it already connects without it. either way im doing that right now

---

### Post by the.scarecrow on 2011-02-04
> **drkPu1se said:**
> so i did a fresh install. when i try to connect wirelessly under wireless networks it says device not ready (firmware missing)

am i not doing something right?

when i do the rfkill thing it says that none of my things are blocked.

The fresh install was step 4.

What happened when you did step 1, step 2 and step 3?

As step 4 was on condition that step 3 worked okay.

---

### Post by drkPu1se on 2011-02-04
> **the.scarecrow said:**
> The fresh install was step 4.

What happened when you did step 1, step 2 and step 3?

As step 4 was on condition that step 3 worked okay.



well i tried doing the wireless thru LiveUSB but to no avail. should i just start assuming ubuntu doesnt like my laptop or viceversa?

---

### Post by TBABill on 2011-02-04
First do: ```
sudo apt-get update
``` then

```
sudo apt-get install --reinstall bcmwl-kernel-source 
```

THEN go to SYSTEM>>ADMINISTRATION>>HARDWARE and select STA, then let it run and restart the computer.

---

### Post by the.scarecrow on 2011-02-05
> **drkPu1se said:**
> well i tried doing the wireless thru LiveUSB but to no avail. should i just start assuming ubuntu doesnt like my laptop or viceversa?

I think 100s of ppl are using Ubuntu with BCM4312 wireless cards so it really should be working.

Did you do this step
2 Connect to the router with a cable to access the internet

and were you able to connect to the internet via this cable to the router prior to installing the STA driver? I seem to remember that on occasions the driver was downloaded from the internet rather than taken from the Live USB. My impression is that booting from a Live CD makes a more successful job of retrieving the drivers if no internet connection is working.

I heard Broadcom is open sourcing the drivers so it may not be long before these cards are fully supported without all this hassle. Lets hope so anyway.

---

### Post by TBABill on 2011-02-05
> **TBABill said:**
> First do: ```
sudo apt-get update
``` then

```
sudo apt-get install --reinstall bcmwl-kernel-source 
```

THEN go to SYSTEM>>ADMINISTRATION>>HARDWARE and select STA, then let it run and restart the computer.
Since you have a fresh install, just do the above. That's all you should need to do but you MUST be connected via ethernet to download from the Internet to do this. And you must enable non-free repositories if you haven't already.

---

### Post by drkPu1se on 2011-02-07
soo umm i am to connect to wifi with liveUSB but not after I install it. Should i like install the propitiatory drivers when i have liveUSB running then install?

---

### Post by drkPu1se on 2011-02-07
> **TBABill said:**
> Since you have a fresh install, just do the above. That's all you should need to do but you MUST be connected via ethernet to download from the Internet to do this. And you must enable non-free repositories if you haven't already.

i have actually no idea about what you are talking about the non-free repositories. i am a complete newb who is sick with windows bull shiza. and when i used ubuntu before i actually enjoyed it a lot

---

### Post by drkPu1se on 2011-02-07
> **drkPu1se said:**
> i have actually no idea about what you are talking about the non-free repositories. i am a complete newb who is sick with windows bull shiza. and when i used ubuntu before i actually enjoyed it a lot

oh and i forgot. could you explain how to unlock non-free repositories? sorry. thank you

---

### Post by the.scarecrow on 2011-02-07
> **drkPu1se said:**
> soo umm i am to connect to wifi with liveUSB but not after I install it. Should i like install the propitiatory drivers when i have liveUSB running then install?

Yep, install the STA drivers and see if WiFi is working. Then do the fresh install but you will probably have to install the STA drivers again once it has completed the installation on your hard drive.

To enable the non-free repositories. (I never had to do this to install the WiFi drivers and to complete it you need a working internet connection). However, you will need to do this to enjoy your Ubuntu experiance after WiFi is working.

System>Administration>Synaptic Package Manager
you will be asked for your admin. password
Click Settings (top left)
Repositories>Ubuntu Software tab
Make sure the top four boxes are checked down to and including "Software Restricted By Copyright....." then click the Close button.

For the following to work you need access to the internet!
Then click Reload (top left)
When its completed updating, close Synaptic Package Manager.

Now you will have access to the non-free software and lots of other essential software as well.

---

### Post by drkPu1se on 2011-02-07
no offense to any one but i now feel retarded. i tried one of the earlier methods and i found out that i failed at doing it correctly. i now am running ubuntu 10.10 maverick meercat with no problemo! i will quote with the solution with a few comments in the next post

---

### Post by drkPu1se on 2011-02-07
> **TBABill said:**
> First do: ```
sudo apt-get update
``` then

```
sudo apt-get install --reinstall bcmwl-kernel-source 
```

THEN go to SYSTEM>>ADMINISTRATION>>HARDWARE and select STA, then let it run and restart the computer.

i did not do the update because i did it through update manager. 

and i didnt do the double hyphen before reinstall. bam

bam bam bam. TBABill thank you. this is the solution :) 

thread solved.

---

