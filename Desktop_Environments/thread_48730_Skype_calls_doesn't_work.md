---
title: "Skype calls doesn't work"
date: 2005-07-13
forum: Desktop Environments
---

### Post by mojo_risin on 2005-07-13
Hi,

I use skype perfectly in my kubuntu 5.04 box except for making calls. It hangs up. I tried with several versions but it's always the same. I also tried to run from the console but I get no (error) messages.
Does anybody has the same problem?

---

### Post by dave9191 on 2005-07-13
I havent used it in a while, but when making or accepting a call it would spend ages waiting for the sound card and then give up. So either start skype with arts support or make artsd release the sound card before you make the call. I cant remember the commands for either of the top of my head. 

Dave

---

### Post by Sav on 2005-07-14
Have you checked the "full duplex" flag in the audio configuration of kcontrol?

---

### Post by dave9191 on 2005-07-14
Just a note, any changes you make in Kcontrol will not efffect skype unless you start it using the artsd. 

artsdsp skype

Dave

---

