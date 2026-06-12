---
title: "Enlightenment update fail due to broken package"
date: 2012-12-22
forum: Desktop Environments
---

### Post by Buntu Bunny on 2012-12-22
> Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The following packages have unmet dependencies:

evas-loaders: Depends: libefl (>= 201212211037) but it is not installed
              Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
              Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
libedbus1: Depends: libefl (>= 201212211037) but it is not installed
libedbus2: Depends: libefl (>= 201212211037) but it is not installed
libedje1: Depends: libefl (>= 201212211037) but it is not installed
libeeze1: Depends: libefl (>= 201212211630) but it is not installed
libefreet1: Depends: libefl (>= 201212211630) but it is not installed

So far I've never encountered this type of problem. Do I need to disable ppa:hannes-janetzek/enlightenment-svn? Before I type that command in terminal, I would like to know what it will do. Can someone tell me please?

---

### Post by Frogs Hair on 2012-12-22
I have used the PPA in the past and the maintainer made errors at times. I usually just waited for updates which came sometimes twice daily. Do not mix the PPA with any other E17 packages from the repository or the package system will break. Go ahead and run the command with the PPA enabled.

---

### Post by Buntu Bunny on 2012-12-22
> **Frogs Hair said:**
> I have used the PPA in the past and the maintainer made errors at times. I usually just waited for updates which came sometimes twice daily. Do not mix the PPA with any other E17 packages from the repository or the package system will break. Go ahead and run the command with the PPA enabled.

Thank you Frogs Hair! This is what I get when I run the command

```
(Reading database ... 419759 files and directories currently installed.)
Unpacking libefl (from .../libefl_201212220429-538~precise1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libefl_201212220429-538~precise1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libecore_evas.so.1.7.99', which is also in package libecore1 201210092056-5139~precise1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libefl_201212220429-538~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Are you saying that I should wait a bit and keep trying?

---

### Post by Frogs Hair on 2012-12-22
I would wait for the next round of updates.

---

### Post by Buntu Bunny on 2012-12-22
That's what I needed to know. Thanks Frogs Hair!

---

### Post by Mr.Goose on 2012-12-22
Buntu Bunny thanks for raising this issue. My system is also similarly messed up due to this bug. And thanks to Frogs Hair for your clear explanation of the situation. I had suspected as much myself.

But with all due respect chaps, describing the matter as "solved" is a tad premature IMHO. It isn't *actually* solved until the PPA maintainer solves it, by fixing the dependency error(s) in his packages. Is it?

In the meantime, anyone who is using his PPA will be unable to upgrade their systems, do any security patches or install any software. 

I will attempt to contact the guy and alert him to the problem. Hopefully this might speed things up a bit.  Then we can mark the problem as truly *solved*.

Best wishes, G.

---

### Post by Mr.Goose on 2012-12-22
As a temporary fix (**NOT** a permanent solution that justifies the matter being described as "*solved*"!) the following enabled my package management system to work properly:-
 
```
sudo apt-get remove libedbus1 libedbus2 libedje1 libeeze1 libefreet1 libemotion0 libethumb libethumb-bin libethumb-data
```

I took the view that getting E17 working was not as important as being able to receive security updates and install other stuff, if I needed to.

HTH. G.

---

### Post by Buntu Bunny on 2012-12-22
> **Mr.Goose said:**
> But with all due respect chaps, describing the matter as "solved" is a tad premature IMHO. It isn't *actually* solved until the PPA maintainer solves it, by fixing the dependency error(s) in his packages. Is it?

In the meantime, anyone who is using his PPA will be unable to upgrade their systems, do any security patches or install any software. 

I will attempt to contact the guy and alert him to the problem. Hopefully this might speed things up a bit.  Then we can mark the problem as truly *solved*.

> **Mr.Goose said:**
> 
I took the view that getting E17 working was not as important as being able to receive security updates and install other stuff, if I needed to.

Mr. Goose, thank you for pointing that out. I agree with your concerns. I confess I was a bit hesitant to mark it solved because it actually *isn't *yet. My hopes were that it would be solved with a proper update. 

Needless to say that was easily remedied and we can wait until we're satisfied it is solved properly.

---

### Post by Mr.Goose on 2012-12-22
Well, I have just emailed Hannes Janetzek (the PPA maintainer) and alerted him to the issue. Judging by all the work he has done on his PPA, he seems a very hard-working and enthusiastic sort of chap. My guess is he will be on the case pretty soon.

Best wishes, G.

---

### Post by Frogs Hair on 2012-12-22
After trying repository packages and 3 different PPAs I decided my next E17 experience would come via Bodhi.

By all means use the PPA if you want but it is hard to get a really good experience running E17 on top of Ubuntu with Gnome 3 applications. I like E17 and trying as a stand alone desktop on Bohdi was far Superior to PPA experiences.   

[http://www.bodhilinux.com/](http://www.bodhilinux.com/)

---

### Post by Buntu Bunny on 2012-12-22
> **Frogs Hair said:**
>  I like E17 and trying as a stand alone desktop on Bohdi was far Superior to PPA experiences.   

I've read that about E17, but confess that the DE I use most is Xfce. I do like Enlightment though, so I keep it. 

What do you think about [Elive]("http://www.elivecd.org/") for Enlightenment?

---

### Post by Mr.Goose on 2012-12-22
I'm a KDE guy myself. After somewhat problematic beginnings, KDE4 has become really rather good now. Its silky smooth feel coupled with its rich functional opulence make most other desktops seem crude and clunky in comparison, IMHO.

But I still enjoy flirting with other DE's and E17 is a very interesting one indeed - with some pretty neat concepts behind it. But like you say Frogs Hair, my experience of E17 via PPA's means they are relatively short-lived flirtations, especially now KDE is so good. 

But I take on board what you say about Bodhi. I have heard many users speak well of it. So perhaps I will give it a whirl on a test box, once Christmas is out of the way.

Best wishes, G.

---

### Post by tlan on 2012-12-23
Thanks for alerting the maintainer, the last round of updates indeed broke my E17, it appears the final release of E17.

I use only Unity which is the best WM and E17, as all other WM proved to be inconsistent.

I for one wish there is more dev building and maintaining for E17, This WM has the potential to be the second in line WM for linux,

And what i did to get past that error which also prevented all other updates

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libefl_201212220429-538~precise1_amd64.deb
 sudo apt-get -f install

---

### Post by Buntu Bunny on 2012-12-24
> **tlan said:**
> And what i did to get past that error which also prevented all other updates

sudo dpkg -i --force-overwrite /var/cache/apt/archives/libefl_201212220429-538~precise1_amd64.deb
 sudo apt-get -f install

That's the problem I'm having now, Ubuntu updates are prevented due to the error. If I deselect ppa:hannes-janetzek/enlightenment-svn from Update Manager's other software prefernces, it wants to remove E17 as well as xscreensaver. (That one I'm not too happy about because I used it; OTOH removal of xscreensaver may have to do with something else (?)

Thanks for the workaround Tlan. Considering how much I use Enlightenment, I need to rethink whether or not it's worth keeping just to doodle with from time to time.

---

### Post by scoon on 2012-12-24
Hey there, 

I had the same problem as well and removed **ppa:hannes-janetzek/enlightenment-svn** repository and added **ppa:efl/trunk**.  

Thanks, 

Skip

---

### Post by Buntu Bunny on 2012-12-24
> **scoon said:**
> Hey there, 

I had the same problem as well and removed **ppa:hannes-janetzek/enlightenment-svn** repository and added **ppa:efl/trunk**.  



Hey Skip. Any problems with that PPA? Update Manager was complaining that PPAs are usually the problem. I've never had any trouble until now.

---

### Post by scoon on 2012-12-24
> **Buntu Bunny said:**
> Hey Skip. Any problems with that PPA? Update Manager was complaining that PPAs are usually the problem. I've never had any trouble until now.

Hey there,

None.  I just changed ppa's last night and all has been good ever since.  

Thanks, 

Skip

---

### Post by Frogs Hair on 2012-12-24
> I've read that about E17, but confess that the DE I use most is Xfce. I do like Enlightment though, so I keep it. 

What do you think about Elive for Enlightenment?

This distro has been around for while and really don't know much about it under the hood as far as what Debian version is used. At one time it was considered one of the best E17 distros. There isn't much for current news on their site.

---

### Post by Buntu Bunny on 2012-12-24
I read it's supposed to be very lightweight, so I might try it on my oldest computer, just to see.

---

### Post by Mr.Goose on 2012-12-25
Good evening chaps. 

Seems that Hannes Janetzek's PPA is fixed now.

Thanks Hannes - if you're reading this. 

Best wishes, G.

---

### Post by Buntu Bunny on 2012-12-26
> **Mr.Goose said:**
> Good evening chaps. 

Seems that Hannes Janetzek's PPA is fixed now.

Thanks Hannes - if you're reading this. 



Excellent news Mr. G Thank you!

---

### Post by Tux Aubrey on 2013-01-07
For anyone still having problems (particularly seg faulting on starting e17) try deleting your ~/.e folder and setting things up again (mine did a second seg fault after that but was fine from that point onwards.  A few modules come with warnings (eg. iTask, Tclock)but have worked OK for me.

Thank goodness e17 is back!

---

