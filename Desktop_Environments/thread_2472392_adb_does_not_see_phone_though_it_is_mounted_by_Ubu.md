---
title: "adb does not see phone though it is mounted by Ubuntu 20.04"
date: 2022-02-25
forum: Desktop Environments
---

### Post by johnaaronrose on 2022-02-25
When I plug in my phone or tablet (after doing the 7 times Developer Options) using a USB lead to connect to my standard Ubuntu 20.04 box, the phone/table realises and gives me the option of File Transfer (the default) etc and mounts the phone on the Ubuntu list of apps (vertical list of icons on the left). However, I've tried various versions of adb (e.g. package

---

### Post by TheFu on 2022-02-25
It has been a long time since I used ADB. It can be fussy.  I don't think it can be used when a device has any other connection already.

I've also had failures when the adb used was in a snap package. Those never work for me.  I always have to install it outside any constrained environment.

I have an adb cheat-sheet in my personal wiki so I can get the command+options I need quickly.
```
$ adb devices  # get list of android connected devices
```

Is there a specific command you seek?
Oddly, I don't have the connection command in my notes. ;)

---

### Post by #&amp;thj^% on 2022-02-25
> **johnaaronrose said:**
> When I plug in my phone or tablet (after doing the 7 times Developer Options) using a USB lead to connect to my standard Ubuntu 20.04 box, the phone/table realises and gives me the option of File Transfer (the default) etc and mounts the phone on the Ubuntu list of apps (vertical list of icons on the left). However, I've tried various versions of adb (e.g. package

Phone should be mounted as MTP means Media Transfer Protocol. PTP means Picture Transfer Protocol, which means that the phone appears to the computer as a digital camera.
Phone Id is necessary as well:
```
lsusb
```
My output is something like this:

```
Bus 002 Device 097: ID abc1:1234 Fictional Company, Ltd.
``` 

In this case, abc1 is the Vendor ID.

Create an adb_usb.ini file: Run the following

```
echo "0x<your device's Vendor ID>" > ~/.android/adb_usb.ini
```

Restart adb
```

adb kill-server
adb start-server

```

---

### Post by johnaaronrose on 2022-02-25
I must have accidentally deleted the rest of my post. I think that I was going to say that I'd installed adb from the standard Ubuntu 20.04 packages using Synaptic which called in a bunch of other packages (e.g. android-sdk-platform-tools-common package)/ I used 'adb devices'. Is there a  better version of adb? BTW I think that I last used adb with Ubuntu 18.04 when it didi work.

---

### Post by johnaaronrose on 2022-02-25
That didn't work. adb still shows no devices. I did 
```
echo "0x<0e8" > ~/.android/adb_usb.ini
```

Results are:
```
john@desktop:~$ cat .android/adb_usb.ini
ox<0e8d>
john@desktop:~$ adb kill-server
john@desktop:~$ adb start-server
* daemon not running; starting now at tcp:5037
* daemon started successfully
john@desktop:~$ adb devices
List of devices attached

john@desktop:~$ 



```

---

### Post by #&amp;thj^% on 2022-02-25
will you please show:
```
lsusb
```
with the phone mounted.
I'm looking for:
```
Bus 003 Device 013: ID **[COLOR="#FF0000"]22b8[/COLOR]**:2e82 Motorola PCS XT1541 [Moto G 3rd Gen]

```

---

### Post by johnaaronrose on 2022-02-25
It's the MediaTek one:
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 003 Device 027: ID 0e8d:2008 MediaTek Inc. USB 2.0 Hub [Safe]
Bus 003 Device 008: ID 1a40:0101 Terminus Technology Inc. Hub
Bus 003 Device 007: ID 189a:2019  
Bus 003 Device 006: ID 062a:4c01 MosArt Semiconductor Corp. 
Bus 003 Device 005: ID 248a:8367 Maxxter CanoScan
Bus 003 Device 004: ID 1241:1503 Belkin Keyboard
Bus 003 Device 002: ID 1a40:0201 Terminus Technology Inc. FE 2.1 7-port Hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:0c31 Sunplus Innovation Technology Inc. SPIF30x Serial-ATA bridge
Bus 001 Device 004: ID 8087:0025 Intel Corp. 
Bus 001 Device 002: ID 058f:3841 Alcor Micro Corp. USB 2.0 PC Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by #&amp;thj^% on 2022-02-25
so you entered it wrong from your post: <0x<0e8>
If your sure it's your phone id, (Sure would like to know what phone it is)
use <0e8d> without the<>
```
echo "0x0e8d" > ~/.android/adb_usb.ini
```

---

### Post by johnaaronrose on 2022-02-26
@1fallen the echo without the <> also failed. The phone is a Blackview A80Pro. Same problem on MeberryM7 tablet.

---

### Post by #&amp;thj^% on 2022-02-27
> **johnaaronrose said:**
> @1fallen the echo without the <> also failed. The phone is a Blackview A80Pro. Same problem on MeberryM7 tablet.

Ok, now it makes a little more sense, you just might have to use (cough choke) Windows for this: [https://androidadbdriver.com/blackview-a80-pro-usb-drivers/](https://androidadbdriver.com/blackview-a80-pro-usb-drivers/)

---

### Post by johnaaronrose on 2022-03-03
Ubuntu 20.04 now sees phone with adb 28 using 'adb.exe devices'. I don't know what I have done to get that.<br>VirtualBox Windows 10 VM also fails with adb (v1.0.32 &amp; 1.0.39) not seeing Blackview A80Pro phone. I'd like to download adb v1.0.40 (as that's the requirement to run B4A Windows app under Wine in Ubuntu.But I can't find that version anywhere. I've followed the instructions on <a data-cke-saved-href="http://adbcommand.com/articles/How%20to%20build%20adb%281.0.40%29%20for%20windows%20on%20Ubuntu" href="http://adbcommand.com/articles/How%20to%20build%20adb%281.0.40%29%20for%20windows%20on%20Ubuntu">http://adbcommand.com/articles/How%20to%20build%20adb%281.0.40%29%20for%20windows%20on%20Ubuntu</a> but I get 'fatal: cannot make .repo directory: Permission denied' on <br>'repo init -u [https://android.googlesource.com/platform/manifest](https://android.googlesource.com/platform/manifest)'. I know nothing about repo. Anybody have any ideas about this repo problem?

---

### Post by johnaaronrose on 2022-03-07
> **1fallen said:**
> Ok, now it makes a little more sense, you just might have to use (cough choke) Windows for this: [https://androidadbdriver.com/blackview-a80-pro-usb-drivers/](https://androidadbdriver.com/blackview-a80-pro-usb-drivers/)

Interestingly, adb.exe (i.e. adb version for Windows) does not see my phone with 'adb devices': I've tried various versions (e.g. 32,41) both in Windows 10 and a VirtualBox Windows 10 VM. I've now got the Linux version 30 of adb and it sees my phone.
I

---

### Post by johnaaronrose on 2022-03-07
Interestingly no version of adb.exe (on VirtualBox Windows 10 VM and Windows 10 on somebody else's Windows 10 box) sees my phone. I've tried various versions of adb.exe (e.g. 32 & 40).

---

### Post by johnaaronrose on 2022-03-07
That failed (on both VirtualBox Windows 10 VM & somebody's else's  but got Linux to see phone by using SDK files that somebody else pointed me to.

---

