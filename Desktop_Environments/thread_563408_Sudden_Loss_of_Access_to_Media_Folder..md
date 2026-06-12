---
title: "Sudden Loss of Access to Media Folder."
date: 2007-09-29
forum: Desktop Environments
---

### Post by tgbrowning on 2007-09-29
Greetings,

[running feisty]

Just has a very nasty shock. Logged on to my computer and was informed that I did not have permission to look at anything in the files in the media folder. I haven't made any changes to my system recently so I'm kind of perplexed as to what might have happened. 

About the only think I can think of is that there was a system update yestderday and that affected quite a bit of the core and if I recall, had a number of security fixes involved. 

Anybody have any idea if this is something that was caused by the latest updates?  Anybody else have this problem? 

I know I can get into them via the terminal with no problem, but damn, it kind of annoys me that I can't just look at things like I used to. 

If it wasn't associated with the security update, anybody have any idea why this would suddenly happen?

---

### Post by taurus on 2007-09-29
Where is that media directory located anyway?

---

### Post by tgbrowning on 2007-09-30
It's in the root directory, right along with bin, sbin and the others. I've got it fixed, but I'm still puzzled WHY it got changed. What actually happened is something changed the permissions on both the media and lost+found dirctory, disallowing "others" and "groups" from read, write and execute.  

Complete mystery to me HOW that happened.

 Once the media directory got changed, could no longer see anything that had been mounted.  Very odd.

Browning>>>

---

