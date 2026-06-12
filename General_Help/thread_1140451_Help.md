---
title: "Help?"
date: 2009-04-27
forum: General Help
---

### Post by F6F Freak on 2009-04-27
Is there a way for me to downgrade to the LTS?
I am running jaunty, which I managed to screw up horribly, is there a way to downgrade without re-install. I would settle fro intrepid at the moment.

---

### Post by mb_webguy on 2009-04-27
The only way to really downgrade to any previous release is a clean install of the older release.

---

### Post by cybergalvez on 2009-04-27
What is the problem, most things can be fixed without having to reinstall the whole thing.

---

### Post by lovinglinux on 2009-04-27
If you have a separate partition for /home then just reinstall without formatting it. You need to use the manual setup for this, so you can mount the existing home partition.

---

### Post by Iowan on 2009-04-27
> **F6F Freak said:**
> Is there a way for me to downgrade to the LTS?
I am running jaunty, which I managed to screw up horribly, is there a way to downgrade without re-install. I would settle fro intrepid at the moment. You realize that Hardy is the latest LTS - not Intrepid?

---

### Post by F6F Freak on 2009-04-30
Yes. I know that hardy is the LTS. I am not stupid.
Not that you said I was.

---

### Post by F6F Freak on 2009-05-01
Attached is one of the errors.

---

### Post by F6F Freak on 2009-05-01
Do I need root power to get this working?
I get a similar error upon trying to get a distribution upgrade.

---

### Post by Iowan on 2009-05-01
Oops, post got duplicated...

---

### Post by Iowan on 2009-05-01
> **F6F Freak said:**
> Yes. I know that hardy is the LTS. I am not stupid.
Not that you said I was.There are a couple of threads where posters seem to think ALL releases have an LTS version. Just wanted to make sure you knew otherwise...

Try running **sudo apt-get upgrade** - which is to say, yes, you probably need root power to get this working.

---

### Post by lisati on 2009-05-01
> **F6F Freak said:**
> Do I need root power to get this working?
I get a similar error upon trying to get a distribution upgrade.

Probably: an "apt-get upgrade" can make drastic changes to your system, so the process will need some kind of confirmation that you're sure you want to go ahead.

---

### Post by F6F Freak on 2009-05-01
Here is what I get. Nothing really happens.
I tried running the update manager, but it didn't help much.

---

### Post by F6F Freak on 2009-05-01
I also noticed that I am having a lot of trouble getting cario dock to work. I don't care about that for the moment, but I beleive that the root cause is the same.

---

### Post by F6F Freak on 2009-05-01
Big surprise. Another problem.

---

### Post by F6F Freak on 2009-05-01
Oh. Joy.
What the crap is wrong?
I am getting quite mad.
No matter what I try that same thing keeps popping up.

---

### Post by F6F Freak on 2009-05-01
I am tring to install the kubutu enviroment. Maybe that will help.

---

### Post by michy99 on 2009-05-01
In regards to the last error, it looks like you have another package manager open. Synaptic or Add/Remove.

---

### Post by sailthesea on 2009-05-01
I had something like this when building media support I rebooted and allowed update manager to run right through and things were much better Still a few hang ups though!

---

### Post by F6F Freak on 2009-05-01
I installed the KDE manager, and using konsole, things are going much better. Will update you if any more troble emerges.

---

