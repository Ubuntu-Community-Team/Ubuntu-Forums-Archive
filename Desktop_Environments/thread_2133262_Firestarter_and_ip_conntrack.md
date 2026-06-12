---
title: "Firestarter and ip_conntrack"
date: 2013-04-07
forum: Desktop Environments
---

### Post by hiflyer on 2013-04-07
I am using Ubuntu 12.10 upgrade up to date on a dell D630
I have firestarter installed (over many versions) and it used to show the active connection but no longer does.
If I 
sudo firestarter 

and then hit the active connections, in the terminal window I get the following error repeatedly until I stop the active connection display.

Error reading /proc/net/ip_conntrack: No such file or directory

I look in /proc/net and there is no such file. Suggestions on the web state that I should 
I check that conntrack is installed and appearently should be, to be able to do the modprobe command to get the file. so I do

sudo apt-get install conntrack

which install just fine

then I do

sudo modprobe ip_conntrack
and it does not complain but the is no file ip_conntrack file created.:confused:

What am I doing wrong or what is missing.
I can do a 
sudo conntrack -L 

and get a list of connections.

tia

---

### Post by Frogs Hair on 2013-04-07
Synaptic states in the description that Firestarter is no longer being developed and is "missing critical features", but they did update the user manual last year available at the website .

---

