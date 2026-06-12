---
title: "It's british summer time"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-15
Select time zone > London > It's GMT

NO IT ISN'T it's British summer time! You are one hour too fast! Yes you can sync with internet servers to fix it if they weren't all down at the moment, but i shouldn't have to. 

Why does it do everything wrong?

---

### Post by desdinova on 2005-06-15
It doesn't do anything wrong - it ask for it  at install - you must have selected the wrong timezone

Easily fixed

System -> Administration -> Time and Date ->

---

### Post by Dave_is_sexy on 2005-06-15
I did not select the wrong time zone, and i can see the time zone in settngs.

It does not acknowledge that the clocks change twice a year - i can see it is set to London now. It is wrong ---> add to bugs

---

### Post by desdinova on 2005-06-15
Did you set the clock back right - mine doesn't show any wrong behavior?

---

### Post by Dave_is_sexy on 2005-06-15
What do you mean did i set the clock back? The clocks went back ages ago - this is 4 or 5 days old.... and totally fucked already, and still completely useless

---

### Post by desdinova on 2005-06-15
Can you please mind your language, please?

---

### Post by desdinova on 2005-06-15
My ubuntu machine is showing the correct time - are you dual booting it?

My suggestion is to manually correct the time and it will stay corrected

---

### Post by Dave_is_sexy on 2005-06-15
yeah I could'nt survive without a working OS so i'll be dual booting with a linux distro for at least a year. 

The ubuntu clock is set to copy the hardware clock and adjust to london timezone. The hardware clock is GMT. GMT is set from london (greenwich). but it's not GMT here at this time of year.

I'm convinced it is a bug. I have changed the clock, but it's still a bug. I would tell them if the report system wasn't such a hassle

---

### Post by desdinova on 2005-06-15
As you're dual booting, its likely windows is altering the clock

[https://www.redhat.com/archives/fedora-list/2004-September/msg03882.html](https://www.redhat.com/archives/fedora-list/2004-September/msg03882.html)

---

### Post by Dave_is_sexy on 2005-06-15
but the windows clock is right

---

### Post by desdinova on 2005-06-15
Then enable ntp and let it correct for Windows inability to play nice then - probably the easiest fix - or tell Linux your timezone is UTC - its a byproduct of the dual boot and assumptions made by Windows and Linux

---

### Post by Dave_is_sexy on 2005-06-15
oh i tried that, it said the server was down

---

### Post by desdinova on 2005-06-15
In the Date/Time applet there's a choice of around 20 different servers you could use

---

### Post by TravisNewman on 2005-06-15
it IS most likely the windows clock throwing you off. Did you read that link?

I know the windows clock is right, but it's throwing it off because windows defaults to using local time on the hardware clock, and linux defaults to using UTC on the hardware clock.

---

### Post by Dave_is_sexy on 2005-06-15
well windows is wrong now, cos ubuntu has gone and written it's wrong time back to the hardware clock. Arr

---

### Post by xmastree on 2005-06-15
[QUOTE=Dave_is_sexy]well windows is wrong now, cos ubuntu has gone and written it's wrong time back to the hardware clock. Arr[/QUOTE]
Why not just set the hardware clock to BST, and edit whichever file it is in ubuntu (can't remember just now, it's somewhere in /etc Try greping for UTC in that directory) to reflect the fact that the HWC is not set to UTC.

That's what I'm doing. My hardware clock is set to local (gmt + 8 ) and both my windows and ubuntu system times are correct.



Had a look at lunchtime.

The file is:
/etc/default/rcS

Mine has this:

# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no

My Hardware clock is local time, Windows shows the correct time, as does ubuntu.

---

### Post by btdown on 2005-06-16
If I were you, I would just move to a different timezone.](*,)

---

