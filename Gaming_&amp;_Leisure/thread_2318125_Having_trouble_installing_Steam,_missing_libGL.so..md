---
title: "Having trouble installing Steam, missing libGL.so.1"
date: 2016-03-23
forum: Gaming &amp; Leisure
---

### Post by carlo19 on 2016-03-23
Yesterday, I jumped ship from W10 to Ubuntu 14.04.04. I wanted to install Steam, so I downloaded the .deb file from the website and ran it. I ran the steam-launcher after the install's finished. This is where I think something's wrong.

Steam wants (needs?) to install these packages: **libgl1-mesa-dri:i386**, **libgl1-mesa-glx:i386**, and **libc6:i386**. After I gave my password, a popup shows up, telling me I am missing the 32-bit libGL.so.1, then a "*Fatal error: Failed to load steamui.so*"

Now, I am currently stuck reading threads having the same dilemma. I tried doing what they generally advised: install libraries (like this: [http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005)), uninstall and reinstall Steam, etc. to no avail. Then I thought I shouldn't proceed anymore, as I don't even know what these commands [might] do (I'm scared I might harm my computer :<).

I know there are a lot of people asking the same thing on the internet, but somehow it doesn't work for my case. I would appreciate it if you guys could suggest something I could do, or direct me to some websites I may have skipped. Thanks !!:)

---

### Post by MikeCyber on 2016-03-23
There are two steam packages. One from synaptic and the other download  from steam. I would remove all, including in your home the hidden steam  folder. 
cd ~
rm -rf .steam
Than try the other one.

---

### Post by carlo19 on 2016-03-25
@Mike: Could you tell me if I got it right? Basically, if one didn't work, delete everything and do it the other way? Here's what happened, assuming my interpretation's correct

I tried installing through Synaptic, it said that I have broken packages? 
Then I tried installing Steam through the steam package again, and a popup appeared again that says I am still missing a different library: a certain **libc.so.6**. I tried installing by using

*sudo apt-get install '^libc6.*' *(based here: [http://ubuntuforums.org/showthread.php?t=2242632](http://ubuntuforums.org/showthread.php?t=2242632))

and it said that it's unable to fetch some archives.

---

### Post by MikeCyber on 2016-03-25
As I've said remove all including the hidden directory .steam in your home directory. Also never use root unless you have to. You can click in synaptic "fix broken packages"

---

