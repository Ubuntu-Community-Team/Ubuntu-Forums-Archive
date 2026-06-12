---
title: "Vista stopped loading - and other question"
date: 2009-04-20
forum: General Help
---

### Post by Zaydene on 2009-04-20
I installed Ubuntu and was able to dual boot Vista and Ubuntu for a day, then all of a sudden when I try to load Vista I just get a black screen. Because I'm really fond of Ubuntu so far, besides the fact I need to learn how to get the hang of the terminal stuff I was going to keep this as my main OS. Before I installed it, I gave Ubuntu a 50g partition and kept 100g for Vista, but since Vista doesn't work, I want to merge my partitions and get rid of any trace of Vista.

Tl:dr I would like to wipe out my Vista partition and HP recovery part and use them all for Ubuntu.

*When I try to use Pidgin to get on Windows Live, it never verifies my account and I can't use it. Is it possible to use Wine and WLM to run?

I'm super new to this OS and forum, so sorry if I posted incorrectly.

---

### Post by jose187 on 2009-04-20
I think you can use the partition editor in the Ubuntu Live CD to get rid of Vista and the recovery disk.

I have never had a problem with Pidgin, but there are other messenger services out there. Have a look at Add/Remove Applications.

---

### Post by codeseer on 2009-04-20
> **Zaydene said:**
> I installed Ubuntu and was able to dual boot Vista and Ubuntu for a day, then all of a sudden when I try to load Vista I just get a black screen. Because I'm really fond of Ubuntu so far, besides the fact I need to learn how to get the hang of the terminal stuff I was going to keep this as my main OS. Before I installed it, I gave Ubuntu a 50g partition and kept 100g for Vista, but since Vista doesn't work, I want to merge my partitions and get rid of any trace of Vista.

Tl:dr I would like to wipe out my Vista partition and HP recovery part and use them all for Ubuntu.

*When I try to use Pidgin to get on Windows Live, it never verifies my account and I can't use it. Is it possible to use Wine and WLM to run?

I'm super new to this OS and forum, so sorry if I posted incorrectly.

Ok, so the Ubuntu and partitions issue first. What you need to do is take the Ubuntu Live CD and boot it up, select the 'try without making changes' option from the boot menu and then launch GParted from the desktop. Just type 'gparted' in the terminal. GParted will allow you to delete the Vista partition and the recovery partition, then resize the Ubuntu partition to fill up the then blank space.

If you can give more specific information on the Pidgin problem, perhaps we can help you on that.

---

### Post by Zaydene on 2009-04-20
Wow, super fast reply. 

Unable to authenticate: Authentication Failure
When I open the buddy list, if I click re-enable, the tickbox just unticks.

Also, when I do the partition solve, will my settings I've made so far stay the same?

---

### Post by codeseer on 2009-04-20
Yeah, your settings will remain intact.

---

### Post by Zaydene on 2009-04-20
Ok, I think I know the problem, on Vista, I used Windows Live Messenger, never used MSN, so, is there a Windows Live messenger I can use for Ubuntu?

---

### Post by codeseer on 2009-04-20
Well this may be strange, but from what I've read so far, some people have had success by simply changing the password on their account.

---

### Post by Zaydene on 2009-04-20
But is "Msn" the same as Windows Live?

---

### Post by codeseer on 2009-04-21
> **Zaydene said:**
> But is "Msn" the same as Windows Live?

I think so.

---

### Post by Zaydene on 2009-04-21
I ran terminal and tryed gparted, and got 
Root privileges are required

---

### Post by Jammanuser on 2009-04-21
> **Zaydene said:**
> I ran terminal and tryed gparted, and got 
Root privileges are required
Use
```
sudo gparted
```

-Jam man

:guitar:

---

### Post by Zaydene on 2009-04-21
I deleted the vista partition and the recovery part, now how do I go about filling up the unused parts with ubuntu

---

### Post by Jammanuser on 2009-04-21
> **Zaydene said:**
> I deleted the vista partition and the recovery part, now how do I go about filling up the unused parts with ubuntu
Use the "Expand" option (I believe its called), and expand it to the mamimum amount of MBs or GBs (depending on which one the program goes by) available on the disk.

---

