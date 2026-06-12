---
title: "How to check for website updates....."
date: 2008-12-22
forum: General Help
---

### Post by yousillygoose on 2008-12-22
Hey hey.  I have some pretty basic bash knowledge.  I have the ability to write a script that checks a website and can alert me when something changes on it (using lynx).  My problem is that the website I am trying to check uses https.  Lynx doesn't support https!

I was wondering if any of you know of a way I can check an https site with a command line browser.  The browser must allow you to save sessions like lynx does (meaning that if i close the program and open it again I will remain logged in).  Thanks

ysG

---

### Post by eBoxNet on 2008-12-22
Check this and you may be able to add ssl functionality to lynx

[http://www.subir.com/lynx/patches.html](http://www.subir.com/lynx/patches.html)

---

### Post by yousillygoose on 2008-12-22
I have seen that but the download links for the patches are dead...

---

### Post by eBoxNet on 2008-12-22
sorry to hear that.
try this one :[http://my.brandeis.edu/bboard/q-and-a-fetch-msg?msg_id=0001ac](http://my.brandeis.edu/bboard/q-and-a-fetch-msg?msg_id=0001ac)

---

### Post by yousillygoose on 2008-12-22
All of the links there are listed as unstable...

---

### Post by eBoxNet on 2008-12-22
yes..i think thats kind of normal.don't know :confused:

---

### Post by yousillygoose on 2008-12-22
there has been 1 more recent release than the version in the repos.  I'm attempting to configure it but it's kicking my butt giving me a nice error about curses headers.  I'm really unsure if this will even help anything.  Anywhere it speaks of SSL support the threads were 5 years ago and outdated links are present :(

---

### Post by yousillygoose on 2008-12-22
I need "ncurses" and I'm a fool for not figuring it out sooner, I really hope this supports SSL

---

### Post by yousillygoose on 2008-12-22
well i'm a fool.  The updated lynx does not support SSL either!  What do I do?!?!?!?!?

---

### Post by dcstar on 2008-12-22
> **yousillygoose said:**
> Hey hey.  I have some pretty basic bash knowledge.  I have the ability to write a script that checks a website and can alert me when something changes on it (using lynx).  My problem is that the website I am trying to check uses https.  Lynx doesn't support https!

I was wondering if any of you know of a way I can check an https site with a command line browser.  The browser must allow you to save sessions like lynx does (meaning that if i close the program and open it again I will remain logged in).  Thanks

ysG

Just use wget and compare file timestamps.

---

### Post by yousillygoose on 2008-12-22
Hmm, it is a webpage that requires me to login...wget would not be able to access that.  Basically, I need to login to a secure site that posts substitute teacher jobs.  These jobs are picked up QUICK!  I want to write this script so that it notifies me by EMAIL and Sound once a new job is posted (by checking automatically every 10 or so seconds).  I have to be able to login either by built in macro (like lynx has) or by cookies saving the session.  Lynx is by far the best command line browser but it is flawed in this sense.  If there is a way to do this with wget DO TELL!!!!

Thanks
ysG

---

### Post by flyingbrass on 2008-12-22
Maybe curl can do what you need.  [http://linux.about.com/od/commands/l/blcmdl1_curl.htm](http://linux.about.com/od/commands/l/blcmdl1_curl.htm)

---

### Post by yousillygoose on 2008-12-22
I'm looking into curl.  I have never used it before and it is a bit over my head.  Do you have any knowledge of how to do what I'm looking to do with it?

---

### Post by flyingbrass on 2008-12-22
We're in the same boat.  I found out about curl some time ago when I wanted to do essentially the same thing you're attempting.  It seemed like a good tool for the task. Skimming its man page is as far as I got.

---

