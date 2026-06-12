---
title: "elementaryOS won't let me use my external keyboard"
date: 2014-03-24
forum: Debian
---

### Post by noxit2 on 2014-03-24
[COLOR=#000000][FONT=Consolas]Hi guys, 

I'm totally new to Linux and just installed elementary OS on my Laptop, but I have one problem:
My external usb keyboard doesn't work. I'm typing with my laptop keyboard right now, which works fine. I searched around the internet and I found this lsusb command to check if my keyboard is being recognized by the system and it is! Here's the code (the bold entry is my keyboard):

[/FONT][/COLOR]```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 008: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 003 Device 003: ID 04f2:b35f Chicony Electronics Co., Ltd 
Bus 003 Device 009: ID 1bcf:0005 Sunplus Innovation Technology Inc. 
**Bus 003 Device 012: ID 04d9:a055 Holtek Semiconductor, Inc. **
Bus 003 Device 011: ID 1058:1021 Western Digital Technologies, Inc. Elements 2TB
```[COLOR=#000000][FONT=Consolas]

After that I ran over this xev command, but the results kind of confused me. There were two entries for every key input i did on my laptop keyboard and none but 2 keys on my external keyboard produced an entry: the menu key and the backspace key! I used this command: **xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'** and here are the results for the backspace key and the menu key:

```

keycode 22 = (keysym 0xff08, BackSpace), state = 0x10keycode 22 = (keysym 0xff08, BackSpace), state = 0x10
keycode 135 = (keysym 0xff67, Menu), state = 0x10
keycode 135 = (keysym 0xff67, Menu), state = 0x10

```

So my keyboard is recognized and two keys are 'working', but what about the rest? 
I tried other solutions I found on my research like unplugging/replugging the keyboard, having it unplugged while booting and then plugging it in, trying other usb ports... nothing solved my problem.

Unfortunately no one answered in the official elementary OS live chat, so I hope you guys can help me.

Thanks in advance for your help!
[/FONT][/COLOR]

---

### Post by Stinger on 2014-03-25
Hi noxit2, welcome to the Ubuntu forums.

I need a little info regarding your laptop, make and model, hardware specs. etc.

How new is your laptop and keyboard ?

Also, did you try to connect another usb keyboard to you laptop and what was the result ? 

Does the usb ports work with other hardware, mouse, usb-stick, printers, etc. ?

How much equipment do you have connected to the usb ports ?

Lots of questions ;) take your time.

---

### Post by noxit2 on 2014-03-25
Hey Stinger,

first of all: Thank you very much for your reply!

My Laptop is a HP Sleekbook 15 with an Intel i5 3317U CPU and a nVidia GeForce 630m graphics card. Beside that I'm trying to get a Sharkoon Tactix keyboard running. The laptop is 10 months old, the keyboard about half a year. Unfortunately I don't have another keyboard to try out, I'd have to buy another one which would be even more unfortunate.

I'm using a USB mouse on this very laptop right now and it works like a charm. I'm also using an external HDD which also didn't cause any problem, that's it with the USB devices (additionally, I have an external display connected via HDMI, although I don't think that this could be the source of the problem...?)! In my efforts to get the keyboard running I switched all of the ports for the devices and even tried to unplug all other devices except the keyboard but this didn't work out either... This forum is like my last resort :D

I think I should also add that the keyboard already didn't work when I was using elementary OS as a live system (the mouse and the HDD worked!) and I hoped that the problem would be solved by itself if I installed the OS properly.

I hope I was able to answer your questions to your content, I'd be happy to provide you with any information you need to help me solve my problem. 

Thanks again!

---

### Post by oldfred on 2014-03-25
Someone just posted that his new UEFI has a setting for USB ports like UEFI only. He changed that setting to auto.

My old BIOS also has settings for USB keyboard & mouse. While both Windows & Ubuntu would work without that setting, I have to turn it on for grub to have working keyboard.

---

### Post by noxit2 on 2014-03-26
> **oldfred said:**
> Someone just posted that his new UEFI has a setting for USB ports like UEFI only. He changed that setting to auto.

My old BIOS also has settings for USB keyboard & mouse. While both Windows & Ubuntu would work without that setting, I have to turn it on for grub to have working keyboard.


Hi oldfred,

thank you for your reply.

I just checked my BIOS settings but didn't find a setting like you mentioned, only USB 3.0 support, which already was set to switch automatically to 2.0 when booting, so this probably isn't the source of my problem.

Additionally I should mention that the keyboard works fine in GRUB, i can perfectly chose to boot either Win8.1 or elementary OS with my keyboard, it just stops working when reaching the elementary OS log-in screen.

---

### Post by Stinger on 2014-03-26
Ok then.
To sum it up. Your keyboard is working. 
There doesn't seem to be excessive power drain on the usb ports. But your hardware is quite new ( and has hybrid graphics )
Have you tried the 14.04 development release, live version will do ? it could be that a newer kernel and x-server would solve the problem with you quite new hardware.
It can be done in elementary too via the LTS Enablement Stack, I'll show you how if the if the 14.04 live image works for you.

---

### Post by noxit2 on 2014-03-26
Alright Stinger, 

I think you are on the right track there, I'm on 14.04 live version right now and my keyboard works like a charm!

It would be really great if you'd show me how to get this to work on elementary as well, thanks!

---

### Post by Stinger on 2014-03-27
To install the Saucy hardware enablement packages in Precise ( the newest until Trusty is released ), please run the following command:

```
sudo apt-get install --install-recommends linux-generic-lts-saucy xserver-xorg-lts-saucy libgl1-mesa-glx-lts-saucy
```
Remember to reboot to activate the new kernel and x-server.
[LTS Enablement Stack page]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack") 

But since you've got hybrid graphics you can try this instead if you dare ( I think you should be safe but I can't promise ):

    NVIDIA systems:
[LIST]
[*]        Install the lts-saucy stack ("linux-generic-lts-saucy" and "xserver-xorg-lts-saucy" as I descibed above )
[*]
[*]        Make sure that no other NVIDIA driver is installed including bumblebee (keep the nvidia-common package).
[*]        sudo apt-get purge bumblebee-nvidia
[*]        Install nvidia-319 (or nvidia-319-updates) and nvidia-prime.( I can see that nvidia-331 is available in the repositories too maybe you would try that instead ;) )
[*]        Reboot the system (restarting X won't be enough).
[/LIST]
[HybridGraphics page ]("https://wiki.ubuntu.com/X/Config/HybridGraphics")

Hope it works, unfortunately I can't try it myself :)

---

### Post by noxit2 on 2014-03-27
Wow, this worked out for me! You, dear sir, are my heroe of the week :D I only had to run the first command to install the hardware enablement packages, now my keyboard is working!

I guess I don't need to run the dual graphis drivers commands then? I didn't even install an NVIDIA driver before, so I'm not really sure if I have any driver for my dedicated graphics card. Should I install the drivers with your commands or was that simply an alternative if the installation of the hardware enablement packages wouldn't have been enough?

Anyway: Thank you! You just made me really happy :)

---

### Post by Stinger on 2014-03-27
Happy to have been of assistance ;)

You don't need the drivers for hybrid graphics, but you could benefit on 3D performance I would think, but then again there could be issues I don't know of, the hybridgraphics page hasn't been updated to Saucy.

If you don't miss anything, there is no need for installing the packages. You know, "Never touch a running system" ;)

Try runnig this command tells a lot about your graphics:
```
lspci | grep VGA & sudo lshw -C video
```
Remember to type in your password when asked for

---

### Post by noxit2 on 2014-03-27
You're probably right, this should suffice as I don't really need a lot of 3D performance in elementary. For the rare times I want to play games I can switch over to Win 8.1 :D

Just for your information: This was the output after running the command you mentioned:

```

  *-display UNGEFORDERT   
       Beschreibung: 3D controller
       Produkt: NVIDIA Corporation
       Hersteller: NVIDIA Corporation
       Physische ID: 0
       Bus-Informationen: pci@0000:01:00.0
       Version: a1
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress cap_list
       Konfiguration: latency=0
       Ressourcen: memory:d2000000-d2ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(Größe=128) memory:b2000000-b207ffff
  *-display
       Beschreibung: VGA compatible controller
       Produkt: Ivy Bridge Graphics Controller
       Hersteller: Intel Corporation
       Physische ID: 2
       Bus-Informationen: pci@0000:00:02.0
       Version: 09
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: msi pm vga_controller bus_master cap_list rom
       Konfiguration: driver=i915 latency=0
       Ressourcen: irq:47 memory:d3000000-d33fffff memory:c0000000-cfffffff ioport:5000(Größe=64)

```

Don't really know what to make of that, maybe you can tell me more :)

---

### Post by Stinger on 2014-03-27
I can tell you this:
You are probably German ;)
In the upper half you have got
> *-display UNGEFORDERT   
       Beschreibung: 3D controller
       Produkt: NVIDIA Corporation
and the bottom half says
>   *-display
       Beschreibung: VGA compatible controller
       Produkt: Ivy Bridge Graphics Controller
       Hersteller: Intel Corporation
Meaning that you are not using the Nvidia graphics but the Intel graphics.

---

### Post by noxit2 on 2014-03-28
Haha, you're good! Yes, I'm german :D

I just read a bit about this whole nVidia driver thing in Ubuntu and I decided to give bumblebee a try as this project seems to be the only solution which is able to switch between the internal and the nVidia GPU at the moment. I just installed it and my system is up and running and it seems to work just fine.

So I guess this matter is done! Thank you so much again, Stinger!

---

### Post by Stinger on 2014-03-28
I'm glad that [Bumble Bee]("http://bumblebee-project.org/index.html") works for you but I would go for nvidia-prime. GPU switching has been implemented and it seems to be improving.
You can read more about it here:
[Using Nvidia Graphics Drivers With Initial Optimus Support In Ubuntu 13.10 Got Easier With Nvidia-Prime ]("http://www.webupd8.org/2013/08/using-nvidia-graphics-drivers-with.html")
and here:
[More Work To Support Nvidia Optimus Lands In Ubuntu 14.04 Trusty Tahr]("http://www.webupd8.org/2013/12/more-work-to-support-nvidia-optimus.html")

The [“nvidia-prime” package in Ubuntu]("https://launchpad.net/ubuntu/+source/nvidia-prime") is available in version 0.5 for elementary ( Precise ) too, newest version nvidia-prime (0.5~hybrid0.0.3) in precise-proposed.
Works with Nvidia Graphics Drivers 319.12+ ( I personally would use the newest, nvidia-331 )

---

### Post by noxit2 on 2014-03-28
Alright, i just installed nvidia-331 and prime and it seems to be working fine, too! I guess I won't need my nvidia GPU that often, so I'll probably have it set to use the internal GPU for the most time. Thanks for the information about that topic!

---

### Post by Stinger on 2014-03-28
You are very welcome :)
Ps.
The Steam client is available in Ubuntu too, one never knows, maybe you'll be running [3D games]("http://www.omgubuntu.co.uk/2013/12/top-10-linux-games-2013") and apps on Linux before you know it :-o
I think I just promised myself a beer when this was solved
Cheers ;)

PPs.
Please don't forget to use the thread tools to mark this thread as solved

---

### Post by noxit2 on 2014-03-30
I already installed Steam but didn't have the time for a game or to, yet :D That beer is well deserved, cheers to you!

---

