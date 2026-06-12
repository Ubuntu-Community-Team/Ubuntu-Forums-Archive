---
title: "Any way to get Xbox 360 Controller to work?"
date: 2015-08-17
forum: Gaming &amp; Leisure
---

### Post by The Bright Side on 2015-08-17
Hey guys!

I've recently bought an Xbox 360 controller and it works perfectly in Windows. Under Ubuntu, though, games simply act as if it doesn't exist. I tried Outlast, Amnesia and Spec Ops: The Line, though I'm not sure the latter two support controllers to begin with. Outlast definitely does, but as I said, it acts as if the controller wasn't there.

jstest-gtk shows that the driver-wise, the controller is installed: it shows up, and when I check the properties, I can see that it works properly. Every button press is recognized. Looking around the Internet, it seems like other people have no problems at all using Xbox 360 controllers in Ubuntu - it seems to be plug-and-play.

Am I missing something?

Running Ubuntu GNOME 15.04, 64-bit, latest version of Steam. Let me know if you need any other particular system specs.

---

### Post by ODTech on 2015-08-17
I was also struggling earlier today. I got mine working but the binding were all messed up. Then i stumbled on the steamos driver and reverted everything else back to default and installed it. Worked 100% after first reboot.

[https://launchpad.net/~mdeslaur/+archive/ubuntu/steamos](https://launchpad.net/~mdeslaur/+archive/ubuntu/steamos)

> sudo add-apt-repository ppa:mdeslaur/steamos

Not sure if all the packages are necessary but i installed them all anyway.

> sudo apt-get install steamos-compositor steamos-modeswitch-inhibitor steamos-xpad-dkms 

---

### Post by The Bright Side on 2015-08-17
Nice, thanks ODTech! Before installing the steamos packages, which things did you try and then revert?

---

### Post by ODTech on 2015-08-17
> **The Bright Side said:**
> Nice, thanks ODTech! Before installing the steamos packages, which things did you try and then revert?

1. I tried with xpad only that comes with vanilla ubuntu 14.04. The driver didn't even load. Blacklisted xpad
2. Installed xboxdrv and jstest-gtk. It didn't work, out of the box. I did not try to rebind the controller manually. 
3. Removed xboxdrv and installed ubuntu-xboxdrv (a branch of the original xboxdrv and supposed to work better). Same result as the vanilla xboxdrv.
4. Uninstalled ubuntu-xboxdrv and jstest.gtk and removed the xpad blacklist.
5. Added the ppa from my previous post and installed the packages from it. Rebooted my computer.

After the reboot the pad started working 100% for any game i tested, amongst other Bioshock Infinite, Borderlands2 and Teleglitch DME.

Edit: By "didn't work out of the box" i mean the buttons and axis binding was a mess

---

### Post by The Bright Side on 2015-08-17
Thanks man! I will try that as soon as I get a chance!

---

### Post by The Bright Side on 2015-08-17
Dammit. The packages in the repo are too old for 15.04. Thanks for the suggestion nonetheless!

---

### Post by ODTech on 2015-08-18
> **The Bright Side said:**
> Dammit. The packages in the repo are too old for 15.04. Thanks for the suggestion nonetheless!

Too bad. 

I recently returned to ubuntu 14.04 after a gaming phase on windows and i always use LTS versions since i like things stable and supported.

I suspect i won't be going back to windows any time soon thanks to the efforts of Valve.
My steambox in the making will be windows based to start with, until i've caught up the backlog of games i have on steam then i'm converting it to steamos.

---

### Post by Kpenguin on 2015-08-19
Have you tried the xbox driver package (ubuntu-xboxdrv)?
See here: [URL="http://www.omgubuntu.co.uk/2014/06/ubuntu-xbox-controller-support-xboxdrv-driver"]http://www.omgubuntu.co.uk/2014/06/ubuntu-xbox-controller-support-xboxdrv-driver
[/URL]

---

