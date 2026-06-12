---
title: "Compiz Lag while Maximizing from Taskbar"
date: 2009-08-20
forum: Desktop Environments
---

### Post by Acidwarlord on 2009-08-20
Hi,

my system:
Ati mobility Radeon 2600
```
dertester@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc M76 [Radeon Mobility HD 2600 Series]

```
Intel T7300 2x2ghz  2Gb Ram  Acer 7720G
Ubuntu Jaunty  2.6 .28. 15
---------------

When i minimize a programm in the Taskbar and then click on it, to get it back, my system freezes for about 1sek(depends a bit on the size of the Window) an then smoothly slides the window back on the Desktop to use it.

Minimizing works without lag. Using the benchmark in compiz (F12+super) it shows about 125frames...(ATM when i maximize it stucks at 125 and when the window pops up it continues at 125, but dosnt break in to 0frames)

The CPU stays under 100% while this action...

I can move my mouse all the time, when i play a video, it shortly stucks but musik play smoothly.

All other Effects like "wooble windows" are working perfect;)

Catalyst Control Center 2.6
2D Driver 8.60.40
Open GL 2.1.8575

Installed via Ubuntu system-settings-hardware driver, only had to activate the driver...

Any Tipps, whats missing or how i can fix this lag?
If i disable the Effects for maximizing in compiz settings manager, the problem is NOT solved...

---

### Post by Acidwarlord on 2009-08-20
Hi,

i was able to solve my Problem:

**_First: Install newest Ati Driver_**
> 1. Go into Restricted Drivers and disable Ubuntu's ATI proprietary driver.

2. Go to ATI's website ([http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)) and download the latest linux driver for your card. It will be a .run file

3. Run "sudo apt-get install dpkg-dev debhelper libstdc++5 dkms build-essential cdbs fakeroot" to make sure you have all the required packages

4. Make the .run file executable

5. In a terminal, run "./ati-driver-installer<VERSION YOU HAVE>-x86.x86_64.run --buildpkg Ubuntu/9.<whatever version Ubuntu your running>" . If you need to, you can do --listpkg instead of --buildpkg to see what the available Ubuntu versions are included.

6. It will output many .deb files into the directory the .run file was in. You will only need the following 2...

7. "sudo dpkg -i fglrx-kernel-source_<VERSION YOU HAVE>.deb"

8. "sudo dpkg -i xorg-driver-fglrx_<VERSION YOU HAVE>.deb"

9. Then run "sudo aticonfig --initial" to create a new xorg.conf

10. Reboot

I took the Radeon -> HD 2600 for my mobility Radeon, unlike windows it worked without problems^^


**_Second: Xserver and this grafics got some issues, so i installed the xsever without backfill_**

Link:
_[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)_

1.Add ```
deb http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main 
deb-src http://ppa.launchpad.net/ubuntu-x-swat/xserver-no-backfill/ubuntu jaunty main 
``` to your sources, directly or use packet managment

2.> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9

3. sudo apt-get update
4. sudo apt-get upgrade
5.reboot

Most information was found here:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186?comments=all)

[http://ubuntuforums.org/archive/index.php/t-1107559.html](http://ubuntuforums.org/archive/index.php/t-1107559.html)

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

---

### Post by tolzkutz on 2009-12-13
I just want to say thank you for this how-to. Very helpful!

---

### Post by OldMerovingian on 2010-03-11
With the upcoming release of 10.04, I am not sure this will remain an issue, but I added the following to my repositories and it stopped ALL lag!  Thanks to all for your help!

[https://launchpad.net/~k0ekk0ek/+archive/ppa](https://launchpad.net/~k0ekk0ek/+archive/ppa)

---

### Post by darkshines87 on 2010-03-30
Hi ppl,

I have a HD 2600 Mobility Card in my Laptop and the maximizing lag is making me freaking crazy! I couldn't solve it by any suggested Updates. I just tried OldMerovingian's solution, but that just killed my Xserver (again ](*,)](*,)](*,)](*,)](*,)](*,))

I really hope they fix it with the next driver...

[EDIT]
OMG I can't believe how numb I am! :D

This lag was freaking me out so much, I forgot to reset xorg.conf. 
@OldMerovingian your solution works like a charm! Thank you so much!

---

### Post by PAgore on 2010-04-01
Hi, i wanted to say Thank You!

especially to [OldMerovingian]("http://ubuntu-ky.ubuntuforums.org/member.php?u=925887") !!!

Maybe the solution of _"_[Acidwarlord]("http://ubuntu-ky.ubuntuforums.org/member.php?u=62500")" works as well.

But the "**ppa:k0ekk0ek/ppa" **solved a lot.

I'm using Karmic Koala on my Laptop
"Toshiba Satellite P300D" with "ATI Mobility Radeon HD 3670".
For a long time i had problems with my ATI Driver and Compiz!
I wasted about 10h or more.
Thanks again!
[]("http://ubuntu-ky.ubuntuforums.org/member.php?u=62500")

---

### Post by Rellix999 on 2010-04-09
> **OldMerovingian said:**
> With the upcoming release of 10.04, I am not sure this will remain an issue, but I added the following to my repositories and it stopped ALL lag!  Thanks to all for your help!

[https://launchpad.net/~k0ekk0ek/+archive/ppa](https://launchpad.net/~k0ekk0ek/+archive/ppa)

Thank you so much! You've helped me fix a problem I was trying to fix for days! Really appreciate it.
Info: I'm running an Ati HD5770 using the proprietary driver from the official ati site. Let's just hope they fixed this in 10.04.

I've made a small step-by-step tutorial:
1. System -> Administration -> Software Sources
2. In the tab Other Software add:    ppa:k0ekk0ek/ppa
3. Close this window
4. Terminal: sudo apt-get update
5. Terminal: sudo apt-get upgrade
6. Terminal: sudo /etc/init.d/gdm restart

---

### Post by pazuzuthewise on 2010-05-01
Having a Radeon 3470.
Same problem in Ubuntu Lucid final with fglrx from the Ubuntu repo.
Also, with compiz disabled, the 2D acceleration is horrible. (seems to be deceleration).
Will try the Ati driver.

---

### Post by gianttaco on 2010-05-01
sounds like your computer sucks ***

---

### Post by miguelastico on 2010-05-05
> **Rellix999 said:**
> Let's just hope they fixed this in 10.04.


I would say they didn't...

---

### Post by darkshines87 on 2010-06-19
Bug is solved with the new fglrx driver: [U]10.6

:guitar:
[/U][]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

---

