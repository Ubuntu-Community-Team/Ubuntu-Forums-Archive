---
title: "Is linux really this pokey?!"
date: 2009-06-08
forum: General Help
---

### Post by gribbsy on 2009-06-08
Hello.  I am running a Gateway machine thats about 8 years old.  2 GHz processor, 1.2 GB Ram.  I'm dual-booting with Windows XP and Ubuntu.

This is my first experience with Ubuntu.  I thought that with the lower overhead (no antivirus, no firewall) that the system would be faster overall than it was under windows. This has not been the case.  I takes longer to boot, bring up windows, load video and audio, etc...  Have I overlooked something?  I appreciate that this is a free operating system but am disappointed with how it matches up against Windows XP.

---

### Post by mrtomservo on 2009-06-08
What version of Ubuntu did you install?

---

### Post by philcamlin on 2009-06-08
try kubuntu it seems your hardware isnt the greatest 
kubuntu will rip on your pc because its lighter then ubuntu still with all the apps 

ubuntu is GNOME kubuntu is KDE  kde is a lightweight desktop 

if thats still to slow try xubuntu thats for older pc's thats for people with >128mb ram

---

### Post by paradigm2 on 2009-06-08
> **gribbsy said:**
> Hello.  I am running a Gateway machine thats about 8 years old.  2 GHz processor, 1.2 GB Ram.  I'm dual-booting with Windows XP and Ubuntu.

This is my first experience with Ubuntu.  I thought that with the lower overhead (no antivirus, no firewall) that the system would be faster overall than it was under windows. This has not been the case.  I takes longer to boot, bring up windows, load video and audio, etc...  Have I overlooked something?  I appreciate that this is a free operating system but am disappointed with how it matches up against Windows XP.

One of mine is 1.6 Ghz, ~700 mhz and it is faster than with windows XP.  I would first look at the video card ad the options being used.

Go to a terminal and type

```

lspci

```

This will give us more general details as to your hardware (including video card).

---

### Post by Tynach on 2009-06-08
Not sure what to say. My experience has always been the oposite; Had a box with 128 MB of RAM running Ubuntu, and another with 1.5 GB of RAM running XP, and the Ubuntu box out-performed the XP box.

I would claim a driver issue, but you have not given us your full specs... What type of graphics card, processor (2 Ghz can be good or bad, depending on the actual processor), etc.

---

### Post by Arup on 2009-06-08
Its most likely a driver issue, even though Ubuntu is made for newer PCs with better specs it runs far better on older machines as well than XP or Vista. In your case, please install Xubuntu which is made for older spec PCs and laptops. Kubuntu uses KDE which is even heavier than Gnome in operation.

---

### Post by H2SO_four on 2009-06-08
No, its hokey pokey.  And you turn yourself around.

---

### Post by yoasif on 2009-06-08
> **philcamlin said:**
> try kubuntu it seems your hardware isnt the greatest 
kubuntu will rip on your pc because its lighter then ubuntu still with all the apps 

ubuntu is GNOME kubuntu is KDE  kde is a lightweight desktop you're kidding, right? maybe the login is faster for kde, but GNOME is still lighter weight than both kde3 and kde4, in my experience. 

if you're looking for speed, i would recommend debian with the lxde desktop. 

[http://wiki.lxde.org/en/Debian#Lightweight_systems_CD](http://wiki.lxde.org/en/Debian#Lightweight_systems_CD)

---

### Post by synapsys on 2009-06-08
Did you create a swap partition?

---

### Post by rcayea on 2009-06-08
> **Arup said:**
> Its most likely a driver issue, even though Ubuntu is made for newer PCs with better specs it runs far better on older machines as well than XP or Vista. In your case, please install Xubuntu which is made for older spec PCs and laptops. Kubuntu uses KDE which is even heavier than Gnome in operation.

Question for Arup,

Is there some sort of official or unofficial test I could run to find out how much my ubuntu box kicks my xp box in terms of running faster/lighter?

I am curious if you are going simply on observation. I would really like to post any evidence that my linux pc is better than my xp one. 

Thanks,
Randy

---

### Post by Tynach on 2009-06-09
Well, to start with, for a fair comparison, the test must be run on IDENTICAL hardware, in an IDENTICAL fasion (same type of hard drive, so no IDE drive vs. SATA drive on the same PC either).

Next, find a heavy program that runs NATIVELY on both (NO WINE). I personally use Blender.

In your program, run something processor intensive. In Blender, I render a scene. Blender tells me how much time it takes to render, and I compare the render time on both XP and on Linux.

Linux beats the crap out of XP every time for me.

Edit: Also, render the same scene, from an identical source... For example, I load a .blend file from my thumb-drive, thus comparing thumb-drive speed as well. It makes it VERY fair, and rather revealing.

On my laptop, I run Vista and Ubuntu. Vista's speed results really aren't even worth talking about, though. We all know it's slow.

Also, WHO IN THEIR RIGHT MIND THINKS THAT KDE IS LIGHT???!!! KDE is nice, and I use it a lot, but it is NOT light. XFCE is light, and Xubuntu is rather good... Though a bit odd. No rectangular selection on the desktop. I think I have obsessive compulsive disorder or something... I always have to make 3 rectangles on my desktop every time I close out of a program, as large as I can. Otherwise, I feel weird.

Anyway... I don't use XFCE, but it's nice. My not using it has nothing to do with if it is good or bad.

---

### Post by dmizer on 2009-06-09
> **gribbsy said:**
> Hello.  I am running a Gateway machine thats about 8 years old.  2 GHz processor, 1.2 GB Ram.  I'm dual-booting with Windows XP and Ubuntu.

This is my first experience with Ubuntu.  I thought that with the lower overhead (no antivirus, no firewall) that the system would be faster overall than it was under windows. This has not been the case.  I takes longer to boot, bring up windows, load video and audio, etc...  Have I overlooked something?  I appreciate that this is a free operating system but am disappointed with how it matches up against Windows XP.

No, Ubuntu should run fine on your system, and should run faster than XP. You probably have a video card driver problem. Please open a terminal and run this command:
```
lspci
```
And post the results here.

---

### Post by Tipped OuT on 2009-06-10
> **philcamlin said:**
> [B]try kubuntu it seems your hardware isnt the greatest 
kubuntu will rip on your pc because its lighter then ubuntu[/B] still with all the apps 

ubuntu is GNOME kubuntu is KDE  kde is a lightweight desktop 

if thats still to slow try xubuntu thats for older pc's thats for people with >128mb ram


Try Kubuntu!? That's even worse! KDE is high on resources! Are you nuts!!??
*back to sanity* Try **Xubuntu**, not Kubuntu.

---

### Post by Arup on 2009-06-10
> **rcayea said:**
> Question for Arup,

Is there some sort of official or unofficial test I could run to find out how much my ubuntu box kicks my xp box in terms of running faster/lighter?

I am curious if you are going simply on observation. I would really like to post any evidence that my linux pc is better than my xp one. 

Thanks,
Randy

If you have a x64 system, just do some basic encoding, you will see your XP machine blown to bits, on my 8 core PC, encoding audio and video is around 40-60% faster on average than Win. XPx64 is the fastest Win OS, Vista is a joke.

---

### Post by jocko on 2009-06-10
> **Tipped OuT said:**
> Try Kubuntu!? That's even worse! KDE is high on resources! Are you nuts!!??
*back to sanity* Try **Xubuntu**, not Kubuntu.
With 2GHz cpu and 1.2 Gb ram Ubuntu (gnome) should run very well, at least it does on my 1.86Ghz cpu and 1.5Gb ram.
The only thing that makes my computer feel a *little* bit sluggish with jaunty is the video driver (open source radeon driver, as my radeon 9600 is no longer supported by ATI's proprietary driver).
In my experience a freshly installed windows xp feels about as responsive as ubuntu, but after installing antivirus on xp performance degrades pretty much as every file is scanned before it's loaded.
With those specs there is probably no huge performance difference between gnome and xfce, except a sligthly faster load time for xfce as less data needs to be read from the disk when the desktop environment loads (the hard drives are the slowest components on any computer, so this is true even with a 4*3Ghz quad core cpu and 16 Gb of ram).
xfce's advantage over gnome should only be really obvious if the amount of ram is limiting for normal use, which it isn't with 1.2Gb

---

### Post by ryanhaigh on 2009-06-10
ARGHHH STOP THE MADNESS! 

A PC with those specs should run any version of X/K/Ubuntu perfectly well so can we stop recommend people download another 700mb just to try a different desktop environment.

As well as providing the output of the command lspci you might also want to look at the system monitor (System>Admin>System Monitor) and see what CPU and memory usage are.

As an alternative to lscpi you could use the following which I believe provides more information and is easier to read. 
```
sudo lshw -html > ~/system.html
```
You can then attach that file (/home/username/system.html) here so that the helpful forum can look at exactly what hardware you have and maybe provide some insight into the cause of your problems.

---

