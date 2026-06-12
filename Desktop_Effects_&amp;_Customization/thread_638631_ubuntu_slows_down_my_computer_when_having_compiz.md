---
title: "ubuntu slows down my computer when having compiz"
date: 2007-12-12
forum: Desktop Effects &amp; Customization
---

### Post by Helbo15 on 2007-12-12
Hi 

I've got this system 

3Ghz P4 
2gb ram 
ATI RADEON 9700 pro 128mb ram

and it starts with I'm logging in the first 10-15 min it runs fine but then it starts to slow down everything I do untill about 20-25 mins. after start it is at a state were I allmost can't do anything not even move the mouse without waiting 5-10 sec. on it to do so 

any idea what it could be wroong ?

I've installed compiz and wine and wine-doors and that's about it i think hmm oh yea and some music programs of some sort to my littlebrother don't know what they do but he liked them.

but the first time I noticed the slowdown was after I've installed wine and wine-doors they were the last thing I installed at the computer

however I have a feeling it's the compiz that is causing the slowdown just don't know what to do about it ?

---

### Post by tgalati4 on 2007-12-12
Sounds like a memory leak.  Run:

>free

often in a separate terminal and make note of your free RAM during your session.  As it fills up, you will start to swap and that will slow a machine down.  Wine uses quite a bit of RAM.

---

