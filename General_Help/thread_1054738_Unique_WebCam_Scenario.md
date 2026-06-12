---
title: "Unique WebCam Scenario"
date: 2009-01-30
forum: General Help
---

### Post by kmac on 2009-01-30
Here's the deal:

When I leave my dorm, I'm pretty sure one of my roommates is logging into my netbook and screwing with stuff. I'd like to catch them in the act and get it to stop. Obviously, a monitoring or security program would seem like an easy fix. However, I have a few issues with standard programs:

-Limited disk space on the netbook, so the video capture cannot be saved locally
-I have no access to the router, so a web-stream wouldn't work due to no access to port-forwarding
-I don't have anywhere else to set up an FTP server for remove saving.

I thought maybe a way to make Skype run in the background silently, automatically logged in to a new account, and have it automatically accept a video chat from another Skype client. I wouldn't be sure how to go about doing that, though. I guess any streaming program that does not require any special port-forwarding would be grand.

Any other suggestions are welcome :)

--Kyle

---

### Post by halovivek on 2009-01-30
Give your account password very strong. Dont share it to anyone.

---

### Post by kmac on 2009-01-30
Which is easy enough, yes. Each of my roommates had the password for a project we set up on my netbook.

I could easily change the password and put it to a stop, but I'd like to know *who* is doing it, and catch them.

--Kyle

---

### Post by sloggerkhan on 2009-01-30
Maybe you could just add a bit of script to your xsession that appends a username, date, and time to a logfile and maybe triggers your camera to take 2 or 3 stills whenever someone logs on.

---

### Post by kmac on 2009-01-30
> **sloggerkhan said:**
> Maybe you could just add a bit of script to your xsession that appends a username, date, and time to a logfile and maybe triggers your camera to take 2 or 3 stills whenever someone logs on.

So no ideas on streaming?

---

### Post by kmac on 2009-01-30
--*bump*--

---

### Post by kmac on 2009-01-30
...bump...

---

### Post by kmac on 2009-01-30
ok, i got skype to start a login from sh, and also automatically answers calls with video. so really, i just need a way for skype to run silent so it won't be seen and terminated by the intruder

---

### Post by Chris Musampa on 2009-01-30
'Motion' runs in the background, can record video or snapshots (no problem with slow old pc or limited space).  Its in the repos.
[http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome](http://www.lavrsen.dk/twiki/bin/view/Motion/WebHome)

---

### Post by kmac on 2009-02-07
--bump--

---

