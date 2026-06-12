---
title: "Trying to install Linux on a very old PC"
date: 2006-08-14
forum: Desktop Environments
---

### Post by sbutton on 2006-08-14
Hello,

I'm trying to install Ubuntu on a PIII 450 MHz, with only 64 Mbytes of RAM. I might consider upgrading the memory, but haven't been able to find anyone who supplies PC100 memory (haven't really looked that hard yet though).

I only need this system to go into my kitchen, so my wife can check her emails / web and perhaps Skype as we have moved our main PC's out to a new office in the garage. 

I even tried the alternate ubuntu image, but that hung during the install. Perhaps I should try again, but harder this time?

So, should I :-

1) Upgrade the RAM and install ubuntu.
2) Install something like Damnsmalllinux 

Any other ideas?

Thanks,

Steve

---

### Post by Titus A Duxass on 2006-08-14
I'd go DSL or Feather.

---

### Post by Diiba on 2006-08-14
I think that DSL could run fine on your computer without ram upgrade if you are installing it not bootting it from ram.

---

### Post by az on 2006-08-14
> **sbutton said:**
> Hello,

I'm trying to install Ubuntu on a PIII 450 MHz, with only 64 Mbytes of RAM. I might consider upgrading the memory, but haven't been able to find anyone who supplies PC100 memory (haven't really looked that hard yet though).


PC133 ram can work for you. It will just run slower.

Get 256 megs or more.

---

### Post by DagonSphere on 2006-08-14
Yes, I would install more ram for Ubuntu.  Maybe try Xubuntu instead -- XFCE requires less memory than Gnome, but i think it'd still be sticky on 64 Megs

I installed Damn Small on a friends computer (500 MHz Celron with 64 Megs) and it runs fine.  If all she's doing is web stuff, and not using anything like OpenOffice or the like, then DSL with 64 megs will work great.  I haven't used Feather.

Be careful, some PC133 is **NOT** backwords compatible with PC100, so be careful with any PC133 you buy.  Here's a good site for RAM, and they have PC100: [www.oempcworld.com](www.oempcworld.com)  I've bought from there before and haven't had any problems.

For clarity, PC133 will not slow down your computer.  PC133 runs faster than PC100, and when the two are mixed, they all run at the slowest speed - PC100 - which is what you have.  PC133 won't hinder the speed of the computer, it just won't run as fast as the chips are capable of.

---

### Post by ardchoille on 2006-08-14
I would install more ram and go with Ubuntu. I run Ubuntu on a PII and it runs fine with Ubuntu, but I run the xfce desktop (xubuntu-desktop) or I use Ubuntu with the fluxbox or WindowMaker window managers. There are some good, light, window managers and desktops. You can find a nice listing at:

[http://www.xwinman.org](http://www.xwinman.org)

Try searching for your memory at [http://www.newegg.com](http://www.newegg.com)

I have always had good experiences with them.

---

### Post by VirtuAlex on 2006-08-14
Search by your pc model, or if it is custom made, by motherboard model. And yes it may be tricky, you can run into troubles sometimes, so buy from sellers who have guarantees. I've spend something around $40 on PC100 256 from memory-up.com, but my compaq recognized only 128. Weird. I called customer service and they exchanged it with PC133 module.

---

### Post by az on 2006-08-14
> **VirtuAlex said:**
> Search by your pc model, or if it is custom made, by motherboard model. And yes it may be tricky, you can run into troubles sometimes, so buy from sellers who have guarantees. I've spend something around $40 on PC100 256 from memory-up.com, but my compaq recognized only 128. Weird. I called customer service and they exchanged it with PC133 module.

Sometimes you need low-density ram and sometimes you just need to switch the order of your ram modules (if you have more than one)

---

### Post by goatflyer on 2006-08-14
Feather is a much more complete distro (IMHO) than DSL which seems to have gone through contortions just to fit in 50MB.

---

### Post by VirtuAlex on 2006-08-15
> **azz said:**
> Sometimes you need low-density ram and sometimes you just need to switch the order of your ram modules (if you have more than one)
I'm not sure what's the low-density ram, but honestly I do not want to know. And believe me I switched these damn modules in every possible way to no avail. I poured chicken blood, beat the drums, and sacrificed the BIOS. It counted new module as 128 no matter what. But anyway, PC133 worked for me. Gnome is not choking any more. I've spend one buck extra on postage to return PC100.

---

### Post by missmoondog on 2006-08-15
that machine would run fine with 256mb's memory. 1 stick of 256 and the one you have will make 320mb's. provided that the 64mb's is just one stick or, depending on how many slots you have in that machine. once the memory is upgraded kubuntu (kde desktop) would run fine on there also. 

i didn't like xfce when i tried it as most of the programs aren't even linked to their corresponding apps correctly.

---

### Post by Lord Illidan on 2006-08-15
I've had DSL live cd work on a school computer 133 mhz, and some 64 mb of RAM. Way to impress your friends, eh...looked bloody cooler than Windows 95!

---

### Post by sbutton on 2006-08-15
Thanks for the replies everybody. I've ordered a 256 Mbyte PC100 stick from OFFTEK, for under £30 ($56 US) that should sort me out.

Not touched Linux much since RedHat 9.1 (and back to 4.1 or something like that) so really looking forward to getting back into it... :razz:  and hopefully getting more machines in my house converted to something more secure and usable than The Other operating system. [-o< 

My next challenges are going to be cramming everything into the 9 Gbyte HDD (should be OK I guess as the distro is on 1 CD and I'm not going to be storing anything/much locally) and adding a wireless network card (already have one) and getting that working. (last resort I could run a ethernet cable -- but this is going to involve drilling a couple of holes in my house and putting the cable down the outside wall!)

Will probably want to do more "stuff" with this machine quite soon and will soon outgrow it.

BTW, does anybody know of a good Voice Chat application (Like Skype) which can stay running / connected ALL THE TIME, but with a Push To Talk feature. I don't want to leave an open Skype call running as that would be annoying, but it seems a pain to have to initiate a Skype call (and get the other end to answer) just to shout something like "There's a parcel for you, can you come and sign" or "would you like tea or coffee?" as my office is a bit too far from the house to use traditional shouting (without computers). Boy, this is a hard thing to explain in a few words... but I've seen it done when working on a trade floor in a bank. (if that helps??) 

Thanks,

Steve

---

### Post by lupine_nickt on 2006-08-15
Getting Xubuntu installed in 64MB of RAM is relatively easy - all you need to do is - as early as possible - to turn swap on.

There's a virtual terminal on F2, so if you go into that just after the installer has finished scanning the CD and loading various modules (right before it tries to set up the network, IIRC). Partition the hard drive using fdisk (if nothing else, just split it into 2 partitions for now - a big one at the beginning, and 256MG-1GB or so at the end for swap; you can then delete the big one in the GUI partitioner that comes later, and set it up as needed). Then write the table to disk, reboot if necessary (it'll tell you), run 'mkswap /dev/hda2' (or whatever the correct partition is), then run 'swapon /dev/hda2'. 

Then you can go back to the installer (F1), and continue as usual.

VoIP applications for linux include linphone and ?kcall? - I prefer linphone - but none of them interoperate with Skype, because it uses proprietary protocols, whereas linphone etc. just use SIP. Skype does have a linux client, however. 

As for the push to call functionality... personally, I'd implement it with a pair of pliers, a button (one of those ones that are 'on' only while you 're pushing them down) and the headset lead... I don't know of an ideal software alternative, although you might be able to do something with the mixer (mute the microphone except when it's needed?).

xF,

...Nick

---

