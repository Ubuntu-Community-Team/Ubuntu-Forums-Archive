---
title: "Live CD and automatic login"
date: 2009-09-28
forum: Desktop Environments
---

### Post by drkfce on 2009-09-28
I am at wit's end here.  For the past 4 days, I have been obsessed about a problem that I am having producing a live CD for a company that I work for.

This all started when my boss wanted this live CD to be able to automatically log in.  No problem, right?  Just go to "/etc/gdm/gdm.conf" and edit the "AutomatedLogin" to equal "ubuntu" and "AutomatedLoginEnabled" to "true", correct?  And, for good measure, configure "TimedLoginEnabled" to "false".

Incidentally, this seems to work for all the machines that I have.  Everyone that I plop the CD into, it automatically logs in.  However, the problem is that the ONE place where it doesn't work, EVERY SINGLE TIME is my boss's laptop.  For some reason, instead of logging in automatically, it counts down from 10 seconds, meaning that it somehow decided to use the TimedLogin, despite the fact that I EXPLICITLY disabled it.

Why does this change on a live cd, a device specifically designed to not change its configuration between systems, except in cases of hardware, and I sincerely doubt that the hardware has anything to do with the log in screen.

Another thing that confuses me is that when I go through "/var/log/syslog" on my boss's laptop and another machine, both of them say that "TimedLoginEnable" and "AutomaticLoginEnable" are false.  Later on, it says that "Automatic login" was successful in both files as well, despite one actually NOT automatically logging in.

Does anyone have any suggestions?  I hope this is the correct forum for this, as I thought this had to do more with gdm than hardware.

This may help.  Pertinant parts of my gdm.conf file and syslog files:

-------------------------gdm.conf-------------------------
# Automatic login, if true the first attached screen will automatically logged
# in as user as set with AutomaticLogin key.
AutomaticLoginEnable=true
AutomaticLogin=ubuntu

#TimedLogin, useful for kiosks.  Log in a certain user after a certain amout
# of time.
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=1
-------------------------gdm.conf-------------------------


+++++++++++++++++++++++++syslog+++++++++++++++++++++++++++
ubuntu gdm [4475]: DEBUG: Attempting to parse key string: daemon/AutomaticLogin=
ubuntu gdm [4475]: DEBUG: Attempting to parse key string: daemon/TimedLogin=
ubuntu gdm [4475]: DEBUG: Attempting to parse key string: daemon/AutomaticLoginEnable=false
ubuntu gdm [4475]: DEBUG: Attempting to parse key string: daemon/TimedLoginEnable=false
...
ubuntu gdm [4475]: DEBUG: setup_automatic_session: Automatic login: ubuntu
...
ubuntu gdm [4475]: DEBUG: setup_automatic_session: Automatic login successful
+++++++++++++++++++++++++syslog+++++++++++++++++++++++++++

---

### Post by undecim on 2009-09-29
The Ubuntu live cds (as far as I remember) all log in automatically when you first log in, and only do a timed login if you log out after that. What version of the live CD are you using?

EDIT: Does the syslog say anything about X crashing? If X crashes after a successful automatic login, it will probably revert back to a timed login.

---

