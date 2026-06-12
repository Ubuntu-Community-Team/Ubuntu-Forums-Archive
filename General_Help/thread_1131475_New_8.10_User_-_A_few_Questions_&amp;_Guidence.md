---
title: "New 8.10 User - A few Questions &amp; Guidence"
date: 2009-04-20
forum: General Help
---

### Post by Vyp3r on 2009-04-20
Hello Everyone, after reading a while ago about this distro and a constant niggling with my Vista freezing playing AVI files and a system rebuild on the cards I thought i would check out 8.10 Finally.

A few quick things:

1. Running a Palit Sonic 9600GT with Display Port to my Dell 24" Ultrasharp and DVI to my samsung 730BF but can not work out how to get dual monitors working. Its either one or the other. I did some googling but can not seem to find a solution that works.

I havent gone into the nitty gritty stuff as I am too new for that, looking for a app that allows me to control them manually, IE, Ultramon or something.

2. Running Sun VirtualBox with XP PRO SP3 but can not get it to detect my USB keys or my WD640GIG HDD (which both appear in Ubuntu). I wish to allow the HDD to be access from Host and Virtual machines (going to do a vista and w7 virtual soon).

3. Do I need to run any security programs on my windows installs (and my Ubuntu for that matter) or am I pretty safe?

4. Whats a good video editing software to use to edit a AVI file?

Many Thanks and I hope i am able to get a few issues sorted so I can enjoy my Ubuntu experience!

- Rob.

---

### Post by 3Miro on 2009-04-20
2. Depends on the version of Virtual Box that you are running. The one in the repositories does not support USB, go to Virtual Box web-page and get the other version. They also have a manual that tells you how to share folders between guest and host.

3. Ubuntu is generally safe, windows is just as vulnerable. Depending on the settings you might have an extra firewall for windows, but otherwise it works the same way with the pros and cons.

for 1 and 2 - I don't know.

---

### Post by Ocxic on 2009-04-20
install nvidia-settings to control the 9600GT that will allow you to use twinview.

---

### Post by KhurramM on 2009-04-20
video editing software to edit a AVI file:

try mplayer/mencoder

on cli:
man mencoder
for details.

Hope it helps.

---

### Post by andrew.46 on 2009-04-21
Hi Vyp3r,

> **Vyp3r said:**
> 
3. Do I need to run any security programs on my windows installs (and my Ubuntu for that matter) or am I pretty safe?


Can I recommend the following document that speaks of security under Ubuntu in some depth:

Ubuntu Security
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

and gives many, many links to sites and documents that discuss the matter in great detail.

All the best,

Andrew

---

### Post by abcuser on 2009-04-21
> **Vyp3r said:**
> 2. Running Sun VirtualBox with XP PRO SP3 but can not get it to detect my USB keys or my WD640GIG HDD (which both appear in Ubuntu). I wish to allow the HDD to be access from Host and Virtual machines (going to do a vista and w7 virtual soon).
Hi,
Have you enabled USB device in VirtulBox GUI?
Have you inserted USB device in such a way that guest is not in fullscreen? Windows should pops-up driver install - that will install VirtulBox USB driver
Reboot you guest

P.S. Please if you have multiple problems post each problem in new thread, it will be easier to read. Also try to post VirtualBox problems to virtualization forum: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)
or official VirtualBox forum: [http://forums.virtualbox.org/](http://forums.virtualbox.org/)
Regards

---

### Post by lisati on 2009-04-21
For video editing, it depends on how ambitious you are.You might want to check out Kino.  One of the main reasons I keep Windows around is that I kinda like the features in the video editing software I've paid good money for.

---

### Post by abcuser on 2009-04-21
> **Vyp3r said:**
> 2. Running Sun VirtualBox with XP PRO SP3 but can not get it to detect my USB keys or my WD640GIG HDD (which both appear in Ubuntu). I wish to allow the HDD to be access from Host and Virtual machines (going to do a vista and w7 virtual soon).
Hi,
by the way, which version of VirtualBox are you using? Open-source version does not support USB. Please read: [http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)
Regards

---

### Post by Vyp3r on 2009-04-21
Thanks guys for the replies.

I have ditched Ubuntu on my main rig, went back to XP as i was getting too frustrated but kept it on my HTPC rig - where i really want it.

So my virtual problems dont exist any more, so thats fine now. Thanks for the link about the security stuff, I will take a read.

Now i just need to work out how to Add the deb sources into your software sources repo's as I am trying to install XMBC (got it on my xp rig, LOVE IT) but want to use it on Ubuntu.

I will go searching and see what i can dig up.

Thanks!

---

