---
title: "How do I *stay* logged in on Ubuntuforums?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Luke771 on 2006-06-29
It happens all the time: Every time I want to post something on Ubuntuforums I have to log in again. No difference between using my real IP or a Tor server.

I can't stay logged in more than a couple of minutes at the time: I must write my messages on Gedit and then copy/paste to the editor. I added ubuntuforums.org to the white list of sites that can set long-life cookies (Preferences/Privacy/Cookies/Exceptions) but that didn't change anything: If writing a post takes me more than some minutes, I'll have to log in again in order to post it.

Same thing happens with several other Apache powered log-in websites, no matter what OS I'm running (different Linux distros, WinXP pro, LiveCDs etc) so I guess that the problem may actually be my ISP; I have a very lousy fiber connection, 10MB/sec nominal and behind NAT, I have no access to the NAT box and I never get actual speeds over 1 MB/s (that's on the good days).

But on the other hand, it only happens on Apache servers,so it may be an Apache bug or a result of the combination Apache server/lousy ISP.

I tried to e-mail  my ISP about that but I haven't gotten any answers so far.

In the meantime, I'm posting this, hoping for some advice if someone knows any tricks to stay logged in, also as a start point for "me-too posts" so we can see wheter or not the problem is ISP related.

---

### Post by Kouya on 2006-06-30
in the main page when you log in ..click "remember me"..

---

### Post by Luke771 on 2006-07-25
That wouldn't work because I have Firefox configured to delete cookies each time I close it.
The problem is not that I want to stay logged in over multiple sessions, it's  that the system kicks me off after a while.
I write a post and when I hit "submit" I get the "not logged in" message, so I log in again but than my post is gone.
I learned to back it up before trying to send it but that's not the point.
I thought it could be an IP problem; I use Tor and that makes me switch IP address every now and then, so I tried logging in with my "real" IP adress, but that did not solve the limited-time-login problem.
I also tried checking the remember-me checkbox, no result.
Must say that since I log in without Tor and checking "remember me" I've not been "kicked off" as often, but it still happens.

---

### Post by horace on 2006-07-25
I used to have the same problem, but a combination of ticking 'remember me' and specifically allowing ubuntuforums in firefox cookie settings seems to have fixed it (and I also have firefox set to delete cookies on close, but am still remembered next day if I close down but don't actively log out).
hth.

---

### Post by metalheart on 2006-07-25
Is your systems date set correctly?
Are cookies from ubuntuforums.org visible in Edit -> Preferences -> Cookies -> View Cookies window?

---

### Post by Slicedbread on 2006-07-25
Maybe setting the permissions to read for your account and giving root write permissions, usually works in windows.

---

