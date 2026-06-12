---
title: "Breezy startup now shows text-only login screen"
date: 2006-04-24
forum: Desktop Environments
---

### Post by chriscrutch on 2006-04-24
Let me start with this:  I'm a Linux newbie.  I've only been running Ubuntu for a few weeks now, and I'm still trying to just get everything working correctly.

To that end, I was messing around with some stuff on my dual-boot (Ubuntu and XP) machine earlier today, trying to get my sound card to completely work.  I guess I screwed something up.  It used to be, that when I booted into Linux with GRUB, Ubuntu would start up GNOME for me and drop me at a desktop with no intervention (I had turned on auto login, since I'm the only user on this machine).  

Now, GNOME no longer starts.  I get a text-only login screen.  Ok, that's not a huge problem.  I login, get the command line.  From there, I can type "startx" and bring up what I'm used to seeing.  But that adds two extra steps that I didn't have to do before.

How do I get things back to the way they used to be?  Be gentle with the flaming, remember, I'm a noob.  :-)

--chriscrutch

---

### Post by aysiu on 2006-04-24
Can you try typing this where you would ordinarily type *startx*? ```
sudo /etc/init.d/gdm restart
```

---

### Post by chriscrutch on 2006-04-24
It didn't seem to do anything.  After typing it in and pressing enter, I was asked for the password, which I dutifully supplied, and then, nothing.  No output whatsoever.  Simply another command prompt.

--chriscrutch

---

### Post by aysiu on 2006-04-24
[QUOTE=chriscrutch]It didn't seem to do anything.  After typing it in and pressing enter, I was asked for the password, which I dutifully supplied, and then, nothing.  No output whatsoever.  Simply another command prompt.

--chriscrutch[/QUOTE] That's a bad sign. Does the same thing happen if you type ```
sudo apt-get update
```?

---

### Post by chriscrutch on 2006-04-24
No, I actually get output with that one, both in a Terminal inside GNOME and in the command-line environment that I have before running startx.

Before each of my repositories when I run "apt-get update" is either "IGN" or "HIT".  All seems to go smoothly.

---

### Post by aysiu on 2006-04-25
Okay. It's not a bad sign then. Maybe try this? ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```

---

### Post by kh4nh on 2006-04-25
[QUOTE=aysiu]Okay. It's not a bad sign then. Maybe try this? ```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm restart
```[/QUOTE]

Why did you suggest him to install ubuntu-desktop. I think he was asking how to have X start automatically.

"From there, I can type "startx" and bring up what I'm used to seeing. But that adds two extra steps that I didn't have to do before"

---

### Post by aysiu on 2006-04-25
[QUOTE=kh4nh]Why did you suggest him to install ubuntu-desktop. I think he was asking how to have X start automatically.[/QUOTE] Installing the *ubuntu-desktop* metapackage ensures you have everything you need for a GUI desktop experience. The fact that *sudo /etc/init.d/gdm restart* did nothing means something important is missing. That "something important" could just be GDM, but *ubuntu-desktop* makes sure you have all your bases covered.

---

### Post by kh4nh on 2006-04-25
[QUOTE=aysiu]Installing the *ubuntu-desktop* metapackage ensures you have everything you need for a GUI desktop experience. The fact that *sudo /etc/init.d/gdm restart* did nothing means something important is missing. That "something important" could just be GDM, but *ubuntu-desktop* makes sure you have all your bases covered.[/QUOTE]

I think he already has ubuntu-desktop installed. He should open up /etc/inittab and do some editing there. If he sees something like id:3:initdefault: he should change it to id:5:initdefault:

---

### Post by aysiu on 2006-04-25
[QUOTE=kh4nh]I think he already has ubuntu-desktop installed.[/QUOTE] How do you know?

---

### Post by kh4nh on 2006-04-25
[QUOTE=aysiu]How do you know?[/QUOTE]

"Now, GNOME no longer starts. I get a text-only login screen. Ok, that's not a huge problem. I login, get the command line. From there, I can type "startx" and bring up what I'm used to seeing. But that adds two extra steps that I didn't have to do before."

---

### Post by aysiu on 2006-04-25
[QUOTE=kh4nh]"Now, GNOME no longer starts. I get a text-only login screen. Ok, that's not a huge problem. I login, get the command line. From there, I can type "startx" and bring up what I'm used to seeing. But that adds two extra steps that I didn't have to do before."[/QUOTE] That doesn't mean *ubuntu-desktop* is installed. Having Gnome installed is not the same as having the *ubuntu-desktop* metapackage installed.

---

### Post by chriscrutch on 2006-04-25
Success!  Thanks so much for your help and your incredibly quick responses.

Just so I can learn, "gdm restart" is like the Linux (or GNOME) equivalent of restarting Windows after configuration change, correct?

As an aside, aysiu, how are you at hardware problems?  I still have a sound card that only half works....  :-)

Thanks again.

--chriscrutch

P.S. I'm almost positive that I did not have ubuntu-desktop installed before the problem.  I remember seeing that in Synaptic and noticing that it was unchecked.  I did, however, have ubuntu-minimal installed, and that didn't seem to be there after the problem occurred.  Maybe something I had been doing messed up that package, and therefore GNOME?

---

### Post by aysiu on 2006-04-25
[QUOTE=chriscrutch]Success!  Thanks so much for your help and your incredibly quick responses.[/quote] Great. Glad it worked out.

> 
Just so I can learn, "gdm restart" is like the Linux (or GNOME) equivalent of restarting Windows after configuration change, correct? GDM is the Gnome Display Manager that manages the login screen. Without it, you need to type *startx* to start Gnome. There's no real Windows equivalent for this.

> 
As an aside, aysiu, how are you at hardware problems?  I still have a sound card that only half works....  :-) I actually stink at hardware problems, especially sound, as my sound has always worked, and I've never had to tinker with it.

---

