---
title: "Forcing a time sync?"
date: 2009-04-26
forum: Desktop Environments
---

### Post by paulehoffman on 2009-04-26
I have a HardyHeron instance running as a virtual machine, and I have the system doing automatic time syncs. After I restart the machine, I want to force it to do a time sync. Opening "Date and Time" doesn't help, because there is no "Sync Now" button. How do I force it to go out to one of the sync servers and update?

---

### Post by djbushido on 2009-04-26
Should automatically update. Look at the command "hwclock" to get some down 'n dirty ways of setting the system clock.

---

### Post by paulehoffman on 2009-04-26
> **djbushido said:**
> Should automatically update. 

It does not, even after logging out and logging in again. I'm not sure what you mean by "should".

---

### Post by djbushido on 2009-04-27
What I mean by "should" automatically update, means that the system clock will set itself depending on what time zone it believes you are in. I'm not sure how often "should" is though.
If you want to do a time sync after a restart, look at the program anacron. You can create an event to use hwclock to set the time clock.
Finally, what is wrong with the system time?

---

### Post by paulehoffman on 2009-04-27
> **djbushido said:**
> What I mean by "should" automatically update, means that the system clock will set itself depending on what time zone it believes you are in. I'm not sure how often "should" is though.

This is not relevant to my question. When I start a system from a snapshot, the system doesn't know it has been asleep. I need to tell it that, or I need to tell it to resync just because I want it to.

> **djbushido said:**
> If you want to do a time sync after a restart, look at the program anacron. You can create an event to use hwclock to set the time clock.

Again, not relevant. anacron is meant for time-based events, and this is a triggered event.

QUOTE=djbushido;7158870]Finally, what is wrong with the system time?[/QUOTE]

It is in the past when I start up the snapshot.

---

### Post by djbushido on 2009-04-27
First of all, slow down and chill out. Getting antsy only makes things worse. Trust me. Been there, done that.
Okay anacron is NOT for time based events. CRON is. ANAcron, i.e. WITHOUT time (cronos=time) schedules events based on login, etc. Lets get that perfectly clear.

Second, you never posted that you were starting from a snapshot. I assumed that you shut down and restarted. Sorry.

Third, do you know if your system is using UTC? If you don't, post back this command - "cat /etc/default/rcS"

Finally, are you dual-booting windows? EDIT: No.

EDIT: You actually want to use cron. Every five minutes you can force a hardware clock update, as you don't log out and in for anacron. Look at doing a five minute event. But also, still post back the above command.

---

### Post by Namtabmai on 2009-04-27
Sorry for the command line but I'm unsure about how to do this through the gui

```
sudo ntpdate pool.ntp.org
```

You might need to install the ntpdate package if it's not already installed.

---

### Post by paulehoffman on 2009-04-27
> **djbushido said:**
> First of all, slow down and chill out. Getting antsy only makes things worse. Trust me. Been there, done that.
Okay anacron is NOT for time based events. CRON is. ANAcron, i.e. WITHOUT time (cronos=time) schedules events based on login, etc. Lets get that perfectly clear.

Slowed and chilled.

I looked at the man page for anacron, which starts off "anacron - runs commands periodically". I then read the first sentence of the description, " Anacron  can  be  used  to execute commands periodically, with a frequency specified in days." and stopped.

The next sentence makes clear what you said.

> Second, you never posted that you were starting from a snapshot. I assumed that you shut down and restarted. Sorry.

My fault: "restart" was ambiguous. I don't think there is a generic term for "started from a VM-style snapshot or from hibernation". Maybe "revive".

> EDIT: You actually want to use cron. Every five minutes you can force a hardware clock update, as you don't log out and in for anacron. Look at doing a five minute event. But also, still post back the above command.

Actually, no. Five minutes is too long for some of the tasks I want to do after un-sleeping.

As Namtabmai suggests, I will use 'sudo ntpdate'. I really want to say "act like you just woke up and do wakey-uppy kinds of things", or at least a button in Date and Time saying "resync now", but can live with ntpdate.

---

### Post by djbushido on 2009-04-28
Okay. Just for the record, you can use anacron to schedule events based on login, startup (which is what I thought you were doing) or something else. Anyway, I have no idea how to use ntp time. Sorry.

---

### Post by wewantutopia on 2010-01-20
So, is there a way to force a time sync to the server I've selected?  My system time is incorrect compared to the US official time web site by over 1 minute.  I have the time/date settings set to sync to a server but it doesn't seem to want to.

Is there a way to force Ubuntu to sync time with server on demand?

Running 9.10

---

### Post by djbushido on 2010-01-21
W00t! Revived post!
Anyway, are you saying that trying to use ntpdate is not working?
If so, then I know that at least I will not be able to help you. What you can try and do is force the computer using hwclock, but be warned that this is a very low-level program, and very easy to make a mistake.

---

### Post by wewantutopia on 2010-01-21
I'm not sure about ntpdate,  I mean system>administration>Time and Date.  Then click to make changes>password>select servers.  After having selected a server it never syncs in the future.  Right now it is > 1 minute off.  I tried ntpdate in terminal (not sure if that is the command for the gui) and I get:

 no servers can be used, exiting

Any Ideas?

Thanks!

---

### Post by wewantutopia on 2010-01-21
I just tried sudo ntpdate ntp-0.cso.uiuc.edu and got:

the NTP socket is in use, exiting

---

### Post by djbushido on 2010-01-21
Try it with the way described earlier in the thread.
And if that doesn't work, look up how to do hwclock. It's low-level, but it should work.

---

