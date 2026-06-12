---
title: "KDE won't start on 3.13.0-44"
date: 2015-01-16
forum: Desktop Environments
---

### Post by marcovo on 2015-01-16
Hi,

A few days ago my Kubuntu installation updated to linux version 3.13.0-44 . However, after that KDE refuses to start, the only thing that's showing after booting is a commandline-login. I tried to use 'sudo apt-get update' and 'sudo apt-get dist-upgrade' there, but that didn't solve the problem. When I boot from 'Advanced options for Ubuntu' and select 3.13.0-43 it all does work, so KDE does work then.
What is the problem here? Why is KDE not working under 3.13.0-44, opposed to 3.13.0-43 where everything's fine?

---

### Post by PaulW2U on 2015-01-16
> **marcovo said:**
> Hi,

A few days ago my Kubuntu installation updated to linux version 3.13.0-44 . However, after that KDE refuses to start, the only thing that's showing after booting is a commandline-login. I tried to use 'sudo apt-get update' and 'sudo apt-get dist-upgrade' there, but that didn't solve the problem. When I boot from 'Advanced options for Ubuntu' and select 3.13.0-43 it all does work, so KDE does work then.
What is the problem here? Why is KDE not working under 3.13.0-44, opposed to 3.13.0-43 where everything's fine?

I can't solve your problem but you might want to give us a description of your hardware and/or details of any proprietary drivers that you have installed.

I have two Samsung laptops that I successfully updated to 3.13.0-44, i.e. Kubuntu 14.04 LTS. Both are running fine here.

---

### Post by marcovo on 2015-01-16
Hi,

Thanks for you reply. I'm running Kubuntu 14.04.1, I once installed Nvidia drivers but I don't know whether they're active or not. I'm not sure how to tell...
I have a Q8200 processor and a nvidia GeForce 9800 GT video card. I first had 12.04 and then updated to 14.04, so this is not a 'clean' installation of 14.04.
Is there any more info I could provide?

---

### Post by PaulW2U on 2015-01-17
> **marcovo said:**
> I once installed Nvidia drivers but I don't know whether they're active or not. I'm not sure how to tell...

Sorry for the delay in replying, I've been busy trying to get something working on a cheap laptop. :(

To see if you have any Nvidia drivers installed go to System Settings | Driver Manager and allow the search to complete. If they are installed I would then remove them, see if the PC will boot with the newest kernel and if it does re-install the drivers if you really need them.

Have you tried starting lightdm with either of the following commands? 

**sudo service lightdm start** or **sudo service lightdm restart**

---

### Post by marcovo on 2015-01-19
I did try **sudo service lightdm start**, it didn't really do anything. Would it be helpful to try the **restart** option?

I have 5 nvidia drivers listed in driver management, and 1 X.Org server. By 'remove them', do you mean I should really remove them, or is selecting X.Org server also OK?

BTW; this is the list:
Using NVIDIA legacy binary driver - version 304.125 from nvidia-304
Using NVIDIA legacy binary driver - version 304.125 from nvidia-304-updates
Using NVIDIA binary driver - version 331.113 from nvidia-331 (<-- This one is selected right now)
Using NVIDIA binary driver - version 331.113 from nvidia-331-updates
Using NVIDIA binary driver - version 340.65 from nvidia-340 (Recommended Driver)
Using X.Org X server -- Nouveau display driver from xserver-xorg-video-nouveau

I wonder if it's a good idea to activate the recommended driver here? I don't know why it's not selected; maybe it gave problems in the past or sth like that..

---

### Post by vinnywright on 2015-01-19
after you get the nividia driver removed and reinstalled (if you chose to reinstall it) check to make sure that you have the "dkms" package installed ,,,,, the "dkms" package will rebuild the nvidia driver when you get a new kernel for that kernel .

this is prob. what happened to you , you had a working driver , got a new kernel , the driver did not get rebuild for the new kernel , no working video driver for the new kernel .

VINNY

---

### Post by marcovo on 2015-02-10
It's been a while... and I updated to 3.13.0-45 (I guess?) now, and now everything works fine again... The dkms package was installed already, should I need to run 'dkms' in the console or sth like that (if anything like this happens again)?
Regarding my previous post, would it be wise to upgrade to nvidia 340.65 ?

Thanks for the tips!

---

