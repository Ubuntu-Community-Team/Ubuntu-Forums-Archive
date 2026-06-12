---
title: "How to Network Sound in Ubuntu?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Nick Wilson on 2006-09-18
Hi everyone, untill my very recent switch to Ubuntu, i was using KDE, and to solve this particular need I would have tried the "networked sound" option. (I have never tried it, but im guessing it does what it says right?).

The situation is that i have a desktop in the living room, and a couple upstairs -- though i spend most of my time in the kitchen on the laptop (nearest the coffee grinder...)

What i'd like to do is move my nice harmon kardon speakers from upstairs where they rarely get used, to the downstairs desktop, **but play music on the laptop** and have it come out on the desktop.

with me?

Reason being that the speakers would quickly get ruined if i kept them in the kitchen, and i'd like to have full control over the sound from where i happen to be.

I can't find anything about networked sound under gnome, so here I am.

Sugesstoins most welcome!

thx

---

### Post by Poeffie on 2006-09-18
Have you tried SSHing from your desktop to the laptop, and playing the files in terminal mode? There are some nice programs for that and I'm 100% sure it works.

---

### Post by _mrv on 2006-09-18
One possibility is also to install Gnump3d into your desktop in the livingroom and use web browser from other desktops to control it:

[http://www.gnu.org/software/gnump3d/](http://www.gnu.org/software/gnump3d/)

 _mrv

---

### Post by lamego on 2006-09-18
Just go into synaptic and search for "streaming server", there are several options.

---

### Post by Nick Wilson on 2006-09-18
Thanks for the ideas everyone. Just to clarify, i'd like ot use rythmbox/amarok, or whatever on the laptop, playing files either on the laptop or in a shared directory elesewhere but have the sound networked -- ie, for the sound to be handled by one machine, but the playing, and file storage handled by another. 

unless i misunderstand, i dont htink the solutions above would be right for that?

thanks again.

---

### Post by CatKiller on 2006-09-18
If you have your speakers connected to your desktop, and then use SSH to connect from your laptop:

**nick@laptop:~$ssh -X nick@desktop**

then any programs that you run on the desktop through your SSH connection from the laptop will spit sound out of the desktop speakers. No configuration or anything, it's just the way it works.

---

### Post by Nick Wilson on 2006-09-20
yep, i get the idea of using ssh, but as far as im aware, im not going to have much luck running amarok or any other graphical player through a shell connection right?

What i really want to know is if networked sound can be acheived under gnome?

---

### Post by arkangel on 2006-09-20
this is why he is using -X in his command ,  with -X you will have graphic app

---

### Post by odinfromvalhalla on 2006-09-20
you can install [http://pulseaudio.org/](http://pulseaudio.org/)

i'm sure you will find a tutorial somewhere.

---

### Post by beerfan on 2006-09-21
If you don't mind going to the command line, you can use the following to open rhythmbox, for example, on your laptop from your desktop (just as catkiller suggested).

```
nick@laptop:~$ ssh -Xf nick@desktop rhythmbox
```

You'll notice in the titlebar of the rhythmbox window that it will say "(on desktop)" or whatever the hostname is.

If you plan to do this all the time and want to make a shortcut, you can use the command above and you would always be prompted for a password. You can get around that by creating an authentication key with no password. This could be very risky though, depending on what your environment is like so do some reading before thinking about doing it. Here is a page which explains how.

[http://www.raoul.shacknet.nu/2005/11/10/ssh-with-keys/](http://www.raoul.shacknet.nu/2005/11/10/ssh-with-keys/)

---

### Post by CatKiller on 2006-09-21
> **Nick Wilson said:**
> yep, i get the idea of using ssh, but as far as im aware, im not going to have much luck running amarok or any other graphical player through a shell connection right?

As arkangel and beerfan have pointed out, the -X option enables X11 forwarding. **man ssh** will tell you more about SSH, although there's a *huge* amount of information in that particular man page, so don't be scared that you won't understand much of it.

As an example, to prove to you that you can do all sorts of things with SSH, if I'm using my computer my other half can use another computer on the network, run **ssh -X m@weatherwax**, and then type **firefox** and **mozilla-thunderbird** to check her email and browse the Internet with her own bookmarks. Then, if she's looking at MySpace or something, the sound will come out of my speakers. I haven't yet found a way to make this not happen, to be honest.

You'll need the **openssh-server** package installed on your desktop computer. I believe the **openssh-client** is installed by default, so the laptop shouldn't need any configuration.

---

### Post by MikePiff on 2007-07-18
This just doesn't work for me.  I have done everything I should have, enabled network sound in System Settings, tried ssh -X and also xdmcp but though I can see videos and watch audio playing, no sound whatsoever comes from my laptop speaker. (But it is OK playing locally.)

---

