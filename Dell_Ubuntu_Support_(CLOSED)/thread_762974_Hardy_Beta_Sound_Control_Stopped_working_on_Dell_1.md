---
title: "Hardy Beta: Sound Control Stopped working on Dell 1420n"
date: 2008-04-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aidave on 2008-04-22
Has anyone noticed this?  Something changed with the latest updates and now the volume controls on the laptop don't affect anything.  Even the mute is ignored.

---

### Post by jeffreyldavidson on 2008-04-23
I just upgraded my 1420N to Hardy also and have the same problem. I does not recognize the sound hardware.

---

### Post by aidave on 2008-04-23
I'm still getting sound, are you?

---

### Post by aidave on 2008-04-23
I tried setting the "Default Mixer Tracks" to "SigmaTel (OSS Mixer)" in the Sound applet and now the sound buttons on the laptop are working.  Strangely, even if I go back to the original ALSA default, the sound controls still work!  Haven't seen if a reboot will affect it yet.

---

### Post by martinlall on 2008-04-23
I've got no sound at all with Hardy.

After I installed kernel 2.6.25, Hardy won't find any sound mixers. The volume icon is always muted.
I have tried to install Sigmatel audio drivers, and alsa mixers and so on and so on. Nothing.

My sound card is Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

If i click on the volume icon it says: 

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Volume control says: No volume control GStreamer plugins and/or devices found.

And under sound preferences i have no audio mixers.

Any clue?

Martin

---

### Post by notwen on 2008-04-23
Have you attempted to change the levels in alsamixer from a terminal?  Open up a terminal and enter the following command:

```
alsamixer
```

ESC will exit it saving the settings.

---

### Post by martinlall on 2008-04-23
Terminal gives an error. Like everything else i try...

alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by notwen on 2008-04-23
I'm stumped, I'll be waiting for Dell to release their own custom Hardy image.  These custom images generally include the additional drivers/packages for our specific machines along w/ including any bugs/fixes found since the official release of Hardy.  I would guess Dell to have their custom images out within a month following Hardy's official release.  =]

---

### Post by martinlall on 2008-04-23
> **notwen said:**
> I'm stumped, I'll be waiting for Dell to release their own custom Hardy image.  These custom images generally include the additional drivers/packages for our specific machines along w/ including any bugs/fixes found since the official release of Hardy.  I would guess Dell to have their custom images out within a month following Hardy's official release.  =]

Let's hope so. 
And kernel 2.6.25 is way too good, to turn back to kernel 2.6.24-* :P

---

### Post by ghindo on 2008-04-23
I am getting the same problem as well, which is a shame, because everything else is working better than before!

I tried ```
alsamixer
```to no avail, and can't think of what else to do!  Could anyone help?

---

### Post by martinlall on 2008-04-23
> **ghindo said:**
> I am getting the same problem as well, which is a shame, because everything else is working better than before!

I tried ```
alsamixer
```to no avail, and can't think of what else to do!  Could anyone help?

What kernel and dist you are using? 
8.04 LTS with kernel 2.6.25?

---

### Post by ghindo on 2008-04-23
> **martinlall said:**
> What kernel and dist you are using? 
8.04 LTS with kernel 2.6.25?I'm using the Hardy 8.04 Release Candidate with kernel 2.6.24-16

---

### Post by aidave on 2008-04-23
I'm using 2.6.24-16 and have sound.

---

### Post by martinlall on 2008-04-23
> **ghindo said:**
> I'm using the Hardy 8.04 Release Candidate with kernel 2.6.24-16

What laptop are you using at? And what is your soundcard exact model?
A little more information would be helpful.


Thank you.

---

### Post by martinlall on 2008-04-23
> **aidave said:**
> I'm using 2.6.24-16 and have sound.

Please give more information about your laptop.

---

### Post by ghindo on 2008-04-24
> **martinlall said:**
> What laptop are you using at? And what is your soundcard exact model?
A little more information would be helpful.


Thank you.I'm using the Dell Inspiron 1420n, just like the OP.  I'm not sure what my soundcard's exact model is - how do I check?

---

### Post by martinlall on 2008-04-24
> **ghindo said:**
> I'm using the Dell Inspiron 1420n, just like the OP.  I'm not sure what my soundcard's exact model is - how do I check?

Type in terminal: lspci

---

### Post by ghindo on 2008-04-24
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

---

### Post by jetpeach on 2008-04-25
i have no sound, 1420n with kernel .24-16
i believe the problem is actually with the kernel recognizing our card - the output of lshw -C sound tells an interesting story


lshw -C sound
WARNING: you should run this program as super-user.
SCSI
  *-multimedia UNCLAIMED
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

somebody elsewhere said the problem went away for them "after the most recent updates". it hasn't for me though... i'm running kubuntu 8.04, although this should impact the kernel and output of the lshw command.

---

### Post by martinlall on 2008-04-25
My sound works perfectly in 8.04 with kernel 2.6.24-16
But the problem is in 2.6.25.. 

I haven't found any solution yet.

---

### Post by mavo on 2008-04-25
I had the same problem and found a solution here:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)

---

### Post by duncanbourne on 2008-04-25
Thanks for that. I followed the instructions and the sounds now works on my 1525. Unfortunately, it is now very quiet and tinny sounding :-(

Anyone else find the same?

Duncan

---

### Post by gregoryg on 2008-04-25
I'm also suffering from the sound issues after the upgrade. I'm using an Inspiron 1420 n. I followed the wiki instructions, but they didn't quite work. 

For instance, in the third sterp "Restore name of sound driver that old modem driver renamed:" the sound driver had not been renamed. There were also no old sound drivers to remove.

---

### Post by trooperchix on 2008-04-26
I'm running a 1420N as well, the audio id:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

I'm at a loss too.  This version works better, save for audio which in turn is causing my Amarok to flip out.  Give me a holler too if anyone figures this one out...  

:confused:

---

### Post by WBL on 2008-04-27
> **mavo said:**
> I had the same problem and found a solution here:
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)

Tried that on my 1525n-didn't do anything at all.  :confused:

-WBL

---

### Post by steeny124 on 2008-04-27
I use an inspiron 1420 and when I upgraded to Hardy my sound did not work either.  I used [this thread]("http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+alsa") to fix it.  However, my sound controls/buttons don't work.  I tried switching my default mixer track device under sound to SigmaTel STAC9228 (OSS mixer), but that doesn't work.  When I pull up alsamixer, the Master volume control does not control the speakers, it appears to be the PCM that makes the actual sound go up and down.  

Any help or even a pointer to a different thread that addresses this (I have looked for one) would be appreciated.

---

### Post by trooperchix on 2008-04-27
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)

Yep, that fixed it kind of...  Now it appears my little buttons work, they play well with the volume gui but...  still no sound.  I get Amarok running right (it stopped flipping out because now the system at least recognizes the sound card even though it isn't working...)  Now, if anyone can figure out how to actually modulate volume and link those functions to the now working buttons, I'd be estatic.  It's got me by the tail...

---

### Post by steeny124 on 2008-04-27
> **trooperchix said:**
> [http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound)

Yep, that fixed it kind of...  Now it appears my little buttons work, they play well with the volume gui but...  still no sound.  I get Amarok running right (it stopped flipping out because now the system at least recognizes the sound card even though it isn't working...)  Now, if anyone can figure out how to actually modulate volume and link those functions to the now working buttons, I'd be estatic.  It's got me by the tail...

I had the same problem.  It recognized my soundcard and the volume gui worked and everything.  I ended up using [this thread]("http://ubuntuforums.org/showthread.php?t=616845&highlight=hda+intel+alsa") to fix it.  Now, that thread is primarily for hda intel sound cards.  

To figure out what kind you have, the easiest way I figured out (there are probably easier ways) was

```
sudo apt-get install hwinfo
```

```
hwinfo --sound
```

which should display something like this:

```
steeny124@dell:~$ hwinfo --sound
27: PCI 1b.0: 0403 Audio device                                 
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_8086_284b
  Unique ID: u1Nb.wUq5O6bR3r1
  SysFS ID: /devices/pci0000:00/0000:00:1b.0
  SysFS BusID: 0000:00:1b.0
  Hardware Class: sound
  Model: "Dell HD Audio Controller"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x284b "HD Audio Controller"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x01f3 
  Revision: 0x02
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe9fc000-0xfe9fffff (rw,non-prefetchable)
  IRQ: 20 (111544 events)
  Module Alias: "pci:v00008086d0000284Bsv00001028sd000001F3bc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Note the line, "Driver, HDA Intel"

Sorry if this is all really obvious stuff that you already know, but hopefully it will be useful to somebody!

Edit: to figure out what kind of soundcard you actually have:

```
cat /proc/asound/card0/codec#* | grep Codec 
```
or```
aplay -l
```

---

### Post by frbe0101 on 2008-04-28
steeny124,

thx, that fix the sound!

---

### Post by steeny124 on 2008-04-28
> **frbe0101 said:**
> steeny124,

thx, that fix the sound!

Yay!  It's a great moment, the first problem I've helped fix.

---

### Post by martinlall on 2008-05-01
I tried that:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

And now i can edit my volume and select sound mixers in preferences.

But still no sound..
Maybe this helps someone.

---

### Post by ghindo on 2008-05-01
> **martinlall said:**
> I tried that:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

And now i can edit my volume and select sound mixers in preferences.

But still no sound..
Maybe this helps someone.Are you using Hardy?  What kernel are you using?

---

### Post by rafa&#322; on 2008-05-01
strange, sound works on 2.6.24-14-generic and 2.6.24-16-generic
but doesn't work on 2.6.24-16-386

---

### Post by purplepaint on 2008-05-02
> **rafa&#322 said:**
> strange, sound works on 2.6.24-14-generic and 2.6.24-16-generic
but doesn't work on 2.6.24-16-386

I've found that as well (using Inspiron 1525)

This may be a strange-sounding question (still new to Ubuntu/Linux), but is it worth using the GRUB menu to boot the previous kernel each time I start the machine and then just wait for Dell to release their own image?  If yes, how easy is it to get hold of it when it's released?  If you didn't understand, I may have some more questions!

---

### Post by purplepaint on 2008-05-02
I managed to fix it by following the instructions on the Dell Wiki and then turning up everything to maximum in alsamixer.  :guitar:

Now, if I can just be patient and wait for my Firefox extensions to be made compatible with Firefox 3...

---

### Post by bcummings on 2008-05-02
WooHoo!!  I followed the instructions posted on the Dell Wiki and viola!  I have sound.  I purchased my Dell 1420 with 7.10 pre-installed.  I thought I would upgrade the machine to Hardy (8.04) before getting started moving everything over from my old machine.  The upgrade worked, for everything except the sound.  Now the sound is working again too.  I love Ubuntu...:cool:

---

### Post by ghindo on 2008-05-02
The thing that really bugs me about all of this is that my sound works *occasionally*, but not always, and none of the fixes listed here seem to work. :(

---

### Post by mr_tentacle on 2008-05-08
I had the "no sound" problem on my 1420 with the released Hardy.  I tried the fix from the Dell Wiki with no joy, and then found another post suggesting reloading the HDA drivers: that worked, but I needed to do it manually after every reboot, which was a pain.

I found the solution in this thread:

[http://ubuntuforums.org/showthread.php?t=758962](http://ubuntuforums.org/showthread.php?t=758962)

and it worked perfectly. 

Edit **/etc/modprobe.d/alsa-base**  add theses lines to the end of the file:

# fix  sound
options snd-hda-intel model=auto

Save the file and reboot - presto!

---

### Post by ghindo on 2008-05-09
> **mr_tentacle said:**
> I had the "no sound" problem on my 1420 with the released Hardy.  I tried the fix from the Dell Wiki with no joy, and then found another post suggesting reloading the HDA drivers: that worked, but I needed to do it manually after every reboot, which was a pain.

I found the solution in this thread:

[http://ubuntuforums.org/showthread.php?t=758962](http://ubuntuforums.org/showthread.php?t=758962)

and it worked perfectly. 

Edit **/etc/modprobe.d/alsa-base**  add theses lines to the end of the file:

# fix  sound
options snd-hda-intel model=auto

Save the file and reboot - presto!This worked for me!

Thank you so much! :)

---

### Post by Adila01 on 2008-05-13
> **martinlall said:**
> I tried that:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

And now i can edit my volume and select sound mixers in preferences.

But still no sound..
Maybe this helps someone.

Worked like a charm :D :D

---

### Post by joseardzm on 2008-05-20
hi, i have an inspiron 1420 that came with vista (but i install xp instead), intel ICH8 audio, and X3100 integrated video. 

My xp stop working, so i change to ubuntu, 8.04, kernel:2.6.24-16
and when i have audio most of the times, except when i play a youtube video or suspend/hibernate (which takes a lot of time to proceed but works)

i havent been able to carry on your solution because i m a total noob :S

EDIT: I fixed somehow by installing libflashsupport from synaptic

---

### Post by Gwaihirjp on 2008-05-24
Hi I'm having the same kind of problem too with my Ubuntu Hardy. It's a Dell Inspiron 1420 which originally came with Vista and I've dual-booted it with Gutsy before doing the upgrade to Hardy a month ago. Alsamixer seems to be working perfectly well, and when I plug my headset into the output the sound comes out like it should.

But when I pull out the headphone jack, the laptop's speakers are completely silent and don't work at all. I've tried all kinds of solutions including the ones on this thread but they don't seem to work. 

I hope someone can give me a pointer on this because I really want my laptop speakers to work. My audio device is: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by barranza on 2008-05-27
Fix in the reported thread works also for an Acer Aspire 1640

Thanks for the help
Matteo

---

