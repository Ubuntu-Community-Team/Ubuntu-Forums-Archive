---
title: "Woops, Compiz Effects Killed my Desktop"
date: 2008-12-15
forum: General Help
---

### Post by -emory- on 2008-12-15
Hey everyone, I was messing around with my "Advanced Compiz Config Settings", trying to squeeze a bit of speed out of an aging laptop,and I enabled bi-linear filtering and tweaked a few other settings, when all of a sudden the screen turned all 16bit color and then froze up. I did a hard reboot and was greeted by the login screen as usual, problem is that when I try to login, it boots all the way to the desktop, and right when it would load compiz (I have compiz-fusion installed, if that helps) it crashes, and returns to the login screen. Is this a common problem? Has anyone else experienced it? Is there any way to disable compiz effects from booting on startup without reinstalling? Maybe through a live disk? Thanks to anyone who can help me out. I'm in a bit of a problem here because I can't boot up my laptop at all.

---

### Post by gettinoriginal on 2008-12-16
At the boot splash, hit escape, then (I don't remember the option) boot into CL and paste this code

gconftool-2 --recursive-unset -a /apps/compiz

That sets compiz back to all it's defaults.  Good luck :p

---

### Post by -emory- on 2008-12-16
Wow that worked like a charm! Thank you so much. I'm looking for a button to "Thank" you, but I can't seem to find it. How do I do that, or does it automatically count this as a thank you for your forum stats?
Also, the one thing that I needed to change was that instead of bootign into safe mode by pressing esc (That boots into root terminal) I needed to change the session to Failsafe Terminal, and then it worked perfectly!

Edit: Nevermind, found it!

---

### Post by ellalan on 2008-12-16
Its in the bottom right hand corner,last yellow button 3rd next to "qoute" button.

---

### Post by DetCochese on 2009-05-24
DISREGARD, I am still a Linux rookie and confused grub> with the command line for a minute. :D

*****************


I'm having similar issues on a Dell Mini Inspiron 910 with Jaunty.

I went into Compiz advanced stuff to see if I could get the fabled desktop cube enabled and now my desktop GUI is unusable.

I rebooted to splash, escaped to grub> and typed the above mentioned 'gconftool' string with the following result:

Error 27: Unrecognized command


Anyone tell me what I'm doing wrong?

Thank you.

---

### Post by fillintheblanks on 2009-05-24
can you boot into GUI first and press CTRL+ALT+F1
maybe you can type it there.

---

### Post by DetCochese on 2009-05-24
> **fillintheblanks said:**
> can you boot into GUI first and press CTRL+ALT+F1
maybe you can type it there.

Fixed the graphics issue with information in this thread.

Now, on reboot (and subsequent reboots) my wireless network access is disabled??

Whereas it usually auto connects to my established wireless network, there is now a small red and white X over the signal strength bars!

Any ideas? ):P

---

### Post by DetCochese on 2009-05-27
> **DetCochese said:**
> Fixed the graphics issue with information in this thread.

Now, on reboot (and subsequent reboots) my wireless network access is disabled??

Whereas it usually auto connects to my established wireless network, there is now a small red and white X over the signal strength bars!

Any ideas? ):P

Bump.

Or should I start a new thread?  Thanks for the help folks!

---

