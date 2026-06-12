---
title: "Screenlets = Ram Hog"
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by phynix on 2008-03-06
Maybe I am being overly dramatic, but I notice that screenlets use so much ram. Am I just being dumb? It there a way to optimize them so they don't take so much. I have tried gdesklets but they just don't have the same look. Any suggestions?

---

### Post by fracturedmorals on 2008-03-06
I haven't noticed them being too much of a ram hog.....have you tried the bzr version?

---

### Post by Whise on 2008-03-06
maybe he is using some really old screenlets that dont follow the memory leak fix

---

### Post by phynix on 2008-03-06
I will have to try the bzr version. Let me qualify hogging memory it takes 20mb per screenlet. I will try the bzr version. Does anyone have a link?

---

### Post by SomeGuyDude on 2008-03-06
I activate one screenlet and suddenly python's using a buttload of RAM. Don't know what it is.

---

### Post by plun on 2008-03-06
> **phynix said:**
> I will have to try the bzr version. Let me qualify hogging memory it takes 20mb per screenlet. I will try the bzr version. Does anyone have a link?

Latest version from Getdeb

[http://www.getdeb.net/release.php?id=2128](http://www.getdeb.net/release.php?id=2128)

First start after install from the terminal and you also will see if something fails

```
screenlets-manager
```

:)

---

### Post by FuturePilot on 2008-03-06
I don't know why but Python seems to be a RAM hungry language.

---

### Post by fracturedmorals on 2008-03-06
> **FuturePilot said:**
> I don't know why but Python seems to be a RAM hungry language.

Python isn't necessarily RAM hungry. I use it for rapid prototyping in embedded systems, and it seems to be okay for protocols.

The interpreter has about a 2mb footprint, which isn't really much for a full-fledged desktop or laptop system.....:???:

Edit:
Oh by the way;
in order to install the BZR version of screenlets, uninstall your current version, then 
```
bzr co http://bazaar.launchpad.net/~screenlets-dev/screenlets/trunk
```

To install just cd to the directory you just checked out and type:
```
python ./setup.py install
```

If you want to stay up-to-date cd to the directory and do a:
```
bzr update
```

---

### Post by phynix on 2008-03-06
Wow thanks for the info. I will certainly try that out and get back to you. If you guys have any other cool programs like that let me know. I like desktop customization

---

### Post by phynix on 2008-03-06
update installation was painless. Ram went from 493 to 555 with manager and two screenles open. Am I just complaining?

---

### Post by fracturedmorals on 2008-03-07
Do you know if it is cache or application memory?
I know that linux's memory management model is different from what a lot of people are used to due to the fact that it tends to actually make use of any free ram you have as cache. When a new application is opened, this RAM is easily given up for that application memory.

Also...what screenlets do you have open and how much memory do you have?
I could just be totally wrong in thinking that perhaps I'm not seeing the effects of the RAM-hungry screenlets just because I have 2gb of memory.....

---

### Post by phynix on 2008-03-07
I check it with System Monitor if that helps. I only have two open and it takes up 100mb. If this is normal I will just have to deal with it. I was just making sure.

---

### Post by buddylee on 2008-03-10
I've been seeing leaks for quite some time, in particular with the CPUMeter screenlet.  I suspect it has to do with this screenlet using a higher refresh rate compared to most and as such more calls to the screenlets modules.

The initial amount of memory should not concern people as a leak, since this is not how a leak works.  What I experience is that on a system with 8G of memory, I'll see this particular screenlet eat up around 1-2G of it after a couple days.  That's a leak.

Thanks for the previous post about latest binaries.  Going to try that now.

---

### Post by phynix on 2008-03-10
Ya i noticed that too about the CPUMeter.

---

### Post by phynix on 2008-03-12
Just for future reference. If I wanted to uninstall them what would I do.

---

