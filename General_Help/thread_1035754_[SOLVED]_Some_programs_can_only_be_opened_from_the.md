---
title: "[SOLVED] Some programs can only be opened from the terminal!!"
date: 2009-01-10
forum: General Help
---

### Post by omaralqady on 2009-01-10
I have Ubuntu 8.10 and I have a problem with some programs such as the package manager, update manager, software sources, and other programs. The problem is that when I try to open them from their shortcuts from the System menu, I get a tab on the bottom panel that says "Starting Administrative Application", which disappears after a few seconds and nothing happens, but when I try to open these programs from the terminal they work fine ! So how can I fix this??

---

### Post by Taxman415a on 2009-01-10
I get a similar problem, and for me it seems to be that gksu (the app that handles escalating the priviledges needed for programs like those you mentioned) locks up after completing. So I open a terminal and do something like ```
ps -ef | grep synaptic
```
since synaptic was what I was trying to run and I see that gksu is still running.
then issue a ```
sudo kill 13254
```
but replace the number with the process id number you get from the output of the previous command. The one you want is in the first column.

This may not actually be your problem since when it happens for me it locks up the whole desktop and I have to log into another pseudo terminal to do the above, but it might work for you. Once I do it synaptic or whatever runs fine.

If this is your problem you could just grep for gksu directly in the first command. It's not really a great solution, but it works, and I haven't found it annoying enough to look for a real solution. I assumed it was because I installed this system as a pre-alpha and had some cruft lying around.

---

### Post by omaralqady on 2009-01-11
Thanks for replying, I'll try this and post later about the results. :)

---

### Post by omaralqady on 2009-01-11
Unfortunately this did not solve my problem, maybe it could be solved by reinstalling gksu, but I don't know how to do that, so I'll look it up, and see what happens and post back the results.

---

### Post by omaralqady on 2009-01-11
Well, I reinstalled gksu using:
```
sudo aptitude reinstall gksu
```

But this did not make any difference, the same problem still exists, so obviously it's not something with gksu, or maybe not it alone, but I am lost now. :(

Although I did notice that every time I tried to open any of these applications, a new sleeping instance of gksu appears in the System Monitor,
but even when I killed all these instances and tried to open any of these apps, the same problem happens, and a new sleeping instance of gksu appears in the system monitor. :confused:

Help, please :)

---

### Post by omaralqady on 2009-01-11
Issue solved. :o :D

When I searched for reinstall gksu, this page came up: [https://answers.launchpad.net/ubuntu/+question/34350]("https://answers.launchpad.net/ubuntu/+question/34350")

Apparently this guy had the same problem as we did, and someone told him to edit /etc/hosts in a way that is shown in the link, and that's it :D it works fine now.

What you have to do is open /etc/hosts in nano or gedit, and this is what I get:
```

127.0.0.1 localhost
127.0.1.1 3omar.HC  <-----

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

In the second line next to the arrow after "3omar" (computer name) is "HC" (my work group name), all you have to do is edit this line to:
```
127.0.1.1 3omar
```
Which means that you just delete for your work group name, and voila :D.

Thanks a lot Taxman415a, if it weren't for you, I wouldn't have thought about gksu and never found this :D I hope this works for you and anyone who ever has this annoying problem. :D

---

### Post by Taxman415a on 2009-01-11
Great, glad that worked for you. Unfortunately my /etc/hosts file was fine and reinstalling gksu didn't change anything, but I'll see if I can't hunt the issue down.

---

