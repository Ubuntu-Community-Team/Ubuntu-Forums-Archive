---
title: "UBUNTU in Public School"
date: 2006-12-16
forum: Education &amp; Science
---

### Post by KBraun107 on 2006-12-16
HI,
I am a computer technician at a medium sized school in Western NYS. I am also fairly new to the LINUX OS. I have been experimenting at home with different Linux Distros an so far it seem that UBUNTU works the best with most of my computers. I am using UBUNTU right now, I have it on my machine that is set up to boot to either U or XP. Well to get to my point, at the school we a quit a number of Emacs running OS9. The student need to get to the web in many cases. The browsers OS9 use are outdated and no longer can get updated versions, such as IE or Netscape. I thought it might be a good idea to get a LINUX Distro such as UBUNTU on these machines. I have experimented with one of the EMACS and UBUNTU works very nicely on it, using the Firefox browser.

The problem is I would have to sell this idea to those in charge, whom are not that tech savvy. So if some of you could give me some selling points and ideas about Linux for education purposes, that would be great. I have looked at EDUBUNTU on the web, I do not know how different that is than UBUNTU. Also, is there any help desk - asset inventory software for linux that is good?

There was one glitch with UBUNTU which I have not yet figured out, is there a way to get FlashPlayer working on the Linux for MAC versions?

Thank You,
Kelsey

---

### Post by aysiu on 2006-12-16
I think it'd be a tough sell, to be honest.

Wouldn't you have a tough time getting Flash working on any web browser in Linux on those computers?

Whoops! I just re-read your post--you already thought of that.

I would just pop in a live CD and show them... let them know they can run a modern web browser like Firefox but that Flash wouldn't really work.

---

### Post by mips on 2006-12-16
> **KBraun107 said:**
> 
There was one glitch with UBUNTU which I have not yet figured out, is there a way to get FlashPlayer working on the Linux for MAC versions?


I stand to be corrected but there is no PPC flash support. See this complaint often in the PPC forums here. Maybe go have a look there and speak to those in the know about PPC architecture.

---

### Post by pmasiar on 2006-12-18
> **KBraun107 said:**
>  some selling points and ideas about Linux for education purposes, that would be great. I have looked at EDUBUNTU on the web, I do not know how different that is than UBUNTU.

3 biggest selling points are: security, security and security! :-P

Seriously. How long you will get security updates for old macs? With ubuntu, you have newest versiions of all edu programs.

Edubuntu also can work in 'terminal server" mode, when workstations (macs) boot from network, and run X localy, which runs apps on the server (which needs be beefed up - lots of RAM, like 4-6GB). So no local disk or anything, and only server needs backup or any administration - clients just reboot from network. They say you need about 200MB of RAM per client, because most of apps run shared libraries.

Will not be easy to sell then this tho: teachers are there to teach, not to learn new things :-) I am trying to convert our 'Bored by education'.

I tried get them interested and they are not. My next gameplan is to start articles in local newspaper about free software, about how easy is OpenOffice to use, etc. Recruit local students to make presentation in library (for city residents). When residents get interested, get some of them to contact city council. And city council will ask: if free software is so easy to use, why we need to pay Microsoft tax? Dont ask us for more money - you can save them by not paying MS tax.

So this will be longer path, but I hope more likely to succeeed - it grows from the grassroots. And it hits where they are defenseless - in the pocketbook :-)

---

### Post by flowsuit on 2006-12-19
**@ KBraun107**

I suggest you check out schoolforge.net.  It has a great mailing list with people that are eager to assist people in cases such as yours.  The website has undergone changes recently and is picking up momentum.  

Take a look at the Case Study page where you will see schools from around the globe using Open Source applications.

---

### Post by ssam on 2006-12-19
there was a recent thread about using [gnash]("http://en.wikipedia.org/wiki/Gnash") on powerpc ubuntu. It might let you view simple flash animations.

to install on ubuntu (6.10)
goto system -> administration -> software sources
on the internet updates tab enable backported updates, and click close
goto system -> administration -> synaptic package manager
click reload
click search, choose look in name. search for gnash.
click on the white box by mozilla-plugin-gnash, choose mark for installation.
then click apply

you will need to restart firfox for it to work.

---

