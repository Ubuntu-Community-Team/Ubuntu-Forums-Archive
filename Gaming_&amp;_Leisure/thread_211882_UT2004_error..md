---
title: "UT2004 error."
date: 2006-07-09
forum: Gaming &amp; Leisure
---

### Post by andy- on 2006-07-09
Been googling, searching, and asking around for about an hour now. No one seems to have an answer for me. I've tried reinstalling the game twice, patched it twice, checked video drivers, everything is up to date and ready to go as far as I can tell.

After I load up UT2004 I get the splash start screen for a split second, after which it shuts down and gives me the following error message:

[LIST]
[*]andy@andy-desktop:~$ ut2004
[*]Can't find 'ini:Engine.Engine.GameEngine' in configuration file

[*]History:

[*]Exiting due to error
[*]andy@andy-desktop:~$
[/LIST]

Note: there are no sounds from speakers, no sounds from the tower itself. (CD never starts spinning)

I've asked the same thing on UT official support forums, hopefully someone has a solution.

Thanks in advance. :)

---

### Post by Perfect Storm on 2006-07-09
Sounds like permission problems. Have you by any chance started ut2004 just after you installed it by hitting the start ut2004? (if you installed it with sudo sh /blah/blah/blah?) If so .ut2004 in your home directory have the "wrong" permission.

---

### Post by andy- on 2006-07-09
> **Artificial Intelligence said:**
> Sounds like permission problems. Have you by any chance started ut2004 just after you installed it by hitting the start ut2004? (if you installed it with sudo sh /blah/blah/blah?) If so .ut2004 in your home directory have the "wrong" permission.

I did! Right after installation I hit [Yes] to run game. And yes, I used sudo sh blabla. So how do I fix the permission? Should I re-install, not start the game after? Patch it first? (Keep in mind I'm very new to linux.) :D 

Thanks in advance.

---

### Post by Perfect Storm on 2006-07-09
sudo chown -R **<username>**:**<username>** /home/**<username>**/.ut2004/


Next time when you install ut2004. exit the installer first and then ut2004. If you want to reinstall it you have to delete .ut2004 in your home folder first.

---

### Post by andy- on 2006-07-09
Awesome, that fixed the problem. Now I have to play with this problem:

[LIST]
[*]andy@andy-desktop:~$ ut2004
[*]open /dev/[sound/]dsp: Device or resource busy
[*]Couldn't set video mode: Couldn't find matching GLX visual


[*]History:

[*]Exiting due to error
[*]andy@andy-desktop:~$
[/LIST]

](*,)

---

### Post by Vexmaster on 2006-08-10
I have the same problem as well.....:(

---

