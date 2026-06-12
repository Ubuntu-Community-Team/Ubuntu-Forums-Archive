---
title: "After installing kubuntu-desktop Ubuntu won't boot"
date: 2009-12-08
forum: Desktop Environments
---

### Post by kiruri on 2009-12-08
Hi there, I googled the subject but found nothing.

I have installed Ubuntu 9.10 on my Lenovo IdeaPad s12 (VIA Nano) and it worked ok, except suspending.
I've found somewhere on the forums that resume from suspend could be the Gnome problem, so I decided to try KDE.
Installed from Synaptic kubuntu-desktop and others, rebooted - and got to KDE login screen. Tried to log in, but there was blank screen and computer freezed. 
Rebooted - there was no login screen even.
Rebooted in recovery mode - same thing.
Booted from USB starup disk, choosed 'repair broken system' - got to blank screen.
I can not even get to command line (ctrl alt f1).

Any chances to repair my Ubuntu, or should I reinstall it?

---

### Post by C. Bogart on 2009-12-21
Hello, I had the same problem on ubuntu 9.10 after installing kubuntu-desktop from synaptic, I could only see the kubuntu logo splash at boot and then nothing. What I did was to run memtest86+ in grub menu for about an hour, and then I was able to boot with both gnome and kde.
I continued experiencing some boot issues once in a while and went worse with the kernel upgrade, so if you experience the initial issue my advice is to entirely remove kubuntu-desktop as soon as you can log in. After I did everything went as usual.
Here's how you can entirely remove kubuntu-desktop:
[http://www.psychocats.net/ubuntu/puregnome]("http://www.psychocats.net/ubuntu/puregnome")

Regards

---

