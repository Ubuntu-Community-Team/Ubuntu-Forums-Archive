---
title: "Dell Mini 9 with external display freezes sometimes!"
date: 2009-08-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vickoxy on 2009-08-09
So, i noticed that almost every time i plug external display on my dell mini 9 (running ubuntu 9.04), after few minutes i got black/blue screen-i have to do hard restart. First i thought it has something to do with video streaming-but no- it is happening also when i just browse internet whitout video streaming or when it just stays like that...

After restart, i didn´t notice it happening again.

Anyone has idea what should that be?

P.S. Maybe something with extra visual effects (i posted before that i have this flickering on my external display - acer 19" 1366x768 -  when i am using this effects)?

---

### Post by ugm6hr on 2009-08-09
Perhaps something to do with "hot-swapping" monitors?

I would always recommend plugging into monitor before turning on.

---

### Post by vickoxy on 2009-08-09
"hot-swapping"-not sure what it is.

E.g this morning i turned on the computer and external display was plugged in-after few minutes i became just blank blue/black screen...

Thanks

---

### Post by ugm6hr on 2009-08-09
> **vickoxy said:**
> "hot-swapping"-not sure what it is.

Sorry.  I thought you were plugging in the monitor after powering on the Mini.

Your particular issue is obviously something else.

Is there a problem with the monitor itself?  Or with the VGA connection lead?

---

### Post by vickoxy on 2009-08-09
It has obviously something to do with external display/intel drivers, because i have no such issues with internal monitor. 

So, i left for one hour dell mini 9 plugged in (monitor and AC charger). It freezed after some time, but the computer itself was hot as hell-as it was doing something. And i noticed accidentally when i unplugged the charger-it came some "click/bing" sound out of the computer-i repeated it-every time i unplugged it, it produced the same sound...

Strange, or?

---

### Post by ugm6hr on 2009-08-09
> **vickoxy said:**
> It has obviously something to do with external display/intel drivers, because i have no such issues with internal monitor. 

Perhaps... Must be related to the resolution of your monitor.

I have had no problems with 640x480 on external monitors (used for projector presentations) on my Mini.

---

### Post by vickoxy on 2009-08-09
> **ugm6hr said:**
> Perhaps... Must be related to the resolution of your monitor.

I have had no problems with 640x480 on external monitors (used for projector presentations) on my Mini.

Well, strange, because with dell´s hardy i had no such problems (same hardware). And i made from april several times new installation-and i always had these freezing issues with external monitor plugged in. On the other hand-no problem with dell mini 9 internal monitor (or anything else)-no freezing, nothing... (on dell´s hardy i had freezing issues with internal monitor)


Funny, little bit...

---

### Post by vickoxy on 2009-08-09
Ok, so i recallled one thing this afternoon-first time (about two months ago) i noticed that dell mini 9 freezed after the battery was full loaded-as soon as it reached 100% it went down. So i left now for couple hours mini 9 to work only on battery-and for now-nothing-no freezing issue.

But, i have to plug it eventually (what i am doing for last 30 min) and still everything is ok. So, i´ll wait until 100% is reached, and see what will be then.

Is something like this possible because of AC Charger?

P.S. I repeat-this is hapenning only with external monitor plugged in...

---

### Post by hammeraxe on 2009-08-11
I am having very similar issues with my EeePC 900 running 9.04. I thought it had to do with the faulty Intel drivers as there were other problems as well (e.g. laggy scrolling in Firefox and glitches in Flash video). I decided to fix it and my xorg.conf now looks like this:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	1280 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option 		"AccelMethod" "exa"
	Option 		"MigrationHeuristic" "greedy"
EndSection

```

Still, the external monitor bug occurs from time to time. The computer sometimes works for hours without issue, but sometimes it takes just 5 minutes for the external monitor to go blank. I then use Fn+F5 to switch back to the built-in screen, but it is not possible to connect back to the other display without doing a reboot.
I really hope there is a way to solve this.

---

### Post by sd73ta on 2009-08-18
My coworker and I both are having the same issue with our mini 9s aswell only on an external monitors and weve tried a few.

Also you can put the mini into sleep mode (Fn + 1) and then wait a second and hit the power button to wake it and everything is fine till it happens again later.

I also wanted to mention this has been an issue regardless of the resolution settings I use.

---

### Post by honestabeinator on 2009-08-22
Same problem, still can't find a fix

---

### Post by vickoxy on 2009-08-23
Just to point that i have still the same problem-so if anone find solution, please post it here.

BTW-did anyone report this bug-i just do not know with what application/process should it be reported - so, mabe someone with greater experience could do that?

---

### Post by sd73ta on 2009-08-25
anything yet?

---

### Post by vickoxy on 2009-08-26
As said, maybe we should file the bug report-but i have no clue how/what to report on launchpad. So, maybe some with greater experience can point us...

---

### Post by djmh on 2009-08-30
same problem here, so heres kinda a bump - any solutions ?

---

### Post by vickoxy on 2009-12-28
Hi,
just to say that i am using now ubuntu jaunty (mint 7), and still have same problem-sometimes dell mini 9 works whitout problems for hours, but sometimes it freezes/go black after few minutes...

So, if anyone can help...

---

### Post by vickoxy on 2010-01-07
One more question-i am using always gnome distrbutions. Should it be better for me to use xfce or kde? Does anyone has any experiencies with those systems (freezing and other stuff)

I have lot of old pdf books-can anyone tells me which ubuntu version has fastest and the best pdf viewer?

---

### Post by vickoxy on 2010-01-07
And one more thing: only external display freezes in gnome-computer is working after freezing (movies, musik...) and if i press Ctrl+Alt+Del i can reset gnome session, and dell mini 9 works just fine, but i can not bundle my external display-need to restart computer.

---

### Post by odioidentisti on 2010-02-12
same problem!
If I press Ctrl+Alt+F1, the external display works. But I have to reboot to get gnome working again.
I someone of us finds a solution.... please post here!

---

### Post by vickoxy on 2010-02-12
Hi,
i think it is gnome-issue.I installed in october xubuntu and fluxbox and had no such issues any more. 
Now i am using dell mini 19v and xubuntu, and don´t want to tra for some time gnome any more...

---

### Post by odioidentisti on 2010-03-20
I solved adding this line in my xorg.conf in section "Device":

Option          "FramebufferCompression"        "false"

1 week without freezings!

Thomas

---

### Post by vickoxy on 2010-03-20
> **odioidentisti said:**
> I solved adding this line in my xorg.conf in section "Device":

Option          "FramebufferCompression"        "false"

1 week without freezings!

Thomas

What system do you use? And where do you have xorg.con? I think there is no xorc.cong in jaunty or karmic...

---

### Post by odioidentisti on 2010-03-22
I'm with the original Hardy canonical distribution for Dell mini 9.
You can find xorg.conf in /etc/X11/xorg.conf. I'm quite sure you should have a xorg.conf, whatever distribution you have!
Do you have karmic on your dell mini 9? It works well? No hw problems? The canonical distribution is really becoming too old....

---

### Post by vickoxy on 2010-03-22
> **odioidentisti said:**
> I'm with the original Hardy canonical distribution for Dell mini 9.
You can find xorg.conf in /etc/X11/xorg.conf. I'm quite sure you should have a xorg.conf, whatever distribution you have!
Do you have karmic on your dell mini 9? It works well? No hw problems? The canonical distribution is really becoming too old....

That means you use ubuntu 8.04. There is still xorg.conf. In jaunty and Karmic it is not any more. I am using now xubuntu 9.10 with dell mini 10v, and have no problems at all with externl display. Needed to tweak a little bit, but i can say it works now perfect...

Still, sometimes i miss a little bit gnome.

---

### Post by vickoxy on 2010-03-27
> **odioidentisti said:**
> I solved adding this line in my xorg.conf in section "Device":

Option          "FramebufferCompression"        "false"

1 week without freezings!

Thomas

Does anyone knows where to find in ubuntu 9.10 this xorg.conf or lines odioidentisti is conferring to?

---

### Post by bbp on 2010-06-07
NionBohart tried many distro and always that issue.
[http://ubuntuforums.org/showthread.php?t=1385447](http://ubuntuforums.org/showthread.php?t=1385447)
I have been using Gnome for years and I never got that kind of problem before. Usually, when Unix is unstable, it's because of an hardware problem. I'm pretty sure Gnome is not responsible for that.

Let say it's an hardware problem, like a buggy video card. I guess when you reinstall your OS, it used a different driver for the video card (maybe a generic one) and, luckly, the new driver is not able to use the hardware feature that make the computer freeze.

I can not tell since I didn't isolated the bug yet. If I can't get ride of it, I will try with Kubuntu. Thanks for your post by the way ;) At lease you seem to have found a workaround. A hard one but still...

[edit]
I just notice that this post has 3 pages. I'm trying that frame buffer compression setting right now. Thanks for the hint!!

---

### Post by odioidentisti on 2010-06-21
I've installed Lucid Lynx 10.04 Netbook Edition (x86) on my dell mini 9.
No architecture problem (although atom chip is lpia architecture) and no more freezing with external monitor. Everything worked out of the box.

There is no reason to keep the old and buggy 8.04 system on your dell mini!

Thomas

---

