---
title: "How do I become root again...I'm unrooted"
date: 2008-12-05
forum: General Help
---

### Post by ozguitarplayer on 2008-12-05
somehow I've unrooted myself and my password doesn't help...when it gets to the bottom line listed below it's not possible to enter any information at the cursor

nigel@Master:~$ dpkg-reconfigure hhdtemp
/usr/sbin/dpkg-reconfigure must be run as root
nigel@Master:~$ asas2
bash: asas2: command not found
nigel@Master:~$ sudo dpkg-reconfigure hhdtenp
[sudo] password for nigel:


I think this happened after I ran the command..
dpkg-reconfigure hddtemp
...in an attempt to get GKrellM to read hhd temps....

how do I become root again
help...

---

### Post by taurus on 2008-12-05
Did you type in your own password when you ran that command?

```
sudo dpkg-reconfigure hhdtenp
```
Remember, you won't see any echo back when you type in your password so just type it and then hit Enter.

---

### Post by ozguitarplayer on 2008-12-05
thanks taurus..

what you see is what happened, after it said...reconfigure must be run as root i got...
nigel@Master:~$ 
...so not being any smarter I typed asas2 (password)

then I tried it as ...sudo...

and I got the last line but was not able to type anything...I mean nothing happened at all when I tried to type


nigel@Master:~$ dpkg-reconfigure hhdtemp
/usr/sbin/dpkg-reconfigure must be run as root
nigel@Master:~$ asas2
bash: asas2: command not found
nigel@Master:~$ sudo dpkg-reconfigure hhdtenp
[sudo] password for nigel:


...I seem to remember when I set up the...dpkg-reconfigure hhdtemp it went through a few questions and one was I wouldn't be admin anylonger and others could have access....

and what is an echo back?

have to go to work now,,,bugger...back later....I'd prefer to be learning this stuff even if it is really frustration at first

---

### Post by taurus on 2008-12-05
Run

```
sudo dpkg-reconfigure hhdtenp
```
and when you see this line

```
[sudo] password for nigel:
```
That's where you type in your password, asas2.  Of course, the cursor doesn't move when you type it or you won't see any *** on the screen.  That's what echo means.

---

### Post by ozguitarplayer on 2008-12-06
thanks again tuarus, I guess this means that i'm not unrooted and I've learned about echo back, but whats the purpose of not seeing it, why not see the ****

---

