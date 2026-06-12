---
title: "compiz -- is it a virus???"
date: 2010-04-22
forum: Desktop Environments
---

### Post by jvbn on 2010-04-22
I know, it is NOT a virus, but it seems to behave like one. After installing it for the first time, I cannot get rid of it, not even making changes in the configuration editor. I have declared that my Windows Manager is Metacity, but Ubuntu seems to ignore that. If I uninstall compiz, that is the last time I can properly log in. I either get a black screen or the title bars are missing. I then have to log out and log into Xterm and reinstall compiz and run the compiz --replace command. Then I can log in again. How can I get completely rid of compiz and go back to using Metacity with animations and all. Is that possible? Or once you have installed compiz you are done for good? 

Can anybody please help me with this. Please, keep in mind that I am a complete beginner. I have used Ubuntu for only one moth, so bear with me if what I am asking is something too basic. Thanks!

---

### Post by iponeverything on 2010-04-22
If you right click and on destop and turn off effects, compiz is turned off.

---

### Post by Native Dialect on 2010-04-23
Compiz replaced metacity as the official Ubuntu window manager, since Ubuntu 7.1. You can use other window managers, but Compiz is integrated into the system. Not sure if it can be fully removed.

---

### Post by jvbn on 2010-04-23
Thank you very much for your replies. I have finally solved this. What I did was uninstall (purge) compiz, edit the Configuration Manager to make sure that Metacity was my Windows Manager. Lots of things went wrong at that point (title bars disappeared, etc.). 

So I opened a terminal and typed in "metacity" and the bars reappeared. But when I closed the terminal, they disappeared again. 

Then, I thought that maybe I could solve that by adding the command "metacity" to the Startup Applications menu. It worked like a charm. 

Mind you, the option to activate Visual Effects is not working, and I suppose that it is because I removed everything to do with compiz. But I don't need visual effects, and my PC is now working really well. 

So, thanks a again for your help.

---

### Post by mcduck on 2010-04-23
> **Native Dialect said:**
> Compiz replaced metacity as the official Ubuntu window manager, since Ubuntu 7.1. You can use other window managers, but Compiz is integrated into the system. Not sure if it can be fully removed.

Actually it didn't.

Both Compiz and Metacity are installed by default, and when Gnome is loaded a check is made to determine if your system is capable of running the desktop effects or not. If it is, the window manager is set to Compiz, otherwise Metacity is used.

Also, the Desktop Effects settings in the Apperance dialog toggles between running Metacity (set the desktop effects to "none" and Compiz with two different preset configurations.

---

