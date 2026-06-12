---
title: "Getting a Xbox 360 WIRELESS controller to work in 7.10 Gutsy Gibbons 32bit edition"
date: 2007-10-08
forum: Gaming &amp; Leisure
---

### Post by Silent_Hunter on 2007-10-08
I have been following many threads and checking IRC for help in getting a xbox 360 _**[COLOR=Red]wireless[/COLOR]**_ controller to work in the latest Ubuntu (7.10) 32bit edition.  I am starting a  new thread that more specific on the desired goal which should be a lot cleaner then many other threads that get hijacked.   I have no intent and using a wired version, original xbox game pad, ps2 with usb adapter, as many others have suggested; for those solution don't help in the actual problem!  

I have found these two threads to be the most useful, but I still can't the wireless to work.
[http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux](http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux)
[http://ubuntuforums.org/showthread.php?t=404577](http://ubuntuforums.org/showthread.php?t=404577)

---

### Post by MattiViljanen on 2007-10-10
AFAIK, the wireless support is still experimental...

However, the xpad module file goes to diffirent directory in Gutsy than in Feisty...
Here's the source package file with modified Makefile to take [this]("http://ubuntuforums.org/showpost.php?p=3340256&postcount=106") into account.
Yes, I know this is quite an ugly, ugly way to do this, but it works (and I'm yet not much of a programmer)...

For a quick how-to for the new ones around: Decompress the source file to desired location, open terminal, go to that dir and copy-paste:
```
$ sudo apt-get install linux-headers-`uname -r` build-essential automake1.9 jscalibrator libgii1 libjsw2
$ make
$ sudo make install
$ sudo depmod -a
$ sudo modprobe xpad
```
Now plug in the controller - the lights should blink only few times and then go off. To calibrate your pad, Alt+F2 and run
```
jscalibrator
```
[EDIT] And for the record, at least *jscalibrator* recognizes two controllers at the same time just fine.

---

### Post by Silent_Hunter on 2007-10-10
I am starting to get frustrated.  Not sure if I messed up.  I followed your instructions verbatim.  Wireless controller continues to blink and I get an error with jscalibrator.  I attached error message.
I used your MakeFile that came with the compressed file.   It appears you already made the change to the MakeFile.
```
mike@mi:~/Desktop/xpad360$ cat Makefile 
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)

all:
        $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)

install:
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/usb/input
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```

```

mike@mi:~/Desktop/xpad360$ sudo apt-get install linux-headers-`uname -r` build-essential automake1.9 jscalibrator libgii1 libjsw2
[sudo] password for mike:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
build-essential is already the newest version.
jscalibrator is already the newest version.
libgii1 is already the newest version.
libgii1 set to manual installed.
libjsw2 is already the newest version.
libjsw2 set to manual installed.
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf autotools-dev
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  automake1.9-doc
Recommended packages:
  automaken
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 898kB of archives.
After unpacking 3355kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/main autoconf 2.61-4 [448kB]
Get:2 http://us.archive.ubuntu.com gutsy/main autotools-dev 20070306.1 [61.6kB]
Get:3 http://us.archive.ubuntu.com gutsy/main automake1.9 1.9.6+nogfdl-3ubuntu1 [388kB]
Fetched 898kB in 4s (185kB/s)       
Selecting previously deselected package autoconf.
(Reading database ... 216783 files and directories currently installed.)
Unpacking autoconf (from .../autoconf_2.61-4_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20070306.1_all.deb) ...
Selecting previously deselected package automake1.9.
Unpacking automake1.9 (from .../automake1.9_1.9.6+nogfdl-3ubuntu1_all.deb) ...
Setting up autoconf (2.61-4) ...

Setting up autotools-dev (20070306.1) ...
Setting up automake1.9 (1.9.6+nogfdl-3ubuntu1) ...

mike@mi:~/Desktop/xpad360$ make
make modules -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/mike/Desktop/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/mike/Desktop/xpad360/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mike/Desktop/xpad360/xpad.mod.o
  LD [M]  /home/mike/Desktop/xpad360/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
mike@mi:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/input
cp -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick
mike@mi:~/Desktop/xpad360$ sudo depmod -a
mike@mi:~/Desktop/xpad360$ sudo modprobe xpad
mike@mi:~/Desktop/xpad360$ jscalibrator

```

---

### Post by oscrp on 2007-10-20
> **Silent_Hunter said:**
> I am starting to get frustrated.  Not sure if I messed up.  I followed your instructions verbatim.  Wireless controller continues to blink and I get an error with jscalibrator.  I attached error message.
I used your MakeFile that came with the compressed file.   It appears you already made the change to the MakeFile.
```
mike@mi:~/Desktop/xpad360$ cat Makefile 
obj-m := xpad.o
KDIR := /lib/modules/$(shell uname -r)/build
EXTRA_CFLAGS=-I$(shell pwd)

all:
        $(MAKE) modules -C $(KDIR) SUBDIRS=$(shell pwd)

install:
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/usb/input
        cp -f xpad.ko /lib/modules/$(shell uname -r)/kernel/drivers/input/joystick

```

```

mike@mi:~/Desktop/xpad360$ sudo apt-get install linux-headers-`uname -r` build-essential automake1.9 jscalibrator libgii1 libjsw2
[sudo] password for mike:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.22-14-generic is already the newest version.
build-essential is already the newest version.
jscalibrator is already the newest version.
libgii1 is already the newest version.
libgii1 set to manual installed.
libjsw2 is already the newest version.
libjsw2 set to manual installed.
The following packages were automatically installed and are no longer required:
  unixodbc odbcinst1debian1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  autoconf autotools-dev
Suggested packages:
  autoconf2.13 autobook autoconf-archive gnu-standards autoconf-doc
  automake1.9-doc
Recommended packages:
  automaken
The following NEW packages will be installed:
  autoconf automake1.9 autotools-dev
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 898kB of archives.
After unpacking 3355kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy/main autoconf 2.61-4 [448kB]
Get:2 http://us.archive.ubuntu.com gutsy/main autotools-dev 20070306.1 [61.6kB]
Get:3 http://us.archive.ubuntu.com gutsy/main automake1.9 1.9.6+nogfdl-3ubuntu1 [388kB]
Fetched 898kB in 4s (185kB/s)       
Selecting previously deselected package autoconf.
(Reading database ... 216783 files and directories currently installed.)
Unpacking autoconf (from .../autoconf_2.61-4_all.deb) ...
Selecting previously deselected package autotools-dev.
Unpacking autotools-dev (from .../autotools-dev_20070306.1_all.deb) ...
Selecting previously deselected package automake1.9.
Unpacking automake1.9 (from .../automake1.9_1.9.6+nogfdl-3ubuntu1_all.deb) ...
Setting up autoconf (2.61-4) ...

Setting up autotools-dev (20070306.1) ...
Setting up automake1.9 (1.9.6+nogfdl-3ubuntu1) ...

mike@mi:~/Desktop/xpad360$ make
make modules -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/mike/Desktop/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/mike/Desktop/xpad360/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/mike/Desktop/xpad360/xpad.mod.o
  LD [M]  /home/mike/Desktop/xpad360/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
mike@mi:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/input
cp -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick
mike@mi:~/Desktop/xpad360$ sudo depmod -a
mike@mi:~/Desktop/xpad360$ sudo modprobe xpad
mike@mi:~/Desktop/xpad360$ jscalibrator

```

The same problem here. Does anybody have a solution?

---

### Post by RKCole on 2007-10-23
Hello, everyone.

I was just wondering if anyone knows how to get a regular wires Xbox 360 controller up and running in Gutsy?  I had no problem compiling the xpad module in Feisty, but it does not seem to work in Gutsy for some reason.

Any suggestions would be greatly appreciated.

Thanks in advance.

Take care.

---

### Post by macness on 2007-10-23
what happens when you do

```
cat /dev/input/js0
```

---

### Post by RKCole on 2007-10-26
Thanks for the response, macness.

Here is what I get after running the above command:

```

cat: /dev/input/js0: No such file or directory

```

I'm kind of stumped on this one, as the module compiled and installed successfully.

Thanks for the help.

Take care.

---

### Post by Fitzsimmons on 2007-10-29
If you're referring to the module from this thread:

[http://ubuntuforums.org/showthread.php?t=404577](http://ubuntuforums.org/showthread.php?t=404577)

The problem is that the install script provided by this package is placing the file in the wrong place.

Specifically, this line:

```
mv -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/usb/input
```

It appears that drivers/usb/input no longer exists as a directory, so this actually ends up moving xpad.ko to a file named input, in the directory drivers/usb/.

Instead, move the file manually after a successful build:

```
sudo cp -f xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick/
```

Works for me.

---

### Post by psoplayer on 2007-11-08
Sweet! It works for me.
I modified the makefile so you should be able to do
```
make
sudo make install
```
and have it done with.

---

### Post by Nicolae on 2007-11-10
That driver isn't going to work; it doesn't have wireless support for the 360 controller at all. 

I've attached the source I used to build the module.

To install:
```

make
sudo rmmod xpad
sudo cp xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick 
sudo depmod -a
sudo modprobe xpad

```

Once it's loaded you should have js0-js3 in /dev/input, even with no  controller synced to the wireless adapter.

My dmesg output after loading the module:

```

[1034065.968000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input26
[1034065.968000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input27
[1034065.968000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input28
[1034065.968000] input: Microsoft Xbox 360 Wireless Controller (PC) as /class/input/input29
[1034065.968000] usbcore: registered new interface driver xpad
[1034065.968000] /home/nicolae/src/xpad360/xpad.c: driver for Xbox controllers v0.1.7
```

Everything seems to work. 

I don't remember where I got this source from, but I'm pretty sure it was someone on the forums. IIRC there were some slight modifications from the "official" source to get it to work in feisty.

---

### Post by Vitamin-Carrot on 2007-11-11
Can we have one updated straight forward How To for this? jumping between forum posts for diff versions of ubuntu and websites is kinda confusing.

So far nothing I have read/found/downloaded has worked no matter what people have said

---

### Post by psoplayer on 2007-11-11
OK, here's what I did to get it working. Mind you this is for Gutsy only! Download that xpad360 tarball in my previous post. Extract the contents. Open a terminal and change directories into that folder. If you just extracted it to the desktop do this:
```
cd ~/Desktop/xpad360
```
Either way, you should be in the xpad360 folder now. Make sure you have all the basic complier stuff. If you don't know if you do, just do this and you'll be ok either way:
```
sudo apt-get install build-essential
```
Now you should be set up to complile the source code.
```
make
```
Some text should fly by, but if everything is ok, none of them should be any kind of error messages. Now have it automagically installed into the system:
```
sudo make install
```
From this point I could just plug my controller in and it worked! Leave me feedback and i *might* be able to help.

---

### Post by nandotron on 2007-11-12
Hi psoplayer,

thanks for the howto.  I ran into some problems when i got to the stage for 'make':

```
make modules -C /lib/modules/2.6.22-14-rt/build SUBDIRS=/home/enda/Desktop/xpad360
make: *** /lib/modules/2.6.22-14-rt/build: No such file or directory.  Stop.
make: *** [all] Error 2
```


Not sure what it means.  I am using the realtime version of the kernel.  Not sure what the difference between that and the generic version is for that matter.  Any ideas on what I'm doing wrong?

Cheers,

Nando

---

### Post by psoplayer on 2007-11-14
It's looking to use the headers from your kernel that you have as part of the build, and the folder /lib/modules/(kernel name)/build should just be a link to a folder of your headers, which, for me is: /usr/src/linux-headers-2.6.22-14-generic
Try giving me the output from your terminal when running these commands:
```
ls /lib/modules
ls /lib/modules/(whatever the output was from that first line)
ls /usr/src
```
It may be that all is needed is for you to create that link yourself but I can't guarentee this will do anything good:
```
sudo ln /usr/src/linux-headers-2.6.22-14-rt /lib/modules/2.6.22-14-rt/build
```

---

### Post by nandotron on 2007-11-14
Hey man, thanks for the help. 

here's the output of ls /lib/modules:
```

2.6.22-14-generic  2.6.22-14-rt
```

output of ls /lib/modules/2.6.22-14-generic  2.6.22-14-rt:

```

ls: 2.6.22-14-rt: No such file or directory
/lib/modules/2.6.22-14-generic:
initrd   modules.alias   modules.ieee1394map  modules.ofmap     modules.symbols
kernel   modules.ccwmap  modules.inputmap     modules.pcimap    modules.usbmap
madwifi  modules.dep     modules.isapnpmap    modules.seriomap  volatile
```

and there doesnt seem to be any output from: ls /usr/src

---

### Post by psoplayer on 2007-11-14
What you seem to be lacking are the header files for your kernel. Now, I don't even have a good idea of what kernel header files are, but see if this doesn't change your situation:
```
sudo apt-get install linux-headers-rt
```
I don't know why the headers are already installed on my machine and not on yours. I certainly haven't gone out of my way to install them specifically.

---

### Post by Vitamin-Carrot on 2007-11-14
Yay i got mine workign thanks for allt he help guys.

I have noticed that Gens doesnt like it much where as sdlmame LOVES IT!!

will try out on other emu's and game soon.

---

### Post by psoplayer on 2007-11-16
Awesome! I'm glad to hear my attempts at tutorial-town haven't been completely failtrain.

---

### Post by mozetti on 2007-11-16
Do you know if this works with a wireless 360 controller if you use the play & charge usb cord for re-charging the battery?

---

### Post by psoplayer on 2007-11-17
I have no idea at all, although I've never even tried that with Windows, so I don't know. It would be nice if it did. Anyone have experience with the charging cord in windows?

---

### Post by oscrp on 2007-11-18
Yeah, it works!! Thank you :D

---

### Post by Mammlouk on 2007-11-19
I believe that the play n charge cable is only for charging, so in order for it to work you would actually need to use the PC Xbox wireless receiver.

---

### Post by Contrast on 2007-12-12
I spent hours looking for a how-to on this, and couldn't find one that had all the information in one place. The tarball and information presented herein is pieced together from a few different how-to's. Many thanks to the original authors of those.

First, save the attached file to your home folder. Then open a terminal, and run the following commands:
```
tar -xzf xpad360.tar.gz
cd xpad360
make
sudo make install
```
Now, all you need to do is reboot and you should be good to go. You will need to repeat the installation process whenever your kernel is upgraded, so you probably want to keep the original tarball around (you can't just do the "make install" step again, as the module needs to be recompiled for the currently running kernel). Also, the LED on the controller will continue blinking after it's been synched - this is normal. I tested it with Gens and ZSNES and it seems to work fine. There are only two minor caveats, and these may or may not apply to you (I've only tested on this one machine): 1) When you try to bind the triggers to a certain button, each "step" that you press on them (remember that they're analog) is registered as a different button, so you can't use them. If anyone finds a workaround for this, please post it here. 2) You need to resync the receiver with the controller(s) each time you start an emulator or native game.

Unfortunately, I probably won't be able to offer much help if you run into problems with this, since I was doing this on my friend's computer and I don't have one of these receivers, but post any issues you have here and I'll do my best. Also, this is my first how-to, so please let me know if it was helpful and/or if you'd change anything. Thanks.

---

### Post by djbon2112 on 2007-12-16
Hey, I'm trying to get my GH2 Xplorer controller (wired USB) working under Gutsy. I followed your steps, even restarted, but the controller doesn't seem to work. The four lights on it just flash. Any suggestions? I'm a complete Linux noob.

---

### Post by psoplayer on 2007-12-17
I don't have a X360 guitar hero controller of my own, so I can't try anything out myself. Have you gotten a regular wired controller working yet? Does anyone know for sure if the xbox guitar hero controller works in Windows with the regular wired controller drivers?

---

### Post by djbon2112 on 2007-12-18
> **psoplayer said:**
> I don't have a X360 guitar hero controller of my own, so I can't try anything out myself. Have you gotten a regular wired controller working yet? Does anyone know for sure if the xbox guitar hero controller works in Windows with the regular wired controller drivers?

I don't have a regular wired X360 controller :( Just the GH2 one I use for FoF and GH3PC. But as to the drivers, I don't think they're the same, because when installing under windows they come up as "Xplorer Controller" or something like that.

---

### Post by Replicax86 on 2007-12-18
> **psoplayer said:**
> OK, here's what I did to get it working. Mind you this is for Gutsy only! Download that xpad360 tarball in my previous post. Extract the contents. Open a terminal and change directories into that folder. If you just extracted it to the desktop do this:
```
cd ~/Desktop/xpad360
```
Either way, you should be in the xpad360 folder now. Make sure you have all the basic complier stuff. If you don't know if you do, just do this and you'll be ok either way:
```
sudo apt-get install build-essential
```
Now you should be set up to complile the source code.
```
make
```
Some text should fly by, but if everything is ok, none of them should be any kind of error messages. Now have it automagically installed into the system:
```
sudo make install
```
From this point I could just plug my controller in and it worked! Leave me feedback and i *might* be able to help.

Thank you soo much, I had been messing with this thing all day before I found this post, worked perfectly

Edit: After I restarted it doesn't work anymore, tried installing the driver again..still doesn't work :-(

---

### Post by psoplayer on 2007-12-19
djbon2112:
After looking through the source for the driver, I realize that it really doesn't matter how it works in Windows, this driver just doesn't have support for guitar controllers yet. I may be able to add it myself, but I'll have to steal an xbox guitar controller from a friend and brush up on my C coding skills, so don't hold your breath, but subscribe to this thread and keep a look out in your inbox.

Replicax86:
Very strange... What does this output for you?:```
cat /dev/input/js0
```

---

### Post by djbon2112 on 2007-12-19
> **psoplayer said:**
> djbon2112:
After looking through the source for the driver, I realize that it really doesn't matter how it works in Windows, this driver just doesn't have support for guitar controllers yet. I may be able to add it myself, but I'll have to steal an xbox guitar controller from a friend and brush up on my C coding skills, so don't hold your breath, but subscribe to this thread and keep a look out in your inbox.

Replicax86:
Very strange... What does this output for you?:```
cat /dev/input/js0
```

It's alright, I just gave in and installed a barebones copy of Windows XP to game on, save the trouble :p

---

### Post by Replicax86 on 2007-12-19
> **psoplayer said:**
> djbon2112:
Replicax86:
Very strange... What does this output for you?:```
cat /dev/input/js0
```




Says that it doesn't exist.... :(

---

### Post by psoplayer on 2007-12-19
Ok then, what does this do for you?```
modprobe xpad
```

---

### Post by Replicax86 on 2007-12-19
It doesn't do anything at all, just brings the cursor down to the next blank line...by the way thanks for tryin to help me out with this, if its any help the problem started after I restarted following an update, but of course it was throgh synaptic and I'm not sure what all was included in it

---

### Post by psoplayer on 2007-12-21
Ok, I don't think I know enough at this point to be able to help you, but that doesn't mean there's no hope for you. You said you have already tried a complete reinstall of the driver, and that's all I could suggest for you to do. Keep looking around the forum; I'm sure there are others that know more about this than I do.

---

### Post by yoblin on 2007-12-23
thanks a bunch for this, I'll test it out soon..

It looks like I bought a controller just at the right time after people figured out how to get it to work in gutsy :)

---

### Post by kilbane on 2007-12-26
Hello there (first message)!

I'm french and i try to set up a Xbox360 controller. I found this thread and tried it but the only thing the controller does is led flash. I want to play with it on Znes but nothing is recognized. When i do the "cat" command that reply "no file or directory..." and the modprobe does nothing... 

Must I reboot to changes take effect?

---

### Post by Einsidler on 2007-12-27
> **kilbane said:**
> Hello there (first message)!

I'm french and i try to set up a Xbox360 controller. I found this thread and tried it but the only thing the controller does is led flash. I want to play with it on Znes but nothing is recognized. When i do the "cat" command that reply "no file or directory..." and the modprobe does nothing... 

Must I reboot to changes take effect?

I had a similar problem and this worked for me:
```

# sudo modprobe -r xpad
# sudo modprove xpad
```
I guess the old xpad module was still loaded in and had to be removed first since it worked like a dream afterwards.

---

### Post by psoplayer on 2007-12-27
> **kilbane said:**
> Hello there (first message)!

I'm french and i try to set up a Xbox360 controller. I found this thread and tried it but the only thing the controller does is led flash. I want to play with it on Znes but nothing is recognized. When i do the "cat" command that reply "no file or directory..." and the modprobe does nothing... 

Must I reboot to changes take effect?

I don't remember having to restart, but several people have said that they needed to restart before it worked for them, so I would anyway. Then again, Replicax86 had it working until he restarted, so at times I have no idea what is going on.

---

### Post by sk84fun on 2007-12-28
I get error on "rmmod xpad" please help!

```
root@xammax-desktop://home/xammax/.xpad360# make
make modules -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/xammax/.xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/xammax/.xpad360/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/xammax/.xpad360/xpad.mod.o
  LD [M]  /home/xammax/.xpad360/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
[B]root@xammax-desktop://home/xammax/.xpad360# sudo rmmod xpad
ERROR: Module xpad does not exist in /proc/modules[/B]
root@xammax-desktop://home/xammax/.xpad360# sudo cp xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick 
root@xammax-desktop://home/xammax/.xpad360# sudo depmod -a
root@xammax-desktop://home/xammax/.xpad360# sudo modprobe xpad
root@xammax-desktop://home/xammax/.xpad360# 

```

---

### Post by sk84fun on 2007-12-29
So what can i do with this error? Can anyone help?

---

### Post by passcode on 2007-12-30
I found this vary helpful. I was trying to get a xbox ddr pad to work on my box. The drivers that ship with Gusty dont work.

I used what you had and updated the xpad.c to remove the sanity check that was causing the ddr pad not to load. It works find now. I posted the updated xpad.c. Hope it helps someone.

Just:

make
sudo make install

---

### Post by Nicolae on 2007-12-30
Doesn't matter, it just serves to unload the old module if it was there. Assuming you get the right output from dmesg | tail once you modprobe the new module you're fine.

---

### Post by UK-Wobbie on 2007-12-30
How hard is it to get a 360 controller to work? As any one done this be for?

---

### Post by sk84fun on 2007-12-30
If it is not wireless then easy =)

---

### Post by kbless7 on 2007-12-30
PSOPLAYER,

Thanks for all of the posts. I finally got the controller to work and everything is fine. My only question is how to get rid of the flashing lights? I'm not sure if your way was supposed to do that, but they just flash, and its sort of annoying. Thanks for the help.

-Matt

---

### Post by kaytaro on 2007-12-31
unfortunately atm the drivers cant stop it from flashing like its not working even tho it is. I'm sure the people who wrote the drivers are working on a fix, it is a little say, distracting in the dark lol.

---

### Post by Silent_Hunter on 2007-12-31
Nicolae's instructions appear to be working.

---

### Post by psoplayer on 2008-01-01
The flashing ring on the controller seems strange, as well as unfortunate. My controller works fine sans flashing lights with the code posted here. I'm glad to hear you at least have a working controller though.

> **passcode said:**
> I found this vary helpful. I was trying to get a xbox ddr pad to work on my box. The drivers that ship with Gusty dont work.

I used what you had and updated the xpad.c to remove the sanity check that was causing the ddr pad not to load. It works find now. I posted the updated xpad.c. Hope it helps someone.

At the moment I don't have the time to look at your changes, but maybe I'll be able to sort something out. Specifically, what type of pad do you have?

---

### Post by WeAreMany on 2008-01-01
anyone know how to get the M$ chatpad to work with ubuntu?

---

### Post by EnsignR on 2008-01-06
> **Silent_Hunter said:**
> Nicolae's instructions appear to be working.

I concur. I now have it working in Frozen Bubble, the only joystick enabled game I think I have installed... apart from MAME which I haven't been able to get working as yet, but that's probably just me not setting MAME up properly (hopefully) :confused:

Hopefully someone works on a fix to make the lights function as intended, instead of just blinking, as thats the only quirk that I can find   so far (assuming I get MAME working that is)

I might write a step by step tutorial once I confirm everything is working 100% (or close to it). I might even try the Makefile in the sourceforge project to see if that works/makes any difference before I do that.

I am so happy that its finally working (i think) :KS

btw does anyone know the correct settings to use in MAME?

ED: I have found one little quirk. If you turn off your controller (by removing the batteries) once connected, you can't reconnect that controller unless you remove and reinsert the wireless adapter from the USB port.

Oh and I didnt mention above that I am able to connect two controllers at once for two player fun :D


ED2: I fixed my issues with MAME. For some reason, which I'll have to look in to, it's not saving my config changes. Every time I saved the changes it reverted back to the default settings. Solution for this was to create a symbolic link from /dev/js0 to /dev/input/js0

```
sudo ln -s /dev/input/js0 /dev/js0
```

---

### Post by PLAY3ER on 2008-01-11
Hello their follow Ubuntu users 

Want to say first of all Matt your how-to is very good, it worked the 2ed time i tried it, 1st time i messed up, lol,. 

anyway, i know this is a little problem but, has anyone been able to get the Xbox 360 to stop flashing? i mean, it is a little annoying, im not a programmer so, i don't know where to begin to look at all this, and i would want a other install to start to mess around, thanks

:guitar:

---

### Post by EnsignR on 2008-01-11
There is code on sourceforge (under the xbox-linux project) to stop the flashing. It also does a couple of other things I am not sure I want it to do. As such I haven't rebuiilt the module using that code as yet.

I am just happy its working, and am not sure I really wanna risk breaking it

---

### Post by PLAY3ER on 2008-01-11
well, now mine is not working lol, and all i did was restart :p

---

### Post by EnsignR on 2008-01-12
> **PLAY3ER said:**
> well, now mine is not working lol, and all i did was restart :p

Did you re-synce the controller with the adapter.. You have to do that each time you restart.

What is the output you get from **dmesg**?
(or **dmesg | grep box**)

---

### Post by pieisgood on 2008-01-21
never mind... i'm retarded.. 360 controller isn't bluetooth.

---

### Post by G_u_s on 2008-01-29
> **Einsidler said:**
> I had a similar problem and this worked for me:
```

# sudo modprobe -r xpad
# sudo modprove xpad
```
I guess the old xpad module was still loaded in and had to be removed first since it worked like a dream afterwards.
That did the trick perfectly, thanks a bunch, and thanks also to psoplayer, it was really helplful =)

---

### Post by ChameleonDave on 2008-02-09
Hang on, you haven't mentioned what hardware you're using to connect this controller.

---

### Post by Themicles on 2008-02-17
I receive the following error at sudo modprobe xpad

FATAL: Error inserting xpad (/lib/modules/2.6.22-14-rt/kernel/drivers/input/joystick/xpad.ko): Invalid module format

Any help?

---

### Post by lckeeper1 on 2008-02-19
I get the same problem as Them.

I'm still pretty new to how inputs work, so any help would be awesome!

---

### Post by Phil Urich on 2008-02-23
I too am in the "invalid module format" boat...

---

### Post by VitaEdo on 2008-02-27
[I]# sudo modprobe -r xpad
# sudo modprove xpad

I guess the old xpad module was still loaded in and had to be removed first since it worked like a dream afterwards.[/I]

I have the same problem, and sudo modprobe -r xpad seems to do nothing, and modprove does not exist.

---

### Post by Zetto on 2008-02-29
THANX guys, got it working, too.

@VitaEdo: modprove doesn't exist. he simply misstyped :)

so try run "sudo modprobe xpad" again and it should work.

---

### Post by bruno321 on 2008-03-06
I'm using the latest CVS xpad drivers: xpad.c is 0.1.7, xpad.h is 0.1.5. It works fine, but there is a problem which I've spotted with the experimental game Passage:

Found 2 joysticks
No d-pad found on joystick

That is because this driver maps the d-pad as buttons instead of axis. A guy on [this wiki page]("http://gentoo-wiki.com/HOWTO_Xbox_360_controller_on_Linux") said he had solved the problem and provides the working xpad.c. First, the link is broken, though I managed to download it using the Wayback Machine. The problem is, that xpad.c doesn't work for me and, besides, it is based off a quite old version of the drivers. If I knew how to do it I would, but I don't, so, is there a chance somebody might add that function to the new drivers?

And on a different note, the X symbol constantly blinks, I thought that had been fixed... and how could I test the rumble? I tried Audiosurf with Wine but it doesn't work if I have the controller plugged in...

Thanks.

---

### Post by Themicles on 2008-03-06
Solved my problem. I have the RT kernel, and RT headers. I edited the Makefile to replace -generic with -rt.

No more errors... now to learn how to configure this thing.

---

### Post by roderick on 2008-03-07
Anyone have any luck getting a DDR mat working? I have a Mad Catz Bead Pad (usb ID 0x0738:04740) which is not listed directly in the code.

I have attempted several different ways to mod the code, but it either ends up not recognizing the controller, or it segfaults on modprobe and causes a kernel OOPS (crash) [BUG: unable to handle kernel NULL pointer dereference at virtual address 00000006].

I am running Hardy (but have tested on Gutsy) tried both kernel 2.6.22 and 2.6.24.

The crash appears to be in xpad_probe, and I am trying to narrow it down further (no luck yet as I have to reboot after each failed load due to the crashes).

---

### Post by roderick on 2008-03-07
I have a thread started with my experience on this: [http://ubuntuforums.org/showthread.php?t=717079](http://ubuntuforums.org/showthread.php?t=717079)

I have found where the code breaks. It crashes here in the code:

        usb_fill_int_urb(xpad->irq_in, udev,
                         usb_rcvintpipe(udev,ep_irq_in->bEndpointAddress),
                         xpad->idata, XPAD_PKT_LEN, xpad_irq_in,
                         xpad, ep_irq_in->bInterval);

I've added in some test code (diff below) just before it. The code bails if ep_irq_in is NULL (undefined):

@@ -554,6 +556,13 @@

        /* init input URB for USB INT transfer from device */
        ep_irq_in = &intf->cur_altsetting->endpoint[0].desc;
+
+       // Testing for valid input
+       if (!ep_irq_in) {
+               info("ep_irq_in undefined");
+               goto fail2;
+       }
+
        usb_fill_int_urb(xpad->irq_in, udev,
                         usb_rcvintpipe(udev, ep_irq_in->bEndpointAddress),
                         xpad->idata, XPAD_PKT_LEN, xpad_irq_in,

As you can see in the dmesg output below:

[  104.270277] input: Mad Catz Beat Pad 
as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input10
[  104.285890] input: Mad Catz Beat Pad 
as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.1/input/input11
[  104.298252] input: Mad Catz Beat Pad 
as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.2/input/input12
[  104.304010] /home/rgreening/xpad/xpad.c: ep_irq_in undefined
[  104.304558] xpad: probe of 1-1:1.3 failed with error -12

It appears that the call to "ep_irq_in = &intf->cur_altsetting->endpoint[0].desc;" is returning NULL and is not caught by the code. Therefore it crashes.

I guess there's some additional checking and logic that needs to occur there, though I am at a loss as to exactly what needs to be done.

---

### Post by Narada2XK on 2008-03-08
even after install this, how do you use the pad? well for me it isn't or doesn't seem to sync...the controller leds just keep flashing...

---

### Post by roderick on 2008-03-09
I finally solved my issue. I posted the solution in my thread (see solution here: [http://ubuntuforums.org/showthread.php?t=717079](http://ubuntuforums.org/showthread.php?t=717079)).

Patched version 0.0.6 rather than using 0.1.7. Though my controller is not wireless.

---

### Post by SoenceMakeSense on 2008-03-11
im having the same problem. any suggestions?

---

### Post by neogto on 2008-03-12
when i followed the guide i got

> robby@robby-desktop:~/Desktop/xpad360$ ls /usr/src
linux-headers-2.6.22-14          linux-headers-2.6.22-14-rt
linux-headers-2.6.22-14-generic



> robby@robby-desktop:~/Desktop/xpad360$ cd ~/Desktop/xpad360
robby@robby-desktop:~/Desktop/xpad360$ make
make modules -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/robby/Desktop/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
robby@robby-desktop:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick/

and as u can see it went throu and did its stuff 
but my paddle is still blinking lol

im trying to get it to work with zsnes 1.51

---

### Post by neogto on 2008-03-12
i got it working

the paddle will not light up in windows

second after installing the driver u have to reboot linux

and it dose work just fine

---

### Post by jdsony on 2008-03-13
This is normal behaviour. The controller will just flash but will in fact work although I'm having trouble getting mine working again.

---

### Post by btich on 2008-03-17
Hi, Im looking for people who can get their controller to work with the driver from xbox-linux but have the problem with non-stop blinking leds. Could you please try the patch below and report if it works or not.

Original driver:
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c)
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h)

Patch:
```
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;

```

---

### Post by Contrast on 2008-03-29
I should've pointed out that you'll need to repeat the installation process for the module whenever the kernel is upgraded. Hopefully that will solve the issue some of you have been having.

---

### Post by boobsbr on 2008-03-29
> **psoplayer said:**
> Sweet! It works for me.
I modified the makefile so you should be able to do
```
make
sudo make install
```
and have it done with.

It worked like a charm! compiled, installed, rebooted, plugged controller and BAM! zsnes reconized without any problems. thank you so much for your help and contribution!

---

### Post by Dr. Clock on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=570642&page=15](http://ubuntuforums.org/showthread.php?t=570642&page=15)

I edited this comment because:
The moderator squished at least 2 threads together,

so some of the comments in this thread are out of place

a little,

but I am going to try my best to clean up my comments.

---

### Post by bhuthogg on 2008-03-30
Bit of a noob here do i just copy paste above into xpad.c file ?



> **btich said:**
> Hi, Im looking for people who can get their controller to work with the driver from xbox-linux but have the problem with non-stop blinking leds. Could you please try the patch below and report if it works or not.

Original driver:
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c)
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h)

Patch:
```
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;

```

---

### Post by Dr. Clock on 2008-03-30
> **Dr. Clock said:**
> out for:
sudo make install:
cp -f xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick/

My bad I should have said I use:
Ubuntu 7.10 the 64-bit version on an AMD 64 CPU
and also couldn't get Gens to work as well as not being able to get the the Xbox 360 wireless controller to work on it.
It works on my Windows XP computer very well with three different emulators.

---

### Post by Joeb454 on 2008-03-30
I think that the Wireless controller won't work because it requires a USB dongle to connect to the controller.

I'm not sure if there is support for that just yet

---

### Post by psoplayer on 2008-04-01
> **Dr. Clock said:**
> My bad I should have said I use:
Ubuntu 7.10 the 64-bit version on an AMD 64 CPU
and also couldn't get Gens to work as well as not being able to get the the Xbox 360 wireless controller to work on it.
It works on my Windows XP computer very well with three different emulators.

I also use the 64 bit version but the key difference is the fact that you have the wireless controller with the usb receiver. From what I can tell, xpad was written for original Xbox controllers (which were USB all along, just with a different shape connector) that had a regular usb adapter and it was adapted for the wired 360 controllers once they came out. Thinking along those lines, I don't think this driver will work with the wireless controllers (if ever) without major additions of code.

---

### Post by Dr. Clock on 2008-04-13
I use Ubuntu 7.10 the 486 version.
I tried your commands to get this after downloading the tarball to my desktop::
ray@ray-desktop:~$ tar -xzf xpad360.tar.gz cd xpad360
tar: xpad360.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: cd: Not found in archive
tar: xpad360: Not found in archive
tar: Error exit delayed from previous errors
ray@ray-desktop:~$ tar -xzf xpad360.tar.gz cd xpad360
tar: xpad360.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: cd: Not found in archive
tar: xpad360: Not found in archive
tar: Error exit delayed from previous errors
ray@ray-desktop:~$ cd xpad360
bash: cd: xpad360: No such file or directory
ray@ray-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
ray@ray-desktop:~$ sudo make install
[sudo] password for ray:
make: *** No rule to make target `install'.  Stop.
ray@ray-desktop:~$

---

### Post by Dr. Clock on 2008-04-14
Found this link, but still didn't get it working with any emulators  that I have on my linux:
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)

---

### Post by Dr. Clock on 2008-04-15
[http://ubuntuforums.org/showthread.php?t=570642&page=15](http://ubuntuforums.org/showthread.php?t=570642&page=15)

I edited this comment because:
The moderator squished at least 2 threads together,

so some of the comments in this thread are out of place

a little,

but I am going to try my best to clean up my comments.

---

### Post by kbless7 on 2008-04-15
> **Dr. Clock said:**
> I use Ubuntu 7.10 the 486 version.
I tried your commands to get this after downloading the tarball to my desktop::
ray@ray-desktop:~$ tar -xzf xpad360.tar.gz cd xpad360
tar: xpad360.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: cd: Not found in archive
tar: xpad360: Not found in archive
tar: Error exit delayed from previous errors
ray@ray-desktop:~$ tar -xzf xpad360.tar.gz cd xpad360
tar: xpad360.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: cd: Not found in archive
tar: xpad360: Not found in archive
tar: Error exit delayed from previous errors
ray@ray-desktop:~$ cd xpad360
bash: cd: xpad360: No such file or directory
ray@ray-desktop:~$ make
make: *** No targets specified and no makefile found.  Stop.
ray@ray-desktop:~$ sudo make install
[sudo] password for ray:
make: *** No rule to make target `install'.  Stop.
ray@ray-desktop:~$

run
```
cd Desktop
tar -xzf xpad360.tar.gz
cd xpad360
make
sudo make install
```

---

### Post by psoplayer on 2008-04-15
Alright then maybe I was wrong, but I certainly don't know how to get it working, and I only have a wired controller myself, so I am unable to do any experimentation of my own. For that first link you posted, I don't think you are expected to modify the makefile. It seemed like it has already modified for you. Did you try it the way it was?

---

### Post by Dr. Clock on 2008-04-16
Good question, 
It didn't have a make file, so I assumed that he was saying to make a file named: Makefile and copy and paiste the code he has posted.
Anyways I did notice a program that wasn't in Accessories before called: Joystick Calibration, so now I just ran a search in ADD/REMOVE and it is there, but I never added it, so I assumed that this link 
had me download it through the Terminal:
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)
, but it could have been one of the other links that had me do so.
When I open it opens and also puts up a message box saying:
Could not access the path(s), verify that the path(s) are specified correctly and that you have sufficient permission to access them. Also make sure that the joystick in question is actually connected, turned on (as needed), not in use by another program, and that the joystick driver or module is loaded (type 'modprobe <driver_name>').

but I don't know the modules name.

Looking at this program without opening any thing it has an empty box for typing in Joystick Device.
above it for the menu it has:
Calibration: Open, save save as, clean up, and exit,

Joystick: Refresh, reopen, close, and properties..,

View: Representative Ctl+P, and Logical Ctl+L.

Opening Properties it has a menu with a heading named "General" under which it asks for 
Name,
Device,
Driver Version, and
Calibration File

Under the heading: "Force Feedback" of this menu it asks for 
Product ID

Sorry for the rambling, and thank you for responding.

---

### Post by Dr. Clock on 2008-04-16
> **psoplayer said:**
> I also use the 64 bit version but the key difference is the fact that you have the wireless controller with the usb receiver. From what I can tell, xpad was written for original Xbox controllers (which were USB all along, just with a different shape connector) that had a regular usb adapter and it was adapted for the wired 360 controllers once they came out. Thinking along those lines, I don't think this driver will work with the wireless controllers (if ever) without major additions of code.

I just switched back to Ubuntu 7.10 32-bit 486 on an AMD 64 CPU which some people on the myspace group called "Linux Geeks" told me.
However it didn't work with it, but my last post I just posted a few minutes ago was after I had already had switched.
I am reposting to ask how do I adapt an Xbox 360 wired controller?
I mean I know what a USB connection is like the connection on flash drives, but is there another form of USB port I don't about that is bigger and rounder?
, because when I went to the Game Stop store and looked at the Xbox 360 Wired Controllers it wasn't the same shape as the flash drive USB connection was.
If the connection is on the back of my computer will the Xbox 360 Wired controller be long enough or can I get an adapter for it, so I can connect it to the front of my computer?
And if so then would it not work as apposed to plugging in the back of my computer?, and also
would that slow down the speed for the controller's connection, because the USB in the size like that of the flash drives is smaller than the connection on that of the Xbox 360 Wired controller?

---

### Post by psoplayer on 2008-04-18
> **Dr. Clock said:**
> I just switched back to Ubuntu 7.10 32-bit 486 on an AMD 64 CPU which some people on the myspace group called "Linux Geeks" told me.
However it didn't work with it, but my last post I just posted a few minutes ago was after I had already had switched.
I am reposting to ask how do I adapt an Xbox 360 wired controller?
I mean I know what a USB connection it for the flash drives I use, but is there another form of USB port I don't about that is bigger and rounder?
, because when I went to the Game Stop store and looked at the Xbox 360 Wired Controllers it wasn't the same shape as the flash drive USB connection was.
If the connection is on the back of my computer will the Xbox 360 Wired controller be long enough or can I get an adapter for it, so I can connect it to the front of my computer?
And if so then would it not work as apposed to plugging in the back of my computer?, and also
would that slow down the speed for the controller's connection, because the USB in the size like that of the flash drives is smaller than the connection on that of the Xbox 360 Wired controller?

You either didn't look at it carefully enough, or you were looking at an original Xbox controller, because a wired Xbox 360 controller just uses a regular USB port, just like your flash drive uses.

---

### Post by kbless7 on 2008-04-19
What you are looking at is a mid-stream connector. On the 360 controllers there is than an adapter which turns that circular one into a regular usb connector.

---

### Post by Dr. Clock on 2008-04-20
I don't know exactly what you mean.
Did you mean that the Xbox 360 controller I was looking at may have had this connection on the end of it?
[http://www.engsoc.org/~pat/log/xbox/20041002.jpg](http://www.engsoc.org/~pat/log/xbox/20041002.jpg)

, because I didn't yet find a controller like this one unless you are right about me not looking hard enough at it when I went to the Game Stop:
[http://assets.xbox.com/en-us/support/_images/Wired-controller-callouts.jpg](http://assets.xbox.com/en-us/support/_images/Wired-controller-callouts.jpg)

Anyways I will ask next time I go.

Thank you for your help, I will let you know what happens.

---

### Post by Dr. Clock on 2008-04-20
> **psoplayer said:**
> You either didn't look at it carefully enough, or you were looking at an original Xbox controller, because a wired Xbox 360 controller just uses a regular USB port, just like your flash drive uses.

My last comment was for the comment after your last comment.
Maybe it was an older controller like you said, after all when we go to the Game Stop it has used hardware which can be older versions of the same hardware, so I got what you were saying, I just wasn't sure what the other person was saying, but it doesn't matter, so long as I can find a newer one, but
I have found that the stores like:Kmart, Walmart, ect.. generally carry the wireless Xbox 360 controllers.

---

### Post by Dr. Clock on 2008-04-21
OK, I was wrong about Walmart not having corded Xbox 360 controllers.
Anyways here is what I bought:
[http://store.gameshark.com/viewItem.asp?utm_source=Shopzilla&utm_medium=shopping&idProduct=2652](http://store.gameshark.com/viewItem.asp?utm_source=Shopzilla&utm_medium=shopping&idProduct=2652)
, when I went there I had my choice of the controller I bought and
another xbox 360 controller called Neo or something.
The Controller I bought was called MadCatz.
There are both USB just like you said.

---

### Post by psoplayer on 2008-04-22
> **Dr. Clock said:**
> I don't know exactly what you mean.
Did you mean that the Xbox 360 controller I was looking at may have had this connection on the end of it?
[http://www.engsoc.org/~pat/log/xbox/20041002.jpg](http://www.engsoc.org/~pat/log/xbox/20041002.jpg)

, because I didn't yet find a controller like this one unless you are right about me not looking hard enough at it when I went to the Game Stop:
[http://assets.xbox.com/en-us/support/_images/Wired-controller-callouts.jpg](http://assets.xbox.com/en-us/support/_images/Wired-controller-callouts.jpg)

kbless was talking about the breakaway connector which you see in the second photo you linked to. It's a small circular connection built into the cord just before the usb port at the end of the cord. Both original Xbox and 360 controllers have these, but they differ slightly in size. The purpose of them is if something jerks the cord, such as someone tripping over the wire, it would jerk the controller plug or your usb port at an abnormal angle, but instead it will just disconnect the breakaway connector.

---

### Post by psoplayer on 2008-04-22
> **Dr. Clock said:**
> OK, I was wrong about Walmart not having corded Xbox 360 controllers.
Anyways here is what I bought:
[http://store.gameshark.com/viewItem.asp?utm_source=Shopzilla&utm_medium=shopping&idProduct=2652](http://store.gameshark.com/viewItem.asp?utm_source=Shopzilla&utm_medium=shopping&idProduct=2652)
, when I went there I had my choice of the controller I bought and
another xbox 360 controller called Neo or something.
The Controller I bought was called MadCatz.
There are both USB just like you said.

Also, I cannot guarantee that this xpad driver will work with madcatz or other off-brand controllers. In the code there are a lot of 3rd party controllers provided for, but I think most of them are left over from when it was solely an original xbox controller driver.

---

### Post by landeel on 2008-04-22
I have a controller that I think will work with xpad. It's a driving wheel. It's supposed to work with PC, Playstation, Gamecube and XBOX. It does work plug and play with Window$.

My problem is when I plug it, "usbhid" driver loads and gets the device. The device is detected, "/dev/input/js0" gets created, but the controller simply does not respond to any buttons or axes. :confused:

So I have added my controller's ID to "xpad.c", compiled, installed and modprobed.
The device has 2 different IDs : "0x0c12,0x8801" and "0x0c12,0x0005". I've tried it with both IDs. But still usbhid gets loaded when I plug the damn thing. :confused:

I have tried blacklisting the usbhid driver in "/etc/modprobe.d/blacklist", but then when I plug the controller, neither usbhid or xpad get loaded. "modprobe xpad" works, but doesn´t make me a "/dev/input/js0". :confused:

I've found someone with the exact same controller ID and problem here: [http://www.opensubscriber.com/message/xbox-linux-devel@lists.sourceforge.net/4599580.html]("http://www.opensubscriber.com/message/xbox-linux-devel@lists.sourceforge.net/4599580.html")
The guy said:
> Ok i finally found...i had to black list my pad IDs in usbhid and modify the
usb_device_id in the xpad driver; it works now. 

Well, does anyone know how to do that? I'm kinda lost here. I'm about to sell this controller if I can't get it working with Ubuntu! :confused:

---

### Post by landeel on 2008-04-22
Hey, I got it (almost) working with this monster : [http://ubuntuforums.org/attachment.php?attachmentid=66817&stc=1&d=1208916646]("http://ubuntuforums.org/attachment.php?attachmentid=66817&stc=1&d=1208916646")
Well, the input I'm getting is really messed up, I'm not getting button release events, and the axis are seriously messed up. But at least I can get some response from the device now.

---

### Post by Grumbel on 2008-05-04
For those interested, there is an alternative to the xpad kernel driver, namely the xboxdrv userspace driver, coincidently written by myself:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

So in case the xpad driver is causing trouble, that one might be worth a try. If any gamepad doesn't work with it, just drop me a mail.

---

### Post by Dr. Clock on 2008-05-06
[http://ubuntuforums.org/showthread.php?t=570642&page=15](http://ubuntuforums.org/showthread.php?t=570642&page=15)

I edited this comment because:
The moderator squished at least 2 threads together,

so some of the comments in this thread are out of place

a little,

but I am going to try my best to clean up my comments.

---

### Post by cszikszoy on 2008-05-06
I'd be interested to know if you can get this working with ZSNES.  Would you mind testing for me?  I have the wireless controllers but no usb -> wireless adapter

---

### Post by Dr. Clock on 2008-05-07
So far it works with these emulators:
Gens which is a Sega Genesis emulator.

It worked with dega which is a Sega Master System emulator which I downloaded from the internet.
You don't have to configure the controller in dega like the other emulators, but however pause doesn't work, but in Windows XP pause works.

GFCE Ultra NES Emulator works with it, but you have to reconfigure the controller with it every time because you can't save the controller settings.

It works with Zsnes which is a Super NES emulator
which you have to configure the controller and save but only once,
and is my favorite SNES emulator at the moment.


Kamefu never worked for me at all in any way.

I am still on a mission to test these emulators:
PCSX,
VBA Express,
DeSmuME, 
and any other emulators which I haven't tried yet. 

Like Gameboy, Gameboy color, and Atari emulators.

---

### Post by gnivler on 2008-05-07
Great thread, very helpful.  I am ramping up on the learning curve atm so definitely still a hardcore noob, with some dated unix experience.

I have managed to get working drivers installed, following [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller).  I'm running (uname -a) Linux gnivler-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux.

jscalibrate is showing appropriate (apparently) responses to my Xbox360 wireless les paul controller (with wired USB receiver).  It is mapped to js2 apparently.

I've got Guitar Hero III (GH3.exe) running all the way to the main menu with Wine, using Native dxd9_??.dll files that I copied from my paid Vista installation.  The game seems to be working normally, unfortunately with some screen tearing at the moment, and responds to the keyboard.  It doesn't seem to detect the joystick (guitar) controller at all.

Just posting my progress for others and in hopes that someone knows how to force or imply certain controllers be used, or otherwise have ideas to progress my particular issue at present.

---

### Post by gnivler on 2008-05-07
Got the source compiled and installed with your changes, no errors.  Kernel module re-added, et al.
Still have a flashing Xbox ring on my wireless Les Paul guitar controller.  I hold the 'wireless connect' button on the guitar, which makes the ring rotate quickly, then I press the connect button on the wireless receiver and the LEDs flash in sync with each other once, the receiver LED goes solid and the guitar is flashing on all 4 quadrants.  Same behaviour from what I can tell, still not working.

This is the source I compiled:

```
	/* Turn off the LEDs on xpad 360 controllers */
	if (xpad->is360) {
		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
    		int j;
		struct usb_endpoint_descriptor *ep_irq_out;
		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
	}

	return 0;
```

> **btich said:**
> Hi, Im looking for people who can get their controller to work with the driver from xbox-linux but have the problem with non-stop blinking leds. Could you please try the patch below and report if it works or not.

Original driver:
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c)
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h)


---

### Post by gnivler on 2008-05-08
> **Grumbel said:**
> For those interested, there is an alternative to the xpad kernel driver, namely the xboxdrv userspace driver, coincidently written by myself:

[http://pingus.seul.org/~grumbel/xboxdrv/](http://pingus.seul.org/~grumbel/xboxdrv/)

So in case the xpad driver is causing trouble, that one might be worth a try. If any gamepad doesn't work with it, just drop me a mail.


Very nice.. it works for me in my initial testing, with a wireless receiver + les paul guitar controller.  Unfortunately, Guitar Hero still doesn't recognize/use the controller, same as with xpad.

Now to try my wired USB xbox360 controller which was preventing my system from even booting with xpad installed.
Wow, very cool - proper LED status, and the driver turns off the guitar when I ctrl-c it (or at least, the LEDs go off.. the quadrant lights itself back up if I re-launch the driver).

From the readme, I'm trying to figure out how to launch the driver with support for both a wired and wireless controller simultaneously, but haven't had any luck with various combinations of -id and --wid with 0s and 1s.  This is the --list-controller output, assuming it could help:

```
 id | wid | idVendor | idProduct | Name
----+-----+----------+-----------+--------------------------------------
  0 |   0 |   0x045e |    0x028e | Microsoft Xbox 360 Controller
  1 |   0 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 0)
  1 |   1 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 1)
  1 |   2 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 2)
  1 |   3 |   0x045e |    0x0719 | Microsoft Xbox 360 Wireless Controller (PC) (Port: 3)
```

---

### Post by Dr. Clock on 2008-05-09
ZSNES works well with the xbox 360 controller, and
is easy to configure in ZSNES.
then I noticed the sound quality was bad so I adjusted it to 16000HZ which although makes it sound good however then the sound is behind what is happening on the screen, and if I put it on 22050HZ the sound quality is bad, but the sound then is in sync with what is going on on the screen and yes I adjusted all the other sound features that I could see in front or so I think because there is always a way to adjust things in the Linux world, but I don't have the skills to do those kinds of things.
to enter full screen: alt-enter
to exit full screen: alt-enter
to go to ZSNES menu: Esc
I am not sure why I gave up on ZSNES, but I like it better then 
gsnes9x, and snes9express now.
ZSNES even has a clock if you want, so you know what time it is when your playing games on it.
ZSNES used to not work, even if used ADD/REMOVE and or 
Synaptic Package Manager to remove and install, or re-install,
so I downloaded a program called: KPackage in ADD/REMOVE, 
and 
ran a search in the program for ZSNES,
because ZSNES wasn't at the bottom of the huge list they had listed like I thought it would be.

---

### Post by Dr. Clock on 2008-05-09
> **btich said:**
> Hi, Im looking for people who can get their controller to work with the driver from xbox-linux but have the problem with non-stop blinking leds. Could you please try the patch below and report if it works or not.

Original driver:
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c)
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.h)

Patch:
```
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;

```

   I don't get it
I don't mean to be of trouble, but could you please post not just the befores, but also the afters?, so we can see the differences in were we are suppose to copy and paiste the code in what files?

---

### Post by Dr. Clock on 2008-05-09
I found this answer for fixing the Axis 0 and Axis 1 in Gens to work with controllers in general:
[http://ubuntuforums.org/showthread.php?t=687139](http://ubuntuforums.org/showthread.php?t=687139)
the only problem I was having was that 
when I went to places then click on Computer then
click on the name you put for computer which in my case is Ray,
then go to the menu on the top of this window and click view then click on show hidden files, then look for
.Gens, then look for gens.cfg and open it and copy what he says to copy which is:

Patch:
```

P1.Up=4097
P1.Down=4098
P1.Left=4099
P1.Right=4100 

```
in place of what is already there, but before you do all this config the xbox 360 wireless controller in Gens configure the controller so that up, down, left, right, are configured to any buttons, and configure the rest of the configuration to the buttons you want them to be, because it won't matter, because you will be righting over the them(the up, down, left, right inputs)  in the config file anyways, then finish configuring the controller and then paiste the code in the gens.cfg like he said to do.

---

### Post by Dr. Clock on 2008-05-10
[http://ubuntuforums.org/showthread.php?t=570642&page=15](http://ubuntuforums.org/showthread.php?t=570642&page=15)

I edited this comment because:
The moderator squished at least 2 threads together,

so some of the comments in this thread are out of place

a little,

but I am going to try my best to clean up my comments.

---

### Post by gnivler on 2008-05-10
> **Dr. Clock said:**
> I don't get it
I don't mean to be of trouble, but could you please post not just the befores, but also the afters?, so we can see the differences in were we are suppose to copy and paiste the code in what files?

No trouble..  I just figured this out, to do it automatically
Save the code and apply the diff with patch:
Copy the code into a file, call it xpad.diff for example, I don't know what convention exists for this if any.
Go to the directory where you have xpad.c
**$ cat > xpad.diff**

(paste in the code you copied)
(of course you can use another method to get this text into a file this is just one way)
 
```
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;

```

Hit ctrl-d to signal end-of-file, which saves what you pasted into that filename.  Then:
**$ patch xpad.c xpad.diff**

That will apply the diff provided and you can compile with the new code.  It will replaced your xpad.c so make sure you have a backup or the archive to re-extract, I haven't gotten as far as 'patch' making backups.

---

### Post by Dr. Clock on 2008-05-10
> **gnivler said:**
> No trouble..  I just figured this out, to do it automatically
Save the code and apply the diff with patch:
Copy the code into a file, call it xpad.diff for example, I don't know what convention exists for this if any.
Go to the directory where you have xpad.c
**$ cat > xpad.diff**

(paste in the code you copied)
(of course you can use another method to get this text into a file this is just one way)
 
```
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;

```

Hit ctrl-d to signal end-of-file, which saves what you pasted into that filename.  Then:
**$ patch xpad.c xpad.diff**

That will apply the diff provided and you can compile with the new code.  It will replaced your xpad.c so make sure you have a backup or the archive to re-extract, I haven't gotten as far as 'patch' making backups.

Is any of this done in the Terminal?
Like for instance the 2 times you mention 
$ cat > xpad.diff
I am still a little confused, but maybe I will get it if I keep trying.


Thank you.
Obviously I could not do this without anyones help, really really thank you all for your help so far for help and support,

---

### Post by gnivler on 2008-05-10
> **Dr. Clock said:**
> Is any of this done in the Terminal?
Like for instance the 2 times you mention 
$ cat > xpad.diff
I am still a little confused, but maybe I will get it if I keep trying.

Heya.  Yes, the bold parts are in the terminal, I bolded them so it would be clearer which were commands to be typed.  From a conceptual stand point, all you are trying to do is:

1.  create a text file with the "diff" code provided
2.  patch the original xpad.c with the "diff" code, using patch

You are welcome, gotta start somewhere, I am learning right now too so it's good I can help someone out.

---

### Post by gnivler on 2008-05-10
> **Dr. Clock said:**
> Never, this worked for my Wireless Xbox 360 Controller and Receiver:
[http://ubuntuforums.org/showthread.php?t=570642&page=4](http://ubuntuforums.org/showthread.php?t=570642&page=4)

Yo.  Just reading over that thread, but I'm confused about your wording here, can you clarify the context of 'never'?  I've gotten my controllers working in wine with some joytester.exe but it doesn't work with Guitar Hero yet, still looking for more information.

---

### Post by Dr. Clock on 2008-05-11
I don't understand how to:
Go to the directory where you have xpad.c

Does this command put me in xpad.c?
$ cat > xpad.diff

I wouldn't know, but I don't think so, because I think my xpad.c is under this, but I am a newbee, so:
ray@ray-desktop:~$ Desktop/xpad360/xpad.c
Desktop/xpad360/xpad.c: line 1: /bin: is a directory
Desktop/xpad360/xpad.c: line 2: Desktop: command not found
Desktop/xpad360/xpad.c: line 3: Desktop: command not found
Desktop/xpad360/xpad.c: line 4: syntax error near unexpected token `('
Desktop/xpad360/xpad.c: line 4: ` * Copyright (c)  2002 - 2004  Marko Friedemann <mfr@bmx-chemnitz.de>'
ray@ray-desktop:~$ 
, so I have always wondered how Linux hackers go into a directory in the
Terminal?

---

### Post by gnivler on 2008-05-11
> **Dr. Clock said:**
> I don't understand how to:
Go to the directory where you have xpad.c

Referring to terminal here, so open one, then type in
**cd ~/Desktop/xpad360**

> Does this command put me in xpad.c?
$ cat > xpad.diff

I wouldn't know, but I don't think so, because I think my xpad.c is under this, but I am a newbee, so:
ray@ray-desktop:~$ Desktop/xpad360/xpad.c
Desktop/xpad360/xpad.c: line 1: /bin: is a directory
Desktop/xpad360/xpad.c: line 2: Desktop: command not found
Desktop/xpad360/xpad.c: line 3: Desktop: command not found
Desktop/xpad360/xpad.c: line 4: syntax error near unexpected token `('
Desktop/xpad360/xpad.c: line 4: ` * Copyright (c)  2002 - 2004  Marko Friedemann <mfr@bmx-chemnitz.de>'
ray@ray-desktop:~$ 
, so I have always wondered how Linux hackers go into a directory in the
Terminal?

Not sure what you did there, but to answer your question, 'no'.  Next in the terminal type
**cat > xpad.diff**

Paste in the diff code, hit ctrl-d to save.  You should be able to patch the file now with
**patch xpad.c xpad.diff**

And then compile.  This patch was supposed to make the LEDs stop flashing but it didn't seem to work for my controllers.  I'm using the "Userspace Xbox/Xbox360 USB Gamepad Driver" now instead.

---

### Post by Dr. Clock on 2008-05-11
It didn't work for either, but if I must ask, and hate to ask you anymore questions which you have tried your hardest to asnwer:
Does this command:
patch xpad.c xpad.diff
compile the code?
And if not what would the command be generally?

---

### Post by gnivler on 2008-05-11
> **Dr. Clock said:**
> It didn't work for either, but if I must ask, and hate to ask you anymore questions which you have tried your hardest to asnwer:
Does this command:
patch xpad.c xpad.diff
compile the code?
And if not what would the command be generally?

What do you mean 'it didn't work for either'?  Just not clear what you mean there.  The command you wrote there does not compile the code, it just updates the xpad.c file with the new code.  Ironically the answer to your other question about how to compile, is at the page you linked on another page of this thread :)

[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)
from that page:
```
Compiling and installing the drivers

Assuming your current directory is your working directory ("xpad"), all you need to do is to execute the following commands:

make
sudo make install
sudo modprobe -r xpad
sudo depmod -a
sudo modprobe xpad
```

---

### Post by Dr. Clock on 2008-05-11
Thank you for suggesting to backup my files, 
I've been using my 4G flash drive to keep what I had:
It hasn't worked yet:
I restarted by making a text file named: xpad.diff
and going to the terminal, so here is my out put all the way to where I have trouble:
ray@ray-desktop:~$ cd ~/Desktop/xpad360
ray@ray-desktop:~/Desktop/xpad360$ cat > xpad.diff
--- a/xpad.c    2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c    2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
        usb_set_intfdata(intf, xpad);
 
        /* Turn off the LEDs on xpad 360 controllers */
-       if (xpad->is360 && !xpad->isWireless) {
+       if (xpad->is360) {
                char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
                int j;
-               usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+               struct usb_endpoint_descriptor *ep_irq_out;
+               ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+               usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
        }
 
        return 0;ray@ray-desktop:~/Desktop/xpad360$ patch xpad.c xpad.diff
patching file xpad.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 566 with fuzz 1.
ray@ray-desktop:~/Desktop/xpad360$

---

### Post by Dr. Clock on 2008-05-11
> **gnivler said:**
> What do you mean 'it didn't work for either'?  Just not clear what you mean there.  The command you wrote there does not compile the code, it just updates the xpad.c file with the new code.  Ironically the answer to your other question about how to compile, is at the page you linked on another page of this thread :)

[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)
from that page:
```
Compiling and installing the drivers

Assuming your current directory is your working directory ("xpad"), all you need to do is to execute the following commands:

make
sudo make install
sudo modprobe -r xpad
sudo depmod -a
sudo modprobe xpad
```
That is ironic, thank for telling me, I don't think I would have ever understood if I hadn't asked and or didn't get the answer you gave me here.

---

### Post by gnivler on 2008-05-11
> **Dr. Clock said:**
> Thank you for suggesting to backup my files, 
I've been using my 4G flash drive to keep what I had:
It hasn't worked yet:
I restarted by making a text file named: xpad.diff
and going to the terminal, so here is my out put all the way to where I have trouble:
ray@ray-desktop:~$ cd ~/Desktop/xpad360
ray@ray-desktop:~/Desktop/xpad360$ cat > xpad.diff
--- a/xpad.c    2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c    2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
        usb_set_intfdata(intf, xpad);
 
        /* Turn off the LEDs on xpad 360 controllers */
-       if (xpad->is360 && !xpad->isWireless) {
+       if (xpad->is360) {
                char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
                int j;
-               usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+               struct usb_endpoint_descriptor *ep_irq_out;
+               ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+               usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
        }
 
        return 0;ray@ray-desktop:~/Desktop/xpad360$ patch xpad.c xpad.diff
patching file xpad.c
patch unexpectedly ends in middle of line
Hunk #1 succeeded at 566 with fuzz 1.
ray@ray-desktop:~/Desktop/xpad360$

Looks good here - patch is complaining about something wrong with the xpad.diff you created which is why that error appears.  Can you replicate this?  It shows me creating the same file then using cat again (without the > redirect) to list the content of the file, and they are identical, which *should* mean patch will process it properly.

```
mason@beast:~$ cat > xpad.diff
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;

mason@beast:~$ cat xpad.diff
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;
mason@beast:~$ 
```

There is also a Plan B you could use, again from the terminal:
$ gedit xpad.c

Once gedit is open go to the Search menu > Go to line > and enter line 566.  You should see similar code to the block above, starting with 'usb_set_intfdata(intf, xpad);'.  You can manually replace everything between 

 	/* Turn off the LEDs on xpad 360 controllers */
and
 	return 0;

with this code:

```
	/* Turn off the LEDs on xpad 360 controllers */
	if (xpad->is360) {
		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
    		int j;
		struct usb_endpoint_descriptor *ep_irq_out;
		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
	}

	return 0;
```

That is just the code once it's been patched, and is ready to compile with that change.  Going out for awhile, good luck.

---

### Post by Dr. Clock on 2008-05-11
> **gnivler said:**
> Yo.  Just reading over that thread, but I'm confused about your wording here, can you clarify the context of 'never'?  I've gotten my controllers working in wine with some joytester.exe but it doesn't work with Guitar Hero yet, still looking for more information.

Ooops your right, so I just edited it.
O and thank you for trying to help us figure out how to fix the blinking light problem, even if hasn't worked yet, doesn't mean someone can piece together what would work (from what you have shown us all) eventually.

---

### Post by cloud858rk on 2008-05-11
> **psoplayer said:**
> OK, here's what I did to get it working. Mind you this is for Gutsy only! Download that xpad360 tarball in my previous post. Extract the contents. Open a terminal and change directories into that folder. If you just extracted it to the desktop do this:
```
cd ~/Desktop/xpad360
```
Either way, you should be in the xpad360 folder now. Make sure you have all the basic complier stuff. If you don't know if you do, just do this and you'll be ok either way:
```
sudo apt-get install build-essential
```
Now you should be set up to complile the source code.
```
make
```
Some text should fly by, but if everything is ok, none of them should be any kind of error messages. Now have it automagically installed into the system:
```
sudo make install
```
From this point I could just plug my controller in and it worked! Leave me feedback and i *might* be able to help.

Thanks, I used your instructions on Hardy and it works fine. :KS

---

### Post by Dr. Clock on 2008-05-11
> **gnivler said:**
> Looks good here - patch is complaining about something wrong with the xpad.diff you created which is why that error appears.  Can you replicate this?  It shows me creating the same file then using cat again (without the > redirect) to list the content of the file, and they are identical, which *should* mean patch will process it properly.

I am not sure what you are asking for, so here is answer even if it is the wrong one:
In the text file called xpad.diff 
it has this code in it:
--- a/xpad.c	2008-03-17 14:01:22.000000000 +0100
+++ b/xpad.c	2008-03-17 14:13:02.000000000 +0100
@@ -566,10 +566,12 @@
 	usb_set_intfdata(intf, xpad);
 
 	/* Turn off the LEDs on xpad 360 controllers */
-	if (xpad->is360 && !xpad->isWireless) {
+	if (xpad->is360) {
 		char ledcmd[] = {1, 3, 0}; /* The LED-off command for Xbox-360 controllers */
     		int j;
-		usb_bulk_msg(udev, usb_sndintpipe(udev,2), ledcmd, 3, &j, 0);
+		struct usb_endpoint_descriptor *ep_irq_out;
+		ep_irq_out = &intf->cur_altsetting->endpoint[1].desc;
+		usb_bulk_msg(udev, usb_sndintpipe(udev,ep_irq_out->bEndpointAddress), ledcmd, 3, &j, 0);
 	}
 
 	return 0;

---

### Post by Dr. Clock on 2008-05-11
I am going to keep trying plan B till it hopefully works.
Even if we can't get the lights to stop blinking I won't be unhappy, because atleast the controller works for me.
I hope you get your controllers working.

---

### Post by Dr. Clock on 2008-05-11
I tried plan B:
And in Terminal this it the output:
ray@ray-desktop:~$ cd ~/Desktop/xpad360
ray@ray-desktop:~/Desktop/xpad360$ make
Makefile:11: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
ray@ray-desktop:~/Desktop/xpad360$ sudo make install
Makefile:11: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe -r xpad
ray@ray-desktop:~/Desktop/xpad360$ sudo depmod -a
ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe xpad
ray@ray-desktop:~/Desktop/xpad360$ 

Maybe someone else would like to give it a try, I have a headache and need a break for a while, but if you post anymore ideas I will test it sometime.

---

### Post by gnivler on 2008-05-11
> **Dr. Clock said:**
> I tried plan B:
And in Terminal this it the output:
ray@ray-desktop:~$ cd ~/Desktop/xpad360
ray@ray-desktop:~/Desktop/xpad360$ make
Makefile:11: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
ray@ray-desktop:~/Desktop/xpad360$ sudo make install
Makefile:11: *** missing separator (did you mean TAB instead of 8 spaces?).  Stop.
ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe -r xpad
ray@ray-desktop:~/Desktop/xpad360$ sudo depmod -a
ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe xpad
ray@ray-desktop:~/Desktop/xpad360$ 

Maybe someone else would like to give it a try, I have a headache and need a break for a while, but if you post anymore ideas I will test it sometime.

Plan B is just as good, just a different way of doing it.  The problem here is your Makefile needs a TAB instead of spaces, which is exactly what it says.  So 'gedit Makefile' and remove the spaces under all: and install: (look at the file to understand what I mean by that) and type in TABs instead.  You only need to do that on 2 lines.  Check that same URL [https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller) for a fuller description under Creating a Makefile.

---

### Post by Dr. Clock on 2008-05-12
I am sorry if it sounded like I was putting down Plan B.
I felt like having plan B was better then not having plan B, because it gives me a new route to do the same thing.
I thought that what I had written was saying how much I wanted to use plan B, and I wanted to you that you are brilliant in making up another route at our disposal.
My first comment was that I hope plan B works, but when I said plan B didn't work, I didn't mean for it to sound like I had given up on plan B,
I was giving you back the out put of what happened in the terminal.

Your right in thinking it sounded like I gave up on plan B, it was because I can't understand this even with your help, I may be able to getting it working correctly with your help, but that doesn't mean I will ever understand code.
I want to understand code, but like you said I have and we all have to start somewhere to understand.

---

### Post by gnivler on 2008-05-12
> **Dr. Clock said:**
> I am sorry if it sounded like I was putting down Plan B.
I felt like having plan B was better then not having plan B, because it gives me a new route to do the same thing.
I thought that what I had written was saying how much I wanted to use plan B, and I wanted to you that you are brilliant in making up another route at our disposal.
My first comment was that I hope plan B works, but when I said plan B didn't work, I didn't mean for it to sound like I had given up on plan B,
I was giving you back the out put of what happened in the terminal.

Your right in thinking it sounded like I gave up on plan B, it was because I can't understand this even with your help, I may be able to getting it working correctly with your help, but that doesn't mean I will ever understand code.
I want to understand code, but like you said I have and we all have to start somewhere to understand.

Don't worry about it, I didn't get that impression.  Finding a way that works is the goal.  I hope my explaining is helping, I don't want to confuse you.  You are almost done what you are trying to do here though, so don't give up thinking it's far off.  All you need to do is put in those TABs instead of spaces.  A tab is just a character like a or b or 5 or space.  The Makefile wants TABs and it isn't finding them because they didn't come across in the copy and paste, so you need to edit them in yourself.  Keep reading and learning it will click in.

The bad part of all of this is it probably won't even make the LEDs stop flashing :)  Not sure the patch is effective, but I only tried it on my system so I can't say for sure.

---

### Post by Dr. Clock on 2008-05-12
I think I understand what you mean, because I just tried to explain that I just think I learn what tab is by doing a search on the internet, but when I posted it here one example with tab which never works, because it is like clicking with the mouse on the very next thing that can be picked on an internet page, 
and
the other example was how 8 spaces looks just like one hit on a tab for each row.
Then I posted my next comment in place of this comment forgetting I could have just edited this comment with it.
I just realized I forgot to erase the spaces below all and install.

---

### Post by Dr. Clock on 2008-05-12
Here was an out put in Terminal:
ray@ray-desktop:~$ cd ~/Desktop/xpad360
ray@ray-desktop:~/Desktop/xpad360$ make
Makefile:7: *** commands commence before first target.  Stop.
ray@ray-desktop:~/Desktop/xpad360$ sudo make install
[sudo] password for ray:
Makefile:7: *** commands commence before first target.  Stop.
ray@ray-desktop:~/Desktop/xpad360$

---

### Post by Dr. Clock on 2008-05-12
Here is another out put in the Terminal:
ray@ray-desktop:~$ cd ~/Desktop/xpad360
ray@ray-desktop:~/Desktop/xpad360$ make
make modules -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/ray/Desktop/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ray/Desktop/xpad360/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ray/Desktop/xpad360/xpad.mod.o
  LD [M]  /home/ray/Desktop/xpad360/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
ray@ray-desktop:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick
ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe -r xpad
ray@ray-desktop:~/Desktop/xpad360$ sudo depmod -a

ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe xpad
ray@ray-desktop:~/Desktop/xpad360$ 



This test didn't work, but I thought you might want the out put anyways.
Maybe I did something else wrong I will keep pondering.

---

### Post by gnivler on 2008-05-12
> **Dr. Clock said:**
> Here is another out put in the Terminal:
ray@ray-desktop:~$ cd ~/Desktop/xpad360
ray@ray-desktop:~/Desktop/xpad360$ make
make modules -C /usr/src/linux-headers-2.6.22-14-generic SUBDIRS=/home/ray/Desktop/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/ray/Desktop/xpad360/xpad.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/ray/Desktop/xpad360/xpad.mod.o
  LD [M]  /home/ray/Desktop/xpad360/xpad.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
ray@ray-desktop:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/2.6.22-14-generic/kernel/drivers/input/joystick
ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe -r xpad
ray@ray-desktop:~/Desktop/xpad360$ sudo depmod -a

ray@ray-desktop:~/Desktop/xpad360$ sudo modprobe xpad
ray@ray-desktop:~/Desktop/xpad360$ 



This test didn't work, but I thought you might want the out put anyways.
Maybe I did something else wrong I will keep pondering.

Congrats :)   You did it.

---

### Post by Dr. Clock on 2008-05-12
Well, then the code btich gave us didn't work, but of well at least my controller works despite the blinking lights.
Thank you for teaching me some new things I didn't know.

---

### Post by gnivler on 2008-05-14
> **Dr. Clock said:**
> Well, then the code btich gave us didn't work, but of well at least my controller works despite the blinking lights.
Thank you for teaching me some new things I didn't know.

Yeah it didn't work for me either, but the driver does work.  You're welcome good luck :guitar:

---

### Post by Dr. Clock on 2008-05-15
[http://ubuntuforums.org/showthread.php?t=570642&page=15](http://ubuntuforums.org/showthread.php?t=570642&page=15)

I edited this comment because:
The moderator squished at least 2 threads together,

so some of the comments in this thread are out of place

a little,

but I am going to try my best to clean up my comments.

---

### Post by Dr. Clock on 2008-05-21
.

---

### Post by bhuthogg on 2008-05-26
did anyone ever get the lights to stop flashing ?

---

### Post by pascalpotvin on 2008-06-09
Hi guys, I created some code to make the wireless controller to stop flashing. I'm currently cleaning the code before putting it online, so if you want a copy of the driver, just send me an e-mail: [email]pascal.potvin@gmail.com[/email]

---

### Post by k3kiaze on 2008-06-26
Hi,

I can't get this to work on Hardy. The make make install worked without errors.

cat: /dev/input/js0: No such file or directory.

modprobe xpad
WARNING: Error inserting ff_memless (/lib/modules/2.6.24-19-generic/kernel/drivers/input/ff-memless.ko): Operation not permitted
WARNING: Error inserting led_class (/lib/modules/2.6.24-19-generic/kernel/drivers/leds/led-class.ko): Operation not permitted
FATAL: Error inserting xpad (/lib/modules/2.6.24-19-generic/kernel/drivers/input/joystick/xpad.ko): Operation not permitted

I tried [this]("http://linuxgamingtoday.wordpress.com/2008/01/24/install-and-use-usb-based-gamepads-in-ubuntu/") before I found this post.

Any help appreciated.

---

### Post by kbless7 on 2008-06-26
> **k3kiaze said:**
> Hi,

I can't get this to work on Hardy. The make make install worked without errors.

cat: /dev/input/js0: No such file or directory.

modprobe xpad
WARNING: Error inserting ff_memless (/lib/modules/2.6.24-19-generic/kernel/drivers/input/ff-memless.ko): Operation not permitted
WARNING: Error inserting led_class (/lib/modules/2.6.24-19-generic/kernel/drivers/leds/led-class.ko): Operation not permitted
FATAL: Error inserting xpad (/lib/modules/2.6.24-19-generic/kernel/drivers/input/joystick/xpad.ko): Operation not permitted

I tried [this]("http://linuxgamingtoday.wordpress.com/2008/01/24/install-and-use-usb-based-gamepads-in-ubuntu/") before I found this post.

Any help appreciated.

I have to run the following code for it to work.

```
sudo modprobe -r xpad
sudo modprove xpad
```

---

### Post by k3kiaze on 2008-06-26
Thanks for replying so soon. So now, 

modprobe xpad [No Output, just goes to new command line]

cat: /dev/input/js0: No such file or directory

Xbox Controller - All 4 quadrants flash together constantly and then eventually turn off. 
Tried resetting connection, same thing.

---

### Post by kbless7 on 2008-06-26
If they eventually turn off there is something else going on. They should always be flashing (from receiving power). If it does that then eventually turns off there might be something with the current xpad installed. I run hardy now and I have to run the above code every now and then.

---

### Post by k3kiaze on 2008-06-26
Well, it's a [wireless XBox 360 Controller]("http://www.microsoft.com/hardware/gaming/ProductDetails.aspx?pid=090"). So there's a receiver connected to the USB port. 

In windows, If i press the button, flashes a few times and 1st quadrant lights up and starts working.

In ubuntu, like i said before, flashes for about 10 minutes and then turns off. I guess it can't make a connection and turns off to save battery life. Anyway this is what it did even before I followed this guide. So whatever I've done hasn't affected anything.

I'm also on hardy and I re-ran the codes, makes no difference. Thanks for the speedy replies though :)

---

### Post by adam_kimber on 2008-08-17
> **Nicolae said:**
> I've attached the source I used to build the module.

This works fine. All that needs to be done is to change the kernel version in the Makefile and then run. I created an install script just for the hell of it. 

Put the following in a file called install, make the file executable and stuff the following in it. 

```
#!/bin/bash
make
sudo rmmod xpad
sudo cp xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick 
sudo depmod -a
sudo modprobe xpad
jscalibrator
```

That should install the module, as then run jscalibrator to see if things are working.

Cannot seem to get the patch for the flashing lights to work....

---

### Post by Dr. Clock on 2009-01-20
I copied the first half of the instructions and code from this link:
[https://help.ubuntu.com/community/Xbox360Controller](https://help.ubuntu.com/community/Xbox360Controller)
In order to compile and install the new drivers, you will need a few packages. The following command will install them for you: 
```

sudo apt-get install linux-headers-`uname -r` build-essential automake1.9

```
These are packages needed in order to calibrate the controller: 
```

sudo apt-get install jscalibrator libgii1 libjsw2

```
For this code:
Make sure you install the linux-headers version that corresponds to your current kernel.

then
Download the source code that Nicolae attached to his message here:
[http://ubuntuforums.org/showthread.php?t=570642](http://ubuntuforums.org/showthread.php?t=570642)
Then right click on the file and etract the attached source code to
the desktop,
then open a terminal and copy and paiste this code
to find out what kernal version of your Ubuntu is:
```

uname -r

```
Copy and paiste that in the makefile after where it says:
KERNEL_DIR?=/usr/src/linux-headers-
in place of the kernal header that is there.

Then move the folder called xpad360 into your Home folder,

Then use this command to enter into the directory of xpad360:
```

cd /home/ray/xpad360

```
Then use this code to install:
```

make
sudo rmmod xpad
sudo cp xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick 
sudo depmod -a
sudo modprobe xpad

```
Then copy and paiste this code:
```

dmesg

```
then connect your Xbox 360 Wireless Receiver to your computer
and press the center button untill the light on your 
Xbox 360 Wireless Controller starts blinking,
then press the button on the Xbox 
360 Wireless Receiver untill it starts to blink,
then between the left and right buttons hold down the 
tiny button on top of the Xbox 360 Wireless  Controller,
then
then go to Applications,
then go to Accessories,
and open Joystick Calibration,
[B]another way to open Joystick Calibration
is by going to the terminal 
and using this command:```
jscalibrator
```[/B]
and then click on where it says calibrate and hit all the buttons
and move the nobs around in circles a few times to each nobs complete
range of movement outward, then
click on the calibrate button again, it will calibrate, then
when it is done close the Joystick Calibrator and save.
If the black box didn't show waves of green 
and the Joystick Calibration program didn't show 
other signs of movement before you even calibrated 
then you need to wirelessly connect your Xbox 360 Wireless Controller
to you Xbox 360 Wireless Receiver again,
and try my instructions with the Joystick Calibrator again.
Now test it out.
For people who want the knob to work for Gens which 
is a Sega Genesis consol emulator which can be downloaded from here:
[http://ubuntuforums.org/showthread.php?t=290008&highlight=xbox+wired+controller](http://ubuntuforums.org/showthread.php?t=290008&highlight=xbox+wired+controller)
I think I downloaded the one under Gens 2.12b (depreciated).
Anyways here's how to get the knob to work with Gens:
Open Gens and configure the controller,
it won't matter what buttons you configure for the up, down, left and right
actions, but the rest of the controller will matter.
Save that configuration,
then go to Places and open the Home Folder,
and go to view and check the box that is next to Show Hidden Files,
then open .Gens,
then open gens.cfg
and copy and paste this patch in place of the code that is the same in this file:
```

P1.Up=4097
P1.Down=4098
P1.Left=4099
P1.Right=4100

```
I got this patch from here:
[http://ubuntuforums.org/showthread.php?t=687139](http://ubuntuforums.org/showthread.php?t=687139)
And if anyone has a problem with no sound
with zsnes then copy and paiste this code in the terminal:
```

zsnes -ad sdl

```
I got this from here:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=103465&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=103465&page=2)
Thanks to all the contributors from this thread thus far.
I would never ever got my Xbox 360 Wireless Controller working with out you.[/QUOTE]

---

### Post by Dr. Clock on 2009-01-20
O, there are some things I should say:
I wasn't able to get the Xbox 360 Wireless Controller to work on
Ubuntu 8.10 named Ubuntu Intrepid Ibex,
instead what happens is when I Calibrate the controller 
with the Calibrator the Xbox 360 Wireless Controller
instead works the curser on the screen(it works as my mouse).
My mouse can work at the same time,
so instead of sticking with Ubuntu 8.10 I had to go back to
Ubuntu 8.04 named Ubuntu Hardy Heron.

Until now since it works for
   :P:P:P:PUbuntu 9.04 Jaunty Jackalope.:P:P:P:P

---

### Post by Dr. Clock on 2009-02-06
For a long the controller will work without a problem,
and one day it will just not work.
Not even restarting the computer with the xbox wireless
receiver worked connected worked, [B]so
what I have found to work when the controller doesn't work
is to re-run the make commands again.[/B]

So that my desktop is clean,
on this computer I have xpad360 here:
/home/ray/xpad360

instead of here:
/home/ray/Desktop/xpad360

[B]so I use these commands and re-calibrate the controller
in the program called Joystick Calibrator, save, and
it should then work just like before.[/B]

```

cd /home/ray/xpad360

```
Then use this code to install:
```

make
sudo rmmod xpad
sudo cp xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick 
sudo depmod -a
sudo modprobe xpad

```
Then copy and paiste this code:
```

dmesg

```

Sometimes after copying and paisting the make commands

the terminal will ask for your password,

and then it won't go through with the commands,

so in that case just paste the commands again and

another thing don't hit enter after you pasted the make codes

until the terminal stops at this command:
sudo modprobe xpad

then hit enter, and then copy and paste this code

like normal:
dmesg

---

### Post by shateredsoul on 2009-03-31
I got to the last step "sudo make install"

and i got this in response, any ideas?

omar@omar-laptop:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick/
cp: cannot stat `xpad.ko': No such file or directory
make: *** [install] Error 1
omar@omar-laptop:~/Desktop/xpad360$

---

### Post by psoplayer on 2009-03-31
> **shateredsoul said:**
> I got to the last step "sudo make install"

and i got this in response, any ideas?

omar@omar-laptop:~/Desktop/xpad360$ sudo make install
cp -f xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick/
cp: cannot stat `xpad.ko': No such file or directory
make: *** [install] Error 1
omar@omar-laptop:~/Desktop/xpad360$

There was probably an error in the previous step. Can you post what the output was from that?

---

### Post by Penguin Guy on 2009-04-01
Is there any way of getting this working for a wireless Xbox controller if you have a wireless reciver of some kind?

---

### Post by psoplayer on 2009-04-02
As far as I know, this driver will not do anything for a Xbox 360 wirless receiver. Like I posted in your thread about building a 'gaming pc', this kind of thing is just one more detail that gets overlooked by the Linux gaming advocates.

---

### Post by Penguin Guy on 2009-04-02
> **Joeb454 said:**
> I think that the Wireless controller won't work because it requires a USB dongle to connect to the controller.

I'm not sure if there is support for that just yet
Okay, thanks.

---

### Post by Dr. Clock on 2009-04-26
[B][U]Good news,

The Xbox 360 Wireless controller works on 

   :P:P:P:PUbuntu 9.04 Jaunty Jackalope.:P:P:P:P[/B][/U]

---

### Post by Dr. Clock on 2009-05-03
:p:):p:):p:):p:)

---

### Post by Dr. Clock on 2009-05-03
Also a Microsoft Xbox 360 Wireless Receiver cost me $20

which I think is worth it,

so I have 2,

1 for our Windows XP computer,

and the other is on my computer with Ubuntu on it.

---

### Post by Dr. Clock on 2009-05-03
:):p:):p:):p:):p

---

### Post by Dr. Clock on 2009-05-03
I wonder if the xpad360.tar.gz files that 

psoplayer, Nicolae, MattiViljanen and Contrast

attached are the same,


[B][U]but at least I know for sure that 

the xpad360.tar.gz file that

Nicolae attached has worked for me on:
Ubuntu Gutsy Gibbons,
Ubuntu Hardy Heron,
and Ubuntu Jaunty Jackalope.

And I beleive the xpad360.tar.gz file that

Contrast attached worked for

me on Ubuntu Gutsy Gibbons as well.[/B][/U]

---

### Post by Phil Urich on 2009-05-23
> **Dr. Clock said:**
> I wonder if the xpad360.tar.gz files that 

psoplayer, Nicolae, MattiViljanen and Contrast

attached are the same,


[B][U]but at least I know for sure that 

the xpad360.tar.gz file that

Nicolae attached has worked for me on:
Ubuntu Gutsy Gibbons,
Ubuntu Hardy Heron,
and Ubuntu Jaunty Jackalope.

And I beleive the xpad360.tar.gz file that

Contrast attached worked for

me on Ubuntu Gutsy Gibbons as well.[/B][/U]

So was it the one from Nicolae that you used and worked in Jaunty for the wireless receiver?

---

### Post by Dr. Clock on 2009-05-29
Nicolae's will work on 

Ubuntu Gutsy Gibbons,

Ubuntu Hardy Heron,

and

Ubuntu Jaunty,

but you have to:
open a terminal and copy and paiste this code
to find out what kernal version of your Ubuntu is:
```

uname -r

```
Copy and paiste that in the makefile after where it says:
KERNEL_DIR?=/usr/src/linux-headers-
in place of the kernal header that is there.

---

### Post by Kuraboy on 2009-05-29
> **Dr. Clock said:**
> Nicolae's will work on 

Ubuntu Gutsy Gibbons,

Ubuntu Hardy Heron,

and

Ubuntu Jaunty,

but you have to:
open a terminal and copy and paiste this code
to find out what kernal version of your Ubuntu is:
```

uname -r

```
Copy and paiste that in the makefile after where it says:
KERNEL_DIR?=/usr/src/linux-headers-
in place of the kernal header that is there.

I did what you said and when I type make I get this error:
```

make modules -C /usr/src/linux-headers-2.6.28-11-generic SUBDIRS=/home/monthadar/src/xpad360
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /home/monthadar/src/xpad360/xpad.o
/home/monthadar/src/xpad360/xpad.c: In function ‘xpad_open’:
/home/monthadar/src/xpad360/xpad.c:382: error: ‘struct input_dev’ has no member named ‘private’
/home/monthadar/src/xpad360/xpad.c: In function ‘xpad_close’:
/home/monthadar/src/xpad360/xpad.c:408: error: ‘struct input_dev’ has no member named ‘private’
/home/monthadar/src/xpad360/xpad.c: In function ‘xpad_probe’:
/home/monthadar/src/xpad360/xpad.c:496: error: ‘struct input_dev’ has no member named ‘cdev’
/home/monthadar/src/xpad360/xpad.c:497: error: ‘struct input_dev’ has no member named ‘private’
make[2]: *** [/home/monthadar/src/xpad360/xpad.o] Error 1
make[1]: *** [_module_/home/monthadar/src/xpad360] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [all] Error 2

```

any idea what the problem is?

---

### Post by Dr. Clock on 2009-05-31
I am sorry,

did you follow these instructions that I posted?
[http://ubuntuforums.org/showthread.php?t=570642&page=15](http://ubuntuforums.org/showthread.php?t=570642&page=15)

I must say I am still a beginner,

and had really only organized together the

instructions that worked for me.

---

### Post by Dr. Clock on 2009-06-01
Really the best advice I can give is:

If my instructions don't work then

contact the person who posted the xpad360 attachment,

and if they don't know then ask that person who would,

if that person doesn't know ask another person who has posted

here if they know about how to fix your problem.


Because this thread hasn't been all that active,

so the people who were involved with this thread are unlikely

to visit here anytime soon or so I think.

However I want this thread to stay around for people to use.

---

### Post by Dr. Clock on 2009-06-01
OK,

Try down loading my xpad360 which is almost the same as the one Nicolae

posted.

I must say try putting this folder in the HOME directly

rather then /home/monthadar/src/xpad360

put it in the HOME directory so it will look like this:

/home/monthadar/xpad360

I mean maybe I am wrong,

because I have searched google to find the answer to your

question:
[http://www.google.com/search?hl=en&q=struct+input_dev+ubuntu+xbox&btnG=Google+Search](http://www.google.com/search?hl=en&q=struct+input_dev+ubuntu+xbox&btnG=Google+Search)

but there doesn't seem to be any reasonable answer to your question

other then:

The problem is not in the driver, but in the X11 server as described there
[http://ubuntuforums.org/showthread.php?t=953639](http://ubuntuforums.org/showthread.php?t=953639)

which I just quoted from this link:
[http://ubuntuforums.org/archive/index.php/t-982579.html](http://ubuntuforums.org/archive/index.php/t-982579.html)

---

### Post by Dr. Clock on 2009-06-01
You will still have to do these things if you haven't already done so:
```

sudo apt-get install linux-headers-`uname -r` build-essential automake1.9

```
```

sudo apt-get install jscalibrator libgii1 libjsw2

```
Then use this command to enter into the directory of xpad360:
```

cd /home/monthadar/xpad360

```
Then use this code to install:
```

make
sudo rmmod xpad
sudo cp xpad.ko /lib/modules/`uname -r`/kernel/drivers/input/joystick 
sudo depmod -a
sudo modprobe xpad

```
Then copy and paiste this code:
```

dmesg

```
```
jscalibrator
```

then Calibrate your controller and save.

---

### Post by R26Otacon on 2009-06-03
I just installed Ubuntu 9.04(Upgraded from :cool: and now my xbox 360 controller is being picked up well.
the problem is my Right and Left triggers are being picked up as an axis instead of a button. I've scoured up and down the internet for fixes for this in ubuntu 9.04. I can only find solutions for other distro's and whatnot. If anyone could. would you mind helping me or just downright telling me How to have Ubuntu detect "RT" and "LT" as buttons and not axes? it really sucks not being able to use them. Thanks in advance for the help.

---

### Post by psoplayer on 2009-06-05
The triggers are a single axis in Windows as well. It's just how the controller was designed. If you were going to use them as buttons you would have to find a program that would watch that Z axis and emulate two buttons by comparing the current value to a threshold. This kind of behavior could be built into individual programs but I don't know how or if it could be installed as a software layer between the applications and the USB driver.

---

### Post by R26Otacon on 2009-06-06
> **psoplayer said:**
> The triggers are a single axis in Windows as well. It's just how the controller was designed. If you were going to use them as buttons you would have to find a program that would watch that Z axis and emulate two buttons by comparing the current value to a threshold. This kind of behavior could be built into individual programs but I don't know how or if it could be installed as a software layer between the applications and the USB driver.

So after all this time no ones been able to get a definite fix for this axis problem? I mainly want it for usage in MAME under WINE.

---

### Post by psoplayer on 2009-06-06
> **R26Otacon said:**
> So after all this time no ones been able to get a definite fix for this axis problem? I mainly want it for usage in MAME under WINE.

It's not a problem with the controller or the driver so much as it is a problem with MAME not allowing you to use an axis in place of a button in your control scheme. If you're only worried about getting it to behave as a button within programs running in WINE, you might be able to get it to work through some hackery using [AutoHotkey]("http://www.autohotkey.com/"). I don't use AH so I can't help you there but I would suggest asking for help in their forum.

---

### Post by Dr. Clock on 2009-06-07
[http://www.google.com/search?hl=en&q=struct+input_dev+ubuntu+jaunty&btnG=Search&aq=f&oq=&aqi=](http://www.google.com/search?hl=en&q=struct+input_dev+ubuntu+jaunty&btnG=Search&aq=f&oq=&aqi=)

[http://ubuntuforums.org/showthread.php?t=623315](http://ubuntuforums.org/showthread.php?t=623315)

---

### Post by BigSilly on 2009-06-07
Yeah it's the same with my 360 style pad on Windows. The sliders are actually on the same axis and cannot be set as buttons. I have only a handful of games I can successfully use the pad with - Sega Rally Revo, PES 2008, Burnout Paradise, Jade Empire...other games just don't recognise the triggers as buttons, and MAME certainly doesn't. :(  You can use the pad otherwise, just not the sliders.

Sorry matey.

---

### Post by Dr. Clock on 2009-06-07
Since I now know what MAME kind of is

I have tried to get it to work with out any success.

Maybe it's the game I've been trying called Jungle Hunt.

---

### Post by Dr. Clock on 2010-08-07
I just found out that my xbox 360 wireless controller and receiver works out of the box with Ubuntu Lucid Lynx, or at least it worked for me out of the box. Of coarse for each emulator my controller will need to be configured, but that's a given. Eventually I will test some Ubuntu distros as to whether the usual xbox 360 wireless controller and receiver work out of the box. These will be the Ubuntu distros I will eventually test my xbox 360 wireless controllers with:
Gutsy Gibbons, Jaunty, and Intrepid.

Ubuntu Hardy Heron doesn't work out of the box, so the downloadable driver that Nicole posted at the beginnning of this thread will need to be installed with Hardy Heron.

Ubuntu Lucid Lynx appears to working for my xbox 360 wireless controller out of the box.:popcorn:

Also the blinking lights still blink, and I don't know if the triggers that were said not to work work or not.

---

