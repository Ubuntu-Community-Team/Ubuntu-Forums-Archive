---
title: "Netbook Remix No panels and icons"
date: 2010-10-15
forum: Desktop Environments
---

### Post by theautates on 2010-10-15
Hello im having some problems with my netbook edition.

I did a plain install of Ubuntu 10.10 Netbook Remix to my toshiba laptop m645 and all was fine until i have install the nVidia driver. The driver didn't work and only allowed me to use the no gui login. It seems that its having errors with starting the x server. The details are in here >>> [click]("http://ubuntuforums.org/showthread.php?t=1590243&page=3") 

So basically what i did to be able to login with gui was to delete the current xorg.conf file using "sudo rm /etc/X11/xorg.conf" and then typed "sudo dpkg-reconfigure xorg". I rebooted and I can now login with gui BUT the main problem is when i login to Netbook Edition, there are no panels nor icons! It just displays my wallpaper and it doesn't let me do anything except ctrl+alt+F1 and similar shortcuts.

There is no problem logging in to desktop edition all my icons are there and panels. 

Any one has an idea?

---

### Post by franik4ever on 2010-10-18
I have the same problem on my Acer A6R... There are no panels and no icons...
PS Some times Ubuntu really sucks... I'm thinking about going back to Debian...

---

### Post by ankspo71 on 2010-10-18
Hi,
Unfortunately, the Unity desktop on the 10.10 netbook edition requires working 3D capable drivers that are in use, or else there is a chance that it might not work at all (my personal experience). 

For those who have a non-working netbook desktop, can you check to see if you can log out, then click on your username, then see if there is a "Gnome" or "Ubuntu Desktop" session that you can choose log into, so you can check online for drivers and install them, or fix their configuration?

For me to have a working Ubuntu Netbook desktop (without much hassle), I opted to download the Desktop Edition of Ubuntu and installed it, then I installed and activated my Nvidia drivers, and then I installed "ubuntu-netbook" through the package manager. It worked well for me this way, but this is also why I can't give any definitive advice about the netbook's available sessions.

During the RC testing phase for Ubuntu 10.10, I tried downloading and installing the Ubuntu netbook edition ISO, but it gave me trouble getting to a working gnome desktop when I didn't have any 3D capable drivers installed.

Hope this helps.

Edited: 
Adding hardware requirements for the Unity desktop (the netbook desktop):
[https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements](https://wiki.ubuntu.com/DesktopExperienceTeam/UnityHardwareRequirements)
and Ubuntu 10.10 release notes:
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

---

### Post by franik4ever on 2010-10-18
ankspo71, thx for advice

---

### Post by theautates on 2010-10-21
ok ill make sure to follow what you have written there. thanks!

---

### Post by unustamisex on 2011-03-15
re ankspo71:

Hi,
Can you give me direct instructions how to do what you said.
Which Nvidia driver, how to activate and restart etc?

Thanks.

---

### Post by ankspo71 on 2011-03-15
> **unustamisex said:**
> re ankspo71:

Hi,
Can you give me direct instructions how to do what you said.
Which Nvidia driver, how to activate and restart etc?

Thanks.

Hi,
I don't know if half of what I said would still be helpful or not (because I was using a test release of Ubuntu at the time), but I'll explain what I did.

When I tried installing Ubuntu Netbook Edition 10.10 (at that time) it wouldn't give me a working desktop - neither a netbook desktop or a traditional gnome desktop. It was pretty much stuck. I think I remember the system not responding to my keyboard too, so I didn't have a way to access a console either. At the time Ubuntu was still in its testing stages so things like this were expected.

I was supposed to be offered a fallback option as a way to start the traditional Gnome desktop as a result of not having 3D capable drivers installed (which the Netbook Edition required). If it would have worked properly at the time, it would have started the traditional Gnome desktop for me, and I would have been able to install the Nvidia drivers in the "additional drivers" utility in the system menu, then log out and choose the Ubuntu Netbook option from the session menu at the bottom of the login screen, then I could log back into Ubuntu Netbook. I never got as far as getting past that fallback option. I suspected that the fallback option has crashed and was hanging up my system somehow. This is what my second part of advice earlier was supposed to help avoid (since Ubuntu Desktop 10.10 doesn't have this fallback option).

So later I used my Ubuntu Desktop Edition 10.10 live cd and installed Ubuntu as usual. Getting it installed was not a problem, and it booted right into the traditional Gnome desktop. The next thing I did was installed the Nvidia drivers offered in the "Additional Drivers" utility found in the system menu. I have an Nvidia 8400 GS card, and Nvidia "Current" (it's version 260 driver) is the version I always select. Then I rebooted and saw that my graphics drivers were working. Next I went into Synaptic Package Manager and installed the package called 'ubuntu-netbook' so I can turn my Ubuntu Desktop Edition into a Ubuntu Nebook Edition. The installation went well. After installing the ubuntu-netbook package, I was then able to log out, then click on my name in the login window, then choose "ubuntu netbook" from the session menu located at the bottom of the login screen, then entered my password to login to the new netbook desktop. 

Hope this helps.

---

### Post by unustamisex on 2011-03-29
Thank you!
You're very helpful.
Thanks.

---

