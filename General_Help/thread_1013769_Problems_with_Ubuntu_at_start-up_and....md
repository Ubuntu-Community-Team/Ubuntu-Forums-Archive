---
title: "Problems with Ubuntu at start-up and..."
date: 2008-12-17
forum: General Help
---

### Post by Vista1330 on 2008-12-17
My PC: HP DV9913cl for complete specs please visit the hp website and search for this product.

My O/S: Dualboot> Vista Premium x64 and Ubuntu 8.10, Gnome

In the past I have been using Vista and Ubuntu 8.04 with no problems what so ever. 
But since a couple of weeks ago I installed a fresh version of Ubuntu 8.10 on a newly created partition. 
1. When I start-up Ubuntu at the logon when u see the orange-brown start-up bar going from left to right, back and fort. The bar suddenly stops responding and after waiting hours for Ubuntu to continue start-up I pressed the power button on my PC briefly and the bar suddenly began moving again and Ubuntu started up normally. I could work and do everything normally. So from that day on till now everytime I want to use Ubuntu when the bar stops responding I have to press my power button briefly to continue the starting up procedure.
2. When shutting down my PC in Ubuntu 8.04 normally u get the shutting down screen where a orange-brown bar goes from left to right. The problem is now in Ubuntu 8.10 I do not see this bar, is this normal?
3. 2 days ago I see the shutdown bar but the colors are very disorted.
4. Why does Ubuntu read my memory as 3Gib installed, but I have 4Gib installed? This is not a hardware failure because Vista sees 4Gib. And I already opend up my laptop and there are to dimms of 2Gib installed.
5. When my PC is on I put my proccesor frecuency to maximum because at startup it is always at the lowest peak 800mhz. We all understand that working with 800mhz with the current programs is simply not possible. Can't Ubuntu remember that I always want to start my pc at its maximum proccessor frecuency?Ok I understand it is power saving but I am working with my adapter so I do not need power saving(ok electricity is expensive but what the hell I need CPU performance).
I have already updated Ubuntu to kernel blablabla.9. Every update that is possible I have done. Could someone PLEASE tell me what the problem(s) is(are)?I really REALLY like Ubuntu and do not want to use Vista just because I have tiny(but sometimes very annoying) problems.

P.S. I am not an experienced user in Ubuntu but I can help myself.

Ubuntu ROCKS:guitar::popcorn:!!!!!!!!!

---

### Post by /////// on 2008-12-17
1) No idea
2) Sometimes I don't see the bar either but see a black screen with text. The computer still shuts down fine so I don't think this is a problem
3) This isn't a question?
4) This is most likely because you install Ubuntu x32. 32 bit operating systems can only work with a maximum of 4gb of RAM and because of memory allocated for other things, this usually becomes somewhere around ~3gb. On XP x32 I could only see 3.25gb of RAM although I had 4gb.
5) Ok, so let me get this straight, you're running an 800MHz computer which has 4gb of RAM and can run Vista? Are you sure you are running on an 800MHz computer? Onto your question however, you can actually overclock your computer to get the same effect. This can be done through the BIOS but beware, overclocking can cause damage to your system.

---

### Post by Vista1330 on 2008-12-17
> **/////// said:**
> 1) No idea
2) Sometimes I don't see the bar either but see a black screen with text. The computer still shuts down fine so I don't think this is a problem
3) This isn't a question?
4) This is most likely because you install Ubuntu x32. 32 bit operating systems can only work with a maximum of 4gb of RAM and because of memory allocated for other things, this usually becomes somewhere around ~3gb. On XP x32 I could only see 3.25gb of RAM although I had 4gb.
5) Ok, so let me get this straight, you're running an 800MHz computer which has 4gb of RAM and can run Vista? Are you sure you are running on an 800MHz computer? Onto your question however, you can actually overclock your computer to get the same effect. This can be done through the BIOS but beware, overclocking can cause damage to your system.

 Revising:
2. My computer still shutsdown but would it be a bug or something that I do not see the bar?
3. The question is is it normal that now I see the bar but it is very disorted?
4. Ok I understand the 32bit part and a lot of bits and bytes stuff and 4Gib can not be 'read'.
5. When u install Ubuntu on laptop computers, there is automatically a software installed that puts the CPU frequency at its power saving peak at start-up. Now my question is I would like for this power saving option not to be on at start-up of Ubuntu. How do I do that?I have checked al the configuration options but there is no option that lets me do that.

Another P.S. I am an ICT support Analyst(for Windows SERVER, I am thinking of letting my company use Ubuntu Server edition;)), just for the information in case someone wants to explain for me in technical terms how and what to do!
I am a very very new user to Ubuntu so I am still kind of checking this and that out, Ubuntu has SOOOO many new features and option in relation to Vista(Windows) that we all experienced and new Users understand that we will never know all the pings/mods in short period of time...

---

### Post by Vista1330 on 2008-12-17
Bouncing so someone could please help/inform me on my ANNOYING problems!:confused::lolflag:

---

### Post by Vista1330 on 2008-12-17
Could someone please advise me or otherwise inform me about the problems I am having?
I really like Ubunutu but...

---

### Post by Vista1330 on 2008-12-18
Bounce

---

### Post by sPiN1 on 2008-12-18
Although it's against the rules to just say "start over fresh and reformat again" I would probably suggest doing this. Sorry I can't actually help :(

---

### Post by Vista1330 on 2008-12-18
> **sPiN1 said:**
> Although it's against the rules to just say "start over fresh and reformat again" I would probably suggest doing this. Sorry I can't actually help :(

I already tried doing that 4 times and I still get the same problems.

---

### Post by akshaykk on 2008-12-28
I'm having problems booting Kubuntu 8.10 on an hp dv9913cl. The boot process just stops, and resumes when I press and hold down any key. The moment I release the key, though, the boot process freezes again.

---

### Post by akshaykk on 2008-12-29
After looking around, I found a solution to the boot freeze-up problem here:

[https://bugs.launchpad.net/ubuntu/+bug/290129](https://bugs.launchpad.net/ubuntu/+bug/290129)

Basically, you just need to add 'acpi=noirq' to the kernel boot parameters.

---

