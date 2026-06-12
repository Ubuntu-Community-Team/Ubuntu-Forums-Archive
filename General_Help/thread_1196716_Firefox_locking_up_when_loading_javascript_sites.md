---
title: "Firefox locking up when loading javascript sites"
date: 2009-06-25
forum: General Help
---

### Post by unimatrix on 2009-06-25
That's right. When you open a website like [this one]("http://digg.com/music/1_Illegal_Download_3_1_3_Dead_Relatives_2") for instance, Firefox will chew up all your CPU and while it's loading you won't be able to do much else but wait, because it be locking up for brief moments every half a second.
Opera is pretty much the same.
Google Chrome is a bit better.
In Windows, none of them do this.

Obviously nobody will know how to fix this problem, so I'm just pointing it out, because this is yet another thing that keeps people away from Linux.

---

### Post by kssworld93 on 2009-06-25
umm no, it worked fine for me

Try to reinstall JRE (java runtime environment).

depending on what you have installed, this may or may not work

```
sudo aptitude reinstall sun-java6-jre
```

---

### Post by kssworld93 on 2009-06-25
Also, I am interesting in your computer processor speed and/or ram and/or graphics card.

---

### Post by unimatrix on 2009-06-25
I said javascript, not java. They are two different things. And even if this was Java's fault, reinstalling it most certainly wouldn't help, because it's like this on every linux system. Pretty sure yours isn't perfectly smooth either.

As for my specs:
AMD Athlon XP 3500+ 64
nVidia GeForce 6600
2GB RAM

And if my hardware is the problem, then why isn't it a problem on Windows?

---

### Post by hthury on 2009-06-25
Same here too. On Windows it's all okay, but on Ubuntu the Firefox keep freezing after some hours of use.

Since I didn't use other net navigators, I didn't knoew it was the very same for Opera and Chrome.

---

### Post by unimatrix on 2009-06-25
> **hthury said:**
> Same here too. On Windows it's all okay, but on Ubuntu the Firefox keep freezing after some hours of use.

Mine starts immediately. Gets no better or worse after hours of use.

---

### Post by Nostalos on 2009-06-25
Sounds like a slow or high latency internet problem.  I have this problem quite often when using my EVDO modem in low signal areas with Ubuntu.

Try this

edit /etc/sysctl.conf (as root)

and add the following line

```

net.ipv4.tcp_window_scaling = 0

```

Reboot and try it again.

---

### Post by unimatrix on 2009-06-25
> **Nostalos said:**
> Sounds like a slow or high latency internet problem.  I have this problem quite often when using my EVDO modem in low signal areas with Ubuntu.
Reboot and try it again.

I have a 10 megabit FTTH line. I can stably ping my ISP with 3 milliseconds.
Let's give it a try.

---

### Post by unimatrix on 2009-06-25
Didn't make any difference. CPU usage while loading javascript-rich websites is still 100% (don't know how disabling window scaling could've made any change there anyway). 
As I'm typing this the letters are actually lagging behind, because a Digg website is loading in another tab, consuming all of my CPU.

---

### Post by Nostalos on 2009-06-25
Not sure then.   I have loaded the previously mentioned website from several different machines Gentoo, Ubuntu 8.04 -9.04, CentOS, and Redhat entprise along with my various windows boxes.  And can't duplicate the issue myself.

Have you modified your firefox settings? or is it a fresh firefox install?

---

### Post by unimatrix on 2009-06-25
> **Nostalos said:**
> Not sure then.   I have loaded the previously mentioned website from several different machines Gentoo, Ubuntu 8.04 -9.04, CentOS, and Redhat entprise along with my various windows boxes.  And can't duplicate the issue myself.

Have you modified your firefox settings? or is it a fresh firefox install?

I've tried with a fresh Firefox profile (moved ~/.mozilla to a temp folder), and it's the same, so even if I had modified my firefox settings that is not the problem.

So either Linux just sucks so much or Windows is so much better. Now I regret removing Windows :(

---

### Post by unimatrix on 2009-06-25
Hmmmmm....

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/223238](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/223238)

---

### Post by Nostalos on 2009-06-25
> **unimatrix said:**
> So either Linux just sucks so much or Windows is so much better. Now I regret removing Windows :(

No offense, but how can you blame your problem as an individual on an OS when no one else can duplicate the issue.   

I'm a firm beleiver is using whats works best for you.  In this case sounds like windows best for your situation.  So Enjoy.

---

### Post by unimatrix on 2009-06-25
> **Nostalos said:**
> No offense, but how can you blame your problem as an individual on an OS when no one else can duplicate the issue.   

I'm a firm beleiver is using whats works best for you.  In this case sounds like windows best for your situation.  So Enjoy.

I'll make sure to link your post to the first guy who tells me that "Linux is ready for the average user"

---

### Post by lovinglinux on 2009-06-25
When I access the page you provided, everything works fine, but as soon as I give permission to run scripts the CPU usage goes to the roof. The same problem occurs on a couple of web pages with dhtml.

The only workaround I know of is to use [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) and [AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865) extensions, to block the scripts. The page works perfectly when NoScript is enabled. I don't know about the functionality of the site. You might need the scripts to use the page properly.

---

### Post by unimatrix on 2009-06-25
> **lovinglinux said:**
> When I access the page you provided, everything works fine, but as soon as I give permission to run scripts the CPU usage goes to the roof. The same problem occurs on a couple of web pages with dhtml.

The only workaround I know of is to use [NoScript](https://addons.mozilla.org/en-US/firefox/addon/722) and [AdBlock Plus](https://addons.mozilla.org/en-US/firefox/addon/1865) extensions, to block the scripts. The page works perfectly when NoScript is enabled. I don't know about the functionality of the site. You might need the scripts to use the page properly.

Yes, now we're getting somewhere.
NoScript makes things A LOT better. The sad problem is (as you've mentioned) that I need scripts to be enabled for most sites to work properly. And even sadder is the fact that in Windows browsers don't hog up all of the CPU even without NoScript (well at least Firefox doesn't... dunno about Exploder)

So where does the problem lie?
Xorg? nVidia drivers?

---

### Post by lovinglinux on 2009-06-25
> **unimatrix said:**
> Yes, now we're getting somewhere.
NoScript makes things A LOT better. The sad problem is (as you've mentioned) that I need scripts to be enabled for most sites to work properly. And even sadder is the fact that in Windows browsers don't hog up all of the CPU even without NoScript (well at least Firefox doesn't... dunno about Exploder)

So where does the problem lie?
Xorg? nVidia drivers?

I have no idea where the problem lies, but I have this issue since Hardy and it seems to be a known issue. I use nVidia by the way.

---

### Post by mikekchar on 2009-07-10
I've been having what I assume are the same troubles.  I load a page in Firefox that has javascript, everything freezes up, my sound stops, keyboard is unresponsive.  At first I thought it it was a video driver problem (I've got an Intel 945GM), but the mouse pointer still moves (but everything else on the display is stopped and I can't get to another VT -- hard reset required).

I'm now almost 100% sure that it's actually a Pulse Audio problem.  It seems that the increased load of running the javascript induces the problem in Pulse Audio which somehow manages to bork everything.  Probably the reason developers haven't noticed the problem is that they have beefier machines than me.

I'm not sure if this is also the cause for your problems Unimatrix.  You might want to remove Pulse Audio from your system to see if it helps.  

I'm sorry you're having problems.  To be honest, Jaunty has been an absolute disaster for me, so I can relate.  But just because the Ubuntu distribution doesn't seem to work for you doesn't mean that GNU/Linux is crap.  I'm also frustrated that Ubuntu chooses to include software by default that isn't stable on all platforms.  There are other distributions, though.

---

### Post by lovinglinux on 2009-07-10
> **mikekchar said:**
> I'm now almost 100% sure that it's actually a Pulse Audio problem.  It seems that the increased load of running the javascript induces the problem in Pulse Audio which somehow manages to bork everything.  Probably the reason developers haven't noticed the problem is that they have beefier machines than me.

I have already removed pulseaudio from all machines here and they use a lot less CPU. But that doesn't fix the problem on sites heavily populated with dhtml.

---

