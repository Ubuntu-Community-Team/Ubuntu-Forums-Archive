---
title: "[SOLVED] root problems"
date: 2008-12-09
forum: General Help
---

### Post by ekolimits on 2008-12-09
everything i do on my computer belongs to root before my user name... this makes managing everything difficult... how can i make only one user name...get rid of root and only have ekolimits... making ekolimits own everything in linux...not root. is this possible?

---

### Post by HotShotDJ on 2008-12-09
> **ekolimits said:**
> is this possible?No.

---

### Post by ekolimits on 2008-12-09
so how do i login as root or enable user sharing?

---

### Post by p_quarles on 2008-12-09
> **ekolimits said:**
> so how do i login as root or enable user sharing?
What you are asking for is not supported here, because it's a very bad idea, and this forum does not traffic in techniques that will essentially compromise the security and stability of your entire operating system. 

Instead, why don't you describe what particular task you are finding difficult. Someone can most likely provide a way to make that easier for you.

---

### Post by HotShotDJ on 2008-12-09
> **ekolimits said:**
> so how do i login as root or enable user sharing?Just type sudo before the command then enter your password.  The first user you set up is the system administrator and has root access.  I don't know what "enable user sharing" means.

---

### Post by ekolimits on 2008-12-09
everything in this linux i installed does not "belong" to my user name... it belongs to root. because of this it wont let me copy and paste and other simple tasks. i cant do anything without getting complicated... sadly... im trying to extract a file into my sd card and it wont work... i;ve been doing this for a few days already... things come up on my desktop as read only...for some reason and i believe it to be user permissions... i think my user name doesnt have permisson to use root's stuff... i need to enable user sharing.

---

### Post by p_quarles on 2008-12-09
> **ekolimits said:**
> everything in this linux i installed does not "belong" to my user name... it belongs to root. because of this it wont let me copy and paste and other simple tasks. i cant do anything without getting complicated... sadly... im trying to extract a file into my sd card and it wont work... i;ve been doing this for a few days already... things come up on my desktop as read only...for some reason and i believe it to be user permissions... i think my user name doesnt have permisson to use root's stuff... i need to enable user sharing.
Like HotShotDJ said, "user sharing" doesn't mean anything.

If things are going to desktop read-only, something in the system is broken. Try an experiment for us. Plug in the SD card, move a file to your desktop, then run this command:
```
ls -lh ~/Desktop
```
Also, tell us which file you just moved there.

---

### Post by HotShotDJ on 2008-12-09
> **ekolimits said:**
> everything in this linux i installed does not "belong" to my user name... it belongs to root.No.  Everything in Linux does not belong to root.  Things in your home directory belong to you. You should not be trying to copy and paste system files, which root DOES own.  It is SUPPOSED to be difficult to mess with system files.

Please tell me exactly what you are trying to extract to your SD card.  If you are dealing with files in your home directory, it should be a simple "drag & drop" procedure.

> **ekolimits said:**
> i need to enable user sharing.This sentence does not make sense to me.  What do you mean by "user sharing."  Please don't just say it again, tell me what it means.

---

### Post by ekolimits on 2008-12-09
im tired sorry... im going to sleep and ill post questions on this forum later... its what ive been doing for the past few days lol... new to linux and things sure are not easy on this system if you want to do techinical stuff... ill probably reinstall everything again...copying to sd card worked before... but have been messing with things...

---

### Post by HotShotDJ on 2008-12-09
> **ekolimits said:**
> copying to sd card worked before... but have been messing with things...Well... that might explain a thing or two. :)  Perhaps after you get some sleep it will be easier to get things fixed up.

---

### Post by ekolimits on 2008-12-15
i have figured it out!!!!
if you go to the properties of the media that you just mounted and go to permissions the first option allows you to change the owner of the media!! if you "own" the media instead of root than you can make changes to it any time!!! yay no more gksudo nautilus!!! hahahahah! YES!

---

