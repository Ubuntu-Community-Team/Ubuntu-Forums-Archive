---
title: "No drivers for wireless card 1395?"
date: 2008-04-02
forum: Dell  Ubuntu Support
---

### Post by employeeno5 on 2008-04-02
Hi! I just got a Dell M1330 and it's lovely.

I've installed the Hardy Beta on it.

Everything is working peachy with the exception of my wireless card which is the Dell mini 1395 (Broadcom I believe?)

So, everything I've been reading for the past three days from searching these forums and google leads me to believe that a driver should be available in the restricted driver manager for this. 
However there is not one showing up. In fact, my wifi light has never turned on with Linux so far. 
I know it's in there and working only because I've booted into Windows and had it operate.

Now, according to a couple blogs and post on Dell's forums this should also install the driver:
```
sudo apt-get install bcm43xx-fwcutter
```

That package will install and remove fine but it makes no change in my wireless situation at all.

Being desperate I carefully followed to apparently successful (though unsupported guide) here:

[http://www.backports.ubuntuforums.org/showthread.php?t=297092](http://www.backports.ubuntuforums.org/showthread.php?t=297092)

I was careful to follow all directions and even made sure to download the appropriate driver for the 1395, (given that the guide was written for the 1390). Again, everything appeared to install and work with out a[ hiccup. Yet at the end of the process Ubuntu still doesn't even know that I have a wireless card.

I know that given I'm on the Hardy Beta it could be part of the problem. However I get no wireless with a Gutsy live cd either.

I'm hoping, that if someone can't identify this problem or help with a solution, that someone can at least confirm that if I take the time to install Gutsy instead that I should expect to see my driver in the restricted manager or have better luck with some other solution.

I've been using Ubuntu for a long time now on my old laptop (another Dell which the wireless worked out of the box on) and I have no interest in going back to Windows. If I can't get wireless on this I really won't be able to use Linux on my new computer, which would really break my heart.

This is a very popular computer model and I'm surprised I'm not finding other people with this problem or a solution when searching (or rather the small few I did fine appeared to have solutions that do not evoke a response on my rig). 

This is the first time I've felt helpless with Linux since I got it.

Hoping someone can be my digital savior. Many thanks in advanced for even just taking the time to read this.

---

### Post by cousinavi on 2008-04-03
Hi

I got my wireless (Dell Wireless 1505) working on my Vostro 1000 and put the solution I used [here]("http://ubuntuforums.org/showthread.php?p=4611912#post4611912"). 

Hope this helps!

**-Avi**

---

### Post by employeeno5 on 2008-04-03
Hi Avi,

Thanks for the advice. I have looked in my restricted drivers. Ubuntu has no problem recognizing that I have an Nvidia card that needs a restricted driver, but it does not recognize the wireless card at all.

The odd thing is that I also have an E1505 with a card that also needs a restritced broadcom driver and Gutsy has never had any problem recognizing it and offering up the restricted driver (or rather, the driver is open source, but the firmware it depends on it proprietary). Granted I"m using the Hardy Beta, but when I tried Gutsy on this computer it's the same deal: recognizes the video cards need, but not the wireless ones.

I'm wondering if Ubuntu is even detecting that there's any hardware there at all. 
I'm also wondering that if that's the case, would manually installing the firmware help, and if so how do I do that? 

I've found  several posts around the net saying that installing "bcm43xx-fwcutter" installs the required driver and things should just work. However I get no change when I install it via apt-get (it does install and remove properly it just doesn't make anything work).

On one forum post I came across while searching at Dell's webiste, someone said to install that but also gave a link to some firmware to install into the application "restricted-manager".
This application won't install on my Hardy because it's been replaced with "jockey" (i think that's the name, I'm at work and not using Linux) Jockey is what we all know as Ubuntu's restricted driver manager. 

The problem is that the modern restricted driver manager appears to be fully automated and doesn't give me the option to manually import firmware from a file location. 

If anyone knows how to get "restricted-manager" to install (sudo apt-get tells you that you can't have it because jockey is better), or how else I might manually install firmware from a file location, that would potentially be super helpful.

For now, I've done a clean reinstall of Hardy so I can try some new things with a fresh start. I'll be sure to check out that guide when I get home from work today.

Again though, 
I'm getting the impression that getting this firmware manually installed might be the key to my problems. 
Here's a link to the Dell post for reference, in case anyone is curious:
[http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=12478&query.id=158763#M12478](http://www.dellcommunity.com/supportforums/board/message?board.id=sw_linux&message.id=12478&query.id=158763#M12478)

Thanks for the input and thanks to anyone else who might have some ideas on this issue.

---

### Post by cousinavi on 2008-04-03
Hmmm

I don't think it is possible to force the restricted drivers manager to try and add a piece of hardware.

When I tried to get my card working I tried everything I could find. Solutions using bcm43xx-cutter didnt work for me, but maybe thats because my card is a 802.11-n card. I don't know!

In the end it was the "ndisgtk" package that got my card on its feet. I don't know if it is was the package itself or the dependancies, I just go with what works :).

If you are taking a ndiswrapper route does the command,
```
ndiswrapper -l
```
give positive results?

If so it may be that the card is working fine, but network-manger doesn't have the software packages it needs.

I don't believe it is impossible to get your card working satisfactorily.

**-Avi**

---

### Post by employeeno5 on 2008-04-03
I did have any luck with this ndiswrapper solutions.

However I think I found the reason why Ubuntu doesn't seem to even recognize that I have a wireless card at all.

Check out my lspci output:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)
```

Down there at the very bottom. That's my wireless card but it's listed as a USB controller. Anyone else I've encountered on the internet talking about this card, their's list clearly as a wireless card. Mine; USB controller.  I'm not sure at all what to do about that.

I talked to Dell's Ubuntu people. I have to say that I told them right up front that I had not purchased a Ubuntu pre-installed system so I didn't know if their service applied to me at all, and they still were happy to talk to me and offer any support they could. That rules.
However, they said they have never had any luck getting this card to work with Ubuntu which is why the Intel model is the only one they offer with their pre-installed systems.
So, I didn't get much help there, but they were willing to be helpful and were friendly. I really thought that was cool. 

I think I may just buy the Intel card if I can't get this working in the next week or so because I really do need this computer to be portable. I actually meant to buy the Intel in the first place and just made a mistake. I'm hoping this one can still work though. It's true I have Vista to boot into, but running Windows on this machine takes away all of it's sexy. 

I'll keep digging and if I learn anything new I'll post back. Meanwhile if anyone reading this has had a similar problem or any ideas I'll be thrilled to try them.

Thanks again Avi.

---

### Post by cousinavi on 2008-04-04
Hi #5,

I put your strange lspci line into google and found this thread:
[http://ubuntuforums.org/archive/index.php/t-650729.html]("http://ubuntuforums.org/archive/index.php/t-650729.html")

Since the author of the thread got his card going I don't think you have too much to worry about. 

The solution which he used was the one advocated by Dell:
[http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper")

I do think this is your best chance to get things going. I didnt get ndiswrapper working for a few days, and I am 99% sure **my** problem was getting the right packages to allow ndiswrapper to talk to network-manager.

But if you say ```
ndiswrapper -l
``` has never given you positive results then maybe your problem is quite deep.

I think maybe the best thing to try is to remove any ndiswrapper packages, then follow Dell's advice (link above) to the letter.

My only warning would be about the line of code:
```
sudo apt-get install ndiswrapper-common ndiswrapper-utils ndisgtk
```
as I think the package "ndiswrapper-utils" has changed its name. If this line does barf on you just try,
```
sudo apt-get install ndiswrapper-common  ndisgtk
```
This worked for me because the dependencies installed the correct packages. Not elegant, I know.

**-Avi**

---

### Post by employeeno5 on 2008-04-04
Awesome. 
I will give ndiswrapper another run or two. Luckily, as a temporary measure, I found an old USB stick wireless adapter. It's not attractive but it at least means I don't have to huddle in the one corner of my apartment where I've hidden away my modem/router while I work on this issue. 

I might not have time to really sit down with my machine again until tomorrow or Sunday.

I'll be sure to make clean up any previous ndiswrapper stuff before trying it again.


Also, I just want to say for anyone else who's seen this and is/was thinking about getting this model of computer or is nervous about the Hardy upgrade:
Everything except my wireless card worked out of the box with no trouble on the Hardy Beta. Every last little quirk. I know that if you get the Intel brand card they offer instead of the Dell brand that the wireless should work out of the box too.
Webcam, sound, nvidia, card readers, power managerment, suspend /resume, bluetooth, media buttons, remote control, everything. 

The point being that I hope my headache doesn't scare anyone else off. Hardy is really impressive and does a fantastic job working with the M1330's hardware.

---

### Post by capndeathstrike on 2008-04-22
any luck #5?

---

### Post by employeeno5 on 2008-04-22
I actually never had any luck trying any of the ndiswrapper solutions. I was given similar advice and some other ideas on a few other threads as well as on the questions and answers over at launchpad. I found allot of other stuff hanging around the net as well. After more than three weeks of hard work and no wireless response at all, I just broke down and bought a compatible card cheaply, which was more than worth the money.

This is the first problem I've encountered like this in Linux, that I just couldn't get through. It hasn't soured me though.

I think I know why I couldn't get solutions that "should work" to go. When I "lspci" my wireless card would show up, but not as a wireless card but as a USB controller (Broadcom controller? weird.) Everywhere else I checked on the internet where this card was in question, the exact same card was shown to be clearly listed as a wireless card when others used lspci. For whatever reason, the firmware for that card in my machine or it's newest firmware in general or whatever; Linux could not see it as a wireless card (or rather, I'm guessing the card told it was usb controller). 
I'm wondering if it has anything to do with Dell upgrading the card's firmware to work in Vista. I learned from searching around on this issue that that card didn't have any Vista support for a long time. Perhaps some weird shortcut fix involves telling the computer it's a usb device of some kind? I don't know. It's weird though. It does seem however, that I could not get drivers to work in Linux because Linux never even knew that a wireless card was in the machine, it saw it as a third USB controller (the wireless card was listed in the exact same manner as the other USB controllers only "Broadcom" card preceded USB controller info; no mention of network device, wireless, card, or anything else related to it's true nature, just info about being a USB port).

So again, unless you want to make it a little project to solve, don't buy that Dell card. I think most people know Intel is the safe bet in that situation. This was all a rather large headache.

Maybe it's just me. Maybe I really did just miss something here. I don't think so though. I really worked hard on this for a few weeks.

The solution for me ended up being to start with the correct hardware. I know that's not an option in every case, and that we'd like to see a day when all hardware always works, but for me in this case I just needed it to work. It was more than worth an extra thirty bucks to have it solved and have Ubuntu nice and mobile.

Everything else about Hardy on this machine is a pleasure. I'm really impressed with the pending release. I've run into a few quirks recently having used it more, but they're not serious problems and if they're not ironed out by Thursday's release, I'm sure I can figure something out. Most people seem to have great luck with the M1330 and Ubuntu, at least if they're using an Intel  or another known compatible wireless card ;)

---

### Post by employeeno5 on 2008-04-22
Oh, and thanks again to cousinavi and everyone else who tried to help me with this.
It's appreciated to no end. I'm sorry if I've disappointed you by buying a new card. Those links and other searching and threads lead to only more dead-ends for me though.

I'd prefer in all of this to think that I just missed something obvious, or consistently did something incorrectly. I've been over it so many times in so many different ways though.

Bare in mind that I am by no means a Linux or computer expert. I just love using Ubuntu as my desktop (best computer user experience of my life) and have been really enjoying learning more about Linux and computers in general. Most of the time I'm pretty darn capable, but at the end of the day I'm still very very new. 

It's totally possible I was just being foolish/ignorant about something small.

Goodluck to anyone else with this card in a newer machine. I hope it's just me.

---

### Post by gunashekar on 2008-04-22
these wireless problems (specifically broadcom) had been resolved in Gutsy using restricted drivers and even worked during the early alpha releases of Hardy. Unfortunately it is broken since the past three or four kernel upgrades. It appears that hardy is going to be released without fixing this problem and certain users who have these cards would fell left out.

---

### Post by bnhcomputing on 2008-05-03
Did I read this right?  There is no support for dell wireless in Ubuntu 8.x, but fedora and others do?

---

### Post by Tyler H on 2008-05-07
Yeah pretty much.

I just don't understand how the xp drivers would work with ndiswrapper in 7.10 and not in 8.04

Very frustrating. I haven't been this stressed out for a while, 8 consecutive hours going at this issue.

---

