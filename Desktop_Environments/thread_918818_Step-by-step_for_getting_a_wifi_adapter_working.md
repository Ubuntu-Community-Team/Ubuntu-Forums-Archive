---
title: "Step-by-step for getting a wifi adapter working?"
date: 2008-09-13
forum: Desktop Environments
---

### Post by jammadave on 2008-09-13
OK.   So hi again guys!   I never did get Ubuntu running on my home laptop (see my old, old posts if you like) but I did have somebody in the know install it on one of my machines at the office, and I love it.   So much so, that my girlfriend asked me to install it on her desktop machine so she could try it - awesome!

So, I went the easiest route and installed it (Hardy) via WUBI, and after futzing around with the monitor resolution - which was the ONLY install problem - it's up and running...

Problem.  She connects to the internet via a NetGear WNDA3100 USB Wifi adapter, and it's apparently not recognized.

I *know* this topic has been covered before, but it's all Greek to me.  What I need, is for somebody to be nice enough to give me *step by step*, ***click by click*** instructions on how to get this thing working...   

You see, even on my best day I know *nothing* about hardware and drivers.   Somebody is probably going to say something like "oh that's easy, use ndiswrapper!" - But to me, that doesn't mean anything useful - What is it and how do I use it?  Do I translate it into Japanese and write it backwards on my bathroom mirror?  Do I feed it to the neighbor's dog?  (exaggeration to show exactly how little I know about this whole drivers concept)

So I'm hoping somebody out there will forgive my ignorance and really help me out.   I really dig Ubuntu and want to share it with others; I'm no stranger to the terminal and I find software management incredibly awesome - but I'm just a dumb user when it comes to hardware.  

Thanks in advance for any assistance here.   My girl is out of town for the weekend and I was hoping to surprise her with a fully-rocking install when she got back tomorrow night.

Cheers
Dave

---

### Post by blakartz on 2008-09-13
Here's what you

1. install wine (for running windows .exe files in linux)

2. go to this page and download the driver to your desktop.
[http://kbserver.netgear.com/products/WNDA3100.asp]("http://kbserver.netgear.com/products/WNDA3100.asp")

3. right click on the file and select open with wine

4, install the package.

5. download ndiswrapper through synaptic package manager.

6. open ndiswrapper. click on install new driver. and navigate to the folder that you installed the driver into and find the .inf file load that into ndiswrapper.

7. Have a great day.:cool::cool:

---

### Post by jammadave on 2008-09-13
BA - thanks for trying, but I gotta tell ya, none of that would have worked as without the wireless adapter working, the desktop machine has no internet connection at all - the router is downstairs.

But!   Lo and behold I got it!!!   I have my office laptop home with me, so I used that to find the wifi tutorial page on ubuntu help... at first glance it looked very daunting, but I downloaded the ndiswrapper packages to a thumb drive, and got the wifi adapter's drivers off the windows partition of the Wubi'd machine, and IT WORKS!   I had to manually configure the connection to put the router key in and whatnot, but it friggin works.   I feel like I've climbed a technological mountain here - with my history, I'm lucky to get a soundcard to work (no kidding).

I'm posting this from the machine in question, as a matter of fact!

(Now, to see why ubuntuforums keeps forgetting my login cookie over on my office laptop...)

Cheers!
Dave

---

