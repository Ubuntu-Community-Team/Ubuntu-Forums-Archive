---
title: "Compiz Fusion - Hangs on Shutdown"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by Clodaus on 2007-07-24
I tried searching a number of threads but couldn't find anything. Here's the problem:

I just upgraded to Gutsy - everything's working great, including compiz fusion. The only problem is, whenever I try to shut down, kill the process (compiz.real), or use "metacity --replace" (okay - any time I try to shut down compiz), it freezes my system and I'm forced to do a hard shutdown (use the power button).

I have all of the compiz plugins in the gutsy repository installed. Any suggestions?

---

### Post by magli on 2007-08-29
Did you ever solve this? I am having the same problem on Feisty.

---

### Post by gimmic on 2007-08-29
Edit: Nevermind.

Having the same problem as magli.

---

### Post by Davidux on 2007-08-31
I have feisty with compiz-fusion 0.5.2 and nvdia 100.14.11; same error as above

I found this:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/134809](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/134809)

and I tried to change /usr/bin/compiz
indirect=1 -> indirect=0

and now it works again!!!

---

### Post by RockerTux on 2008-02-22
I'm having a similar problem, but INDIRECT is already set to "no" (that is, 0) by default. When I click the shutdown button the system almost hangs - I can still move the mouse and get the hover-activated things, like alt. text on images in the browser or window titles on the taskbar.
I'm using the latest nvidia-driver and compiz packages as of 2008-02-22 12:31 UTC -3.

---

