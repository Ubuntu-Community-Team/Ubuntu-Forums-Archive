---
title: "Blank screen insted of shutdown"
date: 2006-05-31
forum: Desktop Environments
---

### Post by Kilz on 2006-05-31
Hi
I started having this weird problem. I cant shut down normally, restart, or log out. If I do the screen goes black, ctrl-alt-delete wont shut it down. I'm then forced to hold down the power button to shut the PC off.  If I shout down from the login screen it shuts down normally , I'm able to switch users ok.
I did a forum search and didn't find anything like this, any ideas?

---

### Post by bobby19 on 2006-07-21
I have the same exact problem as you do. I think that it is an issue with the ati driver version that came with Dapper because it never did this with Breezy. Do you have an Nvidia or Ati card?

---

### Post by subiet on 2006-07-29
i got the same problem too, i mean, i have ati, and then i installed the fglrx drivers, and since then is when this problem has come, experts please help

---

### Post by kufford on 2006-07-29
I'm having an idential problem on my parent's walmart special. HP a1253b 

Tag for possible solutions?

---

### Post by ssinghi on 2006-07-29
I am also having the same problem, Athlon 64-bit, ATI and fglrx driver. Sometimes, the machine does shuts down properly.:confused: 

 With Breezy the machine was shutting down properly, only Dapper gives this problem.

Any help?

Thanks.

---

### Post by Dubbayoo on 2006-07-29
Same here. Dapper & ATI. I'm going to get an nvidia soon so I can get xgl to work.

---

### Post by kufford on 2006-07-29
bump... This is a really annoying bug...

---

### Post by GoodPanos on 2006-07-30
Same here.  Mine happens though only on Kubuntu and not every time.  I have both Ubuntu and Kubuntu installed on separate partitions.  On Ubuntu fglrx works smoothe; it has no effect on shutdown or reboot.

Any one have a solution??

---

### Post by IbeeX on 2006-07-30
Hi 
amd64 Nvidia same problem here sometimes shutdown don't work. But mostly it das :)

---

### Post by Dzo on 2006-08-01
Got exactly the same issue on a Dell Latitude D600, any ideas what is causing this yet?

---

### Post by subiet on 2006-08-02
my problem has been resolved, i installed the fglrx driver, and then when asked for the driver in reconfig tool i chose ati instead of fglrx.
sometimes, if your system hangs, you can go to another runlevel (say for 2: ctrl+alt+f2) and then login, and then type sudo shutdown -t secs 0

---

### Post by subiet on 2006-08-02
my problem has been resolved, i installed the fglrx driver, and then when asked for the driver in reconfig tool i chose ati instead of fglrx.
sometimes, if your system hangs, you can go to another runlevel (say for 2: ctrl+alt+f2) and then login, and then type sudo shutdown -t secs 0

---

### Post by Dubbayoo on 2006-08-03
Why reinstall fglrx driver but not use it?

---

### Post by TobbeR on 2006-08-03
Hi

I found a solution somewhere for the shut down crash, the session manager KDM/GDM is not properly configured.

For KDM put "TerminateServer=true" in your kdmrc under the [X-:*-Core]: section.

For GDM put "AlwaysRestartServer=true" in the gdm.conf.

I have tested the KDM solution and it worked for me.

Regards
TobbeR

---

### Post by Hachi-Roku on 2007-11-29
hi,
im getting the same problem with gusto. whats the name and where is this conf file your modifying tobber?

---

### Post by Hachi-Roku on 2007-11-29
Disregard...found it. I think it may have worked... although ive only shutdown once since and my shutdown prob appears a bit random. I'll repost after a few and see if it works for good. cheers Tobber

---

### Post by Hachi-Roku on 2007-11-29
The gdm fix has worked for me so far, we'll see if it continues haha. shut down seems  to take a long time in gusty.

---

### Post by Hachi-Roku on 2007-12-21
It didnt work in the long run.

Still get the hang. and its still at random. Very strange.

---

### Post by jorijn on 2008-04-26
Bump. I'm having the same problem on Kubuntu 8.04. None of the above 'tips' worked so far. I have a Ati Xpress 200M and using the fgrlx drivers from the restricted repository.

Installing the drivers from ati.amd.com wouldn't work in any way, cause it didn't load the kernel module.

---

### Post by ivan_p83 on 2008-04-28
I've solved it today at Kubuntu 8.04 (after upgrading from 7.10) and ATI Radeon Xpress 1100.

This what worked for me:

1) switched from 'fglrx' to 'ati' drivers
2) restarted computer (couldn't log out [because of the issue] to restart X Server as prompted)

Here issue solved, but OpenGL screensaver wasn't smooth, so I continued:

3) purged 'xorg-driver-fglrx'
4) installed 'xorg-driver-fglrx'
5) switched from 'ati' to 'fglrx' drivers
6) logout, restart X server, login

Issue solved for me...

---

### Post by ivan_p83 on 2008-04-28
> **Kilz said:**
> ...
I'm then forced to hold down the power button to shut the PC off.
...

Alt+SysRq+E 

it will send TERM signal to all processes except 'init', and rebooting or shutting down will continue without harm to filesystem.

More info: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by Kilz on 2008-04-28
> **ivan_p83 said:**
> Alt+SysRq+E 

it will send TERM signal to all processes except 'init', and rebooting or shutting down will continue without harm to filesystem.

More info: [http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

You are aware that you replied to a post from **[COLOR="Red"]2006[/COLOR]**, right?

---

### Post by ivan_p83 on 2008-04-29
> **Kilz said:**
> You are aware that you replied to a post from **[COLOR="Red"]2006[/COLOR]**, right?

Haven't noticed, just looked through the thread for the history of problem...
but it can be a good reference for those who have this problem too, and "forced" to power off manually. (I, for example, learned about SysRq key not long ago before the upgrade, after few month that I'm using Linux).

---

