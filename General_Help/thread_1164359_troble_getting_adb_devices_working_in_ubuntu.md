---
title: "troble getting adb devices working in ubuntu"
date: 2009-05-19
forum: General Help
---

### Post by banana jama on 2009-05-19
im trying to connect my g1 to ubuntu. i found a google codes forum that said to to the following:
                    > Try creating a file called /etc/udev/rules.d/50-android.rules and
plugging the following line into it:

SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"

Reload udev's configuration (/etc/init.d/udev reload) and try again as
a normal user.

This is on an Ubuntu 8.10 (Intrepid Ibex) installation (64-bit). Works
fine here after that change. Presumably (given the idVendor tag) this
will only work for the G1. 

i went to the folder udev/rules.d and notice that the files were text files so i open text editor and enter the infomation that they said (the subsystem=="usb" stuff) and saved it as 50-android.rules in the folder destination called for and used the following code to restart udev: 
  ```
sudo /etc/init.d/udev reload 
```
which output ok. but i still can't run adb devices it says command not found and i can't see what i did wrong. can someone help?
  im using 9.04 32-bit but i can't see how this would be a problem since the commands given doesn't seem version or bit type specific. any help would be appreciated.

---

### Post by banana jama on 2009-05-19
i figure out that im suppose to put stuff about the id vendor in the file. i used the code sudo Isusb and got this:
    > Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bb4:0c02 High Tech Computer Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0408:030c Quanta Computer, Inc.

my phone is an gtc g1 so i put that info in the file and it now reads:> SUBSYSTEM=="usb", SYSFS{Bus 001 Device 002: ID 0bb4:0c02}=="0bb4", MODE="0666"


i reloaded udev but the command adb devices still doesn't work.

---

### Post by banana jama on 2009-05-19
bump?

---

### Post by pieps on 2009-05-21
Are you sure your phone is set for USB debugging? Go to Settings->Applications->Development and make sure USB debugging is checked.

---

### Post by banana jama on 2009-05-22
yeah usb debugging is checked. the problem is when i type in the command adb devies it says bash command doesn't exist.

---

### Post by Jay-Jay on 2009-06-11
Create a rules file.
```
sudo gedit /etc/udev/rules.d/51.android.rules
```
copy the line below and paste into this file
> SUBSYSTEM=="usb", ATTRS{idVendor}=="0bb4", MODE="0666"
for the newer distros
or > SUBSYSTEM=="usb", SYSFS{idVendor}=="0bb4", MODE="0666"
for backwards compatability with older distros.


Save and close the file.

Unplug and replug your device.

"adb devices" should now show your device

---

### Post by itnet7 on 2009-06-22
Just wanted to confirm creating the udev rule above worked for me on Jaunty. 

Thanks for your time,

Chris C. 
itnet7 #freenode

---

### Post by mojotexas on 2009-10-20
This worked for me as well.
I am running it with an HTC Ion.

---

### Post by mTeryk on 2010-01-09
> **banana jama said:**
> 
which output ok. but i still can't run adb devices it says command not found and i can't see what i did wrong. can someone help?

Your problem isn't with the rules file, it sounds like it isn't even finding the adb tool. Try the command 

```
which adb
```

If it can't find it you need to add the location of your android sdk to your PATH.

edit the file ~/.bashrc in your favorite editor and add the following export commands at the bottom. In the example below I have the SDK in my home directory. (This assumes you are using the bash shell)

```
export  PATH=${PATH}:${HOME}/SDK/android-sdk-linux_86/
export  PATH=${PATH}:${HOME}/SDK/android-sdk-linux_86/platforms/android-2.0.1/tools/
export  PATH=${PATH}:${HOME}/SDK/android-sdk-linux_86/tools/
```

After adding those lines run the command

```
source ~/.bashrc
which adb
```

It should now find adb and then you can see if the rest of your setup is OK.

---

### Post by KhaaL on 2010-03-27
just want to add my solution. i didnt add any exception rule, i just followed these steps:

[I]Quick Howto for ubuntu:

- download SDK 1.5 r3
- enable debug mode on the device: Settings -> Applications ->
Development -> USB debugging
- add udev rule:[http://developer.android.com/intl/de/guide/developing/](http://developer.android.com/intl/de/guide/developing/)
device.html but use Samsung's vendor id instead: SYSFS{idVendor}
=="04e8"
- replace the adb binary by this one: [http://floe.butterbrot.org/external/adb.gz](http://floe.butterbrot.org/external/adb.gz)
- to use ddms on a 64 bit system: [http://coffeecokeandcode.blogspot.com/2009/07/ddms-on-ubuntu-64bit.html](http://coffeecokeandcode.blogspot.com/2009/07/ddms-on-ubuntu-64bit.html)

Patched adb thanks to Flori7500 as mentioned in my previous post.

Cheers, Olaf [/I]

Working fine on lucid beta.

Taken from [http://groups.google.com/group/android-developers/msg/ae589dcd4ce8810d](http://groups.google.com/group/android-developers/msg/ae589dcd4ce8810d)

---

### Post by rockwel on 2010-07-30
> **mTeryk said:**
> Your problem isn't with the rules file, it sounds like it isn't even finding the adb tool. Try the command 

```
which adb
```If it can't find it you need to add the location of your android sdk to your PATH.

edit the file ~/.bashrc in your favorite editor and add the following export commands at the bottom. In the example below I have the SDK in my home directory. (This assumes you are using the bash shell)

```
export  PATH=${PATH}:${HOME}/SDK/android-sdk-linux_86/
export  PATH=${PATH}:${HOME}/SDK/android-sdk-linux_86/platforms/android-2.0.1/tools/
export  PATH=${PATH}:${HOME}/SDK/android-sdk-linux_86/tools/
```After adding those lines run the command

```
source ~/.bashrc
which adb
```It should now find adb and then you can see if the rest of your setup is OK.

thanks! this was my trouble

---

