---
title: "RE posted : Diablo Problem (unanswered)"
date: 2007-06-10
forum: Gaming &amp; Leisure
---

### Post by Dr Gryme on 2007-06-10
I'm having trouble with playing. Allow me to elaborate. It wont let me go into single player mode, it shuts down. Also, when i sign into my d2 account, it loads, and blinks, then shuts down. I have yet to see a diablo2 character in wine. I think it might have something to do with the characters but i'm unsure. Can you help me out?

---

### Post by jso2897 on 2007-06-10
I would do a search with "diablo" and read the threads. Make sure you have the latest version of Wine installed. Make sure your video drivers are current and working right. Use "winecfg" to configure Diablo to run in Win 98 (LOD can run emulated in 98 or XP). Diablo has a lot of isuues with reading the CD - I play it with a noCD crack. Just try different things. It took me all day to get Diablo and LOD installed and working, but I finally got it - you will too. This game really does work in Wine - I promise.:D

---

### Post by Dr Gryme on 2007-06-13
Ok, i have done everything in that tutorial and everything that is feasible. I've also asked my buddies that use Wine for D2 and THEY don't even know how to help me. 

When i try to go to one of the sections that would reveal a character, a little error message comes up saying: "Hey Guys, We got a big error here :[" What the hell do i do with that? It tells me we have a big error, what is the error. Can't anyone help me or guide me to where i have to go?!? PLEASE I BEG OF U!!

---

### Post by JoSch on 2007-06-13
This message usally comes up, if you use a noCD crack. Do you use such?
Do you have accelerated graphics? Do a glxinfo | grep direct if unsure.
Is your wine in default stance? You can delete the .wine directory in your home dir to make sure.
Is your CD drive listed as CD-ROM in your winecfg? It mustnt be listed as harddrive.
Does it install the game, the expansion and the 1.11b patch without problems?
If you want to use a crack - try different ones and make sure you copy all mpq files from the cds into your install dir.
Did you patch the game to the right version before installing the crack?
What wine version do you use?
Just today I installed Diablo II with Expansion, 1.11b patch, nocd crack, bnet support and plugY on four different linux boxes with wine 0.9.38 - it has to work.
Just start from scratch with a new .wine dir if you messed sth. up.

---

