---
title: "gdesklets - Crash"
date: 2005-09-16
forum: Desktop Environments
---

### Post by clapton on 2005-09-16
My Gdesklets always crash, it runs good on or 2 times, and after this it crashs, and sometimes I've got to kill process's because it loads cpu.
Some sugestion? Is there any application for alternative.

This is when it works.

[IMG]http://www.alojarfotos.com/images/clapton/capturaecra_3.jpg[/IMG]

---

### Post by KingBahamut on 2005-09-16
how much of a load is python taking up? 

might be a memory utilization issue.

---

### Post by clapton on 2005-09-16
I don't know, because after the 1st use, never work gdesklet.

---

### Post by KingBahamut on 2005-09-16
apt-get remove gesklets gdesklets-data

cd /home/<username>

rm .gdesklets/ -fr

apt-get install gdesklets gdesklets-data 

and then rebuild your desklets.

---

### Post by clapton on 2005-09-16
I'm gonna do this.
I'll report future errors :)
Thx

---

### Post by clapton on 2005-09-16
Just a paralel question..
Can I put gdesklet run when gnome starts?

How?

---

### Post by KingBahamut on 2005-09-16
Administration > Preferences > Session

Youll find a session startup list in there, just add the command gdesklets , and itll add proper to your session list.

---

### Post by clapton on 2005-09-18
Every thing works.
Thx a lot.

---

