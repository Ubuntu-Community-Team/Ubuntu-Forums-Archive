---
title: "A Problem with Package Manager"
date: 2009-01-19
forum: General Help
---

### Post by Eliad on 2009-01-19
I have Ubuntu 8.10 on my computer. I tried to upgrade it using unsupported (backports) packages. It was a silly thing to do for me, a begginer. Well, the resualt was dramatic. Synaptic crashed and  when I try to run it, there is this message:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


What do I do now?

**P.S.**: I had already tried 'sudo dpkg --configure -a'. But it didn't work. Here is the message had gotten:

> dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted


---

### Post by Titan8990 on 2009-01-19
As a novice Linux user I am going to teach you something very important. Unlike Windows where error messages are a bunch of useless crap that leads you in a wild goose chase, Linux error messages are almost always useful and should be examined closely.

So lets examine your error message:

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
```


This error message tells us to manually run 'dpkg --configure -a' and that is exactly what we are going to do. It **will** fix the problem.


Go to Application -> Accessories -> Terminal

Type the follow and hit enter:

sudo dpkg --configure -a


Good luck and welcome to Linux!

---

### Post by taurus on 2009-01-19
Close synaptic.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by snowpine on 2009-01-19
Enter the following into the terminal:

```
sudo dpkg --configure -a
```

---

### Post by Eliad on 2009-01-19
Thank you folks, especially taurus. It worked.

---

### Post by narcisgarcia on 2009-01-29
1. Updated repositories today with "update-manager"

2. Upgraded packages with the same desktop tool.

3. Update manager warned that not all the packages were well-installed

4. When I run "sudo aptitude search '~i'gstreamer" in a terminal, it returns me the message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Synaptic says the same.

5. When I run "sudo dpkg --configure -a" in a terminal, returns:
Processing triggers for menu ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

6. If I retry the command "sudo dpkg --configure -a", returns:
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

7. Having read [these bug comments]("https://bugs.launchpad.net/ubuntu/intrepid/+source/dpkg/+bug/262451"), I run:
```

sudo dpkg --remove gxine
sudo dpkg --configure -a
sudo apt-get install gxine

```

AND ALL WORKS WELL AGAIN.
Note: I don't know if gxine was the problem, or I only touched a side effect.

---

### Post by mocha on 2009-01-31
narcisgarcia,

Thanks!  This fixed my latest update mishaps.

---

### Post by jackmetal on 2009-01-31
Gotta LOVE this community.  Before I posted a new thread, I decided to check the forum with my error message after this most recent update and found this Thread.  

THANK-YOU narcisgarcia

That solved mine also.

It's strange though.  I did this same update on 4 of my other systems (1 desktop, 2 laptops and my samsung q1ultra UMPC), and ALL went through fine, with no problems.  Then on this desktop (my Media Center), got bit.  :-)

Thanks again.

---

