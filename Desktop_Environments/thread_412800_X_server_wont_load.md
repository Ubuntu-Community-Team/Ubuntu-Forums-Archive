---
title: "X server wont load?"
date: 2007-04-18
forum: Desktop Environments
---

### Post by lysergic on 2007-04-18
Hello there, i'm running Xubuntu Edgy Fit on my laptop,, i just finished installing and configuring everything over the course of the day.. However, since playing around with Live CD's yesterday my battery has just stopped working :S its been fine for ages, but now doesnt power the laptop up.. anyways, thats not the problem.. I was in the middle of a session and accidently pulled out the power cord forgetting the battery didnt work, and it just switched off.. I switched the computer back on, and it all seemed to boot fineish, altho Xubuntu doesnt give you any verbose kind of information about whats going on during bootup.. Anyways, it succefully completely loading, and is it went to load the X server it kinda flickers (like it does before it normally loads) however it doesnt actually load graphics, just stays completely black, and my harddisk continues to do something, i can even hear sounds when i press buttons.. 

How can i fix this problem? i dont even know how to get into the terminal.. This problem is something thats happened to me both with Kubuntu Dapper, and now Xubuntu Edgy.. Is this a problem with my laptop [IBM Thinkpad T22] do you recon? 

Please help me, im gonna be so annoyed if all the work ive done on this system is wasted and im gonna have to reinstall again :S

Also does anybody have any explanation for the complete random case of my battery not working anymore :S is the pii4_smbus module anything to do with this type of hardware??

Thank you

---

### Post by lysergic on 2007-04-18
ok, i seem to have fixed this problem.. seems pretty strange tho.. After being baffled about how to get to the CLI i found out entering the menu in GRUB lets you  load in "recovery mode".. from here i  reconfigured the X server, (not that i had a clue what i was doing, just pressed enter all the time) and then X loaded up :S, really weird, but it seems to be fixed now   :D

---

