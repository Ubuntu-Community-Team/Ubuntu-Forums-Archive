---
title: "how do I install inetd?"
date: 2006-04-25
forum: Desktop Environments
---

### Post by _Chris_ on 2006-04-25
Greetings, 

I'm a newbie at Linux, and need some help installing inetd.  I'm installing VMware Server which requires inetd or xinetd, and towards the end of the installation script, I'm alerted that inetd is not installed.  It asks if you would like to specify a location to search for it manually.  I've tried installing with 'apt-get install inetd', but apparently did not work.  Any pointers would be greatly appreciated.

Thanks,
Chris

---

### Post by qamelian on 2006-04-25
try:

sudo apt-get install xinetd

---

### Post by amunimanghi on 2006-04-25
[QUOTE=qamelian]try:

sudo apt-get install xinetd[/QUOTE]


i agree. that should work

also look in synaptic.
system => administration => synaptic package manager

search for xinetd or inetd

---

### Post by _Chris_ on 2006-04-25
Many thanks.  I will give it a try.  This community is solid!

---

### Post by PhilKarras on 2008-04-15
I tried sudo apt-get install openbsd-inetd & it installed the needed "openbsd-inetd" so I thank you for the form on how to install something missing.
I'm still having problems with Telnet & have posted that question at:

[http://ubuntuforums.org/showthread.php?p=4717039](http://ubuntuforums.org/showthread.php?p=4717039)

if anyone can help I'd appreciate it.

---

