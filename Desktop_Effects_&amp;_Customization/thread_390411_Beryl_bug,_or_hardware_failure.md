---
title: "Beryl bug, or hardware failure?"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by Jofaba on 2007-03-21
I'm coming from a computer that was very overclocked for gaming to linux for education. The computer itself is dual core, SLi, voldmodded etc. I've cleaned the voltmod off, removed one of the videocards, and undid the processor overclocking. I'm running gnome Ubuntu with, I believe, xgl. I say believe, because I can't remember which installation I did but I'm almost positive that it's xgl. 

I have the AMD 64 version of Ubuntu and am running in gnome. I installed Beryl and it was running fine, but now whenever I run it the computer freezes. I can move my mouse, but can't click anything. It's very similiar to the crashes I've gotten over the past couple of weeks both in live cd and hard drive environments. 

I ruined a hard drive by dual booting (either that or just impecible timing for hard drive failure) and finally decided to waste the data on my 300gb drive to try and get a solid OS going. I know that Beryl is beta, but even on a bad disk it was more solid than this. I just want to get it active so that I can play with it. As soon as I activate beryl in beryl screen mode, the computer becomes unresponsive (except for the mouse). 


So, what information do you need in order to try and resolve this issue?

---

### Post by old_geekster on 2007-03-24
You should install "Beryl 2.0".  It is the first stable version since 0.1.0.

I used "Automatix Bleeder" to install it.

Type: sudo gedit /etc/apt/sources.list

Add the following to the bottom of the sources.list:

#AUTOMATIX BLEEDER REPOS START
deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy main
#AUTOMATIX BLEEDER REPOS END

Go to "Synaptic Package Manager" and "Reload".  Then, search for Beryl.  Make certain that it says 2.0 in the description.

Once Beryl is installed, you should run "Update Manager".  This will install the patch for Beryl.  It repairs a bug that occurs with Java.

Good luck!

---

