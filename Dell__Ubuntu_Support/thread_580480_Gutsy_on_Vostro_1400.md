---
title: "Gutsy on Vostro 1400"
date: 2007-10-18
forum: Dell  Ubuntu Support
---

### Post by kamaboko on 2007-10-18
I just gave this a shot.  Got the 64bit version and got  a resounding no go.  It all fell apart during the boot scripts: fail, fail, fail, etc.

---

### Post by aldenhg on 2007-10-19
Was that a fresh install or an upgrade?

---

### Post by jasonlfunk on 2007-10-19
I just installed the 32 bit version. It's working much better then Feisty out of the box (meaning that it actually installed) but my sound isn't working. And my wireless seems pretty shotty, it works but goes and drops connections occassionally. I haven't determined if it is Gutsy or my laptop yet.

---

### Post by kamaboko on 2007-10-19
> **aldenhg said:**
> Was that a fresh install or an upgrade?

it was a fresh install.

since this post i was able to get the live cd to work, but i had no inet connection and the sound didn't work.  aside from this gutsy looks good.  i'd like to get this on the laptop. will need input on the following though:

1. geforce 8400m gs
2. Dell Wireless 1390 802.11g Wi-Fi Mini Card (i believe it's a broadcom)
3. sigma audio

---

### Post by aldenhg on 2007-10-20
You'll proabably need to go through a lot of the same stuff that you have to go through when installing Feisty on the 1400. Keep in mind that the Vostro 1400 and the Inspiron 1420 are the same computer and therefore you can use the same tutorials.
Dell has said that they'll be supplying their own Gutsy isos for the Ubuntu-on-Dell folks, so you might consider waiting for them to delve any deeper. They'll be availiable some time soon. Check [here]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10") for updates.

---

### Post by kamaboko on 2007-10-21
I'm going to sit on the fense for a while on this one.  I got Gusty installed but it was acting really weird.  For instance, each rebot would change my Compiz settings.  For instance, the "wiggle" feature would go and I'd get "blur" in place of it.  Huh????  Weird.  Also, the restricted repository for the Wifi would have to be installed after each reboot.  It would show that it was installed, but it was functionless, so I'd have to uninstall it, and reinstall to get the Wifi to work.  Nah...I'll wait.

---

### Post by ashub on 2007-10-22
Thanks for these posts on vostro 1400. Dell will deliver my Vostro 1400 in a week. It comes with Intel Integrated Graphics X3100, Dell Wireless 1390 802.11g Mini Card and Dell webcam. 
I am very new to the Ubuntu world, and want Fiesty or Gusty to coexist with Vista on my laptop when it arrives. Please help me with the following questions:
1. Should I install 7.04 or 7.10? 
2. If it is 7.04, should I just use the Ubuntu distribution for Inspiron 1420 on dell's website?
3. Will I get to try any of these distributions through a LiveCD before installation. Do the .iso files include the LiveCD?
4. Can I virtualize Ubuntu over Vista? Which VM should I use? Microsoft has VPC2007, I dont think VMWare has a virtual machine for Vista yet.

A typical problem I have seen people talk about on Vostro 1400 is the sound problem, will the dell ubuntu 7.04 for 1420 work out of the box without these problems? What about Intel integrated graphics, wireless and ethernet? 

I am hoping, that Ubuntu install is as easy as popping in a CD and seeing drivers work out of the box. Is that a realistic expectation?

---

### Post by supaman2slick on 2007-10-23
Mostly working for me. I'm on a vostro 1400 with nvidia 8400gs and the hd audio thing. Tried the 64-bit version and it wouldn't even boot fully. Popped in the 32bit and it ran all the way through. I managed to get compiz-fusion working and even AWN. The only thing that doesnt work is the sound. I've tried a few things here and there and no luck. I also have the integrated webcam, but I don't think it works. 

I hope dell comes out with their disc soon.....

---

### Post by BlenderBoy on 2007-10-24
I was able to install Gutsy on a Vostro 1400, nVidia 8400M GS, Intel 3945 WiFi, SigmaTel audio (no speakers yet, only headphones); but I had to use the ALTERNATE CD. After setup Ubuntu booted and launched X, but it was in low-graphics mode until I enabled restricted drivers (a pop-up from the top panel on first time boot; or otherwise, go to System -> Administration -> Restricted Drivers Manager). There was no need to download the drivers from nVidia.

However, I must mention that there appears to be a bug with DNS in Gutsy, please go to [http://ubuntuforums.org/showthread.php?t=581055](http://ubuntuforums.org/showthread.php?t=581055) for more info.

FYI: I got the speakers to work by adding the following to /etc/modprobe.d/alsa-base: options snd-hda-intel model=5stack

I hear options snd-hda-intel model=3stack works too (but I haven't tried it).

---

### Post by Mishok on 2007-10-24
Has anyone got the wifi problem sorted out?  I used the generic Firmware for Bbroadcom 43xx chipset. The card detects all the networks i need, but connecting to them is another story. I select a particular network and nothing happens. The connecting-to-the-network animation starts off but never ends, and  I never get connected to any wireless networks.

---

### Post by aldenhg on 2007-10-24
Yeah, that driver doesn't work so well. I'm guesssing you have the Dell 1390 wifi card wich there are no native drivers for. Sucks, huh? Don't despair, there are plenty of ways to get it working. 
You'll proabably want to use ndiswrapper. Without getting too techie on you, ndiswrapper takes the Windows driver for you wifi card and beats it until it works with Linux. Well, it doesn't *beat* it per say, but it does make it work with Linux, albeit with functionality that is slightly reduced from full-fledged native drivers. You probably won't notice the reduction unless you want to do some wardriving or network cracking. Anyhow, check out [this]("http://ubuntuforums.org/showthread.php?t=405990&highlight=1390+ndiswrapper") thread for all the instructions. I think there's even a neato installer that does all the command line stuff for you.

---

### Post by nutrapi on 2007-10-25
I have the same vostro 1400. I got mine with the t7300 intel, the intel wireless, and I took out one of my 512mb sticks and replaced it with a 2gb stick.

Needless to say I had absolutely no problems loading up 7.10. The biggest problem was getting audio to work. I was able to do this:
"
To get sound working on the Sigmatel STAC9228 included with the new Inspirons, add the line:

```

options snd-hda-intel model=3stack

```
to the /etc/modprobe.d/alsa-base
"

I found this in[ another post]("http://ubuntuforums.org/showthread.php?t=499430&highlight=stac9228"). If it works, thank DaveTRG :-)

---

### Post by SkinnyC on 2007-10-25
Awesome - worked perfectly. Thanks nutrapi

Edit: thanks DaveTRG also :)

---

### Post by muadnu on 2007-10-25
I tried the 64 bit version and it is working fine. I only had to mess with the video for the Nvidia card and use the trick to get sound working. Suspend/hibernate worked using the same tricks as for feisty.

I still have some little problems. I get no splash screen when booting up, and sometimes it takes really long to boot (some times it doesn't). And I can't get my mic to work (though couldn't get it on feisty either). Also, I can't get the sound to work when I log out (though it's not very relevant).

---

