---
title: "Dell Inspiron 1501/Broadcom Trouble"
date: 2010-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Thoric on 2010-08-29
I'm unable to use my Broadcom 4311 wireless device under a vanilla install of Ubuntu 10.04. I've pulled my hair out sifting through the Internet attempting to solve this issue. Everything I have found has failed one way or another.

I've tried using NDISWrappers as well as all Broadcom drivers from Synaptic Package Manager. The closest to success I've had was with b43-fwcutter. However it's minimal at best. By completely removing b43-fwcutter, rebooting & reinstalling. I am  able to get wireless to work for a short time. It will connect & all  connections seem alright & with average connection speed/strength. But this only works if connection is kept constantly active. Restarting also causes fault.

If anyone has any advice I would greatly appreciate it. If this computer had a PCMCIA slot I'd just use my old wireless card. 

Thanks in advance;
                       Thoric

---

### Post by JBAlaska on 2010-08-29
First, make sure you removed all traces of Ndiswrapper.

To get the internal Broadcom wireless working:
Put the Ubuntu LiveCD in your drive and go to: **System, Administration, Software sources** and check the box below "Installable from CDROM". Then open a terminal and do:
```
sudo apt-get update
```

Then:
```
sudo apt-get install bcmwl-kernel-source

```

Now reboot and select the Broadcom STA driver in **System, Administration, Hardware Drivers**

You may need to reboot again to enable the driver.

---

### Post by Thoric on 2010-08-29
Thanks for the help. Unfortunately I have already tried doing this. I thought I might add that I have tried the Broadcom STA drivers & they all have failed with 0% success rate. Yes I was sure to use update cmd prior to doing so. Would I be better off if I were to acquire an older build of Ubuntu? The computer is intended for my mother. She has a bad habit of installing Wild Tangent and other such games. Regardless of my warnings. Which is why I switched her over to Ubuntu. Fairly easy to use for basics, email, chat, browsing the internet and/or silly little games. Only trouble is the wireless works all sketchy, if at all.

---

### Post by JBAlaska on 2010-08-29
What is the error(s) when using the Broadcom STA driver? That is the correct driver for your Laptop, and usually works well.

---

### Post by Thoric on 2010-08-29
That's the bizzar thing about all this. There are no errors. Just using the drivers it won't let me enable wireless it's just greyed out. Also can't seem to use "Function key + F2" which is what they use in place of a physical switch. 

Talking about the function key got me thinking. So apparently the issue was with the function control drivers. After reinstalling them all I had to do was enable wireless using "Fn + F2". Broadcom STA driver still doesn't work though. b43-fwcutter is functioning quite well as the wireless driver however. So Problem is solved.

Sorry for making a new post for something I should have thought of in the first place.

---

### Post by gibbylinks on 2010-08-31
I have this laptop and it works fine. 

You need to connect using ethernet and a cable into your router,  then click "hardware drivers" under preferences or admin (sorry I use control centre and can't remember where it is) and download install "Broadcom STA proprietry driver.

My laptop prompted me to install this when I was connect to the net.

Hope that helps you. :D

Ooops....numpty mode. Just noticed you'd got it sorted

---

### Post by Thoric on 2010-08-31
No problem, I was unaware as to how you mark a thread solved until now. All the little problems that keep stacking up are getting to be discouraging. Bad as it ever gets though, I'll never return to the cold heartless clench of Microshaft.

---

### Post by Miljet on 2010-09-01
> So apparently the issue was with the function control drivers. After reinstalling them all I had to do was enable wireless using "Fn + F2"
I would appreciate a little explanation about exactly what you reinstalled and how you did it.

---

### Post by Thoric on 2010-09-08
> **Miljet said:**
> I would appreciate a little explanation about exactly what you reinstalled and how you did it.

Sorry for the delay in response I've been rather busy lately. Apparently I'm tech support for the neighborhood. 

Okay first off I'm going to reiterate that this was for a **Dell Inspiron 1501** containing the **Broadcom 4311 **wireless chip.
 
So In the beginning, using the **Synaptic Package Manager**, I separately tried the following drivers:
**bcmwl-kernel-source**
[B]bcmwl5700-source
bcmwl-modealiases
broadcom-sta-common
[/B][B]broadcom-sta-source
b43-fwcutter[/B]

All but **b43-fwcutter** had minimal to no success what so ever. With **b43-fwcutter **I could connect however it would drop connection at random, or so it would seem. After a bit of sifting through the **Synaptic Package Manager** I noticed **i8kutils** had been installed. However I did not recall having done so myself.

So I did the following:
Closed the **Synaptic Package Manager**
Opened a terminal (Ctrl + Alt + T)
```
sudo aptitude purge **i8kutils**
sudo aptitude purge **bcmwl-kernel-source**
sudo aptitude purge [B]bcmwl5700-source
[/B]sudo aptitude purge[B] bcmwl-modealiases
[/B]sudo aptitude purge[B] broadcom-sta-common
[/B]sudo aptitude purge [B]broadcom-sta-source
[/B]sudo aptitude purge **b43-fwcutter**
```Using the  **Synaptic Package Manager **I than reinstalled **b43-fwcutter** yet again. That unfortunatly did not work for too long. Still had connection drop issues.

Thought for the sheer sake of things I'd reinstall **i8kutils. **After a failed attempt with the **Synaptic Package Manager **I tried the terminal:
```

sudo aptitude purge **i8kutils**
sudo aptitude update
sudo aptitude install **i8kutils**
```After doing so I opened the **Synaptic Package Manager** again. Ensured **i8kutils** had installed. I pressed "function + F2" to enable wireless. Have yet to experience a problem since. Aside from wireless being disabled by default on boot.

No I didn't have all of those installed & active at one time. At one time the most I had together, but not both active, was ** broadcom-sta-common** & **b43-fwcutter**. I was just illustrating that at one point all had been purged. I am unsure as to why **b43-fwcutter** is the only one to work. Nor do I know why **i8kutils** had issues. Thing that really confuses me is wireless being disabled by default. Actually if there were a script to have it boot enabled that'd be awesome. If not no biggie, just one more step for her to remember.

Anyway I hope if nothing else this can at least save someone the time I lost.

---

### Post by Miljet on 2010-09-10
Thank you very much for that clear explanation. Slightly different chip here --bcm4312, but that gives me a much better idea of what to try. The difficulty I have is that I am trying to fix my granddaughter's computer when she lives two states away. Ah, the joys of troubleshooting over the phone when you can't see the screen in question.

---

### Post by Thoric on 2010-09-11
> **Miljet said:**
> Thank you very much for that clear explanation.
You're quite welcome. Sorry I wasn't terribly clear in previous posts.

> **Miljet said:**
> Slightly different chip here --bcm4312, but that gives me a much better idea of what to try.
My neighbor has the **bcm4312** chip in his lappy. Which worked flawlessly right after installing **broadcom-sta-common**  so that should be the best bet. If that fails **b43-fwcutter** should do the trick. I have heard some instances where people have been "forced" to use **ndiswrappers**. However that was almost always a _***PEBKAC***_ related issue. (User Error)

That's to say if there isn't an issue with the switch and/or function keys. Which is where **i8kutils** comes into play.

> **Miljet said:**
> I am trying to fix my granddaughter's computer  when she lives two states away. Ah, the joys of troubleshooting over the  phone when you can't see the screen in question.
If there's any chance of a, direct, wired connection... I would recommend using remote desktop.
To configure her computer (System\Preferences\Remote Desktop) configuration is rather straight forward. IP address & internal/external network connect-ability is also shown.
almost any VNC client\viewer works well


I know I've repeated myself a bit here.. Just trying lend what ever hand I may have.

---

### Post by SallyVolved on 2010-09-11
I am having the exact same issue with 10.04 on my netbook.  Dell Inspiron mini, came with 8.04 LTS.  Finding a driver for the damned thing is making me go bald (not a good look as I am female).

---

### Post by Thoric on 2010-09-11
> **SallyVolved said:**
> I am having the exact same issue with 10.04 on my netbook.  Dell Inspiron mini, came with 8.04 LTS.  Finding a driver for the damned thing is making me go bald (not a good look as I am female).

Step 1 would be to check out [This Wiki]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Dell Mini 9")

Your netbook may not be the mini 9. However just scroll down & you should find your model.

Step 2 Should be based on model #.

---

