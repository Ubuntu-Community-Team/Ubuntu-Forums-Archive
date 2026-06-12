---
title: "Could not apply stored configuration for monitors"
date: 2010-08-29
forum: Desktop Environments
---

### Post by GoldStar on 2010-08-29
Total newbie to Linux world.

Just installed Ubuntu 10.04 LTS on Microsoft Virtual PC 2007. Installation went OK.

When it starts I see the following message;

"Could not apply stored configuration to monitors. Error on line 1 Char 1. Document was empty or contained white space"

Maximum monitor resolution is 800x600 although my monitors is capable to 1280x1024 and Refresh Rate is 56 or 60. I should be able to choose 72Hz and over.

Thanks in advance

---

### Post by MrKitty on 2010-08-29
I have a similar issue. After an update my "Nvidia Xserver" does not recognize my monitor all of a sudden displaying "unknown" instead of the monitor name and giving me 1024 x 768 resolution instead of the 1600x1200 that it used to -- This is on my user account -- Furthermore, if I switch to the "guest" user, the Nvidia Xserver recognizes the monitor like it used to and displays the proper resolution. What is going on?

---

### Post by gordintoronto on 2010-08-29
GoldStar, I think you need to do more configuration in Microsoft Virtual PC 2007. I'm not sure, because I use VirtualBox, which is free.

MrKitty, your problem is only similar if you are running in a virtual machine. Otherwise, please use Google to find the solution to your problem.

---

### Post by wojox on 2010-08-29
> **MrKitty said:**
> I have a similar issue. After an update my "Nvidia Xserver" does not recognize my monitor all of a sudden displaying "unknown" instead of the monitor name and giving me 1024 x 768 resolution instead of the 1600x1200 that it used to -- This is on my user account -- Furthermore, if I switch to the "guest" user, the Nvidia Xserver recognizes the monitor like it used to and displays the proper resolution. What is going on?

Open a terminal and run

```
sudo nvidia-xconfig
```

```
gksudo nvidia-settings
```

---

### Post by MrKitty on 2010-08-30
That's the fix! Did it! The backup file was correct (It took a restart to take effect). I thought of an opposite solution maybe:

Since the guest account was working properly, could it have worked to copy the xorg.conf file from there if the backup that was on my system was not working?

Edited for... Correctness.

---

### Post by GoldStar on 2010-09-06
I ma now running Ubuntu on Virtualbox (much better than MS's Virtual PC) but still the max resolution is 800x600.

Where do I go next.

---

### Post by pyperdown on 2011-02-20
> **GoldStar said:**
> I ma now running Ubuntu on Virtualbox (much better than MS's Virtual PC) but still the max resolution is 800x600.

Where do I go next.

Discovered this - in your homedir look for the .config dir.

rename the file called monitors.xml.  Logout, login.

---

### Post by 5tj on 2011-05-20
To the VirtualBox Question: Install the guest additions. There is a menu item for doing so.

---

### Post by dwaindibbley65 on 2011-12-03
> **pyperdown said:**
> Discovered this - in your homedir look for the .config dir.

rename the file called monitors.xml.  Logout, login.

Worked for me on Ubuntu 11.10, thanks pyperdown!

---

### Post by Linker101 on 2011-12-14
> **pyperdown said:**
> Discovered this - in your homedir look for the .config dir.

rename the file called monitors.xml.  Logout, login.


This also worked for me on 11.10. I've been struggling with this for days. I now have dual monitors working.

---

### Post by ibod on 2012-01-22
> **pyperdown said:**
> Discovered this - in your homedir look for the .config dir.

rename the file called monitors.xml.  Logout, login.

I just installed 11.10 (not in a virtual PC)
After some setup in 'Nvidia X server settings' to enable the missing second screen.
I have the same message

"Could not apply stored configuration to monitors"

Remember to select 'VIEW show hidden files' to see the .config dir in your home dir
Renaming monitors.xml to old monitors.xml also worked for me. 

No new monitors.xml file is created. 

This configuration problem seems to be happening to several people, and to have been around since at least 10.04

Is this a bug ?

Could anyone explain what is happening to cause this ?

---

### Post by Robynsveil on 2012-02-23
> **pyperdown said:**
> Discovered this - in your homedir look for the .config dir.

rename the file called monitors.xml.  Logout, login.

Thanks, PyperDown - worked a treat!! :KS

---

### Post by kboutelle on 2012-02-28
> **pyperdown said:**
> Discovered this - in your homedir look for the .config dir.

rename the file called monitors.xml.  Logout, login.

I have Ubuntu 11.10 on a Dell Latitude E6400. It has an Nvidia Quadro NVS 160M video card and I'm using a dual monitor setup. I'm using the laptop display and a Dock-DVI connected HP L2045w LCD 20". Everything was fine until one morning that I received the same error mentioned in the first post. 

pyperdown's post is what I needed to fix my system. Thanks!

---

