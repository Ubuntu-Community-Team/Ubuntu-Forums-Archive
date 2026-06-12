---
title: "M1330 with Jaunty. Graphics problem with any Nvidia Driver"
date: 2009-05-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by latho on 2009-05-01
Hi There,

I am a recent convert from Vista to Jaunty. Since installing Jaunty I have had random "crashes" that seem to manifest from a Graphics problem. I can run for a week without a problem and then in one day I experience 5 or 6 incidents.

What is happening is that the system locks up with either a flashing screen or random colours all over the screen. Occasionally the mouse continues to work but I have no disk activity. From there I generally have to do a hard reboot however occasionally the system will just shut down. I have had one or 2 incidents where the system seem to recover or the Xserver restarts.

I have tried with the included default Jaunty drivers. I have also tried the 180.44 and 173 drivers that are available via the Hardware Drivers Gnome Applet. I have also tried the latest release dirver for Linux 180.51. All of them exhibit the same problem.

I have contacted Dell and they have run hardware diagnostics that show no errors. Also, as Vista seems to work fine I'm thinking its more a driver issue than hardware fault.

I disabled Compiz a long time ago to make sure its not that. Also looking at the standard system logs I see nothing that suggests a fault. All I see is missing log entries from the time it hangs to the time I reboot.

This issue can happen on first boot of the day or when the system is stressed. It doesn't seem to be heat related.

My M1330 has a 128Mb GeForce 8400M GS onboard.

Any idea where I can start to obtain some information to assist with fault determination?

Thanks in advance

Andrew

---

### Post by aikiwolfie on 2009-05-01
Run the system without the Nvidia drivers and see what happens. I have an M1330n and don't get this problem. So far as I know Dell have never been clear about exactly what is different in the n-series versions of the product.

Have you tried an earlier version of Ubuntu? Are you using the Dell iso or the Canonical iso?

[http://linux.dell.com/wiki/index.php/Ubuntu_9.04]("http://linux.dell.com/wiki/index.php/Ubuntu_9.04")

---

### Post by latho on 2009-05-03
I am running the Canonical iso and have tried without the Nvidia drivers several times and am doing it again to confirm if that fixes the problem.

Great suggestion to use the DELL distro. I'll try that next.

Its nice to hear that in theory, as you suggest, it should work nicely.

I have a roadmap now of things to try.

Cheers

Andrew

---

### Post by compman25 on 2009-05-05
Time for a new motherboard, that is a very common problem with the 1330 with nvidia chip. I've had mine replaced 6 times so far, and it's starting to do it again.

---

### Post by edwardTheGreat on 2009-05-05
> **compman25 said:**
> Time for a new motherboard, that is a very common problem with the 1330 with nvidia chip. I've had mine replaced 6 times so far, and it's starting to do it again.


I find I don't have problems using the '173' version driver, but when I use the '180 (Recommended)' driver I have strife.

Having said that I'm getting my Motherboard replaced tomorrow morning.

OP here are some links outlining probably what you're experiencing because it sounds exactly the same as mine.

These examples are windows but it's the same thing (same as what happens to me in both windows and ubuntu)

[http://en.community.dell.com/blogs/direct2dell/archive/2008/08/18/nvidia-gpu-update-dell-to-offer-warranty-enhancement-to-all-affected-customers-worldwide.aspx]("http://en.community.dell.com/blogs/direct2dell/archive/2008/08/18/nvidia-gpu-update-dell-to-offer-warranty-enhancement-to-all-affected-customers-worldwide.aspx")

[http://www.youtube.com/watch?v=RgTDXgFbHvk&NR=1]("http://www.youtube.com/watch?v=RgTDXgFbHvk&NR=1")

[http://www.youtube.com/watch?v=tkw47rprZU8]("http://www.youtube.com/watch?v=tkw47rprZU8")

---

### Post by edwardTheGreat on 2009-05-05
In addition here is what I sent to Dell about it the problem from my experiences:

> Current Operating System: Windows Vista Ultimate / Ubuntu 9.04
Operating System this occurred with: Windows Vista Ultimate / Ubuntu 8.04 / Ubuntu 8.10 / Ubuntu 9.04

BIOS: A15

NVidia Information 
------------------
GPU: GeForce 8400M GS
Video BIOS: 60.86.45.00.40

Windows Information
-------------------
Driver: 7.15.11.7644 (From Windows Vista Update - Most Stable up to date driver)
	- Later Versions cause this to happen more frequently
	- Earlier Version (from Dell) is no more or less stable
Forceware Version: 176.44 (From Windows nVidia Control Panel)

Ubuntu Information
------------------
Driver: 173.14.16 (From Ubuntu Repositories)
	- Later Versions cause this to happen more frequently


Comments:
---------

Normally the Screen goes fuzzy/garbled and the system stops responding.


When in Windows the system failed generally with an error message similar to below (I can't remember the exact details):

*** Hardware Malfunction
Call you hardware vendor for support
NMI: Parity Check / Memory Parity Error
*** The System has halted ***

See here for example of garbled screen and Hardware Malfunction - [http://www.youtube.com/watch?v=RgTDXgFbHvk&NR=1]("http://www.youtube.com/watch?v=RgTDXgFbHvk&NR=1")

In Ubuntu, it just hangs. 

Then regardless of operating system I have to turn it off by holding down the power switch, and then restart it.

Then at reboot the screen starts black then fades into displaying lots of colours in vertical lines and eventually fades to white 
See here for example of coloured lines - [http://www.youtube.com/watch?v=tkw47rprZU8]("http://www.youtube.com/watch?v=tkw47rprZU8")




That last part about the screen starting black and then going all colours doesn't happen very often but sometimes it does. The only way to fix it is to hard-power off with the power button and then turn it back on again, and that fixes it (for a random amount of time).

Anyway as I said, I'm still getting my mobo replaced.

Hope that info helps a bit.

---

### Post by dagrnd1 on 2009-05-29
Replacing the mobo should fix it.  I had the exact same problem, and with super cool XPS warrenties, they send the tech out to do it for you!  Once I had mine switched, no more black screens with color changing lines.

---

### Post by Jekshadow on 2009-06-01
Mine has worked perfectly with the Norm ISO (not the Dell). I am running the 180 nVidia driver. Try logging on without the X server, that will determine whether it is a X problem or a hardware problem. If it is a X problem, use Apt-On-CD to backup your apps, then copy all of your files to a drive and then just reinstall. If it is not an X problem, try calling Dell about it. They will most likely just send you a new motherboard.

---

### Post by hornbake on 2009-06-04
Thanks for all the info.  I've been having the same issue on my M1330 in Jaunty and in Vista and am going directly to the phone to get Dell to send me a new motherboard.  
Will post back to confirm that the hardware fix works.

---

