---
title: "Playstation Controller Adapter"
date: 2007-04-28
forum: Gaming &amp; Leisure
---

### Post by cabbage on 2007-04-28
Dear all,

I've just brought an [EMS USB2]("http://www.hkems.com/product/ps2/ps2-usb2.htm") adapter with the aim of using my two playstation dance mats on Ubuntu with [stepmania]("http://www.stepmania.com").

The problem I have is that ubuntu only creates one new joystick device when its plugged in, and so both mats appear as the same one. I get the following in syslog:

> Apr 28 16:35:55 localhost kernel: [11035.732000] usb 1-1: new low speed USB device using uhci_hcd and address 2
Apr 28 16:35:55 localhost kernel: [11035.908000] usb 1-1: string descriptor 0 read error: -32
Apr 28 16:35:55 localhost kernel: [11035.924000] usb 1-1: string descriptor 0 read error: -32
Apr 28 16:35:55 localhost kernel: [11035.924000] usb 1-1: configuration #1 chosen from 1 choice
Apr 28 16:35:55 localhost NetworkManager: <debug info>^I[1177774555.703793] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_b43_3_noserial').
Apr 28 16:35:55 localhost kernel: [11035.944000] usb 1-1: string descriptor 0 read error: -32
Apr 28 16:35:55 localhost kernel: [11035.964000] usb 1-1: string descriptor 0 read error: -32
Apr 28 16:35:55 localhost kernel: [11036.124000] usbcore: registered new interface driver xpad
Apr 28 16:35:55 localhost kernel: [11036.124000] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
Apr 28 16:35:55 localhost kernel: [11036.176000] usbcore: registered new interface driver hiddev
Apr 28 16:35:55 localhost kernel: [11036.216000] input: HID 0b43:0003 as /class/input/input7
Apr 28 16:35:55 localhost kernel: [11036.216000] input: USB HID v1.00 Joystick [HID 0b43:0003] on usb-0000:00:04.2-1
Apr 28 16:35:55 localhost kernel: [11036.216000] usbcore: registered new interface driver usbhid
Apr 28 16:35:55 localhost kernel: [11036.216000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Apr 28 16:35:55 localhost NetworkManager: <debug info>^I[1177774555.998335] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_b43_3_noserial_if0').
Apr 28 16:35:56 localhost NetworkManager: <debug info>^I[1177774556.068602] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_b43_3_noserial_usbraw').
Apr 28 16:35:56 localhost NetworkManager: <debug info>^I[1177774556.269265] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_b43_3_noserial_if0_logicaldev_input').

Just as a test I tried this with windows, and it showed up as two new game controllers, as expected, so I'm wondering if there is some way to tweak ubuntu into creating two devices.

Thanks for your help,

Cabbage.

---

### Post by voidmage on 2007-04-28
I'm having the exact same problem. It looks to be a kernel issue. This wasn't a problem in 2.6.17 (edgy) but isn't working right in 2.6.20 now.

[http://kerneltrap.org/node/2199#comment-233966](http://kerneltrap.org/node/2199#comment-233966)

---

### Post by buttons on 2007-04-28
> **voidmage said:**
> I'm having the exact same problem. It looks to be a kernel issue. This wasn't a problem in 2.6.17 (edgy) but isn't working right in 2.6.20 now.

[http://kerneltrap.org/node/2199#comment-233966](http://kerneltrap.org/node/2199#comment-233966)

Interesting.  I have a pu203 adapter and it apparently has the same problem.  It's definitely a 2.6.20 issue, as my 2.6.19 kernel runs just fine.

---

### Post by DARKGuy on 2007-04-29
You could also cut the PSX connector and use both dance mats with a DB29 male adapter (the one that looks like the printer LPT1 connector), some soldering skills, good brains and a good guide. There are guides online that teach you how to convert PSX pads to parallel port connection. I dunno about dance mats but my PSX controller is working fine and dandy both in Windows and Linux with that. :P Maybe not what you're looking for but it's a try XD jsut make sure you have other dance mats around in case you screw up :P

---

### Post by cabbage on 2007-04-29
Hmm... I've tried the EMS adapter on two different edgy machines and both give the same problem i.e. only one new device. So at least in this case I'm not so sure I can blame the new feisty kernel...

---

### Post by Explodinglemur on 2007-05-16
I did some searching and came across this patch: [http://www.mail-archive.com/git-commits-head@vger.kernel.org/msg10317.html](http://www.mail-archive.com/git-commits-head@vger.kernel.org/msg10317.html)

Grabbed the 2.6.20 source and applied the fix to drivers/usb/input/hid-core.c, built the kernel, installed, and rebooted.  It works!  When I'm more awake I'll see about submitting this to bugs.ubuntu.com and maybe we can get the patch included in the next Feisty kernel update.

---

### Post by cabbage on 2007-05-16
Great work ExplodingLemur! Please let us know what the bug id is if you log it so that I can keep an eye on it - I'd rather not have to compile the kernel if I can avoid it.


Cheers!

---

### Post by voidmage on 2007-05-16
The bug was reported about a month ago:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106622](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106622)

Looks like it should make it into 2.6.22, just in time for gutsy.

---

### Post by Explodinglemur on 2007-05-16
> **voidmage said:**
> The bug was reported about a month ago:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106622](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106622)

Looks like it should make it into 2.6.22, just in time for gutsy.

Your Ubuntu bugtracker search-fu is better than mine :)

---

### Post by voidmage on 2007-05-16
ATTENTION: I am still building my kernel and it's taking a while. For now, directions will be removed until this all is settled.

I'm not sure if this will work for a while, so the best advice I can give is building 2.6.22 (linux-restricted-modules don't exist for .22, afaik).

---

### Post by haylocki on 2007-05-24
Hi,

   I have a working 2.6.22-5-generic kernel on my Feisty system.
   And yes the EMS-II interface is working, now have /dev/input js0 and /dev/input/js1

How I did It :

Open a terminal and :

Type: 
```
sudo gedit /etc/apt/sources.list
```

replace all occurrences of feisty with gutsy

save file

Type : 
```

sudo mkdir /lib/firmware/2.6.22-5-generic
sudo apt-get update
sudo apt-get install linux-image-2.6.22-5-generic linux-headers-2.6.22-5-generic

```

go back to the gedit window and use the undo button to turn all the occurrences of gutsy back to feisty 

save file, and exit gedit.

```
sudo apt-get update
```

You should now see the reboot icon in the right hand side of the top panel, click on this and select reboot. 

Your system should now reboot into the new kernel with a working joypad.

Cheers, Ian

---

### Post by DARKGuy on 2007-05-25
> **haylocki said:**
> Hi,

   I have a working 2.6.22-5-generic kernel on my Feisty system.
   And yes the EMS-II interface is working, now have /dev/input js0 and /dev/input/js1

How I did It :

Open a terminal and :

Type: 
```
sudo gedit /etc/apt/sources.list
```

replace all occurrences of feisty with gutsy

save file

Type : 
```

sudo mkdir /lib/firmware/2.6.22-5-generic
sudo apt-get update
sudo apt-get install linux-image-2.6.22-5-generic linux-headers-2.6.22-5-generic

```

go back to the gedit window and use the undo button to turn all the occurrences of gutsy back to feisty 

save file, and exit gedit.

```
sudo apt-get update
```

You should now see the reboot icon in the right hand side of the top panel, click on this and select reboot. 

Your system should now reboot into the new kernel with a working joypad.

Cheers, Ian

Wouldn't that break Feisty? I'm tempted to try it so I can update my kernel xD but I dunno...

---

### Post by haylocki on 2007-05-25
Hi, 

All you are doing is updating the kernel.

If you find you have problems with the kernel, you can simply reboot with the previous kernel, as that will still be available in the grub menu.

The reason for changing the sources.list file back to feisty, without updating anything but the kernel, was to stop any other updates breaking feisty.

Of course, it's all done at your own risk, and if anyone feels they won't be able to fix their system if it breaks, they would be better off not trying, and waiting for the updated kernel to be back ported from Gutsy to Feisty.

Me I'm just impatient :D and judging by the previous posts so are a few other people.

Cheers, Ian

---

### Post by Explodinglemur on 2007-05-25
That will likely confuse the package manager for future kernel updates on your system.  Gusty is also not anywhere near release status, so who knows what bugs are lurking in that kernel package.  (not likely, but very possible)

---

### Post by haylocki on 2007-05-25
Hi,
     unless feisty tries to update the kernel to an older version than the one I have installed I don't see why it would be a problem. 

As they are already using this version on Gutsy, why would they backport an older version ?

> so who knows what bugs are lurking in that kernel package

So it's wrong to upgrade a buggy kernel, incase you install a buggy kernel ;)

Anyway, each to his own, My system is running fine, and my joypad is working fine.

Cheers, Ian

Edit ;

Installed some upgrades last night, including kernel 2.6.20-16-generic. Had no problems with the upgrade, and can still boot to kernel 2.6.22-5-generic.

---

### Post by Pobega on 2007-05-25
> **haylocki said:**
> Hi,
     unless feisty tries to update the kernel to an older version than the one I have installed I don't see why it would be a problem. 

Even then I don't think that would be a problem. The way of make-kpkg and how GNU GRUB handles different kernels, I think you'll be fine apt-pinning kernels from different released of **any** Debian-based distribution.

---

### Post by yibble on 2007-06-06
Hi,

I hope you're still monitoring this thread. I had the same issue with the EMS USB II under Feisty. Worked perfectly fine in Edgy. I've done some digging, and have now resolved the issue, without compiling an entire kernel. It's possible to just compile the patched module.

I've detailed the steps I followed in a blog post, so sorry for blog-spam: [http://blog.yibble.org/2007/06/06/feisty-usb-joystick-issue-resolved/](http://blog.yibble.org/2007/06/06/feisty-usb-joystick-issue-resolved/)

I hope that helps.

---

### Post by suterb42 on 2007-06-06
I bought a USB adapter at Walmart recently that'll let you use your PS2/XBox/Gamecube controllers with your computer. It also has 2 USB ports. The USB ports work fine under Ubuntu, but I can't figure out how to get my PS2 controller to work. Does anyone have any ideas?

EDIT: It's one of these:

[http://www.futime.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml](http://www.futime.com/display/ft8d91_ps2_xbox_gc_to_pc-usb_converter.shtml)

---

### Post by haylocki on 2007-06-07
Hi suterb42,

What version of Ubuntu are you using ?

If you are using Feisty, then your first step will be to either update your kernel as suggested by me, or follow the instructions posted by Yibble for updating the kernel module.

Cheers, Ian

---

### Post by suterb42 on 2007-06-10
I'm using Feisty. I don't know whether to upgrade the kernel or not because I'm not sure if they have restricted drivers ready for the 2.6.22 kernel. I'll try compiling that patch, although it didn't work the last time I tried. Maybe I did something wrong.

EDIT: The first time I tried compiling it, it gave me a huge amount of errors. I ran "make oldconfig && make prepare", and this is what came out of the second try:

WARNING: Symbol version dump /usr/src/linux-source-2.6.20/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  drivers/usb/input/aiptek.o
  CC [M]  drivers/usb/input/ati_remote.o
  CC [M]  drivers/usb/input/ati_remote2.o
  CC [M]  drivers/usb/input/hid-core.o
  CC [M]  drivers/usb/input/hiddev.o
/bin/sh: scripts/genksyms/genksyms: not found
make[1]: *** [drivers/usb/input/hiddev.o] Error 127
make: *** [_module_drivers/usb/input] Error 2

---

### Post by Explodinglemur on 2007-06-10
suterb42, I had the same problem.  After running make oldconfig and make prepare, run make scripts and then you should be able to compile the module.

---

### Post by suterb42 on 2007-06-10
Here's what I've done so far:

I compiled and installed the patch. Everything worked right on my controller except the arrow keys.I'd get them to move around in jscalibrator, but the cross that tells you if the joystick is centered would jump all over the place. I couldn't get the arrow buttons to work in any other program, either.

I then upgraded my kernel to 2.6.22-6. The arrow buttons won't even work in jscalibrator. The other buttons work fine, though. I tried plugging the converter into different USB slots, with no luck.

---

### Post by haylocki on 2007-06-12
Hi,


is your controller set to analog working ? Try it both ways round.

do the buttons in jscalibrator flicker when you press them ? 

Tried to download the manual on the link you provided, but of course the link for the manual doesn't work. DOH!

Have you tried running jstest ?

The joystick can also be calibrated in kde config. Seems to set up the joystick differently than jscalibrator.

Cheers, Ian

---

### Post by suterb42 on 2007-06-12
The rest of the buttons (button 0, button 1, etc.) all work in jscalibrator, but the arrow buttons don't do much except make little blips on the green status bar beside where the joystick device name is. I can't figure out how to turn analog mode off on the controller. When I press the analog button, it doesn't do anything either. 

I tried running jstest using the --event option. Whenever I hit the arrow keys, it says something like this for every button I press:

Event: type 2, time 5039668, number 9, value 1                 //down arrow pressed
Event: type 2, time 5039668, number 9, value 0                 //down arrow released

However, it's really hard to see that buttons I'm pressing, since I get a lot of similar entries when the controller's just sitting there. (Maybe that's because analog mode is on.) The values of those other entries go all the way up to 128, but I don't know why the values for the buttons I actually press only go up to 1.

I'd try to configure my joystick under KDE, but I don't have KDE installed.

---

### Post by haylocki on 2007-06-14
Hi,

To use the kde calibration tool just :

sudo apt-get install kcontrol

then type :

kcontrol to run it.

Have just run jstest --event on my laptop. You should only get events when the buttons on your joystick are pressed.

my buttons return 0 or 1, which I guess is because they are either on or off. the other values you are seeing are the analog controls, these can go from -32767 to 32767 depending on the program used for calibration. My joypad only returns events on the analog sticks when they are moved. With analog turned off the dpad buttons return  32767 / -32767 instead of the 0 /1

Which PS2 joypad are you using, is it a genuine Sony one ?

Your problem sounds very much like the one I had before updating the kernel so that I could use the fixed joypad driver. Are yiou sure you are running the newer kernel, or patched driver ?

Have you tried using the adaptor in windows ? Just to prove it's working ok. If you don't have windows, maybe take it back to the shop and ask them to test it, with your joystick.

This is a link to a thread which helped me get my joypad working. Just ignore the stuff about the gameport joysticks :

[http://ubuntuforums.org/showthread.php?t=338457](http://ubuntuforums.org/showthread.php?t=338457)

Cheers, Ian

---

### Post by suterb42 on 2007-06-15
My controller is a genuine Sony controller, and the adapter works under Windows. 

When I run "uname -a", it says my kernel is 2.6.22-6-generic.

When I run kcontrol and hit the arrow buttons, the values are between -32768 and 32768. The x in the crosshairs (or whatever it is) doesn't move unless I use the analog sticks, though.

I can turn the red light on the controller on and of by hitting the button below where it says "Analog" while the controller's plugged into my PS2, but it stays on whenever I have it plugged into my converter, no matter how many times I hit the button for it.

I really don't get why any of the programs (kcontrol, for example) see that I'm pushing the arrow buttons and even give values for them, but they don't do anything when I try to use them in a game.

---

### Post by haylocki on 2007-06-15
Hi,  I did a little digging around on the internet after my last post, and discovered that your interface only works in analog mode, that's why you can't turn off analog mode on your joystick.

What games have you tried to use it on ? I'll try them with mine. Getting the joystick to work and getting the joysticks to work with games are 2 different problems.

If you have got the stick calibrated with kcontrol, it is supposed to be more compatible with games, then a joystick calibrated with jscalibrator.

When I press the arrow buttons on my joypad (buttons 13,14,15,16) kcontrol just returns "PRESSED" the same as the other buttons.
if I turn off analog mode, buttons 13-16 still report pressed but I also get values put in the axes
boxes.

The cross hair only moves with my analog sticks as well, unless analog mode is turned off.

I use my joypad on epsxe, and I have just checked that it sees the arrow keys even with the joypad in analog mode.

try installing epsxe (can't remember where I got it from, maybe the epsxe website).
Don't forget the joypad plugin.

once installed goto 

Config -> Ext. Game Pad

I have the  "ammoQ's padJoy Joy Device Driver 0.8" plugin

click on Configure,
check that the "Device file" is pointing to the correct location,
and try to see if the arrow keys are detected ok

I have also successfully used the joypad in mame, you need to enter the  menu and assign the joystick to the correct buttons, but it does work, so maybe you can try that if you don't want to install epsxe. 

Cheers, Ian

---

### Post by suterb42 on 2007-06-15
Whenever I hit an arrow button in kconfig, it doesn't say "pressed". It just gives me a value.

The problem I was having before I tried to fix things was that whenever I ran jscalibrator, the x in the crosshairs (or whatever it is) would move around wildly all by itself. The arrow buttons would work, but not very well. Now I can't get them to work at all.

---

### Post by haylocki on 2007-06-16
Hi, It's looking like your adaptor isn't 100% compatible with the linux driver.

Maybe you can send a message on the mailing list read by the developer that looks after the module. I found the list once, when trying to get my adaptor to work, but unfortunately I can't remember what it is. Try searching for kernel mailing list.

Maybe the easiest solution if you have the money would be to buy a different adaptor.

I use the EMS II USB adaptor, it doesn't have extra usb ports, but supports 2 joysticks, and if used with a PS2 enables you to use a PS1 lightgun. (Hmm.. aparently the PS1 lightgun works anyway ???)

Bit of a cop-out, but is the continued hassle worth the cost of a different adaptor.

Cheers, Ian

---

### Post by suterb42 on 2007-06-16
That still doesn't explain why the arrow buttons quit working after I updated the kernel. I thought that was supposed to fix it.

EDIT: After messing with things for a few minutes, I opened up ZSNES to see what would happen. Not only did the input config screen recognize that I was hitting the arrow buttons, they also worked in the game. That's the only program that I can get the arrow buttons to work with, although I set up Torcs so it could steer with the L1 and R1 buttons. :-D

Do you think there's something specific that makes the arrow buttons not work? I still can't get kconfig to say that I'm pressing the buttons.

---

### Post by suterb42 on 2007-06-17
Here's a quick follow-up:

I went back into Torcs today to see if I could get the arrow buttons to work. I never noticed that something would pop up saying "Calibrate" when I tried making the arrow buttons control the steering, or I just ignored it, thinking it wasn't important. Well, I saw it today and after I configured the buttons, I've got them working right. :-D

---

### Post by haylocki on 2007-06-20
Hi,sorry for the delay, been putting a new hard drive in my laptop, takes forever to backup and restore through USB 1.0. 

Glad you finally got your joystick working :)

You said :> 

After messing with things for a few minutes

Could you post a reply saying what you actually did, so that anyone else following this thread with the same problem will know what to do to get it working.

Cheers, Ian

---

### Post by suterb42 on 2007-06-21
I really don't know what I did. The only thing I can think of that helped was to calibrate the controller under Torcs. I'm guessing it was a typical PEBKAC situation: the controller was working fine and I didn't realize it.

EDIT: I can confirm that it was a PEBKAC. I decided to reinstall Feisty after trying Gutsy for a few days. After updating the kernel by following the walkthrough on page 2, the controller works fine. Sorry for all the aggravation.

---

