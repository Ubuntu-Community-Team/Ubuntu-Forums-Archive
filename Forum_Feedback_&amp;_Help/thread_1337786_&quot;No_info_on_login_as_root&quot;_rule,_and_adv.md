---
title: "&quot;No info on login as root&quot; rule, and advice on reporting a related possible bug."
date: 2009-11-25
forum: Forum Feedback &amp; Help
---

### Post by jwbrase on 2009-11-25
In doing some tinkering, I accidentally discovered an unconventional way to log in as root without first having set a root password (or so it seems). 

I'm not how serious it is, or if it really is in fact a bug, so I don't want to waste the time of the people at launchpad by reporting it before I know exactly how serious it is.

My first instinct would be to bounce it off the forums to see what more knowledgeable people think about it, but given the "don't provide info on how to do a root login" rule, I can't really do that.

Any advice on how to figure out if it's actually a bug, and how serious it is?

On the one hand, it doesn't allow anybody who isn't already a sudoer access to root, so it doesn't seem too serious. On the other hand, it does seem to go against the way that Ubuntu generally treats root (I.e. as an account that one is not supposed to be accessed directly).

So I'm not sure if it's a bug or a known, "yeah, you can do that, but why would you?" issue.

---

### Post by cariboo on 2009-11-25
Are you sure you weren't just using sudo before it timed out? If i remember correctly it is set for about 15 minutes.

---

### Post by lisati on 2009-11-25
> **cariboo907 said:**
> Are you sure you weren't just using sudo before it timed out? If i remember correctly it is set for about 15 minutes.

+1

Sometimes when "log on as root" comes up in discussions, I point people to [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jwbrase on 2009-11-25
Well, it did involve an invocation of sudo, but, after said invocation, a GNOME session logged in as root existed.

---

### Post by bodhi.zazen on 2009-11-26
I would advise you report it as a bug on launchpad.

			 			[Improving Ubuntu: A Beginners Guide to Filing Bug Reports]("http://ubuntuforums.org/showthread.php?t=1011078")

---

### Post by koenn on 2009-11-26
> **jwbrase said:**
> Well, it did involve an invocation of sudo, but, after said invocation, a GNOME session logged in as root existed.

> **bodhi.zazen said:**
> I would advise you report it as a bug on launchpad.
if it's just a case of running panels as root, i'm not sure it is to be considered a bug.

---

### Post by bapoumba on 2009-11-27
@ jwbrase: if you want to check first if it is a real bug, maybe you could PM Bodhi, our root master, with the procedure ?
Bodhi, I hope this is fine with you ;)

---

### Post by bodhi.zazen on 2009-11-27
> **bapoumba said:**
> @ jwbrase: if you want to check first if it is a real bug, maybe you could PM Bodhi, our root master, with the procedure ?
Bodhi, I hope this is fine with you ;)

Good idea, I would not mine reviewing the information.

---

### Post by sisco311 on 2009-11-27
> **jwbrase said:**
> Well, it did involve an invocation of sudo, but, after said invocation, a GNOME session logged in as root existed.


By default, users in the admin group are allowed to run any command as any user from any hosts. Yes, as an admin user you can start an X or GNOME session as root, that's not a BUG.

You need at least one user on the system with full admin rights. As the system administrator is your job to manage the other accounts and restrict their privileges.

---

