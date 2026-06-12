---
title: "Remote Desktop"
date: 2012-07-23
forum: Desktop Environments
---

### Post by wewhitt on 2012-07-23
Hello all,
I installed Vino in an attempt to remote desktop control my Lubuntu machine. I am having no success in accomplishing my task. Is there any step by step process I could follow, that would allow me to remote desktop control my Lubuntu machine. I love this OS so far, but this one thing is bugging me a bit - with the 12.04 Ubuntu - remote desktop is a can of corn .... or piece of cake .... which ever one you prefer. Any help would be greatly appreciated, and I'm not a huge Linux fanboy ... meaning some of the common terms and acronyms I have to look up - so a real easy step by step would be greatly appreciated. 

Thanks for the effort with this OS,

Bill

---

### Post by Dave W. on 2012-07-23
Hello wewhitt, 
I don't know how to use vino.  I have tried TeamViewer and it worked well.  Here is the link.

[http://www.teamviewer.com/en/index.aspx](http://www.teamviewer.com/en/index.aspx)

It comes in a .deb file and can be installed with GDebi package installer. TeamViewer not in the Ubuntu Repository.  You will have to decide if the source is trustworthy.  I often wrestle with things like that.  I do believe the company is reputable.  

 GDebi is available in the Software Center or via Synaptic.  

Dave

---

### Post by penguinslide on 2012-07-23
I agree with Dave W recommendation, teamviewer is no fuss and couldn't be easier to set up and use.

---

### Post by wewhitt on 2012-07-25
You both are very correct - easy install - complete control - secure for the application I am running. Thank you for the advice!!

Bill

---

### Post by QIII on 2012-07-25
If I recall correctly, vino is not installed by default in Lubuntu.

You may have to install it and set it up to accept remote control.

---

### Post by wewhitt on 2012-07-25
You're right - the vino installed during the first portion of the Deb install run. The Teamviewer DEB file took care of that. 

The problem that I'm running into now - is how to get Teamviewer to start up on a reboot. I know in windows you can drop files that don't have windows boot startup's ... in the start folder. Is there something like this in Lubuntu - to place a program in the boot sequence somewhere.

I'm so close to re-purposing this machine - if I can get this to startup on reboot - I will be set!!!

Bill

---

### Post by Kirurgs on 2012-07-25
Here you are: [http://www.omgubuntu.co.uk/2011/11/five-handy-lubuntu-tips/](http://www.omgubuntu.co.uk/2011/11/five-handy-lubuntu-tips/) (section "How to adjust Start Up Applications in Lubuntu", last part).

---

### Post by wewhitt on 2012-07-25
Very nice!!!

Problem solved!!

I have rebooted 4 times to test - can log in each time - I have complete control of my machine, and I can get to it if there is a power cycle. 

Thank you all for the support - it is greatly appreciated!!

Bill

---

### Post by Dave W. on 2012-07-26
Awesome!!

---

### Post by alek66 on 2012-08-18
I know this is a old post. But I installed Lubuntu 12.04 and vino... I did the vino-preferences, and I can't get it to announce it. I could not connect, and avahi is not announcing it.

Any help?

---

### Post by cariboo on 2012-08-19
> **alek66 said:**
> I know this is a old post. But I installed Lubuntu 12.04 and vino... I did the vino-preferences, and I can't get it to announce it. I could not connect, and avahi is not announcing it.

Any help?

Please don't use Vino, as it is one of the easiest ways for a bad guy to crack your system. I'd suggest using VNC over ssh, there is a howto [here]("https://help.ubuntu.com/community/VNC/")

---

