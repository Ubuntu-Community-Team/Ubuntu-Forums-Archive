---
title: "Amarok Issue (another one)"
date: 2006-09-06
forum: Desktop Environments
---

### Post by MHlavsa on 2006-09-06
So I completely wiped my hard drive this weekend and put on a fresh brand new smells like momma's home cookin' version of Dapper (gnome) on.  Then, while trying to get everything back to the way it was, I installed Amarok (from Synaptic), but when I open, I get errors.  The first it told me was that something like dscopserver or dcopserver, I can't remember, wasn't running, so I pulled up terminal and ran that command and then that error was gone.  Then, instead i got a File:/// error.  After I clicked OK it takes me to the screen to add songs to the database, but no matter what I do, either OK or cancel from there, it takes me to the final error screen where it tells me to run a bunch of code in the directory (which I'm not sure where that is because I didn't compile amarok myself.

Ugh!

---

### Post by Jucato on 2006-09-06
Could you check if amarok-xine is installed? it's the sound engine used by Amarok by default. I'm not sure if Amarok would work with GStreamer (which Ubuntu uses).

Which version of Amarok are you trying to install, btw?

---

### Post by MHlavsa on 2006-09-06
Yeah, amarok-xine 2:1.4.3-0ubuntu1 is installed

---

### Post by Jucato on 2006-09-06
I'm presuming what you installed was Amarok 1.4.3? Is dapper-backports enabled, like what the announcement page instructed?

---

### Post by DonPachi on 2006-09-18
I'm having an identical symptom.  Yes I do have backports enabled.

---

