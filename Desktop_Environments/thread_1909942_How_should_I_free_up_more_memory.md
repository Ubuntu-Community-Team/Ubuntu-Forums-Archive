---
title: "How should I free up more memory?"
date: 2012-01-16
forum: Desktop Environments
---

### Post by sakishrist on 2012-01-16
Hello,

I would like your help with the following scenario: I need to make my Ubuntu use as less ram as possible so that I can run a game server on it.

What I thought would be a good starting point was to install LXDE along with Gnome 3 on my Ubuntu 11.10 (I have removed unity).

The thing is that I believe the memory usage is still too high. The system uses ~450MB of ram without any application running. So I was wondering whether there are any services that are not needed for LXDE (maybe some kind of services that are only useful for Gnome) or whether there is another way to make ubuntu use even less memory.

Thanks in advance,
Sakis

---

### Post by Cheesemill on 2012-01-16
What are you using to measure your RAM usage? Alot of tools include the amount of cached RAM in their output which is automatically freed if you need it.

What is the output of:
```
free -m
```

On my servers I don't have a GUI installed at all, I find that is the best way to reduce memory usage :)

---

### Post by sakishrist on 2012-01-16
I use gnome-system-monitor (although I am in lxde). The output I get is:```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          3931       2292       1638          0        322       1413
-/+ buffers/cache:        557       3374
Swap:         7628          5       7623
```I really like the idea of not having a GUI running when the server app will be active but I need one to run a client as well. I know it is not the best idea but I have a shortage of PCs so it is the only option (hehe).

---

### Post by Cheesemill on 2012-01-16
You're right about your memory usage.  It's a common mistake to look at the total used rather than the +/- buffers/cache used amount but you didn't fall for that one. I just wanted to check you were looking at the correct value.

Although with >3GB free you should be OK.

What server are you going to be running?

---

### Post by sakishrist on 2012-01-17
A minecraft one.

---

