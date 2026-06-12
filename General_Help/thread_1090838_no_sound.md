---
title: "no sound"
date: 2009-03-08
forum: General Help
---

### Post by bertolo on 2009-03-08
Since i upgraded to 8.10 i have no ouput sound. anyone can help ?
i still have sound in windows.


i tried this already and nothing:
[http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html](http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html)

---

### Post by bertolo on 2009-03-10
no one ?

---

### Post by Neo_The_User on 2009-03-10
Sorry I didn't see that this was unanswered. What happens when  you try launching the audio control panel?

---

### Post by bertolo on 2009-03-10
do you mean sound preferences ?

---

### Post by Neo_The_User on 2009-03-10
You're using gnome right? Right click on the speaker volume thing on your toolbar and select "Open Volume Control" and tell me if you get any errors. Also post the output of lspci. In a terminal:

```

lspci

```

---

### Post by Crafty Kisses on 2009-03-10
I'm going to suggest you open up a Terminal and run the following command:
```
alsamixer
```
Make sure all the volumes are up to their proper levels, if they are, post back and I or someone else can assist you further.

---

### Post by bertolo on 2009-03-10
No errors on Volume Control. 
[QUOTE=00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:04.0 Mass storage controller: Integrated Technology Express, Inc. ITE 8211F Single Channel UDMA 133 (rev 11)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
04:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
[/QUOTE]

---

### Post by Neo_The_User on 2009-03-10
> **Codename said:**
> I'm going to suggest you open up a Terminal and run the following command:
```
alsamixer
```
Make sure all the volumes are up to their proper levels, if they are, post back and I or someone else can assist you further.

That won't tell him if he has the old fashioned gstreamer error for no reason. Set PCM and Master on full.

Go in System > Preferences > Sound and try changing those settings from set to all ALSA, to all OSS, and see what works.

---

### Post by bertolo on 2009-03-10
[http://img408.imageshack.us/img408/4876/screenshot1b.png](http://img408.imageshack.us/img408/4876/screenshot1b.png)
[http://img13.imageshack.us/img13/5905/screenshotbid.png](http://img13.imageshack.us/img13/5905/screenshotbid.png)

both are fine :/

i have to mention two things:
my screen got speakers and my normal speakers that are plugged in the audio card are very very cheap. but they work using windows.

---

### Post by Neo_The_User on 2009-03-10
Try setting everything to ALSA.

---

### Post by bertolo on 2009-03-10
i am confused already i got so many sound applications:

Gnome Alsa Mixer
Pulse Audio Device Chooser
Volume Control
Volume Control (audio panel)

i wil try everything to alsa again.

---

### Post by Neo_The_User on 2009-03-10
In System > Prefernces > Sound, set all to ALSA. then crank up volume and see if you hear anything.

---

### Post by bertolo on 2009-03-10
nothing ...
i installed pulse audio device chooser... i think it wont let me choose alsa

---

### Post by Neo_The_User on 2009-03-10
> **bertolo said:**
> nothing ...
i installed pulse audio device chooser... i think it wont let me choose alsa

Post error of when choosing ALSA. Try a different kernel too.

---

### Post by bertolo on 2009-03-10
i got no errors...

---

### Post by Neo_The_User on 2009-03-10
> **bertolo said:**
> 
i think it wont let me choose alsa

Then what do you mean by that quote? Try loading different kernel.

---

### Post by bertolo on 2009-03-10
System &#8594; Preferences &#8594; Default sound card &#8594; i only have 2 options pulse audio and intel.

i installed this app in first atempt to get sound.

---

### Post by Neo_The_User on 2009-03-10
> **bertolo said:**
> System &#8594; Preferences &#8594; Default sound card &#8594; i only have 2 options pulse audio and intel.

i installed this app in first atempt to get sound.

Try a different kernel and use OSS.

...That's the last time I'm saying to try a different kernel.

---

### Post by Crafty Kisses on 2009-03-10
> **Neo_The_User said:**
> That won't tell him if he has the old fashioned gstreamer error for no reason. Set PCM and Master on full.

Go in System > Preferences > Sound and try changing those settings from set to all ALSA, to all OSS, and see what works.

Yes I'm aware of that, but there has been several cases where that is the actual issue. Anyway check and see if the snd-hda-intel module is being loaded at start, it's very possible that it isn't. You can load the module by running the following command:
```
sudo modprobe snd-hda-intel
```

---

### Post by bertolo on 2009-03-10
ok i did it and then select wich drivers ? intel digital or intel analog ?

---

### Post by Neo_The_User on 2009-03-10
> **Codename said:**
> Yes I'm aware of that, but there has been several cases where that is the actual issue. Anyway check and see if the snd-hda-intel module is being loaded at start, it's very possible that it isn't. You can load the module by running the following command:
```
sudo modprobe snd-hda-intel
```

Well its never been the case for me when the gstreamer thing isn't lying.

---

### Post by Crafty Kisses on 2009-03-10
What are the results of this?
```
cat /proc/asound/cards
```
Make sure if the Intel sound card is even listed. I'm aware it was listed on lspci, but I want to make sure it's listed under this.

---

### Post by Neo_The_User on 2009-03-10
> **Codename said:**
> What are the results of this?
```
cat /proc/asound/cards
```
Make sure if the Intel sound card is even listed. I'm aware it was listed on lspci, but I want to make sure it's listed under this.

It was listed in lspci meaning the kernel found the hardware register for it. ;) Usually when you **_[SIZE="6"]TRY A DIFFERENT KERNEL[/SIZE]_** it fixes the problem. I compile my own kernels all the time and the audio either works or doesn't work even when you don't change the config file. Its one of those flaky things.

---

### Post by Crafty Kisses on 2009-03-10
> **Neo_The_User said:**
> It was listed in lspci.
I'm not going to start this into some flame, but if you read my OP that you quoted I state, "I'm aware it's listed in lspci". I want to make sure it's listed in that file.

---

### Post by Neo_The_User on 2009-03-10
> **Codename said:**
> I'm not going to start this into some flame, but if you read my OP that you quoted I state, "I'm aware it's listed in lspci". I want to make sure it's listed in that file.

Codename, I'm not doubting you that you saw it in lspci. geeze!

---

### Post by fcuk112 on 2009-03-10
something that has worked for me in the past is the following - 

/boot/grub/menu.lst - there should be the file.

in the line looking something like that:

kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro noapic

you can add acpi=off

kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro acpi=off noapic

---

### Post by Neo_The_User on 2009-03-10
> **fcuk112 said:**
> something that has worked for me in the past is the following - 

/boot/grub/menu.lst - there should be the file.

in the line looking something like that:

kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro noapic

you can add acpi=off

kernel /boot/vmlinuz-2.6.18-3-amd64 root=/dev/sda1 ro acpi=off noapic

ACPI is not related to audio at all. ACPI is power manangement. I just noticed that if you switch kernels, it usually works. You might want to try using a different one.

---

### Post by bertolo on 2009-03-10
> **Codename said:**
> What are the results of this?
```
cat /proc/asound/cards
```
Make sure if the Intel sound card is even listed. I'm aware it was listed on lspci, but I want to make sure it's listed under this.

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xcdcf8000 irq 19


sorry i was dining

i am affraid of switching kernel lol.
any tutorial ?

---

### Post by Neo_The_User on 2009-03-10
> **bertolo said:**
> 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xcdcf8000 irq 19


sorry i was dining

i am affraid of switching kernel lol.
any tutorial ?

yeah.

[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

I don't build my kernels that way though but for starters, thats how.

---

### Post by bertolo on 2009-03-10
> Building and using a custom kernel will make it very difficult to get support for your system.  While it is a learning experience to compile your own kernel, you will not be allowed to file bugs on the custom-built kernel (if you do, they will be Rejected without further explanation).

having sound is not so important that i may risk all system.

---

### Post by bertolo on 2009-03-26
I HAVE SOUND ON LINUX FINNALY! OMG :D

i selected HDA INTEL (Alsa mixer), in preferences i selected everything that appears there and put everything on max. 

:)

this was kind of stupid.... i love ubuntu

PS: in switches HEADPHONES MUST be selected.

---

### Post by mithbuntu on 2009-03-26
Now someone help me in my sound issues thread :P Completely different issue, but still no sound.

---

