---
title: "Fan control &amp; heat on dell M1530"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by drunkenllama on 2008-04-28
got my brand new 1530 last week, installed Ubuntu, love it, except...
I've noticed, the laptop runs CONSIDERABLY hotter on Ubuntu than it does on Vista.
I am kindda new to the linux scene. Am I missing some applets to turn on the fans?
if so can some one give me a good walk through? please.....

This is the last thing i have to fix before i completely forgo windows.

cheers

---

### Post by neptho on 2008-04-29
Did you see if i8k to see if it's overheating?

Open a terminal and run:

```
lsmod | grep i8k
```

If it says 'i8k', it is loaded.  If not, edit your /etc/modules (gksudo vi /etc/modules), and add 'i8k force=1' to it, then save, and exit, then run 'sudo /usr/sbin/update-initramfs -u', and reboot to load i8k.

You may wish to install gkrellm-i8k (synaptic package manager), and use that to control/monitor your fans.  There's a plethora of information on how to setup gkrellm.

---

### Post by timseal on 2008-06-02
funny, I don't have an either an i8k module or a gkrellm-i8k package.  I'm running Hardy (amd64) on a 1420N.

---

### Post by sc00ter on 2008-06-04
Has anyone confirmed whether this works for the XPS M1530 running Hardy?

---

### Post by adult swim on 2008-06-05
the last time i was looking into this i dont think the i8k plugin was working on 64 architectures

---

### Post by Clockswork on 2008-06-19
I installed gkrellm but the manually setting doesnt seem to work :S I click on the tiny fans and the animations start but the fans in my computer doesnt start .. :(

---

### Post by Clockswork on 2008-10-20
The fans kick in much faster if you upgrade your BIOS to A09!

Here is a HOWTO I wrote on how to upgrade your Dell bios in Ubuntu:
[http://www.clockswork.org/?p=3](http://www.clockswork.org/?p=3)

---

