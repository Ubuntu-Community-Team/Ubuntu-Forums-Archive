---
title: "Kubuntu Breezy?"
date: 2005-09-10
forum: Desktop Environments
---

### Post by GreatBunzinni on 2005-09-10
Where can I find the list of the packages that are shipped with Kubuntu Breezy preview? Does it uses GCC 4.0?

Is it possible to upgrade Hoary to Breezy from some apt source?

---

### Post by DarkT on 2005-09-10
1) [http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/) for all breezy packages, No idea where you can find the list of packages that are on the Cd though.
 
2)It uses gcc-4.0 but the kernel is compiled with gcc-3.4 so you may need both.
 
3) You can although whether it will work is another matter. You can try opening up you /etc/apt/sources.list and changing all the hoary entries to breezy (so [http://archive.ubuntu.com/somethingorother/](http://archive.ubuntu.com/somethingorother/) hoary would become [http://archive.ubuntu.com/somethingorother/](http://archive.ubuntu.com/somethingorother/) breezy) and you can comment out the reference to the hoary cd with a # and also comment out things like backports if you're using them. Now you should be able ot upgrade wit hthe commands...
 
apt-get update
apt-get dist-upgrade
 
The latter will take a long time and I've broken my system twice doing it this way, in the end I just downloaded the CD and clean installed, it was quicker and easier in the long run.

---

### Post by GreatBunzinni on 2005-09-10
Thanks for the reply, DarkT. 

So, how is breezy holding up?

---

### Post by exile on 2005-09-10
I'm not a ubuntu developer so I can't talk about Breezy from a deep level, but I have been a ubuntu user for quite a while now.

I tested the latest beta release of Breezy earlier this week on an old dog of a machine (Celeron 333 with 512Mb of RAM) and I was really, really impressed by it's stability and speed. I tried the first beta when it came out and couldn't get it working after the install.

I am looking forward to the final release of breezy. Props to the devs - good work guys and girls.

---

### Post by DarkT on 2005-09-10
[QUOTE=GreatBunzinni]Thanks for the reply, DarkT. 

So, how is breezy holding up?[/QUOTE]
You're welcome.
For me it's been surprisingly stable and there also seems to be a slight speed improvement so all's good apart from the odd little problem (well, it's a beta) and there being no sound from my audigy sound card :( Seems to be a problem for others aswell so hopefully it's being worked on.

---

### Post by bubblegum on 2005-09-11
[QUOTE=DarkT]You're welcome.
For me it's been surprisingly stable and there also seems to be a slight speed improvement so all's good apart from the odd little problem (well, it's a beta) and there being no sound from my audigy sound card :( Seems to be a problem for others aswell so hopefully it's being worked on.[/QUOTE]


Works fine for me. Sound was garbled with a lot of static noise, had to disable artsd launch and use the xine engine with the alsa backend in amarok.

---

