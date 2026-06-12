---
title: "Safely remove USB hard drive in Linux (Ubuntu)/ Do we have the problem?"
date: 2009-04-23
forum: General Help
---

### Post by RRFarFar on 2009-04-23
Hie,

I am using Kubuntu for couple of month, before that it was Ubuntu Gnome for several years. I never really got in depth of ubuntu simply because I do want to do that, I prefer being like it is now.

Anyway in past I was concerned with famous thread here in our forums, which dealt with problem called "Ubuntu is killing your hard drive". I fixed this issue when I had Hardy. Now it is Jaunty here, and I have found an interesting post here:

[http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html]("http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html")

The guy wrote a script and I see a point of using it, because I suspect my usb device (I have two) are not suspended correctly. When I suspend them in XP I hear a sound which is like the drive's head being parked. In linux this does not happen. I suppose this not ubuntu specific problem, but anyway IS IT PROBLEM AT ALL? Experts please give your opinion, I do not want my hardware to be damaged by the software.

And another thing which is more a comment than a question. My laptop is getting hotter and louder whenever I use Linux. By the present date I was unable to address this issue, although I was trying find solution.

Thanks for you comments guys

---

### Post by krnekhelesh on 2009-04-23
Dude after downloading the script, do you run it once or everytime you try to unplug your USB drive?

---

### Post by RRFarFar on 2009-04-23
> **krnekhelesh said:**
> Dude after downloading the script, do you run it once or everytime you try to unplug your USB drive?
I haven't used it yet, just wanted to knwo more about it. In theory it should run at boot:)

---

### Post by RRFarFar on 2009-04-24
This looks like a major issue or not an issue at all. Anyway, no comment?

---

### Post by alberto ferreira on 2009-04-24
I don't belive this is harmful to the hardware. What could result in corrupt data is to remove the drive while it's being read or written.

---

### Post by RRFarFar on 2009-04-24
> **alberto ferreira said:**
> I don't belive this is harmful to the hardware. What could result in corrupt data is to remove the drive while it's being read or written.

Ok, maybe it is not hamful, but I would like my hardware to be properly suspended, so that removal would be really safe. I am not talking about loosing data while it is being written or read. For instance when disconnecting through KDE interface, the blue light on my usb hard drive stays the same, as nothing happened. While in windows it really tuns off.
Do you really think that this is pointless thread?:confused:

---

### Post by RRFarFar on 2009-04-26
Come on guys, does you silence means this issue is nothing?

---

### Post by mb_webguy on 2009-04-26
Well, the original problem about hard drives and aggressive power settings really had nothing to do with Ubuntu, precisely *because* it had nothing to do with Ubuntu.  That's a bit confusing, I know, so let me try to explain...

By default, Ubuntu doesn't mess with the power management settings in a system's BIOS.  People *were* encountering overly aggressive power management settings that resulted in a shorter hard drive lifespan, but it was because of the manufacturer's BIOS settings.  So the problem existed because Ubuntu did exactly what it was supposed to do.

As for the LED on the USB drive...  Windows puts a device into suspend mode when it is "safely disconnected".  Linux doesn't.  In the case of some external hard drives, this could mean that the disk still spins.  While [some people disagree]("http://elliotli.blogspot.com/2009/01/safely-remove-usb-hard-drive-in-linux.html"), it should be perfectly fine to remove a USB device that has been unmounted, since even if the disk is spinning, the read/write head isn't on the disk.  And of course even that only applies to USB hard drives, and not flash drives.  

Basically, considering the number of Linux user/developers and the prevalence of USB devices, if this were actually a problem, it would have been fixed at a very high level by now.

---

### Post by RRFarFar on 2009-04-27
Thanks for your time. I am a bit closer to understanding now. :)

---

### Post by BurnGates on 2009-06-09
ArghHHHH so confused by this issue. I can't even remember if the LED on my Maxtor Basics 500gb used to turn off when I "safely removed" in windows (There's no product support, and no documentation provided with the hardware).  

At the moment the light remains on for several seconds after removing the USB cable. Surely that's not right??

I use this drive as a backup of All my important stuff....don't want to loose it....need someone to sit me on their knee and tell me it will be alright...wah :cry:

---

### Post by ubfu on 2009-07-22
> **RRFarFar said:**
> Ok, maybe it is not hamful, but I would like my hardware to be properly suspended, so that removal would be really safe. I am not talking about loosing data while it is being written or read. For instance when disconnecting through KDE interface, the blue light on my usb hard drive stays the same, as nothing happened. While in windows it really tuns off.
Do you really think that this is pointless thread?:confused:

I had the same dilemma as you.I am worry it'll harm to our hardware especially on those 2.5 USB power hard disk.

If the power doesn't suspend , isn't it like a empty car speeding at 50mph and cuts the power from the engine , just like plugging out the USB.?

---

### Post by sanette on 2010-09-11
I'd like to ask this question again.

In ubuntu, when I plug in an external USB hard disk, I can right-click on the icon and get

"Unmount"
"Safely eject"

The second one really does what I want: I can hear the disc gently spin down to a full stop. Then I can disconnect the cable safely.

But on Kubuntu, there is only one option to "safely remove". And when I use it, no spin down. After that, if I remove the USB cable, I can hear an unpleasant "click" as the disk brutally stops spinning, and I'm afraid this could damage the disk.


I've been trying to modify the "safely remove" script from KDE, but can't even find out where it is located ! Someone 
any idea ???


(kubuntu 10.04 64 bits, dell laptop)

---

