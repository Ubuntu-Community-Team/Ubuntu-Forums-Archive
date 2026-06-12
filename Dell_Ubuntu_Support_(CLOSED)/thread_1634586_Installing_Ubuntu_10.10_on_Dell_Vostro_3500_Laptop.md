---
title: "Installing Ubuntu 10.10 on Dell Vostro 3500 Laptop"
date: 2010-11-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Samsagax on 2010-11-30
Well i got my notebook a few days ago. I was excited for the time i bought it and waited very impatient it's arrival, i live in Argentina and the delay was about 20 days... actually it was 26.

When i was waiting for it (her, she is my little baby now ;P) was planning the installation of Ubuntu as the first thing to do so i'm gonna tell you my experience and how I got a totally functional (almost, still couldn't get the fingerprint reader to work, no driver) Dell Vostro 3500.

**[SIZE=3]Fist things first:[/SIZE]** Get a copy of Ubuntu :) (If you didn't allready)

[B][SIZE=3]Getting rid of W$7

[/SIZE][/B][SIZE=3][SIZE=2]The first thing is to get the following:
[/SIZE][/SIZE]

[LIST=1]
[*]The Windows Installer disc shipped with the pc.
[*]A connection to the internet. (if you want to recover your win7 to it's factory state)
[/LIST]

Ok, now insert the Installer DVD in the drive and restart the machine. You must press F12 for boot options at startup, or change the Boot Priority in the BIOS (Press F2 on startup to enter BIOS).
Ok you should enter the Win7 setup. Follow the steps and in the Partitions screen ERASE the partition of your OS (DIE DIE DIE).

[SIZE=4][COLOR=DarkRed]WARNING!:[/COLOR][/SIZE][COLOR=DarkRed]Do NOT erase partitions named OEM and RECOVERY. The first one the Setup won't let you but the second is vital for getting the win7 as it came from factory.[/COLOR]

Then create a new partition named OS and assign it the size you want. Install Windows on that partition.
Reboot and follow the directions to get to the desktop. When you are there go to the internet to [www.dell.com]("http://www.dell.com") and download the Recovery Software (I did this cos is faster than installing every driver from the resource CD, and it didn't had the drivers for my pc either!!!). Run the Recovery Software and if you made things right (e.i. you didn't erased the RECOVERY partition) you will be able to Recover the Factory Configuration as directed by the application. 

[SIZE=4][COLOR=DarkRed]WARNING!:[/COLOR][/SIZE][COLOR=DarkRed]Do  NOT turn off the machine during this process, will take a little time but is necessary to be completed.[/COLOR]

**[SIZE=3][COLOR=Black]Installing Ubuntu[/COLOR][/SIZE]**

Ok. Here we go! Put the Ubuntu LiveCD in your CD drive and run Install. In the partition dialog get an exchange partition of two times the size of your ram memory (i didn't do that, i got 4 Gb in that partition, i hope that won't be a problem, but the recommendation can apply). The set up a partition for Ubuntu and set it to build on "/".

From this point is very straight forward. The Install will proceed and you will get an Ubuntu OS fully operational out of the box.

A little piece of advice (for now at least): The Nvidia official driver still doesn't work. It doesn't recognize the monitor and you won't be able to boot into the Desktop. I'm still waiting for the new release from Nvidia, but for now i could get all functionality from my GPU with nouveau (I still didn't load complicated graphics, but the animations on the desktop worked extremely fine with no lags).

Ok guys thank you for reading my experience and I hope this will help others. Any questions are welcome.

PS: Sorry about my English, i think is not good enough...

[B][SIZE=3]The Machine (La Máquina)

[IMG]http://laptoping.com/wp-content/032010/Dell%20Vostro%203500.jpg[/IMG]

[SIZE=2]Specs:[/SIZE][/SIZE][/B][SIZE=3][SIZE=2]

Processor: Intel Core i5-460M (2.53GHz, TurboBoost 2.8GHz, 3Mb cache)
RAM: 4 Gb DDR3
HD: 500 Gb[/SIZE][/SIZE]
Video: Nvidia GeForce 310M, 512Mb; Intel HD
The rest in: [www.dell.com]("http://www.dell.com")

---

### Post by caralb on 2010-12-15
Que tal Samsagax,

I'm from Argentina too, and I'm considering buying the Vostro 3500 with Intel i5, 320 Gb Hard Disk and 3 Gb RAM. I really like it, but I've read some reviews where they report about some temperature, cooling and noise problems. I just wanted to ask you if you have experienced some of these problems, because I like Dell but they made me afraid. Is the mate screen OK ?

Thanks in advance for your help. By the way, I'm also planning to installl Ubuntu on it for my FPGA/simulation/electronics work, so you will have a colleague for dealing with drivers, etc ;)

Saludos!

---

### Post by Samsagax on 2010-12-16
Encantado caralb!

Well as I'm supposed to write in English, I will. 

The issue with temperature is true, but is not as "problematic" as you (and me too) had read. The right, center and mid portion of the computer heats, but is not so terrible, just about a 37/38° C. The pc gets loud whenever you run a lot, but i men it, A LOT! of processes at once, there is a reason for that: Power equals heat, speed equals power, do the math. This added to the relative small space in a laptop, is expected to rise a little temperature. As long as you use a side mouse and not the pad mouse you will be confortable and won't notice the heat.
The noise is not an issue either, it happens in the same conditions as above. The fans start running at full capacity to ensure you don't fry your processor. Isn't louder than a desk pc.
The screen is AWESOME, yeah, probably there are better ones but this does not reflect anything and the quality is great, the only "problem" is the angle you see it, will distort colors about a 30° angle up and down but does not distort in right-left angles.

The only drivers with issues are the video driver (still couldn't make nVidia driver to work, but nouveau works fine so far) and the fingerprint reader (comes in handy to write passwords), ill try to work on that.

I'm running side by side a win7 pro for "backup" in games mostly but I've entered 3 or 4 times since I bought this pc.

I have no complains about the service of dell in Argentina, they do exactly as they say. Try to find an offer with free delivery (the one i got) and put that money to a better RAM and HD specs. They are worth it.

Espero haber contestado tu pregunta, cualqueir cosa me mandas un mp acá.

Éxitos!

---

### Post by freechelmi on 2010-12-22
hello Samsagax , thanks for those info. How much did you pay ? Did you have an option to get it without windows?

---

### Post by Samsagax on 2010-12-23
> **freechelmi said:**
> hello Samsagax , thanks for those info. How much did you pay ? Did you have an option to get it without windows?

In my case I paid an offer from Dell with free shipping (that's a lot for my country). Total cost was about 1200 U$S. The same laptop here cost about 1350 U$S but that depends on market and moment. 

Unfortunately this laptop does not come withe the option of another OS than Window$, but it comes with the 64bit Pro edition so thats "OK"... I don't have any idea on how much this will cost without Win7 but an Asus K52JC (the other candidate) was sold with FreeDOS (No OS) but the shipping was expensive. 
Eitherway i kinda "need" Win7 for my design programs (Solidworks and that kind) so I'm dual booting with it (I think I've entered 3 times to win7).

Hope I answered your questions. I'm looking forward for a solution to hybrid cards and nVidia drivers on this laptop (still does not work :() but nouveau is good enough so far.

---

### Post by freechelmi on 2010-12-23
> **Samsagax said:**
> 

Hope I answered your questions. 

Thanks for your answers, so Core I5 , 500G 4G , + Nvidia = 1300$ .

That's quite a lot of money in my mind. 

How much is shipping to argentina usually from Dell ? 50$ maybe More?

---

### Post by Samsagax on 2010-12-23
> **freechelmi said:**
> Thanks for your answers, so Core I5 , 500G 4G , + Nvidia = 1300$ .

That's quite a lot of money in my mind. 

How much is shipping to argentina usually from Dell ? 50$ maybe More?

Try to cantact dell directly, here in argentina the importers want their share on the price and ussually is very high. The laptop cost 1200 and is the best price i could get (with shipping to my house door, some crapware installed and 1 year guaranty and IT service)

---

### Post by fnatter on 2010-12-24
hello Samsagax,

first of all thanks very much for your post, it is very helpful to me.

I have a vostro 3500 running debian lenny IA32, which works fine except
I need the VESA driver for X to work. I think the commercial NVIDIA
driver could be helpful for tuning the graphics card so that the notebook
does not heat up so much?
=> that's why I want to switch to ubuntu.

My experience with the current nvidia driver is that X only boots in very low
resolution showing only part of the screen. What kind of problem do you have
with the commercial nvidia driver?

The GeForce 310M is said to be supported by the current driver:
  [http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html](http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html)
=> does this still not work for you?

Do you know whether the commercial nvidia driver allows to make use of the HDMI or VGA
output under Ubuntu? Or is that even supported by nouveau?

How about 32bit vs 64bit? Should I prefer 64bit?

Final Question: how about suspend to ram / suspend to disk? Does that work with Ubuntu? Under Debian Lenny, suspend to ram hardly works while suspend to disk
works most of the time (but sometimes it doesn't come back up again, probably
due to the webcam driver).

Thanks and I wish you a merry christmas!

---

### Post by Samsagax on 2010-12-24
> The GeForce 310M is said to be supported by the current driver:
  [http://www.nvidia.com/object/linux-d...29-driver.html]("http://www.nvidia.com/object/linux-display-ia32-260.19.29-driver.html")
=> does this still not work for you?

The official nVidia driver does not work. But i think is an X issue cos either the X server or the graphics card does not recognizes the screen.
The nouveau driver provides support for the HDMI (tested it myself ;)) and for 3 screens (YEAH!!), the maximum you probably plug to your laptop and works very good.
The fingerprint reader still does not has a driver but thats just luxury ;) 
The suspend works, but hibernate is slower that turning off and on again te pc, but be careful in one thing: if you change the devices pluged to your pc after you suspend, the X server wont be up and you'll have to restart gdm (probe issue?).

> How about 32bit vs 64bit? Should I prefer 64bit?
Im running 64bit Ubuntu 10.10, i have 4gb ram, if you have 3gb don't know if it worth it, but the OS only works with 600mb in the 64bit version (win7 works with 2gb all-time busy ram, $h...t).

Ok i hope i've answered your questions and if you get the nVidia driver to work please let me know.

---

### Post by ajcsm on 2011-03-15
For noise problem, you can install i8kutils, this lowers the rpm to 2800 (aprox), and the noise is substantially reduced.

---

### Post by Argard on 2011-04-05
Anyone here successful enabled the bluetooth device of vostro 3500 on ubuntu? Please, let me know how.

Thanks in advance :)

---

### Post by Samsagax on 2011-04-05
> **Argard said:**
> Anyone here successful enabled the bluetooth device of vostro 3500 on ubuntu? Please, let me know how.

Thanks in advance :)

I had. Works out-of-the-box in my laptop with Maverick and I use it on daily basis, wireless lan needs Broadcom proprietary driver. In Natty, both wi-fi and bluetooth worked out-of-the-box.

Probably enabling Broadcom proprietary driver will work.

Tell me wich kernel and firmware are you using?

---

### Post by Argard on 2011-04-06
> **Samsagax said:**
> I had. Works out-of-the-box in my laptop with Maverick and I use it on daily basis, wireless lan needs Broadcom proprietary driver. In Natty, both wi-fi and bluetooth worked out-of-the-box.

Probably enabling Broadcom proprietary driver will work.

Tell me wich kernel and firmware are you using?

Thanks for your answer!

I already installed the proprietary drivers and it kept not working. 

lsusb: Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

Kernel: Linux 2.6.35-22-generic x86_64

Device firmware: I don't know how to extract this information.

I will do an kernel update now and later I make a post here to tell the results..

Tks in advance :)

---

### Post by Samsagax on 2011-04-06
It's odd, in my case it worked from the live session.

Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

I've got the same hardware. Here is a tip. Did you turned wireless off in Win7? Seemes that if you turn something off in one OS then the other OS does not recognize it. At least with bluetooth works that way. As long as the wireless is part of the same hardware it should work the same way.

---

### Post by Argard on 2011-04-07
> **Samsagax said:**
> It's odd, in my case it worked from the live session.

Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)

I've got the same hardware. Here is a tip. Did you turned wireless off in Win7? Seemes that if you turn something off in one OS then the other OS does not recognize it. At least with bluetooth works that way. As long as the wireless is part of the same hardware it should work the same way.

Very interesting point, I really turned off my bluetooth on windows, I will restart my computer with windows 7 and set it on and try access again. I will post the result... 

But if this works it will be a very weird issue... :o

---

### Post by Argard on 2011-04-07
> **Argard said:**
> Very interesting point, I really turned off my bluetooth on windows, I will restart my computer with windows 7 and set it on and try access again. I will post the result... 

But if this works it will be a very weird issue... :o

It works! Thanks Samsagax :)
 
It must be activated on windows to work on linux ... this is a big weird behavior!

---

### Post by Samsagax on 2011-04-07
> **Argard said:**
> It works! Thanks Samsagax :)
 
It must be activated on windows to work on linux ... this is a big weird behavior!


Works that way. I think is related with the OS touching things in the BIOS. If you turn off wireless/bluetooth in linux you wont see it on Win7 either.

---

### Post by Argard on 2011-04-07
> **Samsagax said:**
> Works that way. I think is related with the OS touching things in the BIOS. If you turn off wireless/bluetooth in linux you wont see it on Win7 either.

Yes, I thought the same thing and I will not turn it off anymore.

---

### Post by bingotailspin on 2011-04-27
This laptop has the new Nvidia + Intel hybrid graphics card which is not supported on linux.  This means to get to run your awesome nvidia card and produce heat/drain your battery, but you don't get to use it!  You only get the Intel card with some low resolution.  I hate Dell anymore.

There is suppose to be a way to turn off hybrid graphics in the BIOS, but I don't have it.  I talked with Dell and they said I don't have this BIOS option because I installed linux.  That doesn't make sense.  :confused:

---

### Post by kinggo on 2011-04-27
That's why I picked the one with only intel HD.

**@ Samsagax** I've noticed that you raised a bug about wireless led. I had the same problem and then I found your bug report in which you mention that it worked with maverick. So I tried maverick live CD and I installed STA driver and the led came on. And now it works 64bit natty also. I restarted it a couple times already and it still works. 
But what about those notification lights near audio jacks? Mine doesn't turn on. And I don't want to install windows just to try that. I even bought model without windows since I'm not planing using them. Do they work on your machine?

---

### Post by Samsagax on 2011-04-27
> **bingotailspin said:**
> This laptop has the new Nvidia + Intel hybrid graphics card which is not supported on linux.  This means to get to run your awesome nvidia card and produce heat/drain your battery, but you don't get to use it!  You only get the Intel card with some low resolution.  I hate Dell anymore.

There is suppose to be a way to turn off hybrid graphics in the BIOS, but I don't have it.  I talked with Dell and they said I don't have this BIOS option because I installed linux.  That doesn't make sense.  :confused:
That's does not make ANY sense. Linux does not touch the BIOS. Whoever told you so, really don't know what he/she is talking about. Mine doesn't came with a switch IGC off option in the BIOS. But thats a Dell fault. I have a working Win7 partition where nVidia card does work as supposed to. We must call Dell to have a BIOS update with a "compatibility mode" to select hybrid mode or nvidia-only mode. I will make this call tomorrow if I have the chance.

There are indeed some methods to turn off the nVidia card. I'm running with nVidia on but the screen is rendered by the IGC only, works fine in the desktop and some games, but i have a hot useless brick under my keyboard...

Take a look at this awesome group. [http://launchpad.net/~hybrid-graphics-linux](http://launchpad.net/~hybrid-graphics-linux)

They are trying their best to make hybrid graphics run on linux. The PRIME project is also being looked after and any code you may add gets us a step closer to the answer. Even if you don't code, you must post your machine in there, and try some tests.

Hybrid graphics are a rule now in laptops and is mandatory to get this working under linux or our community will loose (not gain i mean) a lot of users. I was unaware of this laptop containing two video cards, but i love linux and the machine works really smooth under linux, even more than window$.

@kingoo Thanks for the update on that issue. I'll test it tonight and report back. That was almost the only thing that was turning em down on upgrading to Natty. Is the wireless hot-switch causing freezes already?
The two leds on the right of the wireless hard-switch are one for the POWER led (it tells you if your machine is on, and blinks slowly if it is suspended), I would be really concerned if that does not turn on; the other is for battery state, this laptop has a really good feature: you can choose not to charge the battery when the AC plug is attached, really useful for short periods of AC plug, would increase the battery lifetime. Also, the battery won't charge from hardware if it has more than 80% of it's capacity when the AC is plugged-in.

---

### Post by kinggo on 2011-04-28
I talked with a guy and service center and he told me to bring it in. So I will next week. 
And one other question, does your card reader works? Mine doesn't. I think it's not even detected by the system.

---

### Post by Samsagax on 2011-04-28
> **kinggo said:**
> I talked with a guy and service center and he told me to bring it in. So I will next week. 
And one other question, does your card reader works? Mine doesn't. I think it's not even detected by the system.

It works fine for me.

---

### Post by kinggo on 2011-04-29
Well, I'll have to check that to. :(

According to this
[IMG]http://support.dell.com/support/edocs/systems/vos3500/en/SM/art/ECC_2.jpg[/IMG]
it must be something with that cable. No status lights, no working card reader and no working express card. And all is on the same board connected wit the same cable.

edit: yes, cable was disconnected :roll:

---

### Post by Samsagax on 2011-06-03
Well, good news. We now are able to actually use the Nvidia card on our beloved Vostros.

Check Martin Juhl's Bumblebee and try it. It worked for me on ArchLinux.

---

### Post by fnatter on 2011-06-04
> **Samsagax said:**
> The official nVidia driver does not work. But i think is an X issue cos either the X server or the graphics card does not recognizes the screen.
The nouveau driver provides support for the HDMI (tested it myself ;)) and for 3 screens (YEAH!!), the maximum you probably plug to your laptop and works very good.


hello Samsagax,

thanks for the answers!

I am about to reinstall my Vostro 3500 with Debian Squeeze (current stable debian).
Therefore, I downloaded a live cd for exactly that distro which comes with
nouveau 0.0.15 in a default config (seems like no xorg.conf, but uses nouveau, by probing as can be seen in the X log).

This works fine except that a monitor attached via HDMI is not recognized in GNOME.
Which version of nouveau did you use? Will an upgrade to 0.0.16 help?
Did you configure anything in xorg.conf to be able to use the HDMI port?

(I don't have the hybrid card, just the GeForce 310M)

Thanks a lot!

---

### Post by fnatter on 2011-06-12
Now the HDMI output (graphics, sound not tested) works for me with Debian Testing 2011-06-08,
and the nouveau driver 0.0.16:
ii  xserver-xorg-video-nouveau               1:0.0.16+git20110411+8378443-1+b1

I'm not sure whether it works with Debian squeeze as it didn't work from the squeeze live cd.

---

### Post by fnatter on 2011-12-08
hi,

with the current 3.x kernels, there is a new Open Source WLAN driver for the Broadcom BCM 43224 (aka Dell 1520):
[http://wiki.debian.org/brcm80211](http://wiki.debian.org/brcm80211)
which works for my Vostro 3500 on Debian testing (wheezy).

---

### Post by bobik314 on 2012-03-09
Hello, I'm a new one to this forum and.. I'm using Debian. Sorry ;)

I have one question for people who use Ubuntu on Vostro 3555. Is suspend/resume working on your system?

---

