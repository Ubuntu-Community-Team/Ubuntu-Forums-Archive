---
title: "Intalled ubuntu in VB"
date: 2009-05-19
forum: General Help
---

### Post by zeldarocks on 2009-05-19
I just installed Ubuntu in VirtualBox, I went to install the Guest additions and I found it super easy this time around, I didn't have to get on the terminal, I just double-clicked the .sh file while exploring the cd image and it installed just like that. I don't remember this being so easy, I even tried doing that in ubuntu 8.10 and it didn't work,how come its working now?

---

### Post by zeldarocks on 2009-05-19
bump

---

### Post by mikezila on 2009-05-19
Dunno.  Maybe VB's guest additions have been upgraded since last time you tried?

---

### Post by snova on 2009-05-19
> **zeldarocks said:**
> I just installed Ubuntu in VirtualBox, I went to install the Guest additions and I found it super easy this time around, I didn't have to get on the terminal, I just double-clicked the .sh file while exploring the cd image and it installed just like that. I don't remember this being so easy, I even tried doing that in ubuntu 8.10 and it didn't work,how come its working now?

How did you do it the first time?

---

### Post by chiefbutz on 2009-05-19
I have also experienced this. I think VirtualBox has changed how the installer works. I believe in the past that it extracted files to the current working directory, which is why it would not run from the ISO without copying the needed files off of the iso. (at least that is what i remember)

Anyway, all the changes there are how VirtualBox does their installer.

---

### Post by zeldarocks on 2009-05-19
Before I had tried to do it from the .run file but it said that it couldn't be opened or something, so I HAD to do it from the terminal (this is in ubuntu 8.10) now (in 9.04), I explored the cd, and clicked on the .sh file, which opened a dos-like prompt (in black, as in windows, not terminal) and did the job, installing the additions. Before I had to get into the terminal, now I can do it as I would an executable in windows...

---

### Post by chiefbutz on 2009-05-19
> **zeldarocks said:**
> Before I had to get into the terminal, now I can do it as I would an executable in windows...

Ah, I see. Yes, that is simply a change in how the installer was programmed by the Virtual Box programmers.

---

### Post by zeldarocks on 2009-05-19
so the terminal is really not necessary, it can be done in a few moments with ease now by a noob to ubuntu pretty much? Also, can you refer me to the VB changes made in the latest version addressing the installation change?

---

### Post by zeldarocks on 2009-05-19
bump

---

### Post by chiefbutz on 2009-05-20
> **zeldarocks said:**
> can you refer me to the VB changes made in the latest version addressing the installation change?

Here is their change log, though I do not see mention of it.

[http://www.virtualbox.org/wiki/Changelog](http://www.virtualbox.org/wiki/Changelog)

I am simply assuming these changes from what I know since I am a programmer myself.

---

### Post by zeldarocks on 2009-05-20
Well documented or not, it's a much easier and seamless installation of the Additions than before, wouldn't you agree?

---

