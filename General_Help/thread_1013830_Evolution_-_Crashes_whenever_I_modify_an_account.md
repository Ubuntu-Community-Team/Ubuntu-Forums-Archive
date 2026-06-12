---
title: "Evolution - Crashes whenever I modify an account"
date: 2008-12-17
forum: General Help
---

### Post by patrick2008 on 2008-12-17
I don't know if this has already been posted or not, but I didnt see it anywhere.

I set up Evolution in Ibex, and whenever I modify a email account in it, say to change the SMTP username, and click on "OK", it will just close out and say nothing. I have the most up to date version. 

I've put in an openSuse 11.0 LiveCD and tested this on the evolution which is bundled in with it and it didnt crash. Are there any known fixes for this? Thanks in advance.

---

### Post by Sam Lars on 2008-12-17
Does openSuse use a newer version?

---

### Post by patrick2008 on 2008-12-17
If I remember correctly. I dont have the LiveCD on hand at the moment. Will confirm this shortly

---

### Post by howefield on 2008-12-17
Looks like Suse 11 ships with Evolution 2.22.1.1 whilst Intrepid ships with 2.24.1.1

---

### Post by Sam Lars on 2008-12-17
Could be a new bug then?
I found [this bug]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/304385"), does it sound like the same thing?  If not, you could also open a new bug and do a backtrace for it.

---

### Post by patrick2008 on 2008-12-17
Ubuntu 8.10: 2.24.2
openSuse 11.0 LiveCD: 2.22.1.1

---

### Post by patrick2008 on 2008-12-17
> **Sam Lars said:**
> Could be a new bug then?
I found [this bug]("https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/304385"), does it sound like the same thing?  If not, you could also open a new bug and do a backtrace for it.

that looks to be it. Would uninstalling Evolution from Ubuntu and then installing the current stable release from Evolution's site possibly repair this bug? From my readings, it seems people have patched it and committed those changes.

---

### Post by misterdasher on 2009-01-07
Did you try uninstalling the Ubuntu version & installing the Evolution version?  Or some other work-around?

---

