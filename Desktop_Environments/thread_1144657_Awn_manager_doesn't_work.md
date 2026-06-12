---
title: "Awn manager doesn't work"
date: 2009-04-30
forum: Desktop Environments
---

### Post by toprasad on 2009-04-30
Hi Guys!

I have installed AWn manager on my linux distribution verion (8.10). When i click on System->Preferences->Awn manager nothing showing on bottom of screen. It worked yesterday night. Now all icons disappering.
:(

when i run avant-window-navigator command in terminal showing following error:

"Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager."

Any help? 

Waiting for replies..

-Prasad

---

### Post by overdrank on 2009-04-30
Hi and as the error stated are you using compiz?
System, Preference, appearance, Then the visual effects tab. :)

---

### Post by amplexus on 2009-05-03
Thanks Overdrank, but that isn't going to work. Lots of us are having the same problem, and when you try to enable visual effects, you get an error message saying 'Desktop Effects could not be enabled". No Compiz or AWN possible for many of us in Jaunty, and no one seems to have posted a workable solution yet.

---

### Post by overdrank on 2009-05-03
> **amplexus said:**
> Thanks Overdrank, but that isn't going to work. Lots of us are having the same problem, and when you try to enable visual effects, you get an error message saying 'Desktop Effects could not be enabled". No Compiz or AWN possible for many of us in Jaunty, and no one seems to have posted a workable solution yet.

What is the model of the graphics card? If it is intel then you may look at the link in my signature.

---

### Post by jarame on 2009-10-18
> **amplexus said:**
> Thanks Overdrank, but that isn't going to work. Lots of us are having the same problem, and when you try to enable visual effects, you get an error message saying 'Desktop Effects could not be enabled". No Compiz or AWN possible for many of us in Jaunty, and no one seems to have posted a workable solution yet.


I actually have a fix for this issue, and it should work. It worked for me and I had this saaaaame issue.

Try this:

[https://help.ubuntu.com/community/CairoDock](https://help.ubuntu.com/community/CairoDock)

follow the instructions for installation then start Cairo Dock. It'll be under Applications>System Tools> Cairo-Dock. When you start it it'll appear with a crappy looking dock at the bottom encased in a black rectangle. And a pop-up window will tell you about this issue and offer to enable Desktop Effects. Click on yes. And AWN-Manager will pop up along with Cairo.

You'll have to play around with the right clicking to close out of them one at a time, but now you have two docks installed as well as desktop effects. :] Let me know if this works.

---

