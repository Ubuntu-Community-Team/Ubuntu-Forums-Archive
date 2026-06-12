---
title: "Beagle"
date: 2006-06-29
forum: Desktop Environments
---

### Post by underwater on 2006-06-29
Does beagle actually do anything?  it doesn't seem like it indexes hardly at all, and it  definitely does not index on the fly.  If I create a file like

touch anewfile


and then I beagle search for anewfile I will get zero results

is inotify not in the kernel or something?  I thought it was in all current kernels?
The beagled is running so what is the deal?  how can I get the awesome on the fly search results like in the video that I see posted on the Beagle's homepage?

Also, does beagle search directories that start with a . ?  The websites simply says it indexes "everything" which is pretty vague...   It doesn't feel like it indexes folders starting with a . but maybe I'm just doing it wrong somehow?  I don't know...

---

### Post by DarkDancer on 2006-06-29
I can't figure out how to get beagle to start, so I couldn't help...sorry.

---

### Post by underwater on 2006-06-29
[QUOTE=underwater]Does beagle actually do anything?  it doesn't seem like it indexes hardly at all, and it  definitely does not index on the fly.  If I create a file like

touch anewfile


and then I beagle search for anewfile I will get zero results

is inotify not in the kernel or something?  I thought it was in all current kernels?
The beagled is running so what is the deal?  how can I get the awesome on the fly search results like in the video that I see posted on the Beagle's homepage?

Also, does beagle search directories that start with a . ?  The websites simply says it indexes "everything" which is pretty vague...   It doesn't feel like it indexes folders starting with a . but maybe I'm just doing it wrong somehow?  I don't know...[/QUOTE]


I killed and restarted beagled and its friends and now it seems to be working much better.  Still don't know about the folders starting with . though

---

