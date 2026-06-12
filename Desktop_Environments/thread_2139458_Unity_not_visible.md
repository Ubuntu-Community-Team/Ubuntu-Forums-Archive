---
title: "Unity not visible"
date: 2013-04-26
forum: Desktop Environments
---

### Post by ramnaray on 2013-04-26
Hi,
On logging into ubuntu my unity, dash disappeared.I tried all the options posted in the form but of no use.I have a temporary hack to start unity every time I log into ubuntu(unit --reset).Any help for fixing this permanently is welcome.
Thanks.

---

### Post by nonparity on 2013-04-27
I am having the same issue too. still digging into it. will update here if I can fix it :)  maybe someone else on here will have an idea too.

---

### Post by grahammechanical on 2013-04-27
Did you try a different video driver? Tell us what doesn't work and we will not repeat useless advice. Tell us the Ubuntu version and we will not give instructions that do not work in your version. Stuff that works in 12.04 does not work in 12.10 or 13.04.

---

### Post by brickmack on 2013-04-27
Im having the same problem. I installed Ubuntu 13.04 (clean install on new computer), and Unity worked fine. Went through and removed a few packages included with it, restarted, and Unity was gone. I tied reinstalling unity and ubuntu-desktop (in case I accidentally deleted something they needed) but that didnt work. I can see my desktop and select ad right click on it, but the top and side bars are gone. I installed gnome and it works, and I can use Unity in the guest session.

Edit: Fixed it. Got a terminal open, opened CCSM ([COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install compizconfig-settings-manage[/FONT][/COLOR] to install, ccsm to run), and found that the unity plugin was somehow disabled. Not sure how hat happened, but its fixed.[COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]

---

