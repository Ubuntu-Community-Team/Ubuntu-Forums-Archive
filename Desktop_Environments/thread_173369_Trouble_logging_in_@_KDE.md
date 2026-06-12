---
title: "Trouble logging in @ KDE"
date: 2006-05-10
forum: Desktop Environments
---

### Post by Icke on 2006-05-10
Hello,

I have been dualbooting XP/Ubuntu and XP/Kubuntu for about a year now without too much trouble, but now I have a problem I can not seem to solve.

When I boot Kubuntu everything seems to go fine and I get to the KDE login screen. **When I login however, the screens goes dark, and I see the hourglas but after two seconds, it goes back to the login screen :( .**

When I try to login with a different (not a good one) password, the GUI tells met the password is incorrect, so the password is not the problem. 

I can log into the console perfectly.

I don't rember doing some crazy stuff with my videodrivers or X.org or something :( .

Using only the console is kinda cool, but it is not the handiest of interfaces for a GUI adept like me, so I really hope that somone can help me :) .

I'm using a laptop with an ATI X600 card, but like I said, II never really had problems with that and I don't remember changing those settings.

Windows XP boots fine.

I created a new user, but tying to log with that results in the same error.

---

### Post by vvl on 2006-05-10
Try having a look at /var/log/syslog after trying to log in to KDE, and paste whatever kdm complains about (if you can find anything).

---

### Post by ComplexNumber on 2006-05-10
**Icke**
how much space is left on your hard drive? if you  find that you are  nearly up to your limit, uninstall some unimportant stuff. then try to login again.

---

### Post by Icke on 2006-05-11
[QUOTE=ComplexNumber]**Icke**
how much space is left on your hard drive? if you  find that you are  nearly up to your limit, uninstall some unimportant stuff. then try to login again.[/QUOTE]

Hmm that might be the problem, I installed some new software the last time I normally booted...

What would be the best way to check the remaining diskspace using only the commandline?

---

### Post by JShadow on 2006-05-12
I'm having a similair problem on my laptop after installing kubuntu-desktop on my dapper ubuntu install. No xorg errors.

---

### Post by ComplexNumber on 2006-05-12
[quote=JShadow]I'm having a similair problem on my laptop after installing kubuntu-desktop on my dapper ubuntu install. No xorg errors.[/quote] you say "similar problem". what is the exact problem, with enough details for people to help you?

---

### Post by Icke on 2006-05-13
[QUOTE=Icke]Hmm that might be the problem, I installed some new software the last time I normally booted...

What would be the best way to check the remaining diskspace using only the commandline?[/QUOTE]
nevermind that, I found out the command: "df -h"

But how much free space should I have available to solve for this problem? 10MB? 100MB? 500MB?


EDIT: fixed it (thanks to mart from #kubuntu)!

I did switched to a text terminal (ctrl+alt+1), did "df -h" and indeed, my linux partition was 100% full. So I did an "apt-get clean", that gave me 1,6GB of free space :D.

However, when I logged in, I feared I deleted too much, because the kicker and window manager did not start automatically (could start them by hand). But luckily this was only because I logged in a "failsafe" session. So I logged out, selected my "default" session and logged in, and now everything is as new :D .

---

### Post by premchapagain on 2006-05-26
I have exactly the same problem today. And it may very well be the space problem. I will some clean up to make more space and see what happens.

---

