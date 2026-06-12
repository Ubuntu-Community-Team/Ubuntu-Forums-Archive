---
title: "Ubuntu virgin needs help, no sound, resolution to small"
date: 2009-03-23
forum: General Help
---

### Post by abefroman999 on 2009-03-23
Ubuntu virgin needs help, I installed Ubuntu for the first time but I don't have any sound, like when I try to play a video on youtube.

Also, my screen resolution won't go above 800x600.

I am assuming the right drivers are not installed, how can I get/install those?

TIA!

---

### Post by Therion on 2009-03-23
First thing to do... Go to Applications/Accessories and click on Terminal.

Copy and Paste the following into it:```
sudo apt-get install ubuntu-restricted-extras
```
Enter your user password when prompted, answer yes to the prompts, agree to the licensing etc.


RE: Screen Resolution...

First, go to the System menu, Administration, Hardware drivers.  
See if there is a Restricted Driver listed for your video card.  
If there is, click on one to enable it.

If there is NOT, open a Terminal like you did before and Cut and Paste the following command into it:```
 lspci | grep VGA
```
You will get a line of output from the Terminal telling you what graphics card or chipset you have.  
Copy and Paste that line of output into a new post here, please.

---

### Post by abefroman999 on 2009-03-23
Thanks!  That fixed the resolution, but the sound won't work still:
root@abefroman-desktop:/home/abefroman#  lspci | grep -i audio
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
root@abefroman-desktop:/home/abefroman# 

root@abefroman-desktop:/home/abefroman# apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@abefroman-desktop:/home/abefroman# 

Any ideas?

---

### Post by S.A.A on 2009-03-23
Had you try System -> Preferences -> Sound. from there set everything to autodetect.

---

### Post by abefroman999 on 2009-03-23
> **S.A.A said:**
> Had you try System -> Preferences -> Sound. from there set everything to autodetect.

Yep, it had all that checked by default.

:popcorn:

---

### Post by BrandonHollis on 2009-03-23
Trident Microsystems CyberBlade/XP (rev 63)

---

### Post by Nikolopulus on 2009-03-25
I have the same resolution problem, this is what I get from lspci | grep VGA:
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 2100
I enabled the restricted driver in the sistem > administration > hardware and it still won't do, I can't either enable the visual efects.
Thanks for all the help

---

