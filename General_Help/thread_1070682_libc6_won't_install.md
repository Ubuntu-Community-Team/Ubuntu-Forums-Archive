---
title: "libc6 won't install"
date: 2009-02-15
forum: General Help
---

### Post by linuksamiko on 2009-02-15
I just installed a recent update for Hardy Heron (64 bit). Everything went well except of libc6 (2.7-10ubuntu4). It just won't stop installing. It is stuck at this point:

```

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

I had a look at dpkg to see if something is happening there during the installation but top tells me this:
```

6716 root      20   0 16580 9.8m  980 S    0  1.0   0:00.18 dpkg

```

Nothing is happening and it won't stop. What can I do about it? Killing the process won't let me do anything with apt-get nor with dpkg becaus they both complain about an unfinished installation.

---

### Post by linuksamiko on 2009-02-15
After a little more investigation I seam to have the problem. It's not libc6 it seams to be **ldconfig** which causes the problem. So now I need somebody to help me out here how do I get my ldconfig to work again?

I found a similar problem here: [link to post]("http://ubuntuforums.org/showthread.php?t=1038569&highlight=%2522ldconfig+deferred+processing+taking+place%2522+stuck")

But there was no real solution. Does anybody know how to handle ldconfig or what I need to do to get it working again?
Since ldconfig seams to have something to do with libraries I assume that the libc6 update changed something that ldconfig didn't like.

---

### Post by linuksamiko on 2009-02-17
Hej everyone,

I found the answere to my problem. Fust in case somebody stumbles upon this and searches for help I like to post how I fixed it (thanks to the help of lummox on debian's IRC):

The problem: ldconfig get's stuck somewhere. This also means that the install process can't be finished because after the installation process (using aptitude, apt-get or dpkg) ldconfig is beeing lunched. The only way to stop ldconfig is by killing the process. But that also means that the installation can't be finished.
Apt-get always asks for "dpkg --configure -a" but once you type it in dpkg configures all the packages and wants to finish with ldconfig (but that won't work). 

You can also try using ldconfig by itself which won't stop neither:
```

sudo ldconfig

```

The solution (that worked for me):
First of all you have to figure out why ldconfig won't finish. You get no errors so you can't search for the reasons. So first of all we gone record all the out puts of ldconfig into one file:

```

sudo strace -o output.txt /sbin/ldconfig

```

It will stop again somewhere so you have to kill the process. But we got the output.txt to see where it got stuck.
Open it and take a look at the bottom. If you got the same problem like me you will see something like that (the lib is mostlikely different so you might have to change this for your case):

```

open("/usr/lib/libglibmm-2.4.so.1", O_RDONLY) = ? ERESTARTSYS (To be restarted)
--- SIGINT (Interrupt) @ 0 (0) ---
+++ killed by SIGINT +++

```

The important thing is the third line from the bottom it says open("PATH-TO-FILE", .....
In my case there was a missing link which pointed from /usr/lib/libglibmm-2.4.so.1 to /usr/lib/libglibmm-2.4.so.1.0.25 so I created the link:

```

sudo ln -s /usr/lib/libglibmm-2.4.so.1.0.25 /usr/lib/libglibmm-2.4.so.1

```

And the problem was fixed.
I hope this is helpful for somebody who might has the same problem.

---

