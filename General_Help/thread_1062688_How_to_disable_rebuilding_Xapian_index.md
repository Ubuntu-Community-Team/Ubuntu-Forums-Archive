---
title: "How to disable rebuilding Xapian index?"
date: 2009-02-07
forum: General Help
---

### Post by Julita on 2009-02-07
Hello! My PC everyday hangs terribly, and the command "top" in terminal shows that the process "update-apt-xapi" is loading my RAM and CPU on 100%. Running "sudo update-apt-xapian-index" shows the percentage of completion of rebuilding Xapian Index, and those minutes are rather ... disturbing, especially when I am typing my BA paper :D Google did not help much...Since there is no such package, i can not remove it. Please, can somebody tell me what should I do? I have not experienced it in the previous *buntu versions, only in Intrepid...

---

### Post by compat on 2009-02-16
the process is update-apt-xapian-index and in low resource systems it will eat all available ram and then start swapping, leaving the system almost in a freeze state.

do a
[PHP]sudo apt-get autoremove --purge apt-xapian-index
sudo apt-get autoremove --purge[/PHP]
this will remove apt-xapian-index and then python-debian and python-xapian

i don't know if it has secondary effects, but it will avoid this anoying process (in low resource systems) to start again

---

### Post by Julita on 2009-02-16
compat, thank you very much!!!!! When I am at home, I'll do it and find out about side effects! :)

---

### Post by Sonsum on 2009-03-02
I did this on my old laptop running 8.10, no negative results so far...

Thanks for saving me tons of resources!

---

### Post by compat on 2009-03-06
hello, i've seen that it is installed when installing other apps, at least in jaunty, i ended renaming the process, 
moved update-apt-xapian-index process to update-apt-xapian-index.disabled in /usr/sbin/ folder

---

### Post by fcormier on 2009-04-10
Here is what I did to disable it:
```
sudo chmod 644 /etc/cron.weekly/apt-xapian-index
```
It makes the file not executable.

---

### Post by Tanker Bob on 2009-06-04
Purging apt-xapian-index caused the quick search feature in Synaptic to become inoperative in Jaunty. Changing the weekly script to non-executable proved the better approach with no side effect so far.

---

### Post by likemindead on 2010-01-07
My old PIII laptop thanks you for this!

^____^

---

### Post by Eiríkr on 2010-05-15
I was bitten by this bug as well, and after some digging around, I found the thread on Launchpad discussing the official fix that will be incorporated into Ubuntu at some point.  Read [post=9304431]this post[/post] I wrote in another thread for an explanation of how to implement the official fix in your system now, and a breakdown of what it does.  

Cheers,

--Eiríkr

---

### Post by cdubet on 2010-11-14
hello if you do not wish to disable it but to make it consume less cpu, you should do like me:
edit **/etc/cron.weekly/apt-xapian-index** (for example with vi or gedit)
replace the line 
*nice $IONICE -c3 $CMD --quiet*
by
**nice -n 19 $IONICE -c3 $CMD --update --quiet**

what it does:
a) run it  with the lowest system priority
b)  update the db and not built it again -> faster

---

### Post by d3v1150m471c on 2011-04-01
if you just wait a few minutes it'll stop. but meh, can't expect linux users to have patience when they can poke at something with a sharp stick :)

---

### Post by Hackie2 on 2011-04-13
> **d3v1150m471c said:**
> if you just wait a few minutes it'll stop. but meh, can't expect linux users to have patience when they can poke at something with a sharp stick :)

If u run out of battery on your slow netbook because of that i think it is more than just not having patience...

---

### Post by kennedyvelez on 2011-08-05
> **compat said:**
> the process is update-apt-xapian-index and in low resource systems it will eat all available ram and then start swapping, leaving the system almost in a freeze state.

do a
[PHP]sudo apt-get autoremove --purge apt-xapian-index
sudo apt-get autoremove --purge[/PHP]this will remove apt-xapian-index and then python-debian and python-xapian

i don't know if it has secondary effects, but it will avoid this anoying process (in low resource systems) to start again


This is sweet! Every MB is counted. Thanks... Spaces, processes and all. Saved.

---

