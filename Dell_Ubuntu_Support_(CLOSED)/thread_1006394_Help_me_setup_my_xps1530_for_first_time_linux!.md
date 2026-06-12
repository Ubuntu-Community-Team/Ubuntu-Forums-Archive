---
title: "Help me setup my xps1530 for first time linux!"
date: 2008-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by heapy on 2008-12-09
Heya,
I am just about to recieve a new replacement hdd from dell. I am to install ubuntu, and have the new 8.10 on a dvd from a linux mag. 
The more i look on these forums the more I am put off taking the plunge and ditching windows!

I looked on the sticky, and saw that dell has released a version of ubuntu called Dell OS Factory Recovery 8.04.1 DVD ISO from: [http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

Should I be installing this instead of the new 8.10? 
I am just worried about all the talk of nvidia drivers not installing, strange trackpad issues and no wireless connections.

My laptop is a xps 1530, with what windows thinks is a nvidia 8600m gt. 
I am actually in the library gathering information for tomorrows delivery and install of ubuntu (i hope!)

any advice is grately recieved,

---

### Post by heapy on 2008-12-09
oh, and am i needed to flash the bios? does that actually help any of the hardware issues i maybe about to have? x

---

### Post by heapy on 2008-12-10
Am just flashing the bios from A07 to A12..

so does anyone offer advice, would it be better to go with ubuntu lts 8.0 because that is what dell ships with new machines? i have just ran 8.10 -in live mode, and my wireless wasn't available - thanks party people!!!

---

### Post by Gausian on 2008-12-10
It will be easier to help  you if you post your hardware specs here.

---

### Post by heapy on 2008-12-10
according to the dell website, entering my service tag i got these specs:

1 N02X5305 1 XPS M1530 CORE 2 DUO T7250 2.00GHZ, 800MH 
1 DISPLAY 15.4" ULTRASHARP WIDESCREEN WSXG 
1 FINGERPRINT READER BIOMETRIC WITH BLACK 
1 MEMORY DUAL CHANNEL 3.0GB (1X2GB + 1X1GB 
1 HARD DRIVE 200GB SERIAL ATA (7200RPM) 
1 8XDVD+/-RW SLIM SLOT-LOAD DRIVE, INCLUDI 
1 GRAPHICS CARD 256MB NVIDIA GEFORCE GO 86 NB8P-GS
1 INTEL? NEXT-GEN WIRELESS-N MINI-PCI CARD 

thanks for your patience : )

---

### Post by jespdj on 2008-12-10
Look here! ;)

[Ubuntu on the Dell XPS M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

Also do a search in this forum, running Ubuntu on the M1530 and specific problems have been discussed in this forum before.

Ubuntu should work fine, the Intel Wireless N card works out of the box and activating the nVidia driver is easy. I'm using the generic Ubuntu 8.04, not the Dell-specific version.

---

### Post by heapy on 2008-12-10
thank you jespdj that link is very inforative.
just out of curiosity, why are you not using the latest 8.10 intrepid? ..

also, is xubuntu 8.04 'hardy heron' the same as ubuntu gnome just cut down to run faster? i quite like the sound of a super fast no frills operating system as long as it can run open office and the other smart programs of the ubuntu edition

(as you can tell i am new to this, so i appreciate your advice

---

### Post by heapy on 2008-12-10
WOAH!! just seen this you tube vid demostrating xubuntu 8.04lts

[http://uk.youtube.com/watch?v=kHhzC0GWjOY](http://uk.youtube.com/watch?v=kHhzC0GWjOY)

.must of needed a well fast computer to do that!!!

edit.. has anyone used this instead of 8.10 intrepid?
[http://linux.dell.com/files/ubuntu/hardy/iso-images/](http://linux.dell.com/files/ubuntu/hardy/iso-images/)

---

### Post by Gausian on 2008-12-10
> **heapy said:**
> WOAH!! just seen this you tube vid demostrating xubuntu 8.04lts

[http://uk.youtube.com/watch?v=kHhzC0GWjOY](http://uk.youtube.com/watch?v=kHhzC0GWjOY)

.must of needed a well fast computer to do that!!!

edit.. has anyone used this instead of 8.10 intrepid?
[http://linux.dell.com/files/ubuntu/hardy/iso-images/](http://linux.dell.com/files/ubuntu/hardy/iso-images/)

you'll be able to run all those effects with your setup. no problem.

i havent tried the dell release, but regular 8.10 works fine on my 1530

---

### Post by heapy on 2008-12-10
now then gausian lad, ta for the reply. 
looking at your post, i noticed you have the same spec as me. does this mean anything to you? **256Mb NVIDIA NB8P-GS Graphics Card** that is what the online retailer thinks is my gfxcard. does that make it a 8400m gs like is stated in your profile thingy?

--also, thanks, i have a dvd with ubuntu 8.10 intrepid. i will probably install that, i was going to download the LTS version thinking my hardware would be more supported?

---

### Post by Gausian on 2008-12-11
im pretty sure that you have the 8600, but type this into the terminal to be sure: (if you havent already installed ubuntu, then use the live cd to get into the terminal)

```
sudo lshw -C video
```

Also ive found the newer versions of ubuntu generally have better hardware support.

---

### Post by heapy on 2008-12-11
thanks fella, im about to install a new hdd and get ubuntu 8.10 installed.. check out my other post for a giggle x

---

### Post by jespdj on 2008-12-11
> **heapy said:**
> thank you jespdj that link is very inforative.
just out of curiosity, why are you not using the latest 8.10 intrepid? ..
Because I need my computer for my job, and 8.04 runs very well on it, I didn't see the need to upgrade to 8.10 with the risk of having a non-working computer.

8.10 also has a bug ([#275998: audio recording very silent](https://bugs.launchpad.net/bugs/275998)) which is a showstopper for me. I need the internal microphone to work because I regularly use Skype on my laptop.

---

### Post by heapy on 2008-12-11
aha! .. maybe i will install the hardy heron after all as i do require a stable machine for work also.

---

### Post by heapy on 2008-12-11
ohhh nooo!!

just installed 8.04.1 hardy heron, everything seemed fine until i decided to un install evolution email in favour of thunderbird.
now when i try and log on, it just shows the heron background and my mouse curser and doesnt boot to show all the menus
 have to ctrl alt del twice to get shutdown or restart options

whats going on there?!

{..bloody feels like i've spilled the beans}

---

### Post by heapy on 2008-12-11
just had to get something called estool from samsung to low level format the drive and start again..

also had to change from achi to sata in the bios for the damn drive to be picked up. i thought ubuntu had achi support? might as well stick with what works eh : ) 

now for that pesky wireless, just done a search and found lots of people having the 'freezing after login' problem. some people blame nvidia, others the link 4965agn wireless.... and others found down grading the kernal to gutsy worked for them?

i have no idea, that is well  my understanding of linux. im so new to this its frustrating me aleady

---

### Post by jespdj on 2008-12-11
> **heapy said:**
> just had to get something called estool from samsung to low level format the drive and start again..
Why did you do this? It is never necessary to low-level format a harddrive. You could just have started the Ubuntu installation again and in the setup process reformat it.

> also had to change from achi to sata in the bios for the damn drive to be picked up. i thought ubuntu had achi support? might as well stick with what works eh : )
Mine is on AHCI and it works. I also have a Samsing 320 GB harddisk.

> now for that pesky wireless, just done a search and found lots of people having the 'freezing after login' problem. some people blame nvidia, others the link 4965agn wireless.... and others found down grading the kernal to gutsy worked for them?
I've never had this, and my M1530 has the same WiFi and graphics card as yours...

You can just leave Evolution installed and also install Thunderbird. You had probably accidentally uninstalled more than just Evolution.

---

### Post by heapy on 2008-12-11
i think you are right lad, i un installed evolution threw synaptic. then i looked at the search thingy and checked for installed stuff. then found loads more with evolution, plus i still had the mail thing on the top bar by firefox. so thought that un installing a bunch of stuff that had evolution in its name would get rid of it completely. a few selections said other parts would be affected like some program that does voip or something... and pigeon or whatsit. 

so how do i get rid of some of the programs i wont use or need without messin the whole damn thing up by accident? i quite fancy that vlc media player.. so totem wont be needed for instance..

cheers for the help mucker

---

### Post by sneeks on 2008-12-11
If you really need to un-install some programs just use add/remove in applications.
it's safer instead of going gung ho in synaptic !!!!!!
But i dont see a problem of just leaving them there really,as with the size of your drive it will not really matter.

---

### Post by heapy on 2008-12-11
cheers sneeks, am bein careful now. just got 8.04.1 installed. just enabled the nvidia drivers, and started updating.. 

200 odd software updates, 200 odd mb... then the system froze!!! **** sake what am i doin wrong lol im cursed


edit: just froze again at the same spot, this time i pressed 'check' instead of install the updates then it just did nothing and i had to hold the power button to turn off. man this sucks

edit2:now i have realized when i turn off wireless the system is stable. so i have connected it to the router via a patch cable but where do i put the wpa2 key?? its not asking me for one so it's not connecting..
 
many thanks

---

### Post by heapy on 2008-12-11
i have no idea what i did differently, but touch wood everything seems grand. all the updates installed. 

i did get a strange thing when it restarted after, i got a black screen with a horizontal line in the middle of the screen, then a double ubuntu symbol... then a bunch of error codes about a 'network device'

another restart later and im now on my xps with ubuntu 8.04.1 all sweet & no lockup !!
no doubt will be on again 2m hoping for your experiences forum people : )

~goodnight

---

### Post by heapy on 2008-12-12
ha, i am cursed. . after thinking everything was sweet i switched the machine on this morning. after the grub 1.5 menu i saw the normal 'ubuntu' spalsh screen load then it just stopped and hung. i held down the power button to turn off, then it boot as normal and im now typing this quite happily. 

why is the system hanging there and randomly like this? can i paste log's into here somehow for youse to look over??

---

### Post by Gausian on 2008-12-12
ive had ubuntu hang on  boot only once and it hasnt happened again.  id say if it isnt a recurring problem then there isnt too much to worry about.

---

### Post by heapy on 2008-12-12
thanks gausian, you are great!! im on ubuntu irc chat trying to get help but its not happening..

i have had the laptop on for 2 hrs and its frozen 4 times already really randomly too. this is the longest session ever.. touch wood lads.. i cant get my head around why its locking up like it is. its frustrating me so much cus i have work to do and no other o.s. i have thought about installing xubuntu ~is that worth a dig?

would some log files help diag the issue? if so, how do i do that oh i am so out of my depth

---

### Post by heapy on 2008-12-12
i have just been on irc, and the #xubuntu channel. some fella on there was dead helpful. i have disabled the nvidia drivers as was suggested, and havent had a crash since..

is this normal!? i followed jespdj's guide to install them & sudo apt-get update to get the latest. everything went smoothly, d/loaded the drivers and they were enabled. i had nice lookin fonts and was able to use the visual effects.

what are my options? im assuming its the nvidia drivers because now sometime after disabling them, my laptop is quite stable (by now it would of locked up im sure). so do i try a different nvidia version? if so, how do i go about doing that?

i appreciate your time lads, i can see light at the end of the tunnel!! nearly there

---

### Post by heapy on 2008-12-12
okay, 
ignoring that random lockup 5 minutes ago everything seems sweet! ha-ha.

if it's not the nvidia drivers, could this be it? or a mix of both?
i have noticed a few strange clicks from the hdd & on jespers m1530 page he had the same prob. something to do with the load_cycle_count increasing...

so i installed smartmontools and ran sudo smartctl -a /dev/sda

..does that mean anything to youse? thanks again x

edit again!: i have been chatting again in irc, and some fellow said hay, isnt ur cpu 64bit? ... that got me thinking should i be using the 64bit ubuntu?? i thought you should only use that with more than 4gb of ram. but thought i'd ask anyway ~cheers

---

### Post by loveandequality on 2008-12-12
there is a Dell support fourum in the home page of this site.

i also got a xps but i got it with Ubuntu factory installd.

---

### Post by heapy on 2008-12-12
is yours 64bit? does it acutally make a difference running 32 or 64bit ubuntu?

---

### Post by heapy on 2008-12-12
OK its not the nvidia drivers, because i am using them now without a problem i think..

i did just have a system hang just this moment, and i checked the syslog and found a bunch of stuff relating to the wireless..

confusion strikes again!

---

### Post by jespdj on 2008-12-12
Random lockups are not normal and might be an indication that there's a hardware problem with your computer, for example with the memory.

When you boot the computer, press the Escape key when you see "GRUB" on the screen. In the boot menu, choose the "memtest86+" option to start the memory testing program. Let it run for a few hours to test the memory in the computer. If the program finds errors, then there is something wrong with the memory, and you should contact Dell about it.

64-bit Ubuntu works just as well as 32-bit. In fact, if you have more than 3 GB RAM in your computer, you'll want to use the 64-bit version to be able to use it all (32-bit is normally limited to about 3.5 GB RAM; I'll spare you the technical details). 64-bit is also faster, especially with CPU-intensive software.

---

### Post by heapy on 2008-12-12
am running that test now,.. probably take a couple of hours.. thanks everyone by the way x
3 hours into memtest and zero errors... 4 pass's so far
i will leave it overnight
untill 2m ubuntu, round 3


edit: 13hrs run time, 18 pass's, zero errors. So it's not the ram

---

### Post by heapy on 2008-12-13
im pretty sure i have found the problem.. i think its the wireless. just done another search as using the internet is the only common thing i have when the system locks up. 
then found this:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/276990)

somehow i need to sort the wireless out to stop the freezing

i just found this: can someone help me do something to 8.04.1 to get this fix going??
**System lock-ups with Intel 4965 wireless**
The version of the iwlagn wireless driver for Intel 4965 wireless chipsets included in Linux kernel version 2.6.27 causes kernel panics when used with 802.11n or 802.11g networks. Users affected by this issue can install the linux-backports-modules-intrepid package, to install a newer version of this driver that corrects the bug. (Because the known fix requires a new version of the driver, it is not expected to be possible to include this fix in the main kernel package.) 


ps. im soooo happy to find a lead to this problem!!!

---

