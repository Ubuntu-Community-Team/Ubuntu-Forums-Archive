---
title: "razerd Segmentation faults in Maverick"
date: 2010-11-23
forum: Desktop Environments
---

### Post by skaramanger on 2010-11-23
Greetings,

I have am using Maverick Meerkat 10.10 

Kernel version:

2.6.35-22-generic

I have a Razer DeathAdder gaming mouse.  I am trying to compile/run this tool:

[Razer config tool]("http://bu3sch.de/joomla/index.php/razer-nextgen-config-tool")

I have jumped through several hoops:

[http://ubuntuforums.org/showthread.php?p=9876151]("http://ubuntuforums.org/showthread.php?p=9876151")

This install was for 10.04.

This link helped with taming the mouse a little:

[http://ubuntuforums.org/showthread.php?t=1343927&highlight=razer]("http://ubuntuforums.org/showthread.php?t=1343927&highlight=razer")

```
xinput --set-prop "Razer Razer DeathAdder" "Device Accel Constant Deceleration" 5
```

```
xinput --set-prop "Razer Razer DeathAdder" "Device Accel Velocity Scaling" 1
```


I get the program to compile (after some problems the usb.h file not being where the system said it was) and I install it following these instructions in the README file that I have attached.

I get a segmentation fault error when the razer daemon razerd tries to start:

  ```
44.202331] input: Razer Razer DeathAdder as /devices/pci0000:00/0000:00:02.1/usb1/1-4/1-4.3/1-4.3:1.0/input/input8
[   44.202408] generic-usb 0003:1532:0016.0008: input,hidraw1: USB HID v1.11 Mouse [Razer Razer DeathAdder] on usb-0000:00:02.1-4.3/input0
[   44.202433] razerd[2514]: segfault at 10 ip 00007fcf976a87aa sp 00007fff28b2cc80 error 4 in libc-2.12.1.so[7fcf9765f000+17a000]

```

It goes w/o saying that I cannot run razercfg or qrazercfg.

If your got this far I hope you have some suggestions for me.  Please take time to follow the links I have provided before replying.  They provide incite to current situation.

Thanks

Skaramanger

---

### Post by skaramanger on 2010-11-23
I've also looked at this link:

[https://wiki.archlinux.org/index.php/Razer]("https://wiki.archlinux.org/index.php/Razer")

---

### Post by realzippy on 2010-11-24
*"..(after some problems the usb.h file not being where the system said it was).."*

...guess you edited *CMakeLists.txt* (line 23),to find usb.h.,
maybe you got a wrong path there ?If so:

..suggest to change line 23 to:

**check_lib(usb /usr/src/linux-headers-2.6.35-22-generic/include/config/usb.h)**

and recompile the stuff,do not forget [this]("http://ubuntuforums.org/showpost.php?p=9871987&postcount=11").

Back in a few hours....

---

### Post by skaramanger on 2010-11-24
zippy:

> **realzippy said:**
> *"..(after some problems the usb.h file not being where the system said it was).."*

...guess you edited *CMakeLists.txt* (line 23),to find usb.h.,
maybe you got a wrong path there ?

Exactly, but... see below

If so:

..suggest to change line 23 to:

**check_lib(usb /usr/src/linux-headers-2.6.35-22-generic/include/config/usb.h)**

I attempted that and discovered that that was not where usb.h was located. Though the system thought is was at where you posted it to be.  I installed libusb.dev from the repositories and it installed it here: /usr/include/usb.h  So I changed line 23 to that and got it to compile with some warnings



and recompile the stuff,do not forget [this]("http://ubuntuforums.org/showpost.php?p=9871987&postcount=11").

Yeah I have that all setup and double checked.

Back in a few hours....

Here are my compile messages:

```
[~/razer]$ cmake .
-- Configuring done
-- Generating done
-- Build files have been written to: /home/xxxxx/razer
 [xxxxx~/razer]$ make
[  0%] Generate udev rules
Generating udev rules
srcdir=/home/xxxxx/razer  bindir=/home/xxxxx/razer  instdir=/usr/local
[ 11%] Built target razer_udev_rules
[ 22%] Building C object librazer/CMakeFiles/razer.dir/librazer.o
[ 33%] Building C object librazer/CMakeFiles/razer.dir/cypress_bootloader.o
/home/xxxxx/razer/librazer/cypress_bootloader.c: In function ‘cypress_print_one_status’:
/home/xxxxx/razer/librazer/cypress_bootloader.c:57: warning: format not a string literal and no format arguments
/home/xxxxx/razer/librazer/cypress_bootloader.c: At top level:
/home/xxxxx/razer/librazer/cypress_bootloader.c:168: warning: ‘cypress_cmd_verifyfl’ defined but not used
[ 44%] Building C object librazer/CMakeFiles/razer.dir/hw_copperhead.o
/home/xxxxx/razer/librazer/hw_copperhead.c: In function ‘copperhead_commit’:
/home/xxxxx/razer/librazer/hw_copperhead.c:264: warning: unused variable ‘value’
/home/xxxxx/razer/librazer/hw_copperhead.c: In function ‘copperhead_read_fw_ver’:
/home/xxxxx/razer/librazer/hw_copperhead.c:250: warning: ‘err’ is used uninitialized in this function
[ 55%] Building C object librazer/CMakeFiles/razer.dir/hw_deathadder.o
[ 66%] Building C object librazer/CMakeFiles/razer.dir/hw_krait.o
[ 77%] Building C object librazer/CMakeFiles/razer.dir/hw_lachesis.o
[ 88%] Building C object librazer/CMakeFiles/razer.dir/hw_naga.o
Linking C shared library librazer.so
[ 88%] Built target razer
[100%] Building C object razerd/CMakeFiles/razerd.dir/razerd.o
Linking C executable razerd
[100%] Built target razerd
 [~/razer]$ 
```

Thanks for your help

Skaramanger

---

### Post by realzippy on 2010-11-24
That looks fine,where is the problem?(sorry,blind and tired in the moment-late here in europe-)

sorry for stupid question:

Have you run

```
sudo make install
```

after "make" (which looks fine?)

---

### Post by skaramanger on 2010-11-24
zippy,

Yeah I ran that and no error messages came back. Only when I attempt to starte the daemon or reboot the computer I get the posted error message and a udev error that admittedly I havn't investigated yet.  It scrolled by in the boot messages.

Thanks again,

Sleep tight,

Skaramanger

> **realzippy said:**
> That looks fine,where is the problem?(sorry,blind and tired in the moment-late here in europe-)

sorry for stupid question:

Have you run

```
sudo make install
```

after "make" (which looks fine?)

---

### Post by realzippy on 2010-11-25
That is strange.Compiled it here,exactly same "make" output,same kernel,aso,
and "qrazercfg" starts the GUI tool (no mouse to configure,do not have a razer),screenshot attached.

..have you noticed (readme) the X11 chapter (.[I].because on configuration events razerd has to temporarly unregister the mouse from the
system[/I])?And have you configured your xorg.conf that way?Note that you will only have a *xorg.conf* when running ATI/NVIDIA proprietary driver.Otherwise you might have to create one...



Edit:

*"Yeah I ran that and no error messages came back.....and a udev error."*
Can you post your "make install" output?BTW,here is "mine":

```
XXXXX@xxxxx:~/razer$ sudo make install
[sudo] password for XXXXX: 
[  0%] Generate udev rules
Generating udev rules
srcdir=/home/xxxxx/razer  bindir=/home/xxxxx/razer  instdir=/usr/local
[ 11%] Built target razer_udev_rules
[ 88%] Built target razer
[100%] Built target razerd
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/librazer.so
-- Installing: /etc/udev/rules.d/01-razer-udev.rules
-- Installing: /usr/local/sbin/razerd
-- Removed runtime path from "/usr/local/sbin/razerd"
-- Installing: /usr/local/bin/pyrazer.py
-- Installing: /usr/local/bin/razercfg
-- Installing: /usr/local/bin/qrazercfg

```

---

### Post by mxx on 2010-11-25
I also have troubles with DeathAdder in Maverick.
```
mxx@ubuntupc:~(0:57)% sudo razerd                    
Razer device service daemon
razer_usb_claim: first claim failed -25
razer-deathadder: USB read 0x01 0x05 failed: -25
hw_deathadder: Failed to get firmware version
zsh: segmentation fault  sudo razerd
```
What does it mean?

---

### Post by skaramanger on 2010-11-26
Zippy,

Whack!

Make install:

```
[xxxxx ~/razer]$ sudo make install
[sudo] password for xxxxx: 
[  0%] Generate udev rules
Generating udev rules
srcdir=/home/xxxxxx/razer  bindir=/home/xxxxxx/razer  instdir=/usr/local
[ 11%] Built target razer_udev_rules
[ 22%] Building C object librazer/CMakeFiles/razer.dir/librazer.o
[ 33%] Building C object librazer/CMakeFiles/razer.dir/cypress_bootloader.o
/home/terryg/razer/librazer/cypress_bootloader.c: In function ‘cypress_print_one_status’:
/home/terryg/razer/librazer/cypress_bootloader.c:57: warning: format not a string literal and no format arguments
/home/terryg/razer/librazer/cypress_bootloader.c: At top level:
/home/terryg/razer/librazer/cypress_bootloader.c:168: warning: ‘cypress_cmd_verifyfl’ defined but not used
[ 44%] Building C object librazer/CMakeFiles/razer.dir/hw_copperhead.o
/home/terryg/razer/librazer/hw_copperhead.c: In function ‘copperhead_commit’:
/home/terryg/razer/librazer/hw_copperhead.c:264: warning: unused variable ‘value’
/home/terryg/razer/librazer/hw_copperhead.c: In function ‘copperhead_read_fw_ver’:
/home/terryg/razer/librazer/hw_copperhead.c:250: warning: ‘err’ is used uninitialized in this function
[ 55%] Building C object librazer/CMakeFiles/razer.dir/hw_deathadder.o
[ 66%] Building C object librazer/CMakeFiles/razer.dir/hw_krait.o
[ 77%] Building C object librazer/CMakeFiles/razer.dir/hw_lachesis.o
[ 88%] Building C object librazer/CMakeFiles/razer.dir/hw_naga.o
Linking C shared library librazer.so
[ 88%] Built target razer
[100%] Building C object razerd/CMakeFiles/razerd.dir/razerd.o
Linking C executable razerd
[100%] Built target razerd
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/librazer.so
-- Installing: /etc/udev/rules.d/01-razer-udev.rules
-- Installing: /usr/local/sbin/razerd
-- Removed runtime path from "/usr/local/sbin/razerd"
-- Up-to-date: /usr/local/bin/pyrazer.py
-- Up-to-date: /usr/local/bin/razercfg
-- Up-to-date: /usr/local/bin/qrazercfg

```

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Thu Apr 22 20:35:23 PDT 2010


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
Section "InputDevice"

    # generated from default
    Identifier     "Mouse"
    Driver         "mouse"
    Option	   "Device" "/dev/input/mice"

EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#
#    # generated from default
#    Identifier     "Keyboard0"
#    Driver         "kbd"
#EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Still looking through my logs trying to find the message referring to UDEV. Sorry didn't post last night holiday here in the states and I was involved in food consumption/digestion :D


Found 'em

```
Nov 26 10:22:31 tz-desktop udevd[423]: SYSFS{}= will be removed in a future udev
 version, please use ATTR{}= to match the event device, or ATTRS{}= to match a 
parent device, in /etc/udev/rules.d/01-razer-udev.rules:6
```


```
# UDEV rules for razer devices
#
# We just send a rescan command to razerd.
# It will pick up new devices and forward information to the applications.

ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="1532", RUN+="/usr/local/bin/razercfg --scan"
ACTION=="remove", SUBSYSTEM=="usb_device", RUN+="/usr/local/bin/razercfg --scan"

/etc/udev/rules.d/01-razer-udev.rules (END) 
```



Thanks again,

Skaramanger

---

### Post by skaramanger on 2010-11-26
mxx,

Can you post an error message from your messages log file (>use dmesg | grep error from the commmand prompt)?

> **mxx said:**
> I also have troubles with DeathAdder in Maverick.
```
mxx@ubuntupc:~(0:57)% sudo razerd                    
Razer device service daemon
razer_usb_claim: first claim failed -25
razer-deathadder: USB read 0x01 0x05 failed: -25
hw_deathadder: Failed to get firmware version
zsh: segmentation fault  sudo razerd
```
What does it mean?



skaramanger

---

### Post by realzippy on 2010-11-26
@ sraramanger
Guess I am out;cannot reproduce the segfault without DeathAdder mouse.
What about some try/error action ?
Since we seem to have a comparable set-up (maverick 32 bit,2.6.35,nvidiadriver,razertool from git(?)) I suggest to
unplug/change the DeathAdder to see if *qrazercfg* will start then,
*as it does here* without a razer mouse connected.

Offtopic,but,what does *[Whack!]("http://www.urbandictionary.com/define.php?term=whack")* mean here?Just improving my english/american vocabulary...

@ mmx
What happens when running in terminal:
```
qrazercfg
```

@ both
Wondering if your problems are related,maybe due to an old firmware?
Once read about some razer mouse firmware updates due to usb problems  even in windows...

---

### Post by skaramanger on 2010-11-27
Zippy,

Whack

> 
What about some try/error action ?
Since we seem to have a comparable set-up 

(maverick 32 bit,2.6.35,nvidiadriver,razertool from git(?)) 


I have a 64bit system.... running Maverick 2.6.35-23-generic Thats the problem isn't it?  Can I add a compile time switch to have the compiler make 32bit code? Or am I out of options?

> 
I suggest to
unplug/change the DeathAdder to see if *qrazercfg* will start then,
*as it does here* without a razer mouse connected.


I'll try disconnecting the mouse and start razerd service after I finish this post. Don't want anything surprises while composing. :)


> 
Offtopic,but,what does *[Whack!]("http://www.urbandictionary.com/define.php?term=whack")* mean here?Just improving my english/american vocabulary...


Sorry 'bout that.  I've seen it used in posts where the responder places the word Whack or the phrase Whackity Whack! to let a reader other than the original poster know that text has been removed or Whacked! Or on the other hand if your familiar with American colloquial phrase used by the Mafioso: Whack is used describe the act of killing a rival.  Here it is used with a somewhat lesser killing deletion of text. :)

> 
@ mmx
What happens when running in terminal:
```
qrazercfg
```


I get: failed to connect to socket errno(111). Connection refused
is razerd running?

> 
@ both
Wondering if your problems are related,maybe due to an old firmware?
Once read about some razer mouse firmware updates due to usb problems  even in windows...

---

### Post by skaramanger on 2010-12-01
> **skaramanger said:**
> Zippy,

Whack



I have a 64bit system.... running Maverick 2.6.35-23-generic Thats the problem isn't it?  Can I add a compile time switch to have the compiler make 32bit code? Or am I out of options?



I'll try disconnecting the mouse and start razerd service after I finish this post. Don't want anything surprises while composing. :)




Sorry 'bout that.  I've seen it used in posts where the responder places the word Whack or the phrase Whackity Whack! to let a reader other than the original poster know that text has been removed or Whacked! Or on the other hand if your familiar with American colloquial phrase used by the Mafioso: Whack is used describe the act of killing a rival.  Here it is used with a somewhat lesser killing deletion of text. :)



I get: failed to connect to socket errno(111). Connection refused
is razerd running?

Can I pleas get a bump?

---

### Post by realzippy on 2010-12-01
*"I'll try disconnecting the mouse and start razerd service after I finish this post"*

....so have you?

---

### Post by skaramanger on 2010-12-01
Zippy,

> **realzippy said:**
> *"I'll try disconnecting the mouse and start razerd service after I finish this post"*

....so have you?

Sorry about not getting back to this in a timely fashion.

I first did a make clean, cmake., make, sudo make install. Now from here I typed this:

```
sudo razerd 
Razer device service daemon
frazer_usb_reconnect_guard: The device did not reconnect! It might not work anymore. Try to replug it.
razer_usb_force_reinit: Failed to discover the reconnected device
razer-deathadder: USB read 0x01 0x05 failed: -32
hw_deathadder: Failed to get firmware version
razer_usb_claim: first claim failed -9
Segmentation fault

```

Before the seg fault, I had the mouse disconnected. I connected the mouse and I tried this:

```
qrazercfg
^CTraceback (most recent call last):
  File "/usr/local/bin/qrazercfg", line 412, in pollNotifications
    def pollNotifications(self):
KeyboardInterrupt
^C^C
Traceback (most recent call last):
  File "/usr/local/bin/qrazercfg", line 419, in scan
    def scan(self):
KeyboardInterrupt
Traceback (most recent call last):
  File "/usr/local/bin/qrazercfg", line 421, in scan
    mice = razer.getMice()
  File "/usr/local/bin/pyrazer.py", line 273, in getMice
    count = self.__recvU32()
  File "/usr/local/bin/pyrazer.py", line 239, in __recvU32
    return self.__receiveExpectedMessage(self.sock, self.REPLY_ID_U32)
  File "/usr/local/bin/pyrazer.py", line 230, in __receiveExpectedMessage
    pack = self.__receive(sock)
  File "/usr/local/bin/pyrazer.py", line 208, in __receive
    hdr = sock.recv(hdrlen)
socket.error: [Errno 104] Connection reset by peer

```

Yes I did try to get out of qrazercfg and eventually I did.  So I don't know if this is reliable or not. However, the message above concerning firmware it the important message.

Thanks for your patience,

skaramnger

---

### Post by skaramanger on 2010-12-01
Zippy,

Check that on the last post.  I redid the test and got qrazercfg to start.  Below are the details:

```
sudo razerd 
Razer device service daemon
Failed to bind socket to /var/run/razerd/socket: Address already in use
 [terryg@tz-desktop ~]$ sudo rm /var/run/razerd/socket*
 [terryg@tz-desktop ~]$ sudo razerd 
Razer device service daemon
razer_usb_claim: first claim failed -9
razer_usb_claim: first claim failed -9
razer_usb_claim: first claim failed -9
razer_usb_claim: first claim failed -9



```

```
qrazercfg

```

At this point I'm able to modify my mouse settings. Everytime I make a change the -9 error message appears in the daemon window. Anyhow whoopee it functions!  I think there is a little more work to do here.  

Thanks again,

skaramanger

---

### Post by skaramanger on 2010-12-11
Well there has been more work done.  I can't get razerd to load upon boot, it segfaults.  I then have to got the the process again:

open a terminal 
disconnect the mouse
start razerd  >>$sudo razerd
plug the mouse in
start qrazercfg
configure mouse

After all this if I stop razerd, start it as a service

>>sudo service razerd start

boom segfault.

I'm going back to the authors website for a review.

Skaramanger

---

### Post by tzi0 on 2010-12-18
Can you explain me, zippy? Here is my steps:
tzi0@tzi0-desktop ~ $ git clone git://git.bu3sch.de/razer.git
Initialized empty Git repository in /home/tzi0/razer/.git/
remote: Counting objects: 928, done.
remote: Compressing objects: 100% (387/387), done.
remote: Total 928 (delta 621), reused 779 (delta 529)
Receiving objects: 100% (928/928), 376.69 KiB | 516 KiB/s, done.
Resolving deltas: 100% (621/621), done.
tzi0@tzi0-desktop ~ $ cd razer
tzi0@tzi0-desktop ~/razer $ cmake .
-- The C compiler identification is GNU
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Looking for usb.h
-- Looking for usb.h - found
-- Check if the system is big endian
-- Searching 16 bit integer
-- Looking for sys/types.h
-- Looking for sys/types.h - found
-- Looking for stdint.h
-- Looking for stdint.h - found
-- Looking for stddef.h
-- Looking for stddef.h - found
-- Check size of unsigned short
-- Check size of unsigned short - done
-- Using unsigned short
-- Check if the system is big endian - little endian
-- Configuring done
-- Generating done
-- Build files have been written to: /home/tzi0/razer
tzi0@tzi0-desktop ~/razer $ make
Scanning dependencies of target razer_udev_rules
[  0%] Generate udev rules
Generating udev rules
srcdir=/home/tzi0/razer  bindir=/home/tzi0/razer  instdir=/usr/local
[ 11%] Built target razer_udev_rules
Scanning dependencies of target razer
[ 22%] Building C object librazer/CMakeFiles/razer.dir/librazer.o
[ 33%] Building C object librazer/CMakeFiles/razer.dir/cypress_bootloader.o
/home/tzi0/razer/librazer/cypress_bootloader.c: In function ‘cypress_print_one_status’:
/home/tzi0/razer/librazer/cypress_bootloader.c:57: warning: format not a string literal and no format arguments
/home/tzi0/razer/librazer/cypress_bootloader.c: At top level:
/home/tzi0/razer/librazer/cypress_bootloader.c:168: warning: ‘cypress_cmd_verifyfl’ defined but not used
[ 44%] Building C object librazer/CMakeFiles/razer.dir/hw_copperhead.o
[ 55%] Building C object librazer/CMakeFiles/razer.dir/hw_deathadder.o
[ 66%] Building C object librazer/CMakeFiles/razer.dir/hw_krait.o
[ 77%] Building C object librazer/CMakeFiles/razer.dir/hw_lachesis.o
[ 88%] Building C object librazer/CMakeFiles/razer.dir/hw_naga.o
Linking C shared library librazer.so
[ 88%] Built target razer
Scanning dependencies of target razerd
[100%] Building C object razerd/CMakeFiles/razerd.dir/razerd.o
Linking C executable razerd
[100%] Built target razerd
tzi0@tzi0-desktop ~/razer $ sudo make install
[  0%] Generate udev rules
Generating udev rules
srcdir=/home/tzi0/razer  bindir=/home/tzi0/razer  instdir=/usr/local
[ 11%] Built target razer_udev_rules
[ 88%] Built target razer
[100%] Built target razerd
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/lib/librazer.so
-- Installing: /etc/udev/rules.d/01-razer-udev.rules
-- udevadm control --reload-rules: 0
-- ldconfig: 0
-- Installing: /usr/local/sbin/razerd
-- Removed runtime path from "/usr/local/sbin/razerd"
-- Installing: /usr/local/bin/pyrazer.py
-- Installing: /usr/local/bin/razercfg
-- Installing: /usr/local/bin/qrazercfg
tzi0@tzi0-desktop ~/razer $ sudo ldconfig
tzi0@tzi0-desktop ~/razer $ 

ive changed my xorg.conf and i copied initscript like it says readme file, but when im trying to qrazercfg i have a Segmentation fault (((

---

### Post by realzippy on 2010-12-19
@ skaramanger & tzi0

What about [contacting]("http://bu3sch.de/joomla/index.php/contact") razer/the guy who wrote the razertool,Michael Buesch?

---

### Post by skaramanger on 2010-12-19
> **realzippy said:**
> @ skaramanger & tzi0

What about [contacting]("http://bu3sch.de/joomla/index.php/contact") razer/the guy who wrote the razertool,Michael Buesch?

Hey Zippy,

Thanks for following up.  Yeah I did contact him.  His first reply to my request was kind of snippity (not terribly friendly) however he did send another note and mentioned that he made some changes and to try the 0.8 version.  

So I downloaded over my original source and tried a make clean.  It crapped out.  A problem with the make file.  I hesitate to contact him again since his first reply was short and mentioned to the effect that its free software and this is what you get. :o 

So I cleaned house and downloaded it through git again and I got it to work, just not after a reboot. And not after the hoops I mentioned in the previous hosts.

So I may yet contact him, but I'm hesitant.  Maybe after the holidays.

Sincerely,

Skaramanger

---

### Post by tzi0 on 2010-12-20
Thanks fo replies. Please report here after. It cares me too

---

### Post by realzippy on 2010-12-20
> **skaramanger said:**
> Hey Zippy,

Thanks for following up.  Yeah I did contact him.  His first reply to my request was kind of snippity (not terribly friendly) however he did send another note and mentioned that he made some changes and to try the 0.8 version.  

So I downloaded over my original source and tried a make clean.  It crapped out.  A problem with the make file.  I hesitate to contact him again since his first reply was short and mentioned to the effect that its free software and this is what you get. :o 

So I cleaned house and downloaded it through git again and I got it to work, just not after a reboot. And not after the hoops I mentioned in the previous hosts.

So I may yet contact him, but I'm hesitant.  Maybe after the holidays.

Sincerely,

Skaramanger

Maybe he had a bad day or was busy;
*"Or visit me. Don't forget to bring beer with you ;-)"*
(contact info) sounds very pleasant to me.Send him a bottle of beer;albeit
this is like bringing owls to athens.
BTW,bought a razer salmosa for gf's computer.Nice DPI/speed switches on the back...
Anyway,if it now works,it cannot be so hard to make it reboot-persistent ...?

---

### Post by skaramanger on 2010-12-21
Well, 

After the reinstall of the source using git and recompiling.  I just now rebooted into the latest updated kernel. I am happy to report that razerd daemon is running and I can start qrazerdcfg and configure the mouse at my leisure.  It doesn't appear to save my last config, but that is small potatoes. I believe that my problem is solved.  So I won't need to ask for more help from Herr Busche.  But I will send him a note of thanks again.

Sincerely,

Skaramanger

Now if Tzi0 still needs help, I won't mark this solved

---

### Post by tzi0 on 2010-12-23
I will try to compile tonight and necessarily leave the reply here. Thanks for you

---

### Post by tzi0 on 2010-12-24
It works for me. Thanks!

---

