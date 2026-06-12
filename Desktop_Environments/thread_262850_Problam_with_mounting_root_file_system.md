---
title: "Problam with mounting root file system"
date: 2006-09-22
forum: Desktop Environments
---

### Post by BeNi.G on 2006-09-22
Hello!

I have a problam to mounting root file system.
When I try to booting ubuntu ,the booting stoped in "mounting root file system".
I hope you can help me fix that.
I can enter Ubuntu with the live cd!

Thenks.

sorry for my bad English

---

### Post by soutSA on 2006-09-22
I had the same problem about a month ago....but I am not one of the brave yet and being a reformed windows tech I did what I normally did with a windows system......reinstall.

There is a better way to see where the system is halting. I think if you press F2 before grub is being loaded it will give you a terminal interface rather then your GUI boot interface. Then you will see on what your system is halting.


Sorry I cannot give anymore information.

---

### Post by BeNi.G on 2006-09-24
OK thanks, but I don't want to reinstall. 

somebody else can help me here.
TNX

---

### Post by BeNi.G on 2006-09-24
ok I booted my system with recovery mode , and I found that the problam is something with my usb mouse driver. I tryed to booting without the usb mouse and it still dont work.
help me please!!

thenks

---

### Post by BeNi.G on 2006-09-25
bump
please I must your help here

---

### Post by henriquemaia on 2006-09-25
It would be more easy if you could give us details of your boot messages. Do you have bootlogd enabled? That's one of the init scripts.

---

### Post by henriquemaia on 2006-09-25
To log your boot, please refer to this other thread:

[**HOWTO: Log Boot Messages**]("http://ubuntuforums.org/showthread.php?t=49925&highlight=boot+log")

---

### Post by BeNi.G on 2006-09-25
First of all thanks you trying helping me!

I dont understand what is bootlogd and what is the init scripts.
I cant copy the massage and past it here. I need to copy it on a paper and to copy it here word after word (just tell me and I will do that).
If you could explain me what this bootlogd maybe I can tell you what you want me to give you .
thanks agine and sorry for my English

---

### Post by BeNi.G on 2006-09-25
> **henriquemaia said:**
> To log your boot, please refer to this other thread:

[**HOWTO: Log Boot Messages**]("http://ubuntuforums.org/showthread.php?t=49925&highlight=boot+log")

thanks ,but I can't open a terminal .(my system can't booting succefuly)

---

### Post by henriquemaia on 2006-09-25
Nor even in recovery mode? You just have to boot in recovery mode and do the steps presented in the HowTo. Note them down to do it in the command prompt you'll see in recovery mode.

---

### Post by BeNi.G on 2006-09-25
I can't open terminal even from the recovery mode (it stoped in "waiting for root file system")

---

### Post by henriquemaia on 2006-09-25
Well, it looks much more serious. Reinstall is really out of question?

---

### Post by BeNi.G on 2006-09-25
Is there a way to Reinstall and keeping my all preferences and my stuff (like upgrading or something)??

If there is no other way I will reinstal (but I install edgy eft beta that comes in 3 days)

If u know someone who can help me send him a link to this thread ,but I hope that you can help me .

---

### Post by henriquemaia on 2006-09-25
You could boot using a LiveCD and then mount your HD partition where you keep your configurations files. After that, you back the folder /etc (where your configurations are kept) remotely or on a CD. Then, reinstalling will not be a problem.

---

### Post by BeNi.G on 2006-09-25
I read about a rescue mode. how can I enter the rescue mode from the live cd ? (I know that this option must be in the liveCD)

---

### Post by BeNi.G on 2006-09-25
I read about a rescue mode. how can I enter the rescue mode from the live cd ? (I know that this option must be in the liveCD)

---

### Post by henriquemaia on 2006-09-25
Never tried. Maybe someone else have a clue on this.

---

### Post by BeNi.G on 2006-09-26
> **henriquemaia said:**
> Never tried. Maybe someone else have a clue on this.

someone else?:-k 
there is someone else here?

---

