---
title: "HOWTO:  Enabling an analog Joystick (+Flightgear)"
date: 2005-08-07
forum: Gaming &amp; Leisure
---

### Post by evilghost on 2005-08-07
After about an hour of searching, I finally was able to get my CH products Flight Sim yoke working under Ubuntu as well as Flightgear.  I will attempt to document and clarify the steps I used to get my joystick working with Ubuntu in addition to FlightGear.  Should any of the information be incorrect, please feel free to correct me.

This howto assumes you have an analog joystick connected to the gameport/MIDI port of your already functioning sound card.

Perform the following steps in a terminal:
```

cd /etc/init.d
sudo gedit joystick

```

Paste the following lines into gedit, and save the file:
```

#! /bin/sh
# /etc/init.d/joystick
#

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Enabling Joystick"
    cd /dev
    rm js*
    mknod input/js0 c 13 0
    ln -s input/js0 js0
    modprobe joydev
    modprobe analog
    echo "DONE!"
    ;;
  stop)
    rmmod joydev
    rmmod analog
    echo "DONE!"
    ;;
  *)
    echo "Usage: /etc/init.d/joystick {start|stop}"
    exit 1
    ;;
esac

exit 0

```

Now, make the file executable.
```

sudo chmod 755 joystick

```

Configure the system to run /etc/init.d/joystick on boot:
```

sudo update-rc.d joystick defaults

```

Enable the joystick:
```

sudo /etc/init.d/joystick start

```

**If you are not using Flightgear, you are done.  Your joystick should now work correctly and be enabled.  If you are using Flightgear and hope to get the joystick working with Flightgear, please proceed with the below steps:**

```

cd ~
fgjs
[Follow the onscreen directions, assigning the buttons/axies (sp?) as needed.]

```

Once you have completed the fgjs program and are happy with the configuration, type:
```

cat fgfsrc.js >> .fgfsrc

```

Now, load FlightGear and your joystick should work and use the button/axis assignments you specified.  If you make a mistake during fgjs or are unhappy with your assignments **BEFORE** you ran the "cat fgfsrc.js >> .fgfsrc" code simply run the below command again to recreate fgfsrc.js
```

rm fgfsrc.js
fgjs

```

I hope this helps someone, if you have problems or find any sections that are incorrect or do not work correctly please be sure to speak up.

---

### Post by xmastree on 2005-08-10
[QUOTE=evilghost]if you have problems or find any sections that are incorrect or do not work correctly please be sure to speak up.[/QUOTE]
```
root@ubuntu:/etc/init.d # /etc/init.d/joystick start
Enabling Joystick
rm: cannot remove `js*': No such file or directory
DONE!
root@ubuntu:/etc/init.d #  /etc/init.d/joystick stop
DONE!
root@ubuntu:/etc/init.d #  /etc/init.d/joystick start
Enabling Joystick
mknod: `input/js0': File exists
DONE!
root@ubuntu:/etc/init.d #

```
Is this a problem? And, how does one actually use the joystick? I was wonding if it's possible to use it for tuxracer.
It's a Thrustmaster FCS MkII

---

### Post by trigeorgis on 2005-08-10
Actually, I have the same error (?)

```

**root@Trigeorgis:/home/george #** * /etc/init.d/joystick start*
[I]Enabling Joystick
mknod: `input/js0': File exists
DONE![/I]
**root@Trigeorgis:/home/george #** *jstest /dev/js0*
*jstest: No such device*

```

My joystick although, is very old and I am not sure if it is works :p

*btw, is a dexxa js.

---

### Post by tigrez on 2005-10-23
I've the same problem. My old joypad Gravis is attached to sound card cmi3878. By default the gameport is disabled, and to enable i need to change and option: "joystick 1". I've searched in the web but I've find nothing to help me... Is a option to add in the alsa.conf? I need to rebuild alsa drivers? 
Please HELP ME!!!!

---

### Post by tigrez on 2005-11-02
I've solved my problem. I think is important do add this thing in the howto:
If you have a joystick port attached sound card you must indicate to alsa to activate this port.
$ cd /etc/modprobe.d/
**$ sudo nano alsa-base**
in this file alsa look the sound card option. Go at the end of the file and add this string:

options snd-xxxx joystick_port=1

where xxxx is the driver of your sound card.

save and restart alsa (or reboot, it's more easy ;-) )
Excuse me for my bad english...

---

### Post by sharke on 2006-01-04
you can add the commands to /etc/init.d/bootmisc.sh file.
for my analog joystick i added
sudo modprobe ns558
sudo rmmod ns558  (this is required on my stem because doesnt load correctly)
sudo modprobe ns558
Thanks to Happytux for this info.
Regards
sharke

---

### Post by kanibalv on 2006-03-25
i did the steps of the main post and kubuntu recognize a joystick in /dev/js0, but my JS is of 2 axis and 8 buttons, and it show 4 axis and 4 buttons, how can i do for resolv this?


kanibalv
[email]kanibalv@gXail.com[/email] ==> X=m

---

### Post by ljubomir on 2006-08-25
> **kanibalv said:**
> i did the steps of the main post and kubuntu recognize a joystick in /dev/js0, but my JS is of 2 axis and 8 buttons, and it show 4 axis and 4 buttons, how can i do for resolv this?


same problem here :(

---

### Post by sc0000 on 2007-03-15
I know the only person who's going to be able to fix this problem is the person who wrote the linux joystick driver 2.0 module, BUT i have a similar problem to everyone. 

I have a SB audigy, and have figured out how to get the joystick port to take button presses but it still thinks that i have a 4-axis gamepad. I don't know if autodetection is messed up or what, but i simply need to tell the computer what's plugged into it. a 2 axis, 6 button gamepad. 

the module which should take the option for this configuration is "analog"
**$ sudo modprobe -v analog js=gamepad8**
but that doesn't work and i don't know the real option to use with the module, or what module to use the option with
here's my dmesg:
> [42949925.400000] gameport: EMU10K1 is pci0000:02:0b.1/gameport0, io 0xdc58, speed 962kHz
[42949925.440000] input: Analog 4-axis 4-button joystick as /class/input/input6
[42949958.900000] joydump: Unknown parameter `js'


---

### Post by sc0000 on 2007-03-16
Well I found the module parameter and added this line to /etc/modprobe.conf 
```
options analog map=gamepad8
```

Now, js0 still fails to work on a regular basis. Here's what I've been trying
```
# mknod /dev/input/js0 c 13 0 
# modprobe -v emu10k1-gp
# modprobe -v gameport
# modprobe -v joydev
# modprobe -v analog
# modprobe -v joydump
```

Everything seems to work but 
```
cat /dev/input/js0
```
returns
cat: /dev/input/js0: No such device

---

### Post by ernierasta on 2007-04-20
I had observed, that after calibration axes don't work. It is easy fix here: 
for USB devices - replug them
for Gameport - unload kernel joystick (joypad) modules and load them again.

It works for me!

---

### Post by MattiJ on 2007-04-25
Thanks for that! had all trouble getting my Logitech wingman cordless usb gamepad to work in cedega and nfs carbon. At first it seemed to get some analog input but moving in some direction all the time. Then I used  jstest /dev/input/js0
 and got this.
Joystick (Logitech WingMan Cordless Gamepad) has 7 axes (X, Y, Z, Rz, Throttle, Hat0X, Hat0Y)

but in cedega joystick setting I put (X,Y,none,none,none,none,none) and that solved the movement trouble. My guess is that wath I got from jtest was not correct.
Anyway after clibration  with jscalibrator I got no analog reaction in nfs! but the simple unplug/replug did fix this.
Hope this can help others hawing similar troubles.

---

### Post by rasemmi on 2007-04-27
Hiho,

thanks to "tigrez" (see above) I finally managed to get my gameport on a sound card "Creative Labs CT4810 - Ensoniq AudioPCI ES1371" working. :) Thanks indeed, tigrez! :)
I first had to enable native ALSA gameport support!

So, I made a little and very brief HowTo for myself just to note down the required steps for my ubuntu future. ;)

If you appreciate my thankful feedback, see below.

Regards raLLi (OK, on the web rasemmi)


Standard analog joystick on standard gameport, raLLi S. 04/2007,
ubuntu 6.06.1 LTS, Dapper Drake.

Works with gameport on sound card:
- Creative Labs CT4810 - Ensoniq AudioPCI ES1371
- Terratec 128iPCI


1)	Check if gameport-driver-module and what ALSA-driver-module is loaded
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Terminal command:

ubuntu@ubuntu-desktop:~$ lsmod
[...]
gameport               15496  3 analog,snd_ens1371
[...]
ubuntu@ubuntu-desktop:~$


2)	Native ALSA gameport support
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Needed for Creative Labs CT4810 - Ensoniq AudioPCI ES1371.
NOT needed for Terratec 128iPCI.


2.1)	Check if gameport is supported natively by ALSA
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
File:
/usr/share/doc/alsa-base/driver/joystick.txt

"The following PCI drivers support the joystick natively..."

Comment:
If your gameport is NOT natively supported by ALSA (as for sound card Terratec 128iPCI) proceed with 3).


2.2)	Check if native ALSA gameport support is enabled
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Terminal command:

ubuntu@ubuntu-desktop:~$ cat /proc/asound/card0/audiopci
Ensoniq AudioPCI ES1371

Joystick enable  : off
Joystick port    : 0x200
ubuntu@ubuntu-desktop:~$


2.3)	Enable native ALSA gameport support
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
File: 
/etc/modprobe.d/alsa-base

Entries:
# Enable native ALSA gameport support for Creative Labs CT4810, Ensoniq AudioPCI ES1371 (default = disabled)
options snd-ens1371 joystick_port=1


2.4)	Reboot
~~~~~~~~~~~~~~


3)	Enable joystick
~~~~~~~~~~~~~~~~~~~~~~~


3.1)	Enter required joystick-driver-modules permanently
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
File: 
/etc/modules

Entries:
# Enable standard-analog-joystick on gameport
joydev
analog

Comment:
Joystick-driver-module "analog" automatically creates the required device-files:
/dev/input/event3
/dev/input/js0

If not, hardware is not yet recognized. Maybe another joystick-driver-module than "analog" is needed for specific joystick.


3.2)	Reboot
~~~~~~~~~~~~~~


4)	Calibrate (and test) joystick
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Terminal command:

ubuntu@ubuntu-desktop:~$ jscal -c /dev/input/js0
Joystick has 2 axes and 4 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 1747, 1747, -2147483648, -2147483648
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 1709, 1709, -2147483648, -2147483648

Calibrating precision: wait and don't touch the joystick.
Done. Precision is:
Axis: 0:     0
Axis: 1:     0

[Follow calibration instructions on screen. The displayed values must change when moving the joystick!]

Setting correction to:
Correction for axis 0: broken line, precision: 0.
Coeficients: 1739, 1739, 321470, 318797
Correction for axis 1: broken line, precision: 0.
Coeficients: 1704, 1704, 328351, 321277

ubuntu@ubuntu-desktop:~$

Comment:
Calibration especially with jscal seems necessary once before joysticks properly work in different programs!


5)	Test joystick (broken!)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Unfortunately the program jstest from the ubuntu 6.06.1 LTS, Dapper Drake package (universe): 
joystick 20051019-1ubuntu1
is broken and quits with a segmentation fault!
Newer or older packages from newer or older ubuntu releases might work.

Terminal command:

ubuntu@ubuntu-desktop:~$ jstest /dev/input/js0
Driver version is 2.1.0.
Joystick (Analog 2-axis 4-button joystick) has 2 axes (X, X)
Segmentation fault
ubuntu@ubuntu-desktop:~$

---

### Post by handy on 2007-04-28
I'll toss this link in here, it may be of some use to someone, I don't know how up to date it is now?

***_[http://www.wingmanteam.com/linux.htm](http://www.wingmanteam.com/linux.htm)_***

---

### Post by TheProphetJonah on 2009-12-23
> **evilghost said:**
> After about an hour of searching, I finally was able to get my CH products Flight Sim yoke working under Ubuntu as well as Flightgear.  I will attempt to document and clarify the steps I used to get my joystick working with Ubuntu in addition to FlightGear.  Should any of the information be incorrect, please feel free to correct me.

This howto assumes you have an analog joystick connected to the gameport/MIDI port of your already functioning sound card.

Perform the following steps in a terminal:
```

cd /etc/init.d
sudo gedit joystick

```Paste the following lines into gedit, and save the file:
```

#! /bin/sh
# /etc/init.d/joystick
#

# Carry out specific functions when asked to by the system
case "$1" in
  start)
    echo "Enabling Joystick"
    cd /dev
    rm js*
    mknod input/js0 c 13 0
    ln -s input/js0 js0
    modprobe joydev
    modprobe analog
    echo "DONE!"
    ;;
  stop)
    rmmod joydev
    rmmod analog
    echo "DONE!"
    ;;
  *)
    echo "Usage: /etc/init.d/joystick {start|stop}"
    exit 1
    ;;
esac

exit 0

```Now, make the file executable.
```

sudo chmod 755 joystick

```Configure the system to run /etc/init.d/joystick on boot:
```

sudo update-rc.d joystick defaults

```Enable the joystick:
```

sudo /etc/init.d/joystick start

```**If you are not using Flightgear, you are done.  Your joystick should now work correctly and be enabled.  If you are using Flightgear and hope to get the joystick working with Flightgear, please proceed with the below steps:**

```

cd ~
fgjs
[Follow the onscreen directions, assigning the buttons/axies (sp?) as needed.]

```Once you have completed the fgjs program and are happy with the configuration, type:
```

cat fgfsrc.js >> .fgfsrc

```Now, load FlightGear and your joystick should work and use the button/axis assignments you specified.  If you make a mistake during fgjs or are unhappy with your assignments **BEFORE** you ran the "cat fgfsrc.js >> .fgfsrc" code simply run the below command again to recreate fgfsrc.js
```

rm fgfsrc.js
fgjs

```I hope this helps someone, if you have problems or find any sections that are incorrect or do not work correctly please be sure to speak up.
ok, I got this much done, inserting it into init.d

Got this output.
[quotejonah@figpucker:/etc/init.d$ sudo chmod 755 joystick
jonah@figpucker:/etc/init.d$ sudo update-rc.d joystick defaults
update-rc.d: warning: /etc/init.d/joystick missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/joystick ...
   /etc/rc0.d/K20joystick -> ../init.d/joystick
   /etc/rc1.d/K20joystick -> ../init.d/joystick
   /etc/rc6.d/K20joystick -> ../init.d/joystick
   /etc/rc2.d/S20joystick -> ../init.d/joystick
   /etc/rc3.d/S20joystick -> ../init.d/joystick
   /etc/rc4.d/S20joystick -> ../init.d/joystick
   /etc/rc5.d/S20joystick -> ../init.d/joystick
jonah@figpucker:/etc/init.d$][/quote]

Which, you know, so far so far. I do get a little twinge of concern when hitting a "warning" on any script. The LSB part has me at least temporarily whooped.

Assuming that I do get it working right, (and I will) there's another thing, since I got to this thread looking at making the JS work in wiNe, (google) and in specific M$ flight simulator.

So, what's the story in using M$ scenery work in other simulators? It's supposed te be the most comprehensive scenery BUT I haven't personally tried every single simulator yet. Some of it's good, some of it sux dog.

With that scenery and the much less of a memory hawg Linux programs, I could ditch Microsux completely.

---

### Post by TheProphetJonah on 2009-12-23
Next part of that is, though, that wiNe has some difficulties with ALSA. Like "alsa being a sound-card hog".

Which mirrors a Winbloze crash scenario I've seen before, running all M$, popups.

My customer was getting popups while doing his Flight Simulator, using the MSN links to keep the "most up to date real-time weather blah blah blah conditions blah blah super good buy our product blah blah blah" function running, and the popups would cause a memory fault in the sound. Which, with Windoze semi-legendary memory allocation problems, would crash Flight Simulator.

Which is, I think, the bug with wiNe sound. Works great with OSS or jack. as far as I know.

ALSA works great with Linux, with M$ products, eh. WinDuhz doesn't play well with others. Doesn't even play well with M$ programs. I saw that the latest reply to this was 3 years ago. Maybe it's time to reawaken the thread and see if it can port to OSS.

---

### Post by kc8hr on 2010-04-14
> **evilghost said:**
> After about an hour of searching, I finally was able to get my CH products Flight Sim yoke working under Ubuntu as well as Flightgear.  I will attempt to document and clarify the steps I used to get my joystick working with Ubuntu in addition to FlightGear.  Should any of the information be incorrect, please feel free to correct me.

This howto assumes you have an analog joystick connected to the gameport/MIDI port of your already functioning sound card.

I hioope this helps someone, if you have problems or find any sections that are incorrect or do not work correctly please be sure to speak up.

My friend, thanks so much for this HOWTO!

I found an ancient M$ SideWinder joystick at the bottom of my closet, and I have been struggling all damned day trying to get it to work. Your script did the trick!

---

