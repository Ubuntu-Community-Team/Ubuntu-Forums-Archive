---
title: "Gnome Software eating up lots of RAM"
date: 2017-05-02
forum: Desktop Environments
---

### Post by sp40140 on 2017-05-02
I have clean install of 17.04 64 bit Ubuntu (unity). Running on C2Q cpu and 8 gigs ram. Kernel version is 4.10.0-20.
I recently notice that "gnome-software" process is eating up around 500MB (give or take a few) ram. It is surprising to me. 
I looked around and found some bug reports about high memory usage but nothing really concrete.

I use this machine as all purpose server and have VMs running so I do need the ram otherwise I would not worry about it.

Also, I have TWO compiz processes running! is this normal? And one is using 500MB RAM. I understand that compiz is bit heavy. But two processes? 

So my question:
Is this RAM usage normal? if not, how do I fix this?
Should two compiz processes be running or just one?

---

### Post by Autodave on 2017-05-02
That doesn't sound excessively high to me, especially since Compiz is running. Unfortunately, Compiz uses a lot of RAM. Is there a reason why you need Compiz or can it be removed?

I am not real familiar with what you are running since I use Xubuntu. I am wondering whether you would be a lot better off running Xubuntu since you stated the machine is only used as a server?

---

### Post by sp40140 on 2017-05-02
Well, I like Unity and would like it keep it. As I use it as server as well as desktop. It's my jack-of-all-trades. I am under the impression that compiz is needed to run Unity. And I understand compiz eating up half a gig as window manager. But gnome-software surprises me.

---

### Post by sp40140 on 2017-05-02
I just re-boot the machine and now gnome-software is using 55MB! 
May be there is a memory leak somewhere.

---

### Post by QIII on 2017-05-02
Hello!

High memory usage and memory leaks are different things.  I don't think it is a leak.

Next time your memory usage gets high enough that it worries you, check to see how much memory is in use and check cached memory.  My suspicion is that you will find most of your used memory in cache.

---

### Post by deadflowr on 2017-05-03
Not sure about genetic software, but gnome software is set to run at startup.
Basically because the app has so much function going into it that a cold startup by the user would take a long time to actually start, the devs decided that having it running would cut that startup time, dramatically.

In ole releases such as 16.04 you could simply open Startup Applications, locate gnome-software, and uncheck it, and that was that.
However in newer versions they decided to remove that ability.
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1662749]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1662749")

In newer versions that is hidden, so you would need to edit the gnome-software-service.desktop manually.
Simplest edit would be to just change the file NoDisplay= setting from true to false.
Setting that will then make the entry appear in Startup Applications, where you can then disable it.

(Note that the .desktop file may be in two different places.
Either in the users home folder at ~/.config/autostart/gnome-software-service.desktop
or in the system folder at /etc/xdg/autostart/gnome-software-service.desktop
If in the /etc/xdg/autostart folder you will need to run as root/sudo to edit the file)

As with anything there are pros and cons, depending on your preferences.
Pro to turning it off would be if you never use, or hardly ever use, gnome software or it's updater feature, then there is no reason to have it running all the time.
Con would be even though you might never use it, or rarely use it, in those rare times when you do need to use it, the load time to start it would be a lot longer then otherwise should be.

But if you're someone who prefers to update using apt-get or prefers package management through other means like synaptic, then by all means turn off gnome-software.

---

### Post by vasa1 on 2017-05-03
> **deadflowr said:**
> Not sure about genetic software, but gnome software is set to run at startup.
Basically because the app has so much function going into it that a cold startup by the user would take....
+1. I'll fix the thread title.

---

### Post by sp40140 on 2017-05-03
Ok. I see that genome-software is useful.
My question still stands: is 500MB RAM usage normal?

---

### Post by deadflowr on 2017-05-03
> **sp40140 said:**
> Ok. I see that genome-software is useful.
My question still stands: is 500MB RAM usage normal?

Sure.
As with any internet accessible program, over time the cached info can grow larger and larger.
If you feel that is unacceptable, here is a bug report on the same subject:
[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616332]("https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616332")

---

### Post by sp40140 on 2017-05-03
@Robot Pirate Ghost.
Ok. I was just bit worried / curious. And wanted to know if there is something I can do .. some sort of setting / configuration to avoid this much RAM use by it.
It's not that it is unacceptable. It's just that I noticed it and thought this can't be normal.
Sure, it does bother me a bit but not hurting.
BTW, I did see that bug report before I posted here, but there is nothing in there to solve it. And I thought someone here might have some ideas.
So, if there is nothing to be done, then we can leave this thread. Not sure if I can mark it "solved".

---

