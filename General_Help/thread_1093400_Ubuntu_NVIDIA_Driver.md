---
title: "Ubuntu NVIDIA Driver"
date: 2009-03-11
forum: General Help
---

### Post by Maxx730 on 2009-03-11
Is the driver that ubuntu comes with to run nvidia cards the same one that you would download from the web?

---

### Post by chriskin on 2009-03-11
the one that comes in the hardware drivers menu seems to be an optimized version of the official drivers

---

### Post by Maxx730 on 2009-03-11
Damn, I thought maybe they would be better because compiz is crashing when I use it

---

### Post by chriskin on 2009-03-11
this is what is written in the synaptic at least, i don't know for sure
it might be better to try those at the site as well - if it is not better you can always install the other ones again

---

### Post by chriskin on 2009-03-11
i checked the site, those there are later than those given by ubuntu. there might be a bug fix for you on the latest ones.

---

### Post by philinux on 2009-03-11
There is indeed lots of bug fixes. I'm testing jaunty and I use to get scrambled graphics opening say firefox. This is gone now and compiz is much smoother.

If you got space on your drive you could try jaunty dual boot. It's due out next month too.

---

### Post by Maxx730 on 2009-03-11
Well, I bought a 512mb nVidia card because I wanted compiz (even thought I didnt need that much more...) and now when I start compiz and firefox at the same time, compiz goes nuts and the whole computer freezes up. I dont know if that is a driver issue or not though

---

### Post by Therion on 2009-03-11
The hardware manager will install the nVidia 177 series restricted driver.  

You can get the nVidia 180 series driver, if you want, by downloading the required file from the nVidia website and installing it manually.

---

### Post by chriskin on 2009-03-11
which card? i have an 8600M 512mb and compiz works perfectly

---

### Post by Maxx730 on 2009-03-11
NVIDIA Geforce 8400 GS

---

### Post by chriskin on 2009-03-11
it is supposed to be supported by the default drivers

can't say i'm an expert, but i suggest you try those at the site and tell us what happened

---

### Post by Maxx730 on 2009-03-11
Well, I am going to I just need a question answered, when I run the .run file, it says that I have X Server open and I cant install the drivers until it is closed. How do I close it?

---

### Post by aktiwers on 2009-03-11
Here is a quick guide to install the Nvidia .run file:

First make sure its located in your home folder.
Then make sure everything you need to have saved (open apps etc..) are closed and get ready for "fullscreen terminal"

Then hit CTRL+ALT+F1 and login at the prompt.

Type:
```
sudo /etc/intit.d/gdm stop
```
To kill gdm.

Then make your .run file executable:
```
sudo chmod +x YOURNVIDIAFILE.run
```
And then run it:
```
sudo ./YOURNVIDIAFILE.run
```

When done, you need to reboot.
```
sudo reboot
```

And the new driver should be installed.

Cheers

---

### Post by Maxx730 on 2009-03-11
thanks, also, can compiz run on a 32mb graphics card? because Ive seen people say that they have it running decently on a 32mb card and I couldnt on this comp

---

### Post by chriskin on 2009-03-11
by decently they mean that compiz is just running, no cube or atlantis or something that needs a good card

---

### Post by Maxx730 on 2009-03-11
i went to install and it went through the motions and failed because of previous drivers installed. Im guessing those are the drivers that come with linux?

---

### Post by chriskin on 2009-03-11
probably yes, if you have not installed anything else

just uninstall them and install the other ones

---

### Post by cybergalvez on 2009-03-11
the 180 drivers are already in the repositories, so no real reason to build from source is there?

---

### Post by chriskin on 2009-03-11
the 180 are in the repositories?

might you be using jaunty ?

---

### Post by Maxx730 on 2009-03-11
no im using 8.04

---

### Post by chriskin on 2009-03-11
> **Maxx730 said:**
> no im using 8.04

not you, the one who said that 180 are already in the repos


by the way, if your problem is just that another is installed, why don't you uninstall it and install the new ones? you seemed to have solved the other issue, or so i understood

---

### Post by Maxx730 on 2009-03-11
o yeah and i have found out that compiz only seems to crash when im using firefox

---

### Post by aktiwers on 2009-03-11
I can build the drivers even though others are installed.. just answer "YES" to everything the installer asks for.

---

### Post by Therion on 2009-03-11
> **chriskin said:**
> not you, the one who said that 180 are already in the repos
The 180.xx driver is in the Jaunty repo, yes.  

A sneaky user could, I suppose, add that repo to their sources.list just long enough to snag the driver, install it and then disable the repo in question.  

Not that I've done that mind you...

---

### Post by cybergalvez on 2009-03-15
> **chriskin said:**
> the 180 are in the repositories?

might you be using jaunty ?

I'm using 8.10

---

### Post by jocheem67 on 2009-03-15
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

Here's the main thread that discusses the nvidia beta drivers.

Imho you can achieve a lot of improvements by using the 180.** series of drivers.

Installing them however is not exactly newbie-stuff...

There is a 180.** in the repo's though, but you have to look at your sources first.

I'm updating all the time.;)

Got noticable improvements in 2d.

---

