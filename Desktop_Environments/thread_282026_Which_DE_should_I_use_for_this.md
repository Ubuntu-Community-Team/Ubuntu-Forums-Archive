---
title: "Which DE should I use for this?"
date: 2006-10-22
forum: Desktop Environments
---

### Post by DarkN00b on 2006-10-22
I have a question relating to my mother's computer. Recently my mother's WinME install went bye-bye and she wants me to reinstall for her. The problem is that my WinME disk is missing so I installed Gnome-Ubuntu on the machine and it runs (but slowly).

She says she only wants to play games; think Gnome games in the default install and arcade-type games. I want to give her as many of these games as I can, but Gnome just runs too slowly on this machine. So, I need a light weight desktop environment, and the kinds of games she likes. Any suggestions?

Specs of mom's computer:

Intel Cyrix 266Mhz
128Mb memory
ATI Rage II AGP video (4Mb ram) - currently not working
2 HDs - 15GB & 40 GB

And to top it off, she won't let me upgrade anything. :?

---

### Post by aysiu on 2006-10-22
I'd set her up with IceWM or Fluxbox.

I prefer IceWM myself. More details [here](http://ubuntuforums.org/showthread.php?t=263710).

---

### Post by DarkN00b on 2006-10-22
OK, I installed IceWM and related files (Gnome support/etc.

My question now is: How do I set Ubuntu to boot into IceWM instead of Gnome? Or am I not understanding what IceWM does?

I rebooted and Ubuntu just started Gnome as usual.

---

### Post by dhalgren on 2006-10-22
> **DarkN00b said:**
> OK, I installed IceWM and related files (Gnome support/etc.

My question now is: How do I set Ubuntu to boot into IceWM instead of Gnome? Or am I not understanding what IceWM does?

I rebooted and Ubuntu just started Gnome as usual.

log out of session using the quit button and from the log in screen choose <<change session>> A dialogue should pop up asking which session to change to . Choose the new session and then log in again. As a last step just before it actually logs in, another pop up will ask if you want this new sessioin to be your default session. Click whatever message says <<yes>> (I can't remember exactly what it says, sorry)

The next time it boots it will go into whatever you have chosen as your default session.

If the log in screen doesn't have the option to change session, then you will need to go into: user preferences>login and change the log in screen to show all the options.

next time you log out you will be able to change your default session.

Lastly: I hope I haven't forgotten something important here, but it is a fairly straightforward thing to do, so if I haven't given you all the info you need, just look around in the prefernces for logging in, and you will find it easy enough.

Of course, also reply here. Cheers, and I hope your mother likes her ubuntu experfience.

---

### Post by DarkN00b on 2006-10-22
I get no option to choose a session when I log in. IceWM did run on startup, but it appears to be running alogside of Gnome. I still have my top Gnome panel, fully functional. The system slows to a halt about 10 minutes into the session.

---

### Post by aysiu on 2006-10-22
You're saying you don't have this?

---

### Post by DarkN00b on 2006-10-22
Oh yeah I have the options menu. I was expecting a popup or something.

Ok, I logged back in again and chose IceWM. It runs well but now I've lost Gnome Games (of course--Gnome isn't running *slaps forhead*)

Thanks for the help. I think I can go from here.

Edit: Same problem I had with Gnome, HD light comes on and the system crawls to a halt. Maybe this old machine just can't handle Ubuntu.

---

### Post by aysiu on 2006-10-22
You haven't lost Gnome Games. It just isn't being displayed in the menu.

[This](http://ubuntuforums.org/showpost.php?p=1549508&postcount=58) should help you get up and running with IceWM in a Gnome-friendly way.

---

### Post by DarkN00b on 2006-10-22
I'm afraid this isn't going to work. Once the hd light comes on after about 10 minutes, the system is less useful than a brick. It becomes totally unresponsive. I think I'll try to find an old WinMe CD on Ebay or something.
Thanks for your help, but I seriously don't think this old box can handle Ubuntu. Maybe a lighter distro like Damn Small Linux.

---

### Post by DarkN00b on 2006-10-27
I just thought I'd post here again to say that I got it working with Xubuntu. Hercules now runs like a dream. Very snappy for an old coot like him. As a matter of fact I am posting this using Herc!

Specs (one more time):

MFG: E-Machines and me,bought @ Goodwill for $15.00 USD - working
PII 266Mhz
128 MB rem
15 GB HD (The 40 MB was dead :( I'll add another one in the morning.)
ATI Rage II AGP graphics (onboard w/4Megs ram)

Needless to say he won't be doing any direct rendering, but I must say I'm proud of Ubuntu for running so well on such low-end hardware.

---

### Post by butlpbk1 on 2006-11-06
I recently got a very similar box running with Xubuntu.  Then I splurged and bought a new memory card for it that cost more than the original machine! (which I picked up for $25 USD).  The improvement was marked and it now is a very useable machine.  A little patience is needed when opening large image files, but heck it was worth every penny and it keeps a perfectly usable computer out of the landfill.

---

### Post by DarkN00b on 2006-11-07
Alas, Hercules (the machine) died last week and was unfixable. Now I need to find her another machine because she is really wanting to play her games. *sigh*, now I have to spend more time installing and configuring Ubuntu. What a chore. :D

Actually I like doing stuff like this.

---

