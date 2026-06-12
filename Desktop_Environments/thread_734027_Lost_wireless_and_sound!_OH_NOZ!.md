---
title: "Lost wireless and sound! OH NOZ!"
date: 2008-03-24
forum: Desktop Environments
---

### Post by MikeonTV on 2008-03-24
I am duel booting my laptop with Ubuntu (FF) and Vista. I am planning on running the windows OS through VMware in Ubuntu using help from this thread - [http://ubuntuforums.org/showthread.php?t=680553](http://ubuntuforums.org/showthread.php?t=680553) - but I have a couple of problems to conquer first. 

At some point I logged in to Ubuntu and was prompted with new updates to install. So I did and was asked to restart. Then my grub prompted me with a second Ubuntu choice (I used to only have the option of Vista or Ubuntu) it looked like a backup.

So I entered the new version of Ubuntu and to my surprise things looked the same except that my wireless would not connect and my sound was gone (it took a long time to figure out the sound in the first place)

I re entered the backup version and things worked. So some time has passed and the backup now has not sound or wireless. 

Can anyone help me get up to date with the newest version, loose the backup and have sounds/wireless running before I get this vmware up and running?

---

### Post by Sam Lars on 2008-03-24
What is the output of
```
lspci
```
in a terminal?

---

### Post by MikeonTV on 2008-03-25
Thanks for the response. 

In my lspci it gives me
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by Sam Lars on 2008-03-25
For your wireless, you might try this guide.
[http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+dell+wireless](http://ubuntuforums.org/showthread.php?t=297092&highlight=1390+dell+wireless)
Also, before you try that, you might want to upgrade to 7.10 Gutsy, as it seems you're still using 7.04

---

### Post by Sam Lars on 2008-03-25
And for sound you might want to look through this thread as well as the thread it links to.
[http://ubuntuforums.org/showthread.php?t=733764&highlight=82801G](http://ubuntuforums.org/showthread.php?t=733764&highlight=82801G)

---

### Post by jimbo99 on 2008-03-25
To the guy that posted the guides:  WAKE UP.

Ubuntu is for the human being in the world.  It isn't about spewing guides.  Please attempt to help him as if he were a human.

Now, if you had read his comment correctly you would have realized that he already stated that his sound worked and continues to work as long as he uses the old kernel.  He's saying that by simply doing the update he lost his wireless and sound---both of which were working previously.  He further states that they work if he chooses to use the prior version.

Updating in this fashion should not disable features on his unit.  In fact, to the uninitiated this type of problem would be considered inhumane.

I would say that it is inappropriate of Canonical to release updates that break people's units and that it does against the philosophy that Ubuntu is for the human being.

---

### Post by leroyc on 2008-03-25
I can figure out few things:

1. Check the ALSA drivers for the sound.(if needed - recompile them)
2. ls - la /dev/snd (check the ownership or paste it here). Note: your user must be added to the group owning the devices.

3. For the Wireless - feel lucky you dont have it. The NM-Applet is a very stupid application. 

Try the wicd one. Its way better.

I have explained how it works here:
[URL="http://top-web-solutions.com/ubuntu-wireless-application/"]
Ubuntu Wireless
[/URL]

---

### Post by Sam Lars on 2008-03-25
@ jimbo99
Yes, I see your point, but if the guide works, why not point them to it to check it out?  The point is to help them solve their problem, and if that's what they need, then I've done that.  If not, then they can let me know, or they can ask on the guide.  Now they have more options.  And if someone comes along that knows more about it, then I digress.  Better some links to guides than no replies.
If you read to paragraph four of his post, he says that the previous kernel no longer works.  Hence his post.
I agree with you on your last point.  I wish that my hardware would always work between releases.  Unfortunately, that's a weakness of the open source community, as Microsoft has much more clout to get manufacturers to make their hardware work with Windows.  Linux is on its own a lot of times, and I think that the developers do a fantastic job of reverse-engineering things to get them to work.  Also, remember that most of them are not employed at a software giant, but volunteer their time to further the software.
Ideally, software would work always, on everything, just the way we want it to.  Unfortunately, this is not a perfect world.  Things break.  An OS is enormously complex.  It's very hard to make sure everything is working as it should.  That's what bugs are for.
If you want to make sure that your hardware will work, then you should Beta test.  I am.  My wireless doesn't work.  I'm helping out with the bug report and the process of fixing it.
We can only do our best.  If the software doesn't work, that's what we're here for.  To help them figure out their problems and guide them towards a solution, if we can.
In the future, if you have issues like this that you'd like to address, please PM rather than leave it where people are trying to help each other.  Since you left it here, I felt I'd respond to it here.

---

