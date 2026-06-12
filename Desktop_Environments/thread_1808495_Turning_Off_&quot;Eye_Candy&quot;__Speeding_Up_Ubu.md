---
title: "Turning Off &quot;Eye Candy&quot; / Speeding Up Ubuntu"
date: 2011-07-20
forum: Desktop Environments
---

### Post by greenblob on 2011-07-20
I'm running ***ubuntu 11.04*** (natty narwhal) on an ***acer aspire one ZG5*** (a tiny under-powered net book) with ***integrated graphics*** & a ***1.6 GHz Intel atom processor***...

Ubuntu is a HUGE improvement from Windows in terms of speed, but could still do with a bit of a boost...

**[COLOR="Red"]Any ideas on how I can speed up Ubuntu please? [/COLOR]**

Any features (e.g. indexing/graphical effects & animations/other un-needed services) that can be disabled?

Thanks in advance,
Luke

---

### Post by sanderd17 on 2011-07-20
What desktop environment are you using?

If you are using Unity, you can't turn off a lot of effects. But you can install Unity 2D, which has less effects.

If you are using Gnome, at the login screen you can choose for Gnome without effects (the moment where you have to give your password).

If those are still to heavy, you could install LXDE of XFCE. LXDE is the lightest themable desktop environment that I know, and XFCE is a light concurrent of Gnome (almost same functionality, but no effects at all).

I'll list the best known desktop environments from heavy to light (my opinion, not scientific measurements):

Unity
KDE
Unity 2D
Gnome
XFCE
LXDE
openbox, fluxbox ...

---

### Post by Hralgmir on 2011-07-20
There is an interesting post on the forums about altering the /etc/cron.daily/apt file to correct a problem with update-apt-xapian-index which was helpful for me using Ubuntu 10.10, although perhaps at some point this may be incorporated automatically. It could be worth checking though. Also I find disabling the Shockwave Flashplayer plugin which I installed in Firefox can be a performance boost when needed on the internet, and Adblock Plus software can have a similar effect. Neither approach is perfect on all websites though. Using the default desktop background rather than my photograph seems to save a second or so on boot up. Open a terminal and type top to see what is using the processor and RAM when the system is going too slowly, in order to see where the problems are. No doubt there are many more tips out there besides these.

---

### Post by greenblob on 2011-07-20
> **sanderd17 said:**
> What desktop environment are you using?
If you are using Unity, you can't turn off a lot of effects.
Ahh, there's my problem, I'm running Unity... thanks for heads up.

How would I go about installing unity 2d, & how significantly would me speed increase?

I've installed "compiz-config", which has allowed me to turn off animations, but I can't turn any other effects off without half my GUI disappearing... :confused: 

Thanks for the help,
Luke

---

### Post by greenblob on 2011-07-20
> **Hralgmir said:**
>  Open a terminal and type top to see what is using the processor and RAM when the system is going too slowly, in order to see where the problems are.

Excellent Idea, I'll try that now, thanks allot :P

---

### Post by greenblob on 2011-07-20
[CENTER]**[SIZE="3"][COLOR="Red"]BUMP[/COLOR][/SIZE]**[/CENTER]

Any more ideas please?

---

### Post by 2F4U on 2011-07-20
Is Unity set as your desktop environment? If not, I am using Xubuntu (XFCE desktop environment) on an 8 year old ThinkPad X31 with 1.5 GHz Pentium M and 1.5 GB RAM and it runs surprisingly fast, even with desktop effects.

---

### Post by smurphy_it on 2011-07-20
```
Any ideas on how I can speed up Ubuntu please? 
```

Get a real computer to run Ubuntu on ;-)


You could try turning off any services which you don't require.

---

### Post by sanderd17 on 2011-07-20
> **greenblob said:**
> 
How would I go about installing unity 2d, & how significantly would me speed increase?

Just search it in the software center or do
```

sudo apt-get install unity-2d

```

Unity is made for good graphical cards, and if you graphical card isn't so good, than the processor has to take the rendering as his job. A processor isn't made for graphics handling, so that costs a lot of calculating power.

When you use Unity 2D, then the graphics are a lot less heavy, so a light graphical card should be able to manage it without disturbing the processor.

How significant the speed increase would be depends on how good your graphical card is. If you have a good graphical card, than you see no difference between Unity 3D and Unity 2D. Because the processor has nothing to do with it. If you have a light graphical card, than you can see a big difference.

---

### Post by Hralgmir on 2011-07-22
> **smurphy_it said:**
> ```
Any ideas on how I can speed up Ubuntu please? 
```Get a real computer to run Ubuntu on ;-)


You could try turning off any services which you don't require.


While I'm still using 10.10, I'm currently on a Dell CPx H450GT with a 450MHz processor, out of interest. One of the things I have noted is how efficient Ubuntu is in practice, because once the system is booted up, it generally just sit's there in RAM and doesn't use much processor power, except when you do something like open a new window or do something to change what is on screen. Although there are times when the processor is running at full capacity, this only causes limited amounts of delay compared to faster systems. Other constant elements such as download speed or hard drive access speeds (admittedly faster on newer setups, but perhaps not dramatically so without RAID) slow things down and account for a significant proportion of the delay. I was surprised that my setup works as well as it does! Given some hefty calculations, the processor reveals it's limitations, and is not helped much by the 2x AGP graphics. But it's not at all bad, considering all this, so the netbook in question sounds a pretty good machine to me!
Insufficient RAM would be a problem - I have 512MB, which is ample for my needs. Without enough RAM, excess data would be placed on the hard drive slowing things a lot. 
I have not really examined the concept, but I did see a mention somewhere about someone who had a lot of RAM - 4GB - who had added various extra bits of the Linux system into 'the RAM disc' which sounds like it may be possible to place extra items into RAM at startup. I would guess this may slow boot times, but allow commonly used programs to be accessed faster. Conversely, some things like Open Office have a quickstarter option where files can be loaded at startup, ready for use. Disabling this (this was the default setting in my version) will ensure a faster startup to the desktop although enabling it would help OO start faster if it was used frequently. 
( I did see the above quote was made in jest, by the way, but it reminded me of a couple of new points, lest I be accused of misunderstanding the intent!)

---

### Post by smurphy_it on 2011-08-03
yes I was just joking.  Netbooks are generally slow processors, and little RAM.  Turning off services that aren't required can help.  Additionally, as it's an older machine, you can get different distro's which are streamlined for older units (or units that don't have as many resources, like netbooks).

Another thing you could do is use some less resource intensive applications (alternatives for oo for example), and lighter desktop environments (like xfce).

---

### Post by sisyphus1978 on 2011-08-04
I am running 10.04 LTS on the very same netbook and I have just written a phd thesis in LaTex and all my statistics etc in R. This computer is not underpowered in any way. However I am loathed to upgrade to Unity or Gnome 3 (I have tried them out) because 10.04 runs so nicely, and the newer versions just don't.

As for suggestions, maybe install gnome 3 and try fallback mode or try 10.04 (using metacity).

Good luck.

---

### Post by greenblob on 2011-10-21
Thanks all, 
you've been a great help.

I've discovered Ubuntu wasn't taking advantage of my SSD drive, and some other fast components, and also I had no SWAP space, so I fixed these and now it runs birilliantly :p

Once again, thanks very much to all who have posted,
Luke

---

