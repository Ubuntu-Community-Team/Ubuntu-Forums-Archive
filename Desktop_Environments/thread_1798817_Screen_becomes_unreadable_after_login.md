---
title: "Screen becomes unreadable after login"
date: 2011-07-06
forum: Desktop Environments
---

### Post by lildoggie on 2011-07-06
Hi,

I've got a new installation of 11.04 server.  Everything was apparently working just fine, and then the system hung.  I rebooted, and everything looked good up to the login screen.  After I typed my password, the screen started looking good, and then got all fuzzy and messed up (nothing was readable).  The only way I could get anything back was to reboot.  (I *am* able to work via ssh at the command line, though).

As the graphics were fine before (using GDM), and since the GUI looks fine at the login screen, I know the system can do it...

I tried to find information on what might be going wrong, and haven't been able to find anything that fixes the issues.  I thought there might besomething in my config, so I tried logging into another account on the system that doesn't have any user-level configuration, and got the same result (the machine's main purpose is to be a mail and file server).

So it appears to me that something is happening to the graphics configuration after login when GDM loads.  

Any thoughts on what I need to change?

Thanks!

LD

---

### Post by mttrmk on 2011-07-07
You could try reconfiguring your xorg.conf or just check the x log file.

BTW did you install the proprietary drivers or the oss ones?

---

### Post by lildoggie on 2011-07-07
> **mttrmk said:**
> You could try reconfiguring your xorg.conf or just check the x log file.

BTW did you install the proprietary drivers or the oss ones?
Thanks for the reply.

First, no proprietary drivers installed - just the default (which worked fine for a while, and work fine for the login screen).

Strangely (?), I don't have an xorg.conf file -- I thought it should be configured by default, but there's no xorg.conf file in /etc/X11.

I looked at /var/log/Xorg.0.log, and it seemed to correctly identify my ATI Radeon card.  I didn't see anything else in that file that seemed to indicate any problem (but then again I don't know what I'm looking for).

Any additional thoughts?

Thanks again!

LD

---

### Post by mttrmk on 2011-07-08
Hmm...
That's strange . Try creating your own xorg.conf or generate one.

Pus try lxdm to see if it works.If it does then its safe to say that its a gdm related problem.;)

---

### Post by lildoggie on 2011-07-08
> **mttrmk said:**
> Hmm...
That's strange . Try creating your own xorg.conf or generate one.

Pus try lxdm to see if it works.If it does then its safe to say that its a gdm related problem.;)Thanks for the reply.

How would I generate one?  I tried doing a reconfigure, expecting to need to answer some questions, and it just threw me back to the command prompt without doing anything.

What is the command to install/activate lxdm?  

Thanks again!

---

### Post by lildoggie on 2011-07-08
OK, I was able to log in using the "Classic (no effects)" option, and things are fine...   

This is all good, since I don't think I need any effects.  However, I'm just curious what could be causing the problems for the other options...  

Any ideas?

Thanks!

---

### Post by mttrmk on 2011-07-10
> OK, I was able to log in using the "Classic (no effects)" option, and things are fine...

This is all good, since I don't think I need any effects. However, I'm just curious what could be causing the problems for the other options...

My guess is that the drivers couldn't handle the load properly and x crashed.
But I guess it doesn't matter anymore.
Glad you are able to solve your problem.
:)

---

### Post by mttrmk on 2011-07-10
> OK, I was able to log in using the "Classic (no effects)" option, and things are fine...

This is all good, since I don't think I need any effects. However, I'm just curious what could be causing the problems for the other options...

My guess is that the drivers couldn't handle the load properly and x crashed.
But I guess it doesn't matter anymore.
Anyway its good that you were able to solve your problem.

Oh yeah
> What is the command to install/activate lxdm

Its a simple apt-get install lxdm and away.:)

---

