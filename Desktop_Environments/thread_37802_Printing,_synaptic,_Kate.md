---
title: "Printing, synaptic, Kate ?"
date: 2005-05-28
forum: Desktop Environments
---

### Post by ThePainter on 2005-05-28
Hi,
Ive just installed Kubuntu and I have installed my Turboprint printer drivers and set up my printer that was recognised ok, but when I send a print job it just sits there in the Print Job list ?
Nothing else happens.
I have tried removing everything and reinstalling and setting it all up again.
I have used this driver in Mandrake 9.2/10.1, Fedora Core, Ubuntu-warty/Hoary and in Simply Mepis 3.3, and it has worked great in all of them.

Has anyone else had problems with this ?

One other thing, I went to the Kubuntu FAQ and set up the repository list in synaptic and everything seems to be there but everytime I start it up I get an error about loads of packages not being available ?

And one more thing, for some reason when I boot up I get a request for a password to start up "Kate" in root.
I dont even have Kate installed ?
Could this have been put in a start up file somewhere that I can edit to stop this ?

---

### Post by cwaldbieser on 2005-05-28
Is it when you boot the machine or when you log into a Kubuntu session?  If it is the latter, try checking for a script or symlink in ~/.kde/Autostart, or maybe you left it open in a previous session and it is just trying to re-open it?

---

### Post by ThePainter on 2005-05-29
Hi,
The Kate prob seems to have repaired itself.

The synaptic prob is only an irritation, it seems to work OK.

The Printer prob is the most important cos it means I have to go back into XP to print stuff !

The thing that gets me is back in Warty everything worked great but in hoary I started finding bugs so I tried Mepis and it was great but still a few annoying bugs, so I decided to give Kubuntu a go but again more bugs.

It seems ironic that the older ones worked great and as they update them they spoil them.

You cant fix whats not broken, you can only break it ?

---

### Post by tread on 2005-05-29
> One other thing, I went to the Kubuntu FAQ and set up the repository list in synaptic and everything seems to be there but everytime I start it up I get an error about loads of packages not being available ?   

This may be a stupid answer, but its worth a check anyway.
Did you reload package information after adding repositories in sources.list?

---

### Post by ThePainter on 2005-05-29
Hi,
Yes.
I did reload package info.

---

