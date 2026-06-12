---
title: "Dell SP2309W LCD monitor"
date: 2008-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gcshum on 2008-12-31
I'm using Ubuntu Hardy. The monitor's built-in webcam works fine but I cannot make the built-in mics work. I couldn't find anything related to this monitor as it is still quite new. Did anyone manage to solve this problem? I believe the mics use a USB connection since there is no mic input jack on the monitor.

Thanks.

---

### Post by nikkkko on 2009-01-05
Hi, 

I have the SP2208WFP monitor and although the webcam works, the mic does not, nor did I come across anyone who managed to make it work. However, that was a while ago so perhaps there is someone out there now?

(A long winded way of saying, 'bump')

---

### Post by gcshum on 2009-01-05
Is there an easy way to contact Dell for this support? Technical support email? On-line chat?

I tried the 1-800 number for support but there is no option for monitor support. And there is no service tag on this monitor, so I can't contact them through the website either.

It's no very easy to get technical support from Dell. :(

Anyone?

---

### Post by nikkkko on 2009-01-05
You can try the [Dell linux forum]("http://en.community.dell.com/forums/3525.aspx").  I tried it for some laptop support but didn't get very far.

Edit - just saw your post on the Dell forum.

---

### Post by gcshum on 2009-01-16
Called Dell. They tossed me around a few departments. Finally I landed on Ubuntu support department. Turned out they don't support Ubuntu. They told me to go to Canonical or search online for solution. That's how they support their Dell products!

Anyone found a solution yet?

---

### Post by nikkkko on 2009-01-16
I had another look and can't find anyone who has this mic working under linux. FYI

```
lsusb
Bus 003 Device 005: ID 0424:2514 Standard Microsystems Corp. 
Bus 003 Device 004: ID 05a9:2643 OmniVision Technologies, Inc. 
Bus 003 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0458:0048 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 0000:0000  

```

Can you post your output?

I'm wondering which is the mic and if it's even there.

---

### Post by gcshum on 2009-01-18
> **nikkkko said:**
> I had another look and can't find anyone who has this mic working under linux. FYI

```
lsusb
Bus 003 Device 005: ID 0424:2514 Standard Microsystems Corp. 
Bus 003 Device 004: ID 05a9:2643 OmniVision Technologies, Inc. 
Bus 003 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0458:0048 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 001: ID 0000:0000  

```

Can you post your output?

I'm wondering which is the mic and if it's even there.

Mine output of lsusb is as follows:

Bus 011 Device 001: ID 0000:0000  
Bus 010 Device 001: ID 0000:0000  
Bus 009 Device 001: ID 0000:0000  
Bus 008 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 0424:2514 Standard Microsystems Corp. 
Bus 004 Device 003: ID 05a9:2649 OmniVision Technologies, Inc. 
Bus 004 Device 002: ID 0424:2512 Standard Microsystems Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

I believe the 2 lines with Standard Microsystems Corp. are the 2 internal mics. The one with OmniVision Technologies, Inc. is the webcam.

---

### Post by nikkkko on 2009-01-19
There are two mics?  

OK, assuming the Standard Microsystems Corp. devices are the mics, perhaps there is some other usb mic which uses the same hardware?  And which someone has working under linux?

---

### Post by gcshum on 2009-01-20
Yes, according to Dell, there is one mic on left and one on the right of the webcam.

---

### Post by Spitz on 2009-01-30
I have the same problem with the mics, and the output from lsusb is the same:

```
lsusb
Bus 005 Device 007: ID 1976:6025 Chipsbrand Microelectronics (HK) Co., Ltd. 
Bus 005 Device 006: ID 0424:2514 Standard Microsystems Corp. 
Bus 005 Device 005: ID 05a9:2649 OmniVision Technologies, Inc. 
Bus 005 Device 003: ID 0424:2512 Standard Microsystems Corp. 
Bus 005 Device 002: ID 07c4:0251 Datafab Systems, Inc. 
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0461:4d10 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Has anyone had any progress with getting the mics to work?

---

### Post by fooubufor on 2009-01-31
i'm testing on Fedora 10 and am seeing the exact same thing.  The camera works fine, but the mic doesn't.  When i look at the pulseaudio manager, i don't see any devices for the microphone, nor do i seem able to add one.  Whats weird though, is when i open something like Skype, i can see the monitor webcam as an input device.  Choosing it and testing, of course, results in a failure.

The UVC project lists another Omnivision in a different Dell monitor, device 05a9:2643, as supported, but not this device, 05a9:2649.  i haven't seen anything about a patch yet.

---

### Post by mr.phillychill on 2009-02-05
Hello Fellow DELL SP2309W Monitor users,

I've found a way to enable and/or greatly increase the playback level for these built in microphones, with no 3rd party software!

[I'm using Windows XP and wrote this at a novice level]

1) After installing the webcam software make sure to update its actual drivers in the Device Manager. **Start/ Control Panel/ System/ Hardware/ Device Manager/**.
In the drop-down-list click on **Sound, video, and game controllers**. 
Click on **Monitor Webcam **to highlight, right click, in the drop down box chose **update driver**, then click **Next**, and follw the Hardawar Update Wizard insturctions. (If you get an exclamation mark on the driver, this is normal, simply go through the update process again and it should be fixed.) 

2)Go to "**Sound and Audio Devices**" in the control panel; **Start/ Control Panel/ Sound and Audio Devices/** and click on the,"**Voice**" tab.
You should see 2 settings. One for voice playback and one for **Voice recording**. 
In the **voice recording drop down box**, you should have," **Monitor Webcam**" already checked in the box. If not click on the arrow on chose Monitor Webcam, then click apply.

3) Again, in the "**Voice Recording**" box click on "**Volume**". Turn the **volume bar **all the way up.
While still in the **Volume control **click on the,"**Advanced**" tab. This will bring up a box," **Advanced Controls for Capture**". 
In its sub categories will be," Tone controls" and "Other controls". 
Under** Other controls **should be 2 boxes (**AGC and Loudness**) if these boxes are not checked, please check them and then exit by clicking on the **close** button.

MISSION ACCOMPLISHED?

Test your configuration by clicking the," **Test Hardware**" button under voice recording options and follow the Wizard's instructions.

*if still not receiving playback from your microphone you may try checking or uncheck the mute box for your recorder then trying again.

I hope this helps!

Thanks,

Phil

---

### Post by mr.phillychill on 2009-02-05
Opps, did not want to post this.

---

### Post by fooubufor on 2009-02-07
Hehe.. and i thought *i* was taking a risk posting a Fedora comment.
i think the community is pretty forgiving though.  :)

---

### Post by Spitz on 2009-02-08
Haha, yeah, we are quite forgiving.

mr.phillychill: Thanks for you post, but this a Linux forum. Linux is an other [OS]("http://en.wikipedia.org/wiki/Operating_system") than Windows, so our problem is how to get the system to recognize the mics, not just enhance it's performance.

---

### Post by Morganman on 2009-02-13
Hi

I am using this monitor.

Being new to Linux have not yet even had a result with the camera.
How have you peeps acheived this result.

Thanks

---

### Post by nikkkko on 2009-02-13
I did it by installing uvcvideo.  

However, due to some bizarre idiosyncrasy, in terminal I have to: 
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```

not once, but twice or three times and my webcam appears.

---

### Post by Spitz on 2009-02-13
I only know that my webcam works since it worked out of the box with Skype. The mics do however not work, so I can't call with skype :(

---

### Post by forestcomber on 2009-04-25
Anyone have any luck getting the microphones to work ?

I'm running a Dell SP2309W monitor on Ubuntu 9.04 on an Asus eee PC 901.  The resolution is perfect at 2048 x 1152.  The webcam works perfectly.  But I can't get the microphones to work !!

---

### Post by forestcomber on 2009-04-25
The microphones appear as a choice in Skype audio set-up but they don't work.

---

### Post by nikkkko on 2009-04-26
After a fair amount of googling to see if anyone managed to get it to work, I'm afraid I gave up on the mic as a lost cause some time ago.

---

### Post by Thorndog on 2009-10-10
> **nikkkko said:**
> I did it by installing uvcvideo.  

However, due to some bizarre idiosyncrasy, in terminal I have to: 
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```

not once, but twice or three times and my webcam appears.

Interesting, it did the same for me, now hopefully we can find a solution for the Mics we'll have a super skype setup....
aaaargh, I hate to have to boot into that other OS just for this.

---

### Post by nikkkko on 2009-10-12
I bought a usb mic...

---

### Post by lurnin9 on 2010-02-22
Hmmm ... I'm on 9.10 Ubuntu, and I can't even get the USB ports to do anything useful.  Is there a way to activate them?  Are they supposed to be powered, or do they require the attached device to provide the power to the port?  I've tried everything from a simple USB flash drive to USB-based external HDs, DVD-ROM drives, and my iPod, but I can't access any of them through the monitor's USB (downstream) ports.

How can I tell if the OS has even detected them?  The user manual of course has nothing useful.

I'll get to the camera and mics later ...

Thanks,
Lurnin9

---

### Post by compaq64 on 2010-02-22
as nice as Ubuntu is dell wont provide support, it acutally voids your warrenty for some compaies.  Best Buy is one of those companies that wont provide any support if you install ubuntu on the computer.

---

### Post by gotanothergrot on 2010-03-12
> **nikkkko said:**
> I did it by installing uvcvideo.  

However, due to some bizarre idiosyncrasy, in terminal I have to: 
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo
```

not once, but twice or three times and my webcam appears.

wow, for the first time _ever_ my dell integrated webcam is working in Linux just by following the code here:D 

Thanks nikkkko:)

---

### Post by villapad on 2010-03-31
hi, I try my first Ubuntu (9.1) installation and I get to this forum with a diferent question around my Dell SP2309W. 
After the install it just shows a black screen, but, in the left edge, a reddish 2mm thin borderline appears showing that there's Ubuntu there, only misplaced... 
I turn to the monitor to request an auto-center of the picture but it does nothing so I understand there might be a driver issue at stake. 
Would I need a special, separate driver to have manually installed?
Does somebody had this problem or knows what to do?
thanks in advance,

---

### Post by lordbah on 2010-04-03
I was baffled for quite a while as to why my SP2309W webcam wouldn't "just work", when it did for so many other people. Turns out the USB cable needs to be attached directly into the back of the computer. When attached to an external USB hub the camera offers far fewer formats/resolutions/frame rates, and in fact could not be made to work. Note that I don't know if this is true of all USB hubs, or only the cheap one I have.

However I also have not gotten the microphones to work.

---

### Post by lordbah on 2010-04-03
Got the microphones.

Volume icon / right click / Sound preferences / Hardware tab / Monitor_Webcam / Input tab / Monitor_Webcam Analog Stereo / Input volume near max. At first it showed 2 Input levels, and only the top level would ever show anything, and then only when I made very loud noises. Later, it shows only 1 level, which reacts pretty normally to normal volume sounds.

After this Cheese was able to record video with sound. Output was terrible above 800x600 but tolerable there.

No way for me to test it yet with Pidgin or Empathy.

---

