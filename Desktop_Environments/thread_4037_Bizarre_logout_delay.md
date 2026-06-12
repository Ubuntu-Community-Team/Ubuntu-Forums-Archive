---
title: "Bizarre logout delay"
date: 2004-11-11
forum: Desktop Environments
---

### Post by HungSquirrel on 2004-11-11
This just started happening today, and I have no idea why or what's causing it.

When I select Computer -> Logout in Gnome, there is an enormous delay from the moment I click Logout until the moment I see the logout screen.  The delay is anywhere from 10 to 45 seconds, and it's different each time!  I tried restarting X and restarting my PC and neither helped.

Has anyone ever heard of behavior like this?  WTF did I do to my system?

---

### Post by HiddenWolf on 2004-11-11
Could it be the internet connection closing?

During boot I sometimes have a 30 second delay before internet comes up and the kernel resumes booting.
Sometimes it happens, sometimes it doesn't.

---

### Post by HungSquirrel on 2004-11-11
The internet connection is started before X starts and closed after X closes for reboot.  At least, it's supposed to be like that, and is like that on all distros I've used.

At any rate, it does it when the logout screen comes up asking me if I want to logout, reboot, shutdown, etc.  This doesn't just happen before a reboot or anything.

---

### Post by Sebastian Richter on 2004-11-12
Hi,

if had the _exact_ same situation here. I click Computer-Logout and then, it just nothing happens.

I discovered that the delay gets shorter and shorter, when gnome is running for a longer time. If gnomes has run for hours, there is no delay. When gnome is "fresh" started, the delay was quite a minute.

I have now explanation for that behaviour.

Bye,

Sebastian

---

### Post by HungSquirrel on 2004-11-12
Yes, that's exactly how it is for me, too.  I didn't discover the delay before because I rarely logged out.  I only noticed it recently because I was logging out to test Openbox, Fluxbox, and other alternative WMs.

---

### Post by istoyanov on 2004-12-09
[QUOTE=Sebastian Richter]

I discovered that the delay gets shorter and shorter, when gnome is running for a longer time. If gnomes has run for hours, there is no delay. When gnome is "fresh" started, the delay was quite a minute.

I have now explanation for that behaviour.

[/QUOTE]

I have made the opposite observation: when my machine was running for a long time, sometimes the Shutdown is terribly delaying. Several times I had to restart X with CTRL+ALT+Backspace and to shutdown without logging in again.

However, I have no idea why this slow shutdown is happening...

Cheers!

---

### Post by Sepero on 2005-01-06
[QUOTE=HungSquirrel]When I select Computer -> Logout in Gnome, there is an enormous delay from the moment I click Logout until the moment I see the logout screen.  The delay is anywhere from 10 to 45 seconds, and it's different each time![/QUOTE]Same here. This problem is most evident directly after Gnome has started. The most strange part is that I have a CPU monitor running, so I see that there is virtually no activity!

I'm actually surprised no one has posted a solution to this yet. :sad:

---

### Post by Sepero on 2005-01-06
It appears they can't even figure this problem out on the Gnome forums!
[http://gnomesupport.org/forums/viewtopic.php?t=2306](http://gnomesupport.org/forums/viewtopic.php?t=2306)

 ](*,)

---

### Post by wallijonn on 2005-01-06
First you have to see what programs are running.

Applications -> System Tools -> System Monitor -> Process Listing. View All Processes (right button).

Edit -> Preferences. Under "Process Listing" Tab, turn on "Status" and "%CPU" 

Applications -> System Tools -> System Log.

You may have to kill processes one at a time to find out which one is in the dreg queques or is in hibernation. 

My own guess? It may may be something simple, like a bad Fire Fox extension, or a daemon that is hung, something in your hidden .gnome folders, etc.

---

### Post by Sepero on 2005-03-09
I have no doubt that it's Gnome's fault. I really prefer Gnome as a DE too. :(

---

### Post by omniwired on 2007-11-16
This fixed my problem:

I Went to system -> preferences then to session and re activate gnome power daemon and that's it no more long wait. (I read that sometimes the problem is the bluetooth applet).

---

### Post by ridgeland on 2007-12-01
Thanks omniwired,
Turning Power Manager on solved my delay.
I timed it at 50 seconds for the logout window before turning Power Manager back on, but with it on the logout window pops up before I can start my stopwatch.

---

### Post by kikiriki_bg on 2008-01-13
Activating gnome power daemon solved my problem too.

---

### Post by pingpongboss on 2008-05-28
> **omniwired said:**
> This fixed my problem:

I Went to system -> preferences then to session and re activate gnome power daemon and that's it no more long wait. (I read that sometimes the problem is the bluetooth applet).

Thank you!

---

