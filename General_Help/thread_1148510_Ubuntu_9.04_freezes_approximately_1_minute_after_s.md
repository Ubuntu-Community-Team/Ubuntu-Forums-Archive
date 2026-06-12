---
title: "Ubuntu 9.04 freezes approximately 1 minute after startup. Please help."
date: 2009-05-04
forum: General Help
---

### Post by Gck2702 on 2009-05-04
Hi there.

I just installed Ubuntu 9.04.

The booting and the log in works perfect. The loading of the desktop is also without a problem.

BUT about one minute after that, it goes into a hard freeze. Nothing works. Before the minute is over, everything works fine - I can access menu's, open applications etc.

Any help would be gladly appreciated.

Thank you.

---

### Post by sniperwire on 2009-05-04
I'm having the same issue, everything was workin fine for about 2-3 hours then I installed Sun Java and now I'm having this issue.

---

### Post by Gck2702 on 2009-05-04
I didn't even install Sun Java yet. It happened from the first time I started it.

---

### Post by tofiluk on 2009-05-04
does it have to do with your RAM?

---

### Post by sniperwire on 2009-05-04
I don't think Sun Java is the issue but it did start acting up with the same problem as you about 2 minutes after I installed it.

---

### Post by Gck2702 on 2009-05-04
I don't know. I have 1GB DDR2 RAM. Where can I find out whether the RAM is the problem?

---

### Post by unoodles on 2009-05-04
What graphics card do you have? If they are intel, you could be affected by this bug:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/359392)

---

### Post by Gck2702 on 2009-05-04
I have a Nvidia GForce 7600 GT Graphics Card. If that is of any help...

---

### Post by Gck2702 on 2009-05-04
My hard drive is also partitioned between Ubuntu and Vista. Can that be a cause of the problem? Please. I have tried everything and nothing seems to work.

---

### Post by sniperwire on 2009-05-04
I don't think this is causing the problem, I have vista and Ubuntu on the same computer but there on 2 different Hdd's. So that should prove otherwise. btw I'm using an Nvidia 8500GT

---

### Post by SoDanishWasLike on 2009-05-05
The same happens to me. I don't think it is a Nvidia problem because I have a ATI Radeon 9200. 

The only thing I've found that sort of prevents this is to let startup completely and totally take place, then run apps from the menu. Weird.

---

### Post by Priestly_Turkey on 2009-05-06
I have the exact same problem. It happened the from first time I booted up. I've got a Nvidia GForce 7300 GS and I dual boot with Windows XP, but I'm running them on different hdds. I can't find any solution to the problem either.

---

### Post by Priestly_Turkey on 2009-05-07
Well I seem to have fixed my problem. Interestingly, if when I started up the first thing I did was run Open Office Writer and typed some text into that then that seemed to make it not freeze, especially if i kept typing. However, after several restarts, when I booting up while the splash screen was up something happened, I think it was called a routine file system check, anyway that found and fixed some errors and then after I rebooted everything was fine, and its been working fine since then. I don't know if any of that can help anyone else, but that's what happened to me.

---

### Post by ledzepjes on 2009-05-16
I posted this on a similar thread, but this one seems more relevant to me, since the other one describes freezing during start, mine starts but freezes after a min or two after only loading firefox it seems. My laptop, gateway m6809 athlon xp-m 3200+ 512mb 80g 5400rpm hdd with ATI x600 mobility discrete graphics card and broadcom bcm4306 wireless card. I first started using ubuntu 7.04. I now use 9.04, which boots up really fast. But, it freezes after loggin in, and it seems like it only does so after a min or two after loading firefox. I know that I had to do some fernigaling to get my broadcom wireless bcm4306 to work this go around, which required manually installing the broadcom drivers package bcm43xx from synaptic and restarting a couple times. I also have tried but failed at installing video card drivers for my laptop, however it works fine without them, I would just like to install drivers since it is a disrete card, but when trying to use Enyng, it won't recognize the video card. Should the card need drivers? Is this what is causing my freezing issues after loading firefox? Ubuntu 9.04 has been working fine since I installed it, now just today it starts to freeze and only seems to freeze opening firefox. I have installed adobe flash fyi. I also loaded Opera through ubuntu-tweak since it wasn't in synaptic (gripe) but I was able to load the exact set of web pages and the computer stays running with Opera? Is there a problem with firefox? video card drivers needing installed? me? updates? ufo's? the economy? Oh brother.

---

### Post by ledzepjes on 2009-05-17
I must say, I did have addon's installed for firefox, (mouse gestures, tabs mix plus, fox tab, tab scope, adblock plus, download status bar) and after uninstalling all of these, ubuntu seems to be stable now. No more freezing and having to hard shutdown by pressing power button. Now I must find which one of them was causing this freezing, and why?

---

### Post by no_cookies4you on 2009-07-05
I've been having the same problem ever since I upgraded to 9.04.  I was previously running 8.04, so in one night I upgraded to 8.10 and then immediately to 9.04.  I read the warnings about installing all updates for each version before moving to the next, but the update manager didn't find any updates in 8.10 so I just went ahead and upgraded further.

I also have several Firefox add-ons installed, including mouse gestures and adblock.  I'm in Windows now so I guess I'll boot back up and see if I can uninstall those before everything freezes again...

I also have some sort of NVIDIA card although I'm not sure of the specifics.

---

### Post by ivanvajar on 2009-07-05
Just to answer one of the questions: You can test your RAM with LiveCD. There is option for that before after language selection.

---

### Post by sriny1512 on 2009-07-10
Same freezing problem. I did the RAM and HDD test and it was ok. I did not try MEMTEST on Ubuntu live CD, I will reply back after running MEMTEST. 

Thank you friends :guitar: ;)

---

### Post by sefs on 2009-07-10
Can you check that you have a functioning swap partition?  A non-existant or corrupted swap can lead to that sort of behaviour.

The only way though I know how to check though is that I usually have conky installed with various bits of info one of them being a diagram of the swap.  if it says 0/0 then something is usually amiss with the swap.

---

### Post by sriny1512 on 2009-07-10
I did a MEMTEST with Ubuntu live CD, the test was good. Its a new installation of Ubuntu 9.04, do you think there's a be problem with the swap partition? Good thing is I am not experiencing any freeze until now. But when it hapenned for the first time, Ctrl+Alt+Backspace did not work either. I had to restart the system by pressing the reset button. Do you suspect hard drive because I have used Ubuntu since years and I know it just can't freeze like any other OS unless there is some problem. I did a Short Test with Seatools and that was good.

Thanks for the help SEFS. I will get back to you if there is a problem.

---

### Post by AngelX on 2009-07-13
Same freezing of Ubuntu from time to time, I was using 8.10 before with no problems, I upgraded to 9.04 (no fresh install) and now, I would say 4 out 10 times it freezes at starup, nothing responds; then after hard reset it goes in without issues.

No clue what could be wrong. Any help is appreciated.

---

### Post by NinjaNumberNine on 2009-07-16
Type```
 sudo apt-get remove compiz
```then,
```
sudo apt-get remove compiz-core
```then try this: ```
sudo apt-get remove compiz-wrapper
```

Don't worry if some of those are not installed.
The first two are versions for Ubuntu and the third is for KDE.
Oh, and if you do remove these, you will loose two of the options in Desktop Settings > Effects.
(i.e. the wobbly windows and animated minimizing effect, etc.)

---

### Post by cthulhufhtagn on 2009-07-18
I also had this problem. After some trial and error, I found that moving to kernel 2.6.29 seemed to fix it. It should probably also be noted, that before going to 2.6.29 I tried out 2.6.30, which _didn't_ fix it.

Anyone interested in trying out kernel 2.6.29, may want to check out this site [http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/]("http://www.ramoonus.nl/2009/03/24/linux-kernel-2629-installation-guide-for-ubuntu-and-debian-linux/") for an article that explains the process.

---

### Post by lanp16108103 on 2009-07-22
> **sriny1512 said:**
> I did a MEMTEST with Ubuntu live CD, the test was good. Its a new installation of Ubuntu 9.04, do you think there's a be problem with the swap partition? Good thing is I am not experiencing any freeze until now. But when it hapenned for the first time, Ctrl+Alt+Backspace did not work either. I had to restart the system by pressing the reset button. Do you suspect hard drive because I have used Ubuntu since years and I know it just can't freeze like any other OS unless there is some problem. I did a Short Test with Seatools and that was good.

Thanks for the help SEFS. I will get back to you if there is a problem.

The 9.04 Ctrl+Alt+BackSpace is no more...  The new keys are : Right Alt+PrntScrn+K.  To re-enable Ctrl+Alt+BackSpace, look at the end of this post (Don't need to install dontzap) : [http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

---

### Post by rhchia on 2009-07-22
> **NinjaNumberNine said:**
> Type```
 sudo apt-get remove compiz
```then,
```
sudo apt-get remove compiz-core
```then try this: ```
sudo apt-get remove compiz-wrapper
```

Don't worry if some of those are not installed.
The first two are versions for Ubuntu and the third is for KDE.
Oh, and if you do remove these, you will loose two of the options in Desktop Settings > Effects.
(i.e. the wobbly windows and animated minimizing effect, etc.)

i experienced freezes quite often too but not to the extend of 1min after startup. somewhat inconsistant on the duration before frozen. i suspect u are right about compiz could be the reason behind the froze. but i think i heard something to do with the kernel somewhere in the forum.

---

