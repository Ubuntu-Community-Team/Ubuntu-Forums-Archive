---
title: "Help! University Project"
date: 2012-09-27
forum: Education &amp; Science
---

### Post by YuKill on 2012-09-27
So I have this project at my university... for this project I have to find a 10-bit architecture. I already google it and got nothing. In fact, I found one named "Ferranti Mercury" which didnt helped much... 

Can anybody help?  In this project I have to design an 10-bit architecture, so I need an design of a 10-bit architecture already build.

---

### Post by 1clue on 2012-09-27
Wait.  You're trying to design one or you need to find a pre-existing one?

What is this for, an electrical engineering class or a computer programming class?

---

### Post by YuKill on 2012-09-27
In fact, I have to design a 10-bit architecture. Design its OpCode, adressing mode, instructions, pipeline... But just design...
As I dont have such knowledge to do such a thing out of the blank, i need some base. Besides, this design must have some reference. 
It is for a subject named "Computer Architecture and Organization"... something like that

---

### Post by lisati on 2012-09-27
It's likely that the person who set the assignment wants you to think about the various components that go into the design of a CPU and how they communicate with each other.

By the way, from the [forum code of conduct]("http://ubuntuforums.org/index.php?page=policy"):
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

### Post by 1clue on 2012-09-27
OK forgive me for what might seem like an accusation, I don't know you from Adam and I don't really understand your intent.

Speaking from my own university experience you need to be really careful about what you use as a reference.  I don't know of any 10-bit processing systems, and if there are any I suspect your instructor has thoroughly researched it.

I would suggest you find an architecture which has both an 8-bit and a 16-bit "next generation" chip.  There are lots of them.  I believe you'll also find a few which had a 12-bit addressing mode.   Start with the 8-bit architecture since those are relatively simple.  Then look at its 16-bit family member, and see what changed.  Design your 10-bit system and take into account the issues the 16-bit architecture took into account, but only if they had something to do with the additional bits, rather than having something to do with backward compatibility.

I would avoid Intel's 808x chips.  They had an overly complicated addressing scheme.

Again be really specific with your references, and make sure you know the difference between referencing another work and copying it.

I still don't know if you're in a hardware class or a software class.  It sounds to me like a software/archittectural model, prelude to hardware design.

Good luck and have fun.

---

### Post by YuKill on 2012-09-27
Thanks... But I wouldnt copy it (my professor is kind of excentric... I myself didnt understood why did he gave us this project to do, since he didnt taught anything related to that... D=)

 I just needed some reference... something to base on. And, I'm not asking you guys to do my homework. I didnt ask for you to do a 10-bit architeture design to me, I just wanted some help in order to find some 10-bit architecture... since i was not finding..
D=

Thanks anyway... =D

---

### Post by doktorOblivion on 2012-09-27
Personally I would design something close to the old Univac Octal based architecture, using the extra bits to include some modern and useful items.  Of course you are thinking assembly language here, not sure how many Grad Students today get involved in that, normally they are more worry about OSGi, OSx or other more salient issues of our time.  However, if you do it corretly you will learn a lot and have basic understanding of how things like VMWare work.  I assume you are writing this in C?  Good luck, kind of sounds like it might be over your head, good chance to learn.

---

### Post by YuKill on 2012-09-27
Fortunately, my project is not that complicated...
I just have to... describe the components.. For example, how many bits I have to take for the cpu bus, how am I going to use that... How the operational code will work... What addressing modes it will gonna use...

Nothing to implement (for now). I just dont know what to put in this "project". And since this is a 10-bit architecture, I have no base of how do these bits are organized.

---

### Post by 1clue on 2012-09-27
Forgive the implication, we get all sorts of weird posts on Linux forums.

In my experience you can find all sorts of people who can gently nudge you to the proper course here, but historically speaking the Linux community is made of people who read the manual and figure it out on their own.  I seriously doubt you could find somebody to hand you your finished homework even if that was your intent.

What's the timeframe here?  Is this a months-long project or is it due soon?  If it's soon then you probably only need a framework.  I personally liked the days of 8-bit processors of the 80's.  If I were working on this assignment I would design a simple model similar to 6502 or 68000 with a single address space.  Keep it simple and be as complete as you can.

I would also try to work on all the expected components at approximately the same time.  That is, get a rough outline for each component before you start filling in the blanks.  Keep all the components at approximately the same level of detail.  This way you are likely to have the entire picture in your head, and you're more likely to find flaws in your design while there's time to fix them.

Good luck and have fun.

---

### Post by YuKill on 2012-09-27
It would be great if it was a 8-month project... Unfortunately this is a 7-day project... And now that I dont have enough time, I'm a little desperate... D=

I wish I had time to study and learn each component, which I dont have. =/

---

### Post by 1clue on 2012-09-28
So work on an outline, making multiple passes.  Make sure you have something for each component necessary.  That way you always have a 'complete' document, even if it doesn't have enough detail.  And who knows, maybe you'll get enough detail?

---

