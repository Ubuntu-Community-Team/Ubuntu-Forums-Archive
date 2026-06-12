---
title: "Press Num Lock / Caps Lock = Hard Lock?!"
date: 2006-05-18
forum: Desktop Environments
---

### Post by Swad on 2006-05-18
I have never run into this problem on ANY OS--ever that I recall.  I just finished installing Ubuntu 5.10 (server install option) on a Compaq ML370 G1 server.  I am planning to use it as a VMware test server at the office.  There's a problem, though.  Whenever the Caps Lock or Num Lock keys are pressed (there may be others for all I know, such as Scroll Lock--I didn't test any further), the machine hard locks.  The keyboard no longer gets a response out of the machine.  The machine can't be pinged any longer.  It's verified as being completely hard locked.  It tried another PS/2 keyboard to see if it still did this, and it did.

I noticed suring the install process (which I had to make a few attempts at for some other reasons) that it would hard lock with the numlock as well.  I went ahead and pushed past this issue hoping a software update after the install finished would fix it.  Nothing.  The system is fully up to date and I still get this.  The machine worked fine when it ran Windows 2000 Server, so I'm hard pressed to think it is the computer hardware going bad.

Has anyone else per chance ever seen this problem?  I'm stumped and amazed that somthing like that would hard lock a machine.

---

### Post by KingCharles on 2006-05-22
hum...  :-k 

I'm no expert, but maybe there is some kind of hardware mapping to the NumLock and/or CapsLock in the motherboard's bios that could cause the computer to [deadlock]("http://en.wikipedia.org/wiki/Deadlock")?

Maybe a bios update is needed?

---

### Post by miltiad on 2006-08-30
I have the same problem, did you resolve it ?

---

### Post by simke on 2007-02-26
I have a kind of similar problem. When pressing caps/num lock repeatidly in short time (4-5 times) the keyboard just goes dead. The mouse works OK and computer seems responsive. 

I have tested both Ubuntu 5.10 and 6.10 and still get the same behaviour.

The workoround in my case was to pull out the kayboard, wait few seconds and connect it again. Then it works until i use caps/num lock again.

It would be interresting to hear if anybody else had same kind of problem, and what is the solution.

---

