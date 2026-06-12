---
title: "Switching from 11.10's Unity back to GNOME - how?"
date: 2012-03-11
forum: Desktop Environments
---

### Post by Santillana on 2012-03-11
I am aware that I have a lot of learning about Ubuntu Linux before me, but I thought I would take this one final shortcut to start myself off on the right foot first of all.

I changed from 8.10 to 11.10 (with a lot of help) and in the bargain I got Unity. I much prefer GNOME. I would like to get back to GNOME (besides, plenty of course material that I have on my hands is meant to be worked through using GNOME). When I go to Ubuntu Software Center and try to download GNOME, the message is "This link must be opened with an application". :confused:

A few pointers to the right way to go about this would be much appreciated, or generally pointers to good material to read up on as far as how to go about software downloading in 11.10. Synaptic &c. exists, but the best way I will get down to learning about this, Synaptic and what not, is going with the course program and that is structured around GNOME.

---

### Post by vikjon0 on 2012-03-11
for gnome2
sudo apt-get install gnome-session-fallback 

for gnome3
sudo apt-get install gnome-shell

you can install both and select on login.

---

### Post by Santillana on 2012-03-11
Very nice - thank you!

The message back from the first command is

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-session-fallback is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have messed with this before and it seems I installed GNOME 2 without noticing.

Another problem is that I log in without my user name and password so I am not sure where the choice at login would turn up. At least not in the cog wheel symbol top right.

---

### Post by vikjon0 on 2012-03-11
well...selct logout then and you will be logged out. Then login..

---

### Post by Santillana on 2012-03-11
> **vikjon0 said:**
> well...selct logout then and you will be logged out. Then login..

Aha! Right you are. The cog wheel on the login box. Simple and beautiful. Thank you so much!

---

