---
title: "HOWTO : Joystick/Gamepads under Ubuntu"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by adam0509 on 2007-01-14
Hi,

I've seen there isn't a complete HOWTO about gamepad, here it is. I think it would be nice to make this threat STICKY under Gaming and Leisure....




This HOWTO will learn you how to use a gamepad under Ubuntu. It should work for Dapper, Edgy, and all other following version of Ubuntu

*What you need*

    * You need to have activate the « Universe » depository in your /etc/apt/sources.list or from Synaptic
    * A gamepad for gameport or USB.
    * A SoundBlaster card or compatible (gameport only).
    * Knowing how to use a terminal

**Introduction**

Ok, let's begin. First, plug your gamepad. **In 50% of case, the gamepad is auto-detected** (If it's a gameport gamepad, you need to reboot, cause it's not plug'n'play). Just test this, if it don't works, see what's next.


You need to know one important thing under Linux. Most of Linux application use it own algorithm to detect gamepad. It's not like M$ Windows, where there is one tool that centerise all data (and the game use these data). That means that if your gamepad works with "jscalibrator" or other, it may not work with your game. You may need to check configuration of your program (joy_sensitivity for Zsnes for example).

**-------Calibration - Test**

We gonna show different method to calibrate (but especially test) your gamepad.

*---With "jscalibrator" (unapproved, see below)*

Install the package :

```
sudo apt-get install jscalibrator
```

Then calibrate with the command :

```
jscalibrator
```

Clic on "calibrate".

Use all your axes in all direction, so the program could save the minimal/maximal values of your gamepad.

Re-clic on the « Calibrate » button so your data could be saved.

**/!\ **Important **/!\** : Once save, the informations of calibration are stocked in the file ".joystick" in your /home/user.

*---By the configuration centre of KDE*

In the KDE menu, select « Configuration centre of KDE ».

Clic on the section « Périphériques », then « Gamepad ».

Clic on « Calibrer », then proceed to the calibration and follow instructions.

*---By console*

The ultimate method !

```
cat /dev/input/js0
```

If you see waird signs, that mean it should work !

```
sudo apt-get install joystick
```

Joystick is a program to calibrate the gamepad in console. Use these command :

```
jscal /dev/input/js0
jstest /dev/input/js0
```

**-------Manual method**

Your gamepad isn't detected ? You just pluged your gamepad and you do not want to reboot ? OK !

*1°/ Créate gameport on Linux*

In terminal :

You need to place in the correct folder

```
cd /dev/input
```

Create the gameport with command :

```
sudo MAKEDEV js
```

*2°/ Loading modules*

You will need "Drivers". Under ubuntu, these are modules that you will need to load with your linux kernel.

In fist, we gonna do it manually. If all works, we gonna edit some files, so everything could be done at boot.

A/ Test the solution before edit the files

In a terminal, load in memory the modules required according to your gamepad.

For example, for a Sidewinder GamePad (/!\ Check under to know the good modules !!! /!\) :

```
sudo modprobe joydev
sudo modprobe ns558
sudo modprobe sidewinder
```

At all moment you can see the modules loaded with the command :

```

lsmod
lsmod | grep gameport ## to display only lignes containing "Gameport"

```

Now test your gamepad.


**If you success** in calibrating your gamepad, it's good, you choose the good modules. Get to the following section.

**If you get an error message** and don't suceed to calibrate your gamepad, you need to look under to know the good modules.

**Reminder** : To unload a module, you need to use the command _modprobe -r_ (remove) :

```
sudo modprobe -r sidewinder
```

*B/ Load the modules automaticaly at start*

For this, we gonna edit the configuration file "/etc/modules". In a Terminal, enter the following command :

```

sudo gedit /etc/modules (Ubuntu)
sudo kate /etc/modules (Kubuntu)
sudo mousepad /etc/modules (Xubuntu)
```

Take car of casse sensitive. This file « modules » regroups a part of the driver to load with your Linux kernel.

In the end of the file, add this text :

```

## Pilotes de manette de jeu (joystick)
joydev         ## Module for gamepads
ns558          ## Module for gameport
sidewinder     ## Module for MS-SideWinder pads
```

This will give you a file /etc/modules that should look like this :
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

## Pilotes de souris
psmouse
mousedev

## Pilotes de carte de son ALSA Ensoniq ES1371 AudioPCI-97
alias snd-card-0 snd-ens1371
below snd-es1371
snd-seq-device ## Optionnal (this is about MIDI)
snd-seq-midi   ## Optionnal (this is about MIDI)

## Pilotes de manette de jeu (joystick)
joydev         ## Module for gamepads
ns558          ## Module for gameport
sidewinder     ## Module for MS-SideWinder pads
```

In addition of this, you need to create/edit the file /etc/modules.conf, to add lines

```
sudo gedit /etc/modules.conf (Ubuntu)
sudo kate /etc/modules.conf (Kubuntu)
sudo mousepad /etc/modules.conf (Xubuntu)

```

In the end of the file, copy the following lines :

```
alias js0 input
above input joydev ns558 sidewinder
```

Save, and reboot.


**------- MODULES LIST**

*For a sound card with ens1371 chipset*

If you get a sound card with ens1371 (Ex : Sounblaster 64 and 128), you will need to do a small thing before.

First, verify the model of your sound card : in a terminal, type

```
lsmod | grep snd_ens1371
```

If you got something, that's good, continue, if not, you got an other soundcard (But maybe you can continue by replacing what's next « joystick_port=1 » by « joystick=1 » or « joystick » and adapting with your soundcard.)

Edit the file /etc/modprobe.d/options :

```
sudo gedit /etc/modprobe.d/options
```

And add the line :

```
options snd_ens1371 joystick_port=1
```

Reboot, and restart the HOWTO from beginning.

(Thanks PierreR)

*For an Aztech soundcard*

Here too, seems you need to activate the gameport.

So in /etc/modules.conf, add :

```
above snd-trident snd-pcm-oss
alias sound-slot-0 trident
alias js0 input
above input joydev pcigame analog adi
```

*For a MS Sidewinder gamepad*

```
sudo modprobe joydev
sudo modprobe ns558
sudo modprobe sidewinder
sudo modprobe analog ## This one work only for analog pad, like joysticks

```

*For a Logitech WingMan digital gamepad*

```
sudo modprobe joydev
sudo modprobe ns558
sudo modprobe adi ## Specific driver for Logitech gamepads
```

*For a Logitech WingMan gamepad (analog)*

```
sudo modprobe joydev
sudo modprobe ns558
sudo modprobe analog ## Module for analog gamepads
sudo modprobe pcigame ## Module for PCI card (??)
sudo modprobe adi ## Module for Logitech pads
```

*For a MS SideWinder ForceFeedBack Pro*

```
sudo modprobe joydev
sudo modprobe ns558
sudo modprobe analog 
sudo modprobe sidewinder
sudo modprobe iforce ## Force Feedback driver
sudo modprobe evdev ## driver for ???

```

*For a Guillemot dual analog gamepad (gameport, non-USB)*

```
sudo modprobe joydev
sudo modprobe ns558
sudo modprobe guillemot
sudo modprobe analog ## to check
sudo modprobe iforce ## to check
```

Think about the button that activate/desativate the joystick of this pad.

*For a USB gamepad*

(From [http://www.linux-usb.org/USB-guide/x194.html](http://www.linux-usb.org/USB-guide/x194.html) )

If auto-detect don't works (Very rare case !!)...

```
sudo modprobe usbhid
sudo modprobe joydev
```

Now, plugin your gamepad (If havn't do it before) and test.

You just need to add usbhid and joydev in /etc/modules like showing before.


*Other gamepads*

To obtain a complete list of modules, you can type "modprobe -l"

I suggest you to install the "modconf" package :

```
sudo apt-get install modconf
```

Then launch modconf in sudo (It's better to run it with a maximized window) :

```
sudo modconf
```

You will then land on a COMPLETE list of all modules loadable. Get in the folder "joystick", and you will see all joystick driver available ! :)

**About multiples gamepads**

Multiple gamepads works fine. There is just a few bug with "jscalibrator" : /dev/input/js1 points to /dev/input/js0... I gonna report this to launchpad

EDIT : reported directly to author.

**Links**

Kernel doc here: [http://www.freelink.cx/joystick.html](http://www.freelink.cx/joystick.html).

Complete page about gamepads : [http://www.charmed.com/txt/joystick.txt](http://www.charmed.com/txt/joystick.txt)


**Credits :**

HOWTO by me and other french contributers.

Thanks to all french user that are workings such hard to maintain the french wiki

If you have any suggestion/question, post here.

You are free to copy, redistribute, correct, improve this document, even if you don't quote me in credits.

---

### Post by bernardfrancois on 2007-01-19
Thanks for the howto!
Running jscalibrator was sufficient for my 'sidewinder gamepad pro'. 
Now I should test it in a game, I was hoping xmoto would support gamepads, but it doesn't seem to be the case :(

A small remark about the howto:

I think sometimes you have [i]sudo[i]s where it's unnecessary. For example **cat /dev/input/js0** is sufficient. Also all those modprobe's also work without sudo.

---

### Post by adam0509 on 2007-01-27
thanks for the answer !

> **bernardfrancois said:**
> 
A small remark about the howto:

I think sometimes you have [i]sudo[i]s where it's unnecessary. For example **cat /dev/input/js0** is sufficient. **Also all those modprobe's also work without sudo.**

No, you're wrong on this one, because modprobe is directly about Linux-kernel, so you need administrator's right...

---

### Post by adam0509 on 2007-03-10
Another interresting topic about gamepad, and especially gameports :

[http://ubuntuforums.org/showthread.php?t=330607](http://ubuntuforums.org/showthread.php?t=330607)

---

### Post by handy on 2007-03-11
[I'll just toss this link in here, it may help someone with a wheel controller...]("http://www.wingmanteam.com/linux.htm")

---

### Post by satbunny on 2007-05-19
I have a USB gamepad (SaitekP220) and when I use jcalibrator it seem to calibrate. When I use snes9express the buttons work but not the D-buttons.

So I dug about and discovered a programme called jcal which also claims to calibrate. It talks of my pad having 3 axes but I have no idea which one is which, it may be terribly noob of me, but how do you tell?

If I calibrate with jcal, guessing which is which, and then test, it reports calibration. If I then recalibrate with jcalibrator and then test with jcal it reports that it is not calibrated.

Also, is there anothe game using a gamepad that is a standard Ubuntu repository option  so I can see if I have actually calibrated my pad and/or if it is a snes9/snes9express problem?

Thanks folks

---

### Post by adam0509 on 2007-05-19
LINUX IS JUST ****** UP WITH JOYSTICK....



Sorry, I am a little angry, but you problems hapens to about 50% of peoples, me too I got same problems with zsnes 1.42, Gens and VisualBoyAdvance (+vbaexpress frontend, I just send a mail to the author about this...).


The fact is, even if you had calibrated your joystick with jscalibrator or other, no other programs read the ".joystick" generated by this program... It's not like Windows where the software can read the data of calibration center...


I'm gonna send a mail to freedesktop, this can't no longer happens...

---

### Post by Chris S. on 2007-05-20
I just got a gamepad today and had troubles with the analog controls.  I searched around and this is a *very* common problem, but I couldn't find any solution.  This might apply to those people having D-pad problems too, because my gamepad maps the D-pad as an analog input.

Anyway, I believe that after running jscalibrator the analog controls are no longer usable by other programs, even if jscalibrator sees them.  The analog sticks and the D-pad become usable after rebooting my machine.  Mupen64, ZSNES, Mednafen, and PSX all have no problems with any of the buttons, sticks, or the D-pad on my gamepad after rebooting, so long as I don't start up jscalibrator.

Hopefully this will help some people, and probably only those with auto-detected gamepads.  Mine is a Logitech Dual Action, and it works just fine now.  Oh, if anyone has another work-around for this besides a reboot, I'd like to know.

---

### Post by adam0509 on 2007-05-20
**FOUND IT**


jscalibrator gives real values to kernel, that's why it don't works.


**ALL GAMES** will works on Kubuntu, because of the joystick calibration thing give emulate value (it gives 32000 with my sidewinder gamepad, where jscalibrator will give "1"...)

[B]
SO, JUST INSTALL :[/B]

```

sudo apt-get install kcontrol

```

And it will work with ALL games !!!


:) :)


**EDIT :**

That works well with the joystick package too :

```

sudo apt-get install joystick
jscal -c /dev/input/js0

```

then you can : "man jscal" and "man jstest".

```

jstest

```

Verify that jstest takes values likes -32767 / 32767 !!!!

---

### Post by oxygala on 2007-05-30
worked like a charm with my cheap usb gamepad. thanks dude, made my day.

---

### Post by adam0509 on 2007-05-31
You're welcome

Even if the doc isn't perfect ( not like french one who really is : [http://doc.ubuntu-fr.org/materiel/joystick](http://doc.ubuntu-fr.org/materiel/joystick) ), it's a good start.


Maybe I'll try to re-take it on official wiki, but... err... this thing is ugly, I never have been able to find anything in official wiki :| :|

---

### Post by tsuchinoko on 2007-06-02
I have a problem. I'm running snes9express and as soon as i set up a joystick my roms wont open. It gives me an error with what looks like the config file. any help would be appreciated.

---

### Post by adam0509 on 2007-06-08
Hi.


are you runing a linux 32 or 64 bit ???


If 32bits, then try Zsnes, very very great emulator...


(well, I'm gonna test snes9x and I will edit this message later)

---

### Post by tsuchinoko on 2007-06-08
I just installed zsnes, much better. I should of installed it in the first place.

thanks

---

### Post by El Flavio on 2007-07-09
> Then launch modconf in sudo (It's better to run it with a maximized window) :

```
sudo modconf
```

You will then land on a COMPLETE list of all modules loadable. Get in the folder "joystick", and you will see all joystick driver available ! :)

Sorry for being a noob, but I need some help. I found the driver I wanted to install (screenshot 1) and a message popped up (screenshot 2) to "enter command line argument"  and I don't know what to type in. Could you (or anybody) help?

Screenshot 1: [IMG]http://i141.photobucket.com/albums/r71/Austin_is_cool_2006/screenshot1.png[/IMG]

Screenshot 2: [IMG]http://i141.photobucket.com/albums/r71/Austin_is_cool_2006/screenshot2.png[/IMG]

---

### Post by Shpongled303 on 2007-07-13
> **tsuchinoko said:**
> I have a problem. I'm running snes9express and as soon as i set up a joystick my roms wont open. It gives me an error with what looks like the config file. any help would be appreciated.

Hey tsuchinoko,

I had the same problem, it wouldn't read my ROMs, so I uninstalled it and tried another package -- ZSNES from the Synaptic Package Manager.

Unfortunately the version in the SPM is 1.42, but ZSNES at least was able to read the ROMs and everything seems to be working well.

Also, I've found that jscalibrator and joystick packages actually made my gamepad not work -- the directional pads functioned after I uninstalled the packages -- so if all else fails try not using those things or these instructions. :P Worked for me!

[EDIT: ZSNES 1.51 (the newest version) can actually be found in an easy-to-install .DEB package from [www.getdeb.net]](www.getdeb.net])

---

### Post by gottferdamnt on 2007-08-01
Hi,
How make a game pad work in a game with Wine?

---

### Post by adam0509 on 2007-08-13
> **El Flavio said:**
> Sorry for being a noob, but I need some help. I found the driver I wanted to install (screenshot 1) and a message popped up (screenshot 2) to "enter command line argument"  and I don't know what to type in. Could you (or anybody) help?

Screenshot 1: [IMG]http://i141.photobucket.com/albums/r71/Austin_is_cool_2006/screenshot1.png[/IMG]

Screenshot 2: [IMG]http://i141.photobucket.com/albums/r71/Austin_is_cool_2006/screenshot2.png[/IMG]


Hey El Flavio !!!


Good you make it till there.

The "argument" are somthing in the module, some of them needs argument to work (like joystick_port=1 in some audio-card modules...)


To know what argument is possible (it's NOT an obligation !!!), type MODINFO :

```

$ modinfo gamecon
filename:       /lib/modules/2.6.20-16-lowlatency/kernel/drivers/input/joystick/gamecon.ko
license:        GPL
description:    NES, SNES, N64, MultiSystem, PSX gamepad driver
author:         Vojtech Pavlik <vojtech@ucw.cz>
srcversion:     E9508FFBB83734FF64902FC
depends:        parport
vermagic:       2.6.20-16-lowlatency SMP preempt mod_unload 586 
parm:           map:Describes first set of devices (<parport#>,<pad1>,<pad2>,..<pad5>) (array of int)
parm:           map2:Describes second set of devices (array of int)
parm:           map3:Describes third set of devices (array of int)
parm:           psx_delay:Delay when accessing Sony PSX controller (usecs) (uint)

```

the "parm" things are your arguments. "array of int" means "row of entire numbers"...I can't help you better since I don't know exactly what you need...




gottferdamnt => Wrong topic... We talk about gamepads and modules (once you've tested it and worked with at least 1 game, the topic has done it's work...), not about games... you should search a bit in forum, I'm sure you'll find your happiness !!!

---

### Post by stoer on 2007-08-13
> **adam0509 said:**
> **FOUND IT**


jscalibrator gives real values to kernel, that's why it don't works.


**ALL GAMES** will works on Kubuntu, because of the joystick calibration thing give emulate value (it gives 32000 with my sidewinder gamepad, where jscalibrator will give "1"...)

[B]
SO, JUST INSTALL :[/B]

```

sudo apt-get install kcontrol

```

And it will work with ALL games !!!


:) :)


**EDIT :**

That works well with the joystick package too :

```

sudo apt-get install joystick
jscal -c /dev/input/js0

```

then you can : "man jscal" and "man jstest".

```

jstest

```

Verify that jstest takes values likes -32767 / 32767 !!!!


Hey 
many, many thanks.
The D ring on my sidewinder hasn't been working since i reinstalled a month or two back, tried alot of things all to no avail.
Kcontrol did the trick for me, so back to SuperTux from the arm chair :)
Cheers!

---

### Post by Jolly-Swagman on 2007-08-17
Hey Great Tutorial thanks for the Heads up. will be Implementing this with my Logitec Digital Sidewinder extreme Pro Pad

Thanks Jolly Swagman

---

### Post by kingmob on 2007-10-22
I just updated to gutsy, and i'm having many problems with my gamepad now. First qjoypad utilized 100%cpu. I replaced it by a custom package from some frenchdude with the same problem. However, now I have a bogus extra axis being reported by all programs. This axis interferes with several others, making everything unusable.  How do i tell jscalibrator the axis doesn't actually exist???

---

### Post by tukuyomi on 2007-10-27
Hi all
I'm using Debian Testing, but it happens with Gutsy too (2.6.22 kernel)
My Sidewinder Gamepad (MIDI port, not USB) runs, but is not usable.
lsmod reports that analog and emu10k1_gp (my gameport on the SBLive! soundcard) are loaded:
```
lsmod | grep game
gameport               15304  4 analog,emu10k1_gp
```
However, when I od /dev/input/js0, I see lots of garbage, even if I don't touch anything...
```
od /dev/input/js0 
0000000 024454 000027 000000 000201 024454 000027 000000 000601
0000020 024454 000027 000000 001201 024454 000027 000000 001601
0000040 024454 000027 000000 000202 024454 000027 000000 000602
0000060 024454 000027 106376 001202 024454 000027 106376 001602
0000100 024470 000027 000001 000001 024470 000027 000001 000401
0000120 024504 000027 000000 000001 024504 000027 000000 000401
0000140 024520 000027 000001 000001 024520 000027 000001 000401
[...]
```
And that doesn't stop...
Using jscal and jscalibrator don't change anything too
On Feisty and before, I solved my problem by simply blacklisting analog and loading sidewinder instead. That way, my gamepad worked flawlessly on every program I used. od /dev/input/js0 returned 5 lines right away and more as I pressed buttons.

But since 2.6.22 (I suppose) that doesn't work. When modprobe-ing -r analog and modprobe-ing sidewinder, /dev/input/js0 doesn't exist anymore

[http://ubuntuforums.org/showthread.php?t=16089](http://ubuntuforums.org/showthread.php?t=16089)
Here is a topic describing similar problem but there is no real workaround/fix. Anyone can help? Thanks in advance (for reading^^)

---

### Post by pzs on 2007-11-04
This procedure did not work for my Microsoft Sidewinder Force Feedback Pro on Gutsy. After I do this:

```

cd /dev/input
sudo MAKEDEV js
```

and this

```

sudo modprobe joydev
sudo modprobe ns558
sudo modprobe analog 
sudo modprobe sidewinder
sudo modprobe iforce 
sudo modprobe evdev 
```

I get this out of dmesg:

```

[  409.618260] gameport: NS558 PnP Gameport is pnp00:09/gameport0, io 0x200, speed 828kHz
[  409.640285] analog.c: Unknown joystick device found  (data=0x5, pnp00:09/gameport0), probably not analog joystick.
[  411.527673] sidewinder.c: unknown joystick device detected on pnp00:09/gameport0, contact <vojtech@ucw.cz>
[  411.527683] sidewinder.c: ID packet, 42 bits. [01000000000]
[  411.527689] sidewinder.c: Data packet, 16 bits. [0207]
[  417.387224] usbcore: registered new interface driver iforce
```

Then I try jscal or jstest and they say variants on "no such device". Is there anything else I could have missed?

Peter

---

### Post by ArrayedTrouble on 2007-11-17
> **tukuyomi said:**
> My Sidewinder Gamepad (MIDI port, not USB) runs, but is not usable.

I had the same problem and fixed it (for me at least).

> **tukuyomi said:**
> ```
gameport               15304  4 analog,emu10k1_gp
```

The problem seems related to the *analog* kernel module. Please try ```
dmesg|grep input
``` If you get something like ```
input: Analog 4-axis 4-button joystick as /class/input/input7
``` the SideWinder is incorrectly detected (and the resources claimed before the *sidewinder* module can even detect it).

Now, for starters, remove all relevant kernel modules
```
sudo modprobe -r sidewinder
sudo modprobe -r joydev
sudo modprobe -r ns558
sudo modprobe -r analog
```

Then insert them back in without the *analog* module
```
sudo modprobe ns558
sudo modprobe sidewinder
```
I didn't need to specify the joydev module here - it gets auto-loaded.

Now when you try ```
dmesg|tail
``` it should say something similar to ```
input: Microsoft SideWinder GamePad as /class/input/input9
``` You can test it with *jstest* or whatever you choose.

To get this permanently fixed, you have to blacklist the *analog* module like ```
sudo vim /etc/modprobe.d/blacklist-analog
``` (open in whatever editor you like)
Put the following into the file and save it
```
# intervenes with sidewinder module
blacklist analog
```

Now, if you still have *ns588* and *sidewinder* in your */etc/modules*, it should work directly after rebooting.

Hope i could help

---

### Post by eightysix on 2007-11-18
Hm, I tried ArrayedTrouble's solution, but I'm still not getting a response from dmesg saything that my Sidewinder was connected. D:

---

### Post by Sockerdrickan on 2007-11-18
Hm all I had to do was to plug it in lol :S

---

### Post by tukuyomi on 2007-11-18
Nope, it doesn't work for me... :/ the only way is to get back to an older kernel...
```
gameport: EMU10K1 is pci0000:01:07.1/gameport0, io 0xc400, speed 59659kHz
sidewinder.c: unknown joystick device detected on pci0000:01:07.1/gameport0, contact <vojtech@ucw.cz>
sidewinder.c: ID packet, 48 bits. [fbffffffffff]
sidewinder.c: Data packet, 16 bits. [bfff]
```

---

### Post by eightysix on 2007-12-06
Let's perform some thread necromancy here...

Has anyone looked into or tried using a gameport to USB adapter for the Sidewinder? It's been killing me that I haven't been able to use my Sidewinder to play games. :(

Any thoughts?

---

### Post by tukuyomi on 2007-12-06
> **eightysix said:**
> Let's perform some thread necromancy here...

Has anyone looked into or tried using a gameport to USB adapter for the Sidewinder? It's been killing me that I haven't been able to use my Sidewinder to play games. :(

Any thoughts?
Downgrading to Feisty Kernel =)
Seriously, I think that emu10k1-gp is broken, not sidewinder => [http://forums.debian.net/viewtopic.php?t=21852](http://forums.debian.net/viewtopic.php?t=21852)
To be continued...

---

### Post by Wazeem on 2007-12-07
Hello

I am using a Ps2 to usb converter and in windows it always worked normally as a game pad.

In ubuntu the device manager shows the controllers (similar to how windows) but when i run my game (gxmame in this case) the controls dont work. Not even the buttons.

I have tried the calibrator which the controller worked for and I have also installed the Kcontrols too but that changed nothing,

Any help would be appreciated.

EDIT: SOLVED - heres the solution for future readers...
> 
A workaround to this problem is to change .kxmame/options/default so that joytype is the one you want. In my case I want SDL joystick so it would be 5. You just have to make sure you don't go and mess with it in the GUI because then you will have to fix the file all over again.

Please fix the program so that the GUI selects the correct joytype number. ALL versions of this program seem to have this problem.

oh and that solution is for kxmame not gxmame. If your using gxmame i would suggest using kxmame as its much more easier to deal with. And your controller joytype will not be 5 like mine it could be anything. Best thing to do is play with the command line version of xmame and keep trying the joytype <a number> until mame can see your joystick.

---

### Post by thane1 on 2007-12-30
Has anybody had problems with qjoypad3 not being able to recognize keyboard key presses, while trying to program buttons?  I'm puzzled.  First saw this thread a few days ago, while trying to get my old MS sidewinder dual strike gamepad working.  Jscalibrate and joystick didn't seem to do anything at all for me in Ubuntu 7.10 Gutsy.  My joystick was definitely present in /dev/input/js0.  But it wouldn't work in either Doom3 or Sauerbraten (the first 2 games I used to try to get gamepad working.)  After reading online reviews, I bought a Logitech Cordless Rumblepad II, which supposedly ran out of the box.  When this wouldn't run either I finally dumped jscalibrate and joystick and settled on qjoypad3 compiled after (simplified here) installing qt3 cross platform programs and libxtst.  Qjoypad worked fine for the axes but wouldn't "take" any keybd key input, when prompted at the button entry stage.  However at this point, mouse clicks elsewhere on-screen would sometimes delete files, which had to be recovered from Trash.  I've spent hours determining all of my keybd key numbers and then programming the corresponding key numbers into qjoypad's hidden /home/usrname/.qjoypad3 file to get my buttons working.  So it works now for Doom3, but I'll have to manually do this for probably each game in future, unless I can determine how to fix the gui button input problem.  Has anyone had this problem?  I did a bit of reading up on focus, thinking this might be a lead, but not really good enough yet to understand how that works in Ubuntu (or if it even really applies in this case).

---

### Post by Hyrsut on 2008-01-12
hi everyone,

i managed last night to make working my sidewinder force feedback pro on game port.

the way to do it is here :

 [http://forum.ubuntu-fr.org/viewtopic.php?pid=1351690#p1351690](http://forum.ubuntu-fr.org/viewtopic.php?pid=1351690#p1351690)


enjoy....

---

### Post by thane1 on 2008-01-15
I have my usb Cordless Rumblepad II installed and running in Ubuntu 7.10 Gutsy.  Wasn't easy (for me at least), but here's what I needed to do.  Install Qjoypad.  Forget the jscalibrate and joystick programs for a usb gamepad (from my experience anyway).  They may be req'd for non-usb but trying to use them seemed to lead me down a dead end.  This qt3-compiled program needed a bunch of stuff installed first through Synaptic though for a successful instl'n. I needed libqt3-mt-dev (has to be the "3" version apparently, as the "4" version is not backwards compatible.)  qt3-dev-tools (which will be installed with all of the dependencies from above prog by default.  libxtst-dev to take the place of the lXtst requirement.  libqt3-mt and libaudio2.  Also g++ is req'd.  With the qt3 during the compiling, etc process the make command will use qmake instead (Somewhere there should be a simple howto for this, but I'm d***ed, if I could find anything out there to easily explain this stuff to someone, who has never done this before.  Once the configure and qmake procedures are done, "sudo" will need to be used to do the make install step.  I installed the 386 source code version.  I used Doom3 from [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for the test game to set everything up for my gamepad.  I'm running the i486 version of Gutsy Ubuntu and the by-default-installed 386 libraries will let you run Doom3 on the 486 version of linux.  It needs the 5 pak files copied in from the store-bought Windoze Doom3 game cd's (copied into the doom3/base/ directory) and then lastly the software key entered to work.  Once qjoypad3 has been configured for the Doom3 game buttons, mouse movements, etc the game can be played I had to do this by working out the codes for my keybd keys and manually editing the hidden /home/usrname/.qjoypad3/doom3.lyt file, which I had set up, because for some reason qjoypad wouldn't recognize keybd clicks from my MS keybd.  Before starting Doom3 I had to start qjoypad with the command qjoypad --device /dev/input (in order for qjoypad to find my usb gamepad, which shows up as js0 in the /dev/input directory.)  If you want to know if your js0 gamepad actually works by the way, from terminal enter cat /dev/input/js0 and then press some buttons on your gamepad.  If odd characters show up in the cat'ed /dev/input/js0 file as you press buttons, then Ubuntu is recognizing the presence of your usb gamepad.  Thanks to Nate from the qjoypad team for the aforementioned tip.  Hope this explanation helps someone, who was having the same problems as I was.  If there's anything wrong here in my description, please feel free to correct.

---

### Post by PiJ on 2008-02-25
Hello to everyone.

First, thanks for the really good howto, it helped a lot.

But now to my strange problem, that's what I call it.
I've done everything like u described and it works - sometimes :D. After I set the option for the snd_ens1371 as described it worked great, but after trying to run it automatically on linux boot following your instructions, the gamepad wasn't recognized by the system anymore. So I unmade the changes for automatically starting. The result is, that, when I manually make the changes to get the gamepad to be recognized by Ubuntu, it sometimes works and sometimes not.

I have no idea what the problem might be, so maybe someone can help me with that.

My system: Ubuntu Gutsy 32, Soundblaster PCI 128, MS Sidewinder Game Pad.

---

### Post by gear_head on 2008-04-20
Great How To, should be stickied if it hasn't been already>

That being said:

When I rebooted the device js0 no longer existed.

Do I have to run MAKEDEV as root for it to be permanent?

---

### Post by grossaffe on 2008-04-20
> **thane1 said:**
> Has anybody had problems with qjoypad3 not being able to recognize keyboard key presses, while trying to program buttons?  I'm puzzled.  First saw this thread a few days ago, while trying to get my old MS sidewinder dual strike gamepad working.  Jscalibrate and joystick didn't seem to do anything at all for me in Ubuntu 7.10 Gutsy.  My joystick was definitely present in /dev/input/js0.  But it wouldn't work in either Doom3 or Sauerbraten (the first 2 games I used to try to get gamepad working.)  After reading online reviews, I bought a Logitech Cordless Rumblepad II, which supposedly ran out of the box.  When this wouldn't run either I finally dumped jscalibrate and joystick and settled on qjoypad3 compiled after (simplified here) installing qt3 cross platform programs and libxtst.  Qjoypad worked fine for the axes but wouldn't "take" any keybd key input, when prompted at the button entry stage.  However at this point, mouse clicks elsewhere on-screen would sometimes delete files, which had to be recovered from Trash.  I've spent hours determining all of my keybd key numbers and then programming the corresponding key numbers into qjoypad's hidden /home/usrname/.qjoypad3 file to get my buttons working.  So it works now for Doom3, but I'll have to manually do this for probably each game in future, unless I can determine how to fix the gui button input problem.  Has anyone had this problem?  I did a bit of reading up on focus, thinking this might be a lead, but not really good enough yet to understand how that works in Ubuntu (or if it even really applies in this case).

yeah, i had the same problem and found the same solution... trial and error in the config file.

---

### Post by landeel on 2008-04-20
[http://www.mediafire.com/?msitbdej0ad]("http://www.mediafire.com/?msitbdej0ad")
This is patched version of the **jscal** utility from the **joystick** package. It will allow the remapping of buttons and axes directly into the driver.
It's compiled for Ubuntu 7.10 AMD64, but you can recompile it to any version by doing a "**make clean;make**"

I have been looking for something like this for ages. Found it here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142")
I have many joypads / joysticks with many different button layouts, and by using this utility I can reconfigure the button layout by running a simple script, intead of reconfiguring every game and emulator everytime I want to use a different joystick.
Hope you find it useful.

---

### Post by wootah on 2008-06-18
For those with Xbox and Xbox 360 controllers, [see Howto: Use Xbox Controllers (original, 360, 360 wireless, 360 guitar) with Linux]("http://ubuntuforums.org/showthread.php?t=825464") :)

---

### Post by Maike05 on 2008-07-13
Hi, I've a MS Sidewinder precision racing wheel USB.

It is well detected and I've managed to calibrate it, but the programs (jstest, or jscalibrator or kcontrol) detect an 9th button that doesn't exist ! Moreover the buton is pressed by default !

How can I disable it ?

Thanks.

---

### Post by Maike05 on 2008-07-13
Hi, I've managed to disable It by downloading this version of jscal [http://www.mediafire.com/?msitbdej0ad](http://www.mediafire.com/?msitbdej0ad)

1) extract
2) open a terminal in the folder
3) type 'make clean' then 'make'
4) download this file [http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=joystick.diff;att=1;bug=444142](http://bugs.debian.org/cgi-bin/bugreport.cgi?msg=5;filename=joystick.diff;att=1;bug=444142) and place it in the folder.
5) run the prog jscal by typing the full path in a terminal.
6) type '~/jscal-patched-amd4-ubuntu7.10/jscal' /dev/input/js0 -c to calibrate the joystick
7) Finally type '~/jscal-patched-amd4-ubuntu7.10/jscal' /dev/input/js0 -u 3,0,1,5,9,288,289,290,291,292,293,294,295,511
 to disable the 9th button

The last command put the maximum value 511 for the 9th in order to disable it. Minimum is 256.

Now, It works great with wine :)
Hope it helped ;)

---

### Post by minitchoup on 2008-09-28
I managed to run my joystick : a sidewinder force feedback pro (FFP) on gameport with a kernel 2.6.24.

Before, when I load the module sidewinder I had the following message:

"sidewinder.c: unknown joystick device detected"

Detection joystick successful only if it was not powered.

Now it's ok. For this, I edit sidewinder.c like this :
```

line 693-694 :
                                 case 48: /* Ambiguous */
                                         if (j == 14) { /* ID length 14*3 -> FFP */

become :

                                case 16:
                                  sw->bits = 3;
                                case 48: /* Ambiguous */
                                         if (j == 14) { /* ID length 14*3 -> FFP */

```
when the power is turned off, mode = 3 and length = 16 => case 48
when the power is turned on, mode = 1 and length = 16 => case 16

To correct the module, you must do the following :
1/ Edit /usr/src/linux/drivers/input/joystick/sidewinder.c
2/ in a shell : cd /usr/src/linux ; make && make modules_install

To run my joystick I must do in a shell : 

# modprobe joydev
# modprobe gameport
# modprobe sidewinder

---

### Post by AJSB on 2008-11-11
Thank you, Thank you, Thank you !!!! =D>:biggrin:

I finally got, thanks to you, my KOnig Gaming gamepad (6axis + 12 buttons) working with games like True Combat:Elite, Enemy Territory Quake Wars, Enemy Territory Wolfenstein,etc. :D

The game pad is replacing in a very positive way, not only the keyboard but also the mouse :D


> **thane1 said:**
> I have my usb Cordless Rumblepad II installed and running in Ubuntu 7.10 Gutsy.  Wasn't easy (for me at least), but here's what I needed to do.  Install Qjoypad.  Forget the jscalibrate and joystick programs for a usb gamepad (from my experience anyway).  They may be req'd for non-usb but trying to use them seemed to lead me down a dead end.  This qt3-compiled program needed a bunch of stuff installed first through Synaptic though for a successful instl'n. I needed libqt3-mt-dev (has to be the "3" version apparently, as the "4" version is not backwards compatible.)  qt3-dev-tools (which will be installed with all of the dependencies from above prog by default.  libxtst-dev to take the place of the lXtst requirement.  libqt3-mt and libaudio2.  Also g++ is req'd.  With the qt3 during the compiling, etc process the make command will use qmake instead (Somewhere there should be a simple howto for this, but I'm d***ed, if I could find anything out there to easily explain this stuff to someone, who has never done this before.  Once the configure and qmake procedures are done, "sudo" will need to be used to do the make install step.  I installed the 386 source code version.  I used Doom3 from [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for the test game to set everything up for my gamepad.  I'm running the i486 version of Gutsy Ubuntu and the by-default-installed 386 libraries will let you run Doom3 on the 486 version of linux.  It needs the 5 pak files copied in from the store-bought Windoze Doom3 game cd's (copied into the doom3/base/ directory) and then lastly the software key entered to work.  Once qjoypad3 has been configured for the Doom3 game buttons, mouse movements, etc the game can be played I had to do this by working out the codes for my keybd keys and manually editing the hidden /home/usrname/.qjoypad3/doom3.lyt file, which I had set up, because for some reason qjoypad wouldn't recognize keybd clicks from my MS keybd.  Before starting Doom3 I had to start qjoypad with the command qjoypad --device /dev/input (in order for qjoypad to find my usb gamepad, which shows up as js0 in the /dev/input directory.)  If you want to know if your js0 gamepad actually works by the way, from terminal enter cat /dev/input/js0 and then press some buttons on your gamepad.  If odd characters show up in the cat'ed /dev/input/js0 file as you press buttons, then Ubuntu is recognizing the presence of your usb gamepad.  Thanks to Nate from the qjoypad team for the aforementioned tip.  Hope this explanation helps someone, who was having the same problems as I was.  If there's anything wrong here in my description, please feel free to correct.

---

### Post by tulcak on 2009-11-10
this is ********.  what is an operating system supposed to do?  give you a command line?  then, why a GUI?  and why a joystick?  and why a flight simulator?  maybe you can fly blind with a keyboard and audio beeps...

---

### Post by dumpster25 on 2009-12-24
I go my TWO Sidewinder Gamepad (daisychained) working with the following modules sharing one gameport.

I followed the guide on this thread for the snd_ens1731. That's the soundcard I had.

Connect both gamepads to the gameport.

Then in the terminal run:
#sudo MAKEDEV js

Then:

#sudo modprobe -v joydev
#sudo modprobe -v sidewinder

Also by adding the extra line onto /etc/module/options:
options snd_ens1371 joystick_port=1

(On karmic i had to call this file /etc/module/snd_ens1371.conf instead of the name above)

This should be enough to have both gamepads up and running.

I ran into a problem at the beginning. When loading the modules with modprobe I only had one gamepad connected to the gameport. It resulted in only one working even though they were daisychained.

The solution was to unload the modules by running:

#sudo modprobe -rv joydev
#sudo modprobe -rv sidewinder

then delete /etc/input/js with:

#MAKEDEV -d js

Then I reconnected the second gamepad. And then ran:

#sudo MAKEDEV js

And Finally:
#sudo modprobe -v joydev
#sudo modprobe -v sidewinder

dmesg, showed both gamepads being detected.
And jstest showed that they worked corectly. 

Thank you adam0509 for this awesome post. Thanks to this HOWTO I could play Street Fighter II Turbo with my brother on Xmas :D

---

### Post by Rushlight on 2013-04-15
ive tried everything sugested that applies.
i have a logitech dual action usb gamepad. almost all of the apt-gets listed return with a "unable to locate etc..etc..". the joystice one works but.. none of the commands seem to. i have Ubuntu 12.04.2. i NEEEED this to play KSP.

Help PLZ

---

### Post by overdrank on 2013-04-15
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

