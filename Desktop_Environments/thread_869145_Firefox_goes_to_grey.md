---
title: "Firefox goes to grey"
date: 2008-07-24
forum: Desktop Environments
---

### Post by ebursley on 2008-07-24
I have a problem with Firefox 3 on my Ubuntu 8.04 installation. I'm able to start up and use Firefox 3 under most circumstances, but if one instance of Firefox is busy with a form for example, or has a Java applet start, I am unable to start a 2nd instance of Firefox.  When this happens, the first instance turns to a gray screen, and doesn't return. Typically I have to kill the Firefox task, and restart Firefox in order to do anything else.
Does anyone else have a problem like this?

---

### Post by GreenN00b on 2008-07-24
When an application gets gray it means it is not responding. This could happen because the application does a lot of processing at that time.

I had a gray firefox in some situations too but it usually recovers after a coupe of seconds.

---

### Post by ebursley on 2008-07-24
I'm aware that its not responding. My problem is that it happens far too often, but only when I'm using a web form, or internet application in one Firefox browser. Typically I can a new tab and not have a problem, its only when I try to open a new firefox browser that this happen.
Also this only happens on my Ubuntu  / Linux systems, not my Windows systems. So I'm thinking this is a configuration problem.

---

### Post by ebursley on 2008-07-24
Also if one firefox browser is retrieving data from an Internet server, and I try to open a new browser window, this will also cause the open Firefox window to turn gray and hang.

---

### Post by Orlsend on 2008-07-24
I had the same thing with Java, I usually wait for like 30 secs and its usually back...

You can still use FF when its grey (darken)

---

### Post by GreenN00b on 2008-07-24
I experimented a little with applets and I managed to obtain a gray window when closing a tab that was loading a java applet. It never recovered ...

---

### Post by LindaLou on 2008-07-24
I have been experiencing the same situation for the past 2 days, prior to that FF 3 was functioning normal.  The fade to transparent gray is random, with that I mean, viewing a google search page, Ubuntu forum or most recently, just trying to sign out of my gmail which was the only tab open.  I have experimented - working with only one tab open (pain!!) and then having 2 tabs, then 3.  It doesn't seem to matter.  Yes, the web page does come back, but an explanation of why FF 3 is suspended would be greatly appreciated:)

---

### Post by ebursley on 2008-07-25
So it sounds like it not just me then. Has anyone found a bug related to this on Launchpad?  If not, I can file one.

---

### Post by LindaLou on 2008-07-25
I havent seen anything on that site/forum as of yet.  I forgot to mention that my the screen goes transparent gray, I am unable to do anything and it takes numerous attempts for force an X out of FF 3.  I also work on a Linux system called Fenix - it's 100% Brasiliann and I have not experienced this gray screen.

---

### Post by ebursley on 2008-07-25
I've opened a question on Launchpad.
40265

---

### Post by LindaLou on 2008-07-31
Did you receive any follow up to you Launchpad questions?  I'm still experiencing the same transparent gray, and require force to quit rather than wait for FF3 to return to normal.

---

### Post by ebursley on 2008-07-31
Actually yes, the problem was found and verified to be Google Toolbar.  By uninstalling it, my gray screen problems went away.

---

### Post by LindaLou on 2008-07-31
That's strange because, as I mentioned previously, I use a different Linux system at the office (Fenix) also with FF and have never experienced the transparent gray screen.  Granted, Fenix came preinstalled with FF 2.0 and has yet to be updated to FF3.
I'm wondering if it is a CPU problem with my lap top that makes this transparency issue occur? Any thoughts on this?

---

