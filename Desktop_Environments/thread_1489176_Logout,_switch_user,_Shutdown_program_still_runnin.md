---
title: "Logout, switch user, Shutdown program still running error"
date: 2010-05-20
forum: Desktop Environments
---

### Post by Jbike on 2010-05-20
Hello all,

I am running 64 bit version of 10.04 for on an Athlon duel core with nvidia graphics.... any time I try to logout any user I get some text saying that a program is "not responding".  I searched around and cannot find anyone else who has this specific bug on 10.04. Does anyone have any ideas, or did I just miss the (already posted) solution?

Thanks, Jbike

---

### Post by Jbike on 2010-05-28
Same problem persists after many updates.... attached is a graphic of the error. When I try to find the errant process I find a number of processes in the system monitor sleeping, but none active. 

thoughts? 

Jbike

---

### Post by Jbike on 2010-06-25
Still here with the problem. I don't know if this is relevant or not- but it's worth a try. I set my drive up with separate root and home partitions. I was previously running 9.10 but instead of updating through the update manager I did a clean install and chose not to format my home partition. Except for this logout issue, I have been very happy with the results- all of my data and settings were preserved. 

Has anyone else run into this logout issue yet?

Thanks,
Jbike

---

### Post by Jbike on 2010-06-29
Also interesting, after I get the logout error illustrated above  if I navigate to: system=>administration=>system monitor.... to see which process is still running... all remaining processes are sleeping- and I have zero indication which process may be the issue? 

Jbike

---

### Post by Jbike on 2010-07-13
Still here with the problem... My son also has the same issue... program not responding... though it does not happen as frequently (and does not seem to be as annoyed as I am about the matter). His system is also nvidia, though a different GPU

Confused, 
Jbike

---

### Post by wallpaper_thief on 2010-07-15
Hi, I have a similar problem too. It's always "simple-greeter.desktop" or "power manager," never unknown.

---

### Post by Jbike on 2010-07-22
I am now sure that this bug has something to do with the  nvidia drivers. I just cannot guess why I would be having a problem now with 10.04, when 9.10 worked fine?

ideas?
Jbike

---

### Post by wallpaper_thief on 2010-07-22
> **Jbike said:**
> I am now sure that this bug has something to do with the  nvidia drivers. I just cannot guess why I would be having a problem now with 10.04, when 9.10 worked fine?

ideas?
Jbike
It happens on ATI drivers either, which I am using.

---

### Post by Jbike on 2010-08-09
Ok, so on Ubuntu's main download url, 

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

the 64bit desktop edition (what I am running) says: "Not recommended for daily desktop usage" while the 32 bit edition says: "Recommended for most users" Why is this? shouldn't the 64 bit os always be recommended for 64bit processors like my Athlon64? 

Thanks,
James

---

### Post by wallpaper_thief on 2010-08-09
> **Jbike said:**
> Ok, so on Ubuntu's main download url, 

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

the 64bit desktop edition (what I am running) says: "Not recommended for daily desktop usage" while the 32 bit edition says: "Recommended for most users" Why is this? shouldn't the 64 bit os always be recommended for 64bit processors like my Athlon64? 

Thanks,
James

I've run several different versions of 64-bit linux all of which worked fine with a little finetuning to my hardware specs, but Ubuntu 64-bit is buggy beyond redemption. I have some suspicions about Canonical and their practices (and treatment of bugs) but listing them here would probably be counter productive.

---

