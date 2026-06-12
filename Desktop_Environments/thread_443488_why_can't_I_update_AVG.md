---
title: "why can't I update AVG"
date: 2007-05-14
forum: Desktop Environments
---

### Post by fartman on 2007-05-14
I am a beginner when it comes to linux.  I have ubuntu 6.06 installed and I finally figured out how to install avg but now I cannot update it.  It says I don't have permision.  I am the only user on the computer, how can I not have permision?  Please help!

---

### Post by fartman on 2007-05-14
never mind, I figured it out.  I think

---

### Post by padre44 on 2007-10-31
Can you tell me what you did?  I'm having the same issue.

---

### Post by chiefbearclaw on 2007-10-31
This thread addresses some of the update issues along with some how-to's on installing AVG.

[http://ubuntuforums.org/showthread.php?t=136064]("http://ubuntuforums.org/showthread.php?t=136064")

---

### Post by Norwal on 2007-11-11
Found this on another post. I worked for me.

to enable updates to AVG you need to do the following…

* system > administration > users and groups
* enter your root password
* manage groups > select avg > press properties
* select all group members (root, your user, avg)
* press ok, close, close
* reboot your system
* load up the system, load avg and run the update process.

---

### Post by Radiolad on 2007-11-12
> **Norwal said:**
> Found this on another post. I worked for me.

to enable updates to AVG you need to do the following…

* system > administration > users and groups
* enter your root password
* manage groups > select avg > press properties
* select all group members (root, your user, avg)
* press ok, close, close
* reboot your system
* load up the system, load avg and run the update process.

FANTASTIC  :popcorn:

I've just tried this on my PC and it works for me too :)
Many thanks !!

As a matter of interest ... for the **_INSTALLATION _**of AVG I followed an excellent guide on  **howtoforge.com**
Everything was explained with snapshots of GUI and also the 'errors' that might/would be encountered and how to resolve them (except for the final update query as per above.

Cheers, Radiolad.

---

### Post by atarileaf on 2007-11-12
Ok, stupid "noob" question alert but I thought antivirus software was unnecessary with Linux? :confused:

---

### Post by gpilkay on 2007-11-12
AVG is my personal favorite in XP , I have it on my laptop and desktop.  When running in Linux-mode on my desktop, though, I honestly just use Avast (Ubuntu 7.04) as it was the ONLY anti-virus I found that didn't have some sort of hangup.  Just download the .deb, enter the activation licence key (which they give you free in your e-mail) and you're good to go.   I've had no problem.

And yes, you can get away with no antivirus in Linux, but if you swap files with a Windows system a lot like I do, it's a good idea to have it anyway.

---

### Post by atarileaf on 2007-11-12
> **gpilkay said:**
> AVG is my personal favorite in XP , I have it on my laptop and desktop.  When running in Linux-mode on my desktop, though, I honestly just use Avast (Ubuntu 7.04) as it was the ONLY anti-virus I found that didn't have some sort of hangup.  Just download the .deb, enter the activation licence key (which they give you free in your e-mail) and you're good to go.   I've had no problem.

**And yes, you can get away with no antivirus in Linux, but if you swap files with a Windows system a lot like I do, it's a good idea to have it anyway**.

Ok, I don't do that so I should be ok. I'll look into AVG on linux regardless the next time I boot it up. No such thing as too much security eh?

---

### Post by Happibun on 2008-03-09
Thanks for the GUI route to get AVG to update. I've seen lots of command line routes to change a rar file in to a deb one, but all I needed was something simple like that.

I used AVG on my windows systems too, so I know it well and decided to stick with it.

---

### Post by aysiu on 2008-03-09
> **atarileaf said:**
> Ok, stupid "noob" question alert but I thought antivirus software was unnecessary with Linux? :confused:
Maybe the OP is using Ubuntu as a mail server or a file server for Windows computers. Otherwise, it's pretty much useless.

---

### Post by wawadave on 2008-04-02
Norwal thank you for this.

I would  Like to be able to load up ubuntu with as many security apps as i can. so i can scan slaved windoz drives with out fear of there spyware viruses trojins rootkits migrating.
Have had some success running things through wine. 
Yes i could run Ultimate Boot CD for Windows® but i find faster responses and more options from a live os. 

So till i look for my next newby fix have a great day.

---

