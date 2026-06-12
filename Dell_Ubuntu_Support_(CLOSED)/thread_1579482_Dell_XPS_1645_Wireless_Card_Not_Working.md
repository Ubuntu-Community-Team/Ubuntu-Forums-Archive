---
title: "Dell XPS 1645 Wireless Card Not Working"
date: 2010-09-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Hack.The.Pow. on 2010-09-21
Hey guys.  I'm new to the forum and relatively new to linux.  I had my old dell laptop setup with a dual boot of Windows 7 and kubuntu.  I have recently got a Dell Studio XPS 1645(free upgrade from dell).  After setting up my windows 7 partition I partitioned my drive and installed ubuntu.  However to my dismay wireless was not working.

My wireless card is the Intel WiMAX/WiFi Link 6050 Series.

I searched around for solutions and was having trouble with some of the solutions that were presented.  I heard that the firmware was incompatible with ubuntu and to try and use ndiswrapper.  I downloaded  ndiswrapper but had trouble following the instructions i found on how to get it working properly.  If someone could help me out with this it is much appreciated.

I would really love to learn more about linux but without wireless it is very hard.

Thanks in advance!

P.S.  If someone know an easier solution it would be much appreciated!!!!

---

### Post by mörgæs on 2010-09-22
Welcome to the forum.

There was a bug for these cards, but it is solved now:
[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/532451)

Do you have 'lucid-proposed' enabled as a package source?

---

### Post by Hack.The.Pow. on 2010-09-22
I just enabled lucid-proposed as a package source and updated everything.  I restarted and nothing has changed.  

I also tried adding the 6050 microcode to the /lib/firmware folder and still nothing has changed.

Any suggestions?

---

### Post by mörgæs on 2010-09-22
[http://ubuntuforums.org/showthread.php?t=1529993](http://ubuntuforums.org/showthread.php?t=1529993)

If that does not work, you could try 10.10 (beta):
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Hack.The.Pow. on 2010-09-22
thanks I will try that solution sometime.  Do you think installing the beta will be too much of a risk for a linux noob?  

Also if I were to install 10.10 from scratch would I be able to downgrade back to 10.04?  Or should I just stay with 10.04, upgrade to 10.10, and if that is too much of a hassle switch back to 10.04?

Sorry if that seems stupid.

---

### Post by Hack.The.Pow. on 2010-09-22
Woooohooo!!! Finally got it working.  I think the problem was me originally messing around with ndiswrapper and somehow got the wireless card somehow removed from the linux system all-together.  

I then uninstalled ubuntu.  Reinstalled it.  Downloaded the microcode and the package linux-backports-modules-wireless-lucid-generic.  Then I restarted and everything worked perfectly.

Thanks for the help.

---

### Post by mörgæs on 2010-09-23
You are welcome. Please mark the thread 'solved' to help others with the same problem.

---

