---
title: "Time's not the same in gnome and gdm"
date: 2006-08-02
forum: Desktop Environments
---

### Post by rmjb on 2006-08-02
Hi, so I boot into Windows once in a while now and I notice that the time is always off so I reset it there. Then when I boot into Ubuntu it's off here. So I checked *Use _U_TC* in the Clock Preferences and the time displays correctly in my desktop, but on the login screen it's wrong.

And I just ran *date* from the command line and that's wrong too.
I have the correct timezone setup.

Any ideas?

- rmjb

---

### Post by endfx on 2006-08-02
You could try running the date command with the -s option to set it. See "man date" for more details

---

### Post by rmjb on 2006-08-02
I usually set it by synchronising to an Internet NTP server, both in Windows and Ubuntu, but something's screwy with the timezone settings...

- rmjb

---

### Post by ss0007 on 2006-08-02
Ya same thing over here  too ...
Correct time in Ubuntu and wrong time observed in BIOS and Windows OS. .


Any solutions ???

---

### Post by fabertawe on 2006-08-03
> **rmjb said:**
> Hi, so I boot into Windows once in a while now and I notice that the time is always off so I reset it there. Then when I boot into Ubuntu it's off here. So I checked *Use _U_TC* in the Clock Preferences and the time displays correctly in my desktop, but on the login screen it's wrong.

I've been getting exactly the same thing for about a week.

Paul

---

### Post by rmjb on 2006-08-03
Okay guys, after searching the forums with new terms ( specifically UTC ) I've tried something that works.

Firstly why it happens. Ubuntu thinks your PC clock is set to UTC time while Windows expects it to be the time at your timezone. That's why you can check "Use UTC" in the Gnome Clock Preferences and it works.

So now, to resolve this, to get Ubuntu to expect the clock is actually local time, edit *[COLOR="Blue"]/etc/defaults/rcS[/COLOR]* and look for *[COLOR="Blue"]UTC=yes[/COLOR]* and change that to *[COLOR="Blue"]UTC=no[/COLOR]*.

That's all there is to it, reboot and you're good (you might not have to reboot, but I'm sure you'll want to check it in Windows).

- rmjb

---

### Post by ss0007 on 2006-08-05
Hey , 
Thx for the reply .. 
i was about to post another fresh post !!!

---

### Post by fabertawe on 2006-08-07
> **rmjb said:**
> Okay guys, after searching the forums with new terms ( specifically UTC ) I've tried something that works.

It certainly does, nice one rmjb :D 

Paul

---

