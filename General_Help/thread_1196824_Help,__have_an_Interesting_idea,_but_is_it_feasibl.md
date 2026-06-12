---
title: "Help,  have an Interesting idea, but is it feasible?"
date: 2009-06-25
forum: General Help
---

### Post by Aaron_Einstein on 2009-06-25
Hey, Kind of new here to the forum. Not so much to Ubuntu but I still have a question that I haven't been able to figure out on my own so I was hoping you guys could help. :D

So, despite my best efforts to use ubuntu exclusively I still find myself occasionally forced into Windows. Virtualisation is okay but not optimal and I still use Ubuntu about 97% of the time so a bootloader is an inconvenience. I was wondering if there was a way that I could make it so I could put an icon on my taskbar that would load a command that would suspend my current Ubuntu session and boot a certain partition with Windows on it. Then when windows closes it could load back the suspended session?

I think this would be the optimal thing for me to do. That is if it's possible. :confused:
Thank you,
Aaron

---

### Post by dhughes on 2009-06-25
I don't think that's possible, when you suspended one OS other OS has to boot somehow. If you're not dual-booting and not using virtualization of some sort you will have to reboot.

 Someone may be working on such a thing but I don't know, someone else may have an idea but I don't know if it's possible.

---

### Post by Vikhyath on 2009-06-25
Have you tried using VMware??

---

### Post by ddrichardson on 2009-06-25
Its not feasible as suspend is suspended to RAM which even if you could segregate wouldn't be protected from Windows.

Why not hibernate, load Windows and reboot?  Essentially its much the same only using secondary rather than primary storage.

---

### Post by Aaron_Einstein on 2009-06-25
> **Vikhyath said:**
> Have you tried using VMware??
Virtualisation is too slow typically for some of the video editing I do. Also the possiblity of actually being able to occasionally play games maybe would be cool.

> **ddrichardson said:**
> Its not feasible as suspend is suspended to RAM which even if you could segregate wouldn't be protected from Windows.

Why not hibernate, load Windows and reboot? Essentially its much the same only using secondary rather than primary storage.
Oops, I meant Hibernate then. I always mix those two up.


On another note, I think that if this were possible it'd have to be done with GRUB or something. Can you script things in Grub?? That might help.

---

### Post by ddrichardson on 2009-06-25
I suppose you could call the set the grub menu.lst to default to Windows run the hibernate script, then make sure that the menu.lst is set to reinstate Ubuntu as the default when you shutdown or suspend.

---

### Post by philcamlin on 2009-06-25
thatd be so crazy :popcorn:

---

### Post by blur xc on 2009-06-25
I was having a similar idea- probably harder to execute...

What if you had a program, like a proto-OS, that only created an environment where you could launch a real OS, and switch between them.  The 'real' OS's that you launch, could then access all your hardware naively, all cpu, ram, drives, etc...

the difference between this a running a virtual machine is like was mentioned in the other posts, you didn't have to run both simultaneously and limit resources on the virtual machine.

BM

---

### Post by Aaron_Einstein on 2009-06-25
> **philcamlin said:**
> thatd be so crazy :popcorn:
That's what I was thinking :P

---

### Post by ddrichardson on 2009-06-25
> **Barna Madau said:**
> I was having a similar idea- probably harder to execute...

What if you had a program, like a proto-OS, that only created an environment where you could launch a real OS, and switch between them.  The 'real' OS's that you launch, could then access all your hardware naively, all cpu, ram, drives, etc...

the difference between this a running a virtual machine is like was mentioned in the other posts, you didn't have to run both simultaneously and limit resources on the virtual machine.

BM
If the "real OS" has access to RAM, how do you protect it from being accessed by the other?

---

### Post by gunrunner45 on 2009-06-25
Run two separate machines.  One with Ubuntu & one with Windows.  Hook them into a KVM switch so all you have to do use a key combo to switch between them.  Store all your personal files ie:  My Documents & /home on a NAS device.

---

### Post by ddrichardson on 2009-06-25
> **gunrunner45 said:**
> Run two separate machines.  One with Ubuntu & one with Windows.  Hook them into a KVM switch so all you have to do use a key combo to switch between them.  Store all your personal files ie:  My Documents & /home on a NAS device.
Not a fan of maintaining a low carbon footprint I take it? :-)

---

