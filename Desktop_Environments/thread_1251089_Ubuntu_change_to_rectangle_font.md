---
title: "Ubuntu change to rectangle font"
date: 2009-08-27
forum: Desktop Environments
---

### Post by huahsin68 on 2009-08-27
Hi,
 
I am having a critical situation where I have no clue on how this is going to solve. I am using Ubuntu 9.04, not using Compiz or any 3D rendering. Everything back to the default setting. 
 
Yesterday I did an update through the update manager, I didn't restart my Ubuntu, and just Hibernate the PC. At the following day, when I turn on my PC, the font gone. All the font are change into rectangle since in log-in screen, even though I have log-in, the font in desktop environment are change into rectangle as well. This is same to the gnome-terminal too. In conclusion, [SIZE=4][COLOR=red]I can't see any proper 'English' text[/COLOR][/SIZE]. But I can see the start up screen when Ubuntu boot up.
 
Is this cause by the previous update? Do I need to restart my PC everytime I did an update? How to solve the problem in this 'rectangle' environment?
 
Hope I am giving enough information here.
 
 
THanks @!

---

### Post by huahsin68 on 2009-08-28
Hi all,

I have fixed my problem. Recently I have installed Pango v1.24 as required by the project. Later I did an update through Update Manager. I did not go through what was being update during that time. Thus in my next login, I got this rectangle text problem.

Here is the solution, after booting up the Ubuntu 9.04 and come into the login screen, press Ctrl+Alt+F2 to switch to run level 2, and then uninstall the recently installed pango v1.24 by issue the command [SIZE=3][COLOR=DarkRed]sudo make uninstall[/COLOR][/SIZE]. Root access right is required. And then restart Ubuntu will solve the problem.

Basically I do not really understand what run level stuff exactly is although I have been reading some text from wikipedia, I just need a way for me to go back into console mode where I can see the 'English' text and issue some command to the computer. I can't do this using the gnome-terminal because all text was change to rectangle.

Although I have solve this problem, but it create another problem for me where I require pango library in my project. And now I have uninstall it. Sign~ Anyhow, problem solved.

EDIT: Thanks to[ this post]("http://ubuntuforums.org/showthread.php?t=455987") on reminding me the problem.

THanks @!

---

