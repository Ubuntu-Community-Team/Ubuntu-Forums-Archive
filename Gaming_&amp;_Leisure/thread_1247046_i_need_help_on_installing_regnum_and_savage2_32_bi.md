---
title: "i need help on installing regnum and savage2 32 bit"
date: 2009-08-22
forum: Gaming &amp; Leisure
---

### Post by austinmathis on 2009-08-22
can anyone plz help me download and install savage and regnum....savage 2 i have it downloaded i just cant instal it

---

### Post by Perfect Storm on 2009-08-22
Savage 2:
Download the client to your Desktop;

```
mkdir ~/.Games
cd ~/Desktop
chmod +x Savage2Install-2.1.0.1-i686.bin
./Savage2Install-2.1.0.1-i686.bin
```

Troubleshooting; [http://gwos.org/doku.php/guides:64bit:savage_2](http://gwos.org/doku.php/guides:64bit:savage_2) (troubleshooting section)

Note that Savage 2 can't run on intel cards or with ATI Open Source drivers.


Savage 1: [http://gwos.org/doku.php/guides:64bit:savage_1](http://gwos.org/doku.php/guides:64bit:savage_1) (just ignore the "Before Installation" section if you're using 32-bit.

---

### Post by austinmathis on 2009-08-22
umm i have an intel processor wil it still work... oh and i typed in what u gave me and this happened


mkdir: cannot create directory `/home/austin/.Games': File exists
austin@austin-laptop:~$ cd ~/Desktop
austin@austin-laptop:~/Desktop$ chmod +x Savage2Install-2.1.0.1-i686.bin
austin@austin-laptop:~/Desktop$ ./Savage2Install-2.1.0.1-i686.bin

---

### Post by Perfect Storm on 2009-08-22
It's video card I'm reffering to.

The command output looks fine. "mkdir: cannot create directory `/home/austin/.Games': File exists" is nothing to worry about. It means it can't create the directory because it already excisting, therefore it can't create it, logical enough ;)

---

### Post by austinmathis on 2009-08-22
sooo how would i go about installing this so i can play it

---

### Post by Perfect Storm on 2009-08-22
If you followed the command I gave you, it should give you a installation window. You can use the link I gave you to troubleshooting to guide you on how to install it.

---

### Post by austinmathis on 2009-08-22
yea i did the command and all that hapened was the output i gave u

---

### Post by austinmathis on 2009-08-22
hmm idk what graphics card i have could my prolem be that i have an intel card or would it say that

---

### Post by nomnomnom on 2009-08-22
> **austinmathis said:**
> hmm idk what graphics card i have could my prolem be that i have an intel card or would it say that

Are you sure you have an Intel card?

---

### Post by austinmathis on 2009-08-22
no im not sure is there any way i can check

---

### Post by nomnomnom on 2009-08-22
> **austinmathis said:**
> no im not sure is there any way i can check

Type this into terminal;

```
lspci
```

Then paste the output here.

---

### Post by austinmathis on 2009-08-22
K sry for such a late reply my power turned off



lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
austin@austin-laptop:~$

---

### Post by austinmathis on 2009-08-22
i do think i have an intel card 
umm if so thanks for the help nyway....i havent got regnum downloaded yet but im prety sure ima have prolems installing it if i do will u help me??

---

### Post by Vakman on 2009-08-22
> **austinmathis said:**
> i do think i have an intel card 
umm if so thanks for the help nyway....i havent got regnum downloaded yet but im prety sure ima have prolems installing it if i do will u help me??
We will help you with it if you need it.
Also that would not stop Savage 2 from installing so that is not the issue there but you do have Intel graphics so if you did install Savage 2 it will not run.
Also have not viewed this video but it may help you.
[http://www.youtube.com/watch?v=0G7SFYjZsJM](http://www.youtube.com/watch?v=0G7SFYjZsJM)
It is a video tutorial of how to install Regnum Online on Linux.

---

### Post by austinmathis on 2009-08-22
oh thank u for the video but it dosent give me the option to open with archive manager hmm im going to try to download it one more time

---

### Post by nomnomnom on 2009-08-22
> **austinmathis said:**
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
$

You do have an Intel graphics chipset. There is no point in you installing Savage 2, your Intel graphics cannot handle that game.

Sorry...

---

### Post by austinmathis on 2009-08-22
ok thank

---

### Post by austinmathis on 2009-08-22
thank u

---

### Post by austinmathis on 2009-08-22
ik i just installed it but i got this message when i loged in....Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version....
i know my video card isnt to old because when i had windows on this computer regnum worked........
i havent installed any video card drivers and i know i had to do a bunch of stuff to get my wireless card working any drivers i can install if so how
direct x can i even install direct x natively on ubuntu?? if so how??

---

### Post by Vakman on 2009-08-22
> **austinmathis said:**
> ik i just installed it but i got this message when i loged in....Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version....
i know my video card isnt to old because when i had windows on this computer regnum worked........
i havent installed any video card drivers and i know i had to do a bunch of stuff to get my wireless card working any drivers i can install if so how
direct x can i even install direct x natively on ubuntu?? if so how??
Regnum or Savage 2, you can't do Savage 2 so you do mean Regnum correct?

---

### Post by austinmathis on 2009-08-22
yea i mean regnum

---

### Post by austinmathis on 2009-08-23
are there ny dirvers i can install for my graphics card because when i changed over to ubuntu i had to do lots of stuff to get my wireless card working

---

### Post by nomnomnom on 2009-08-23
> **austinmathis said:**
> are there ny dirvers i can install for my graphics card because when i changed over to ubuntu i had to do lots of stuff to get my wireless card working

The Intel drivers are built into Ubuntu, you don't need to download anything. But they seem to suck, so you're kind of screwed anyway.

Again *sorry*.

---

### Post by Perfect Storm on 2009-08-23
Well you can check if xf86-video-intel is still installed.

Other than that don't expect much with that onboard video card. Intel is lousy for gaming and are build for office purpose, let alone that th Linux driver for intel is lousier than its windows counterparts.

---

### Post by austinmathis on 2009-08-23
ive played it on this computer when i had windows

---

### Post by nomnomnom on 2009-08-23
Yes but as I have recently just found out, Intel has much better drivers for Windows than it does for Linux. I have no real experience of Intel drivers myself, but I have been considering getting an Intel GMA950 based mini PC and have read up a lot about this issue. They seem to suck nearly as much as the open source ATi drivers, only they aren't as slow...... :(

---

### Post by austinmathis on 2009-08-23
oh rly?? im getting a dell mini with i think the same card but im going to  be running windows....my computer as of now is just going to keep ubuntu

---

### Post by austinmathis on 2009-08-23
are there ny mmorpgs that i can play....ima mmo junkie....i need a mmo

---

### Post by nomnomnom on 2009-08-23
On an Intel chip I don't know... :(

---

### Post by austinmathis on 2009-08-23
2d mmos would work if u know ny that would be awsem....if not thats fyne thatks alot 4 the help

---

### Post by nomnomnom on 2009-08-23
> **austinmathis said:**
> 2d mmos would work if u know ny that would be awsem....if not thats fyne thatks alot 4 the help

Yeah there are some but I don't play them. Try creating a new thread asking that question and some random nerds will appear and post replies.... :P

---

### Post by austinmathis on 2009-08-23
sweet thanks again man:popcorn: and yes that is popcorn smilie face whi idk :popcorn::popcorn::popcorn::popcorn:

---

