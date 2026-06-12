---
title: "tracker error is in a closed loop"
date: 2009-05-12
forum: General Help
---

### Post by edhawk2 on 2009-05-12
I have a Dell Latitude laptop running Jaunty.  I booted it up this morning and got an error message saying "Tracker.  There was an error while performing indexing: Index corrupt."  I'm given three choices to click on:

Reindex all contents
Cancel 
OK


No matter which button I click on the applet just reappears and reappears and reappears.  Right now, to do any work, I just ignore it, I'm ignoring it, but it is always present now.  

I'm not a programmer.  
How do I resolve this?
Should I be reporting this as a bug?

---

### Post by LoneWolfJack on 2009-05-12
open a terminal window and type

```
killall trackerd
```

if this doesn't help, enter

```
top
```

while you have the notification window and post the result

---

### Post by edhawk2 on 2009-05-12
the "killall trackerd" works during each work session but I have to use it every time I boot.  

Is the tracker necessary?

Am I losing anything by killing it?

How do I permantly rectify this?

Is it a bug?

---

### Post by LoneWolfJack on 2009-05-13
go to system->preferences->sessions and untick tracker and tracker applet.

AFAIK, tracker is an indexing daemon that speeds up file searches, so if you rarely use the search function, it is more of an annoyance than it is a help.

I had performance issues when tracker was enabled because it was constantly eating up at least 30% of my CPU cycles so I deactivated it back when I was using gutsy. One of the first things I did after installing ibex some months back was disabling tracker as well. never had any problems related to that. so if it annoys you, just disable it,

your problem certainly sounds like a bug so you might want to file a report.

---

### Post by moonport on 2009-05-13
I have the same problem, **edhawk2**, since I have upgraded both computers with ***Jaunty***.
The only way is **LoneWolfJack's**: untick tracker.

---

### Post by edhawk2 on 2009-05-13
Okeee Doakeee ---

I think we got it.  However, note, with Jaunty, go to System then Preferences > Startup Applications then unclick tracker and tracker applet.

This seems to solve the problem.

Thanks for the help
Ed

---

### Post by Cygnia on 2009-05-13
Can I break in here with a question about what purpose tracker and trackerd serve in the system in the first place? Does deactivating it mean that we can't use file tagging and smart folders to sort files? What other consequence, if any, is there to not using it?

---

### Post by ojmc on 2009-05-14
official fix .....[http://www.ubuntu.com/getubuntu/releasenotes/904#Tracker%20index%20corruption](http://www.ubuntu.com/getubuntu/releasenotes/904#Tracker%20index%20corruption)

---

