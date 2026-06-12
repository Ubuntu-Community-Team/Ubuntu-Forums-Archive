---
title: "Get error starting Screenlets"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by sjpritch25 on 2007-10-01
Here is the screen shot

---

### Post by santiagoward2000 on 2007-10-01
The problem is that daemon isn't started when you start the computer. But once you've opened the screenlets-manager it should be fixed. Does it appear if you close screenlets-manager and open it again?

---

### Post by sjpritch25 on 2007-10-01
Okay, i opened it again, but can't seem to get it to work.   I click on the item---> Click on Enable---> Click on **Launch**.    Nothing happens.

---

### Post by sjpritch25 on 2007-10-01
Never mind, i got it to work.    Thanks

duh

---

### Post by lizardopulo on 2007-10-20
> **sjpritch25 said:**
> Never mind, i got it to work.    Thanks

duh

how?

I have the same problem
I also add "screenletsd start" on sessions and it starts but options change continuously on every login.

Bye

Lizza

---

### Post by oxboy on 2007-10-23
You should not have to use screenletsd start anymore, since you can use the screenlets manager.  

The problem I was having was that there was no "screenlets" directory in my .config folder.  Check to see if you have one, and if you don't just create one (that is, you should have ~/.config/Screenlets).

---

