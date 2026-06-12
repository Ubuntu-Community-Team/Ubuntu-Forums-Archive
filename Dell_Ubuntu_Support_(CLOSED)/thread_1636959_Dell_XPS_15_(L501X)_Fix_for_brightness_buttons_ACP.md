---
title: "Dell XPS 15 (L501X) Fix for brightness buttons ACPI errors"
date: 2010-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by krunalpatel on 2010-12-03
If your laptop is giving ACPI Brightness error when you press F4 and F5 to higher/lower your brightness and you get no response (Ubuntu 10.10 Maverick) then do the following:

sudo add-apt-repository ppa:kamalmostafa/linux-kamal-mjgbacklight
sudo apt-get update

Then add the updates that show up in Update Manager

Then edit your Grub and add these kernel parameter:

sudo gedit /etc/default/grub

add: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"

(that line should already be there..just edit it)

run: sudo update-grub

Reboot > and your brightness levels should work

---

### Post by nouknouk on 2010-12-05
EDIT: Initially posted [at the wrong place]("http://ubuntuforums.org/showpost.php?p=10203539&postcount=33"). Sorry.

---

### Post by anirudhranganath on 2010-12-08
Hey! this patch doesnt work for me! Did you install any additional drivers? I did not install nvidia drivers. 

When i press Fn+F4/F5, the progress/control shows up on the screen, but stays at max level always. Reducing brightness reduces it by a small amount, before it returns to full brightness. It was in this state even before I applied the patch.

If its of any help, i shall paste my lspci output: 

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
02:00.0 VGA compatible controller: nVidia Corporation Device 0df1 (rev a1)
02:00.1 Audio device: nVidia Corporation Device 0bea (rev a1)
04:00.0 Network controller: Intel Corporation Centrino Advanced-N 6200 (rev 35)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)

```

---

### Post by richcocoa on 2010-12-08
Hey do you think this fix will work on other dell laptops, specifically an Inspison N-4010? I have the same issues as you have mentioned.

Could you also tell me what you have done with the kernel? have you compiled some upstream version that has added this functionality, or have you made a modified kernel? If you have indeed made a custom version of the kernel, do you intend to maintain it?

I ask this because I don't know what to do (a kernel simply is a very important part of the OS, right? So I didn't want to do anything without understanding what I will be doing).

Thank you

---

### Post by krunalpatel on 2010-12-08
I installed updates provided by a conanical ubuntu tech. So far it works. Just follow the instructions and see what u get.

---

### Post by fjgaude on 2010-12-08
I can't say how many or what brands use the Intel GMA500 chipset but here's the site to watch for the good news:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

Have fun!

---

### Post by richcocoa on 2010-12-09
> **krunalpatel said:**
> I installed updates provided by a conanical ubuntu tech. So far it works. Just follow the instructions and see what u get.

I tried the kernel out and it works like a charm. Thanks for taking the trouble to make it available to all of us.

and I am using a Dell Inspiron N4010 laptop. So I guess it may be applicable to other as well. What are your thoughts?

---

### Post by krunalpatel on 2010-12-09
No problem fellas. You do have to have intel i915 chipset to work

---

### Post by CottonCandy on 2010-12-10
I also have a dell inspiron & this fix worked for me too! :D

---

### Post by Gnaural on 2010-12-26
Thanks so much, [krunalpatel]("http://ubuntuforums.org/member.php?u=1185515"), this worked like a charm on an out-of-the-box Dell Studio 15z (s15z-2249CPN) with a fresh 64-bit Ubuntu 10.10 install :D

---

### Post by iammeagain on 2011-03-09
Thanks a bunch for this. :D 
It allows me to get lower brightness than windows. Which is awesome.

It does flash the brightest setting each time I lower the brightness ones step. With the lights off it looks like a strobe light. Also is there a way to go ahead and make it less steps? I'm not too picky about having exact brightness. If it just had a 1%, 30%,60%,90%,100% would be fine. But this has like 5% increments it feels like.

...Now to get this nvidia to turn off and stop draining my battery.
I think I figured it out, thought I would share: [http://ubuntuforums.org/showthread.php?p=10540069#post10540069](http://ubuntuforums.org/showthread.php?p=10540069#post10540069)

---

### Post by T3Ra on 2011-03-11
Thanks a lot krunalpatel for the fix ....

Well I +1 the strode light feel :P ... I dont really know if thats any major issue but for sure the flickers dont look very pretty..

Also if you have the "dim on idle"(Power Management) option on... the screen brightness doesnt come back to normal!

---

### Post by iammeagain on 2011-03-12
I am able to press the customizable button (touch sensitive along the top row, same row as power button) on my laptop to dim the display as well. That one doesn't give me the strobe attack when dimming. Although I'd like the correct button to work.

---

### Post by Aralhach on 2011-04-07
Hey everybody!! I've been having this problem too. I got my laptop (a Dell XPS 15) about a month ago, and put Ubuntu on it (dual-boot).  I had a sound problem but fixed it with the ALSA upgrade thing, but the brightness is still not working... 

I tried the solution posted here but when I added the repository it was down.  I mean, it couldn't find it when I updated and there were no new updates provided when I added it so I'm kinda stumped on what to do here...

I'd appreciate it if you could help me because Ubuntu really drains my battery when I use it (it's like one of the previous guys said, it'll only go down a little bit but not more, it's like it gets stuck there or something).

---

### Post by iammeagain on 2011-04-10
I was able to lower my brightness by tapping the touch sensitive buttons on the top row, same row as your power button. I forget which one, but one of them lowered the brightness for me. I think its the one you can custom set in Windows. That may work as a temporary fix for you.

I'm not sure why the repository is down. I'm only semi decent on Linux, so I'm not sure if someone could upload the needed files in some way if they have already used this? I hope someone can chime in on that.

---

### Post by AcceptedAnarchy on 2011-04-12
Thanks Buddy... works like a charm

---

### Post by bethnard on 2011-10-29
This fix was perfect for me on 11.04. But I have upgraded to 11.10 and the buttons just won't work anymore. I can manually reduce the brightness, but the hotkeys aren't working anymore. Also, the screen won't dim as used to do on 11.04.

Any ideas of how to fix this?

EDIT: The customizable touchsensitive hotkey is working very well to reduce brightness. The hotkey to increase brightness works with double action (example: it increases 10% of brightness while the touch sensitive decreases only 5%). The hotkey to reduce brightness is completely messed.

---

### Post by Ju4n on 2011-11-11
> **bethnard said:**
> This fix was perfect for me on 11.04. But I have upgraded to 11.10 and the buttons just won't work anymore. I can manually reduce the brightness, but the hotkeys aren't working anymore. Also, the screen won't dim as used to do on 11.04.

Any ideas of how to fix this?

EDIT: The customizable touchsensitive hotkey is working very well to reduce brightness. The hotkey to increase brightness works with double action (example: it increases 10% of brightness while the touch sensitive decreases only 5%). The hotkey to reduce brightness is completely messed.

exactly the same here, have you tried doing the same? because I haven't.

---

