---
title: "display goes blank after gnome logout or terminal switching"
date: 2005-12-03
forum: Desktop Environments
---

### Post by Roybotnik on 2005-12-03
Hi friends,

I'm having a strange problem.  Whenever I log out of gnome, my display goes completely blank.  This problem also happens if i try to ctrl+alt+backspace to reset the xserver, ctrl+alt+fkey to switch to another terminal, and even when I shut down(screen goes blank immediately after I click shutdown, it doesn't display the normal shutdown 'stuff').  I have used Ubuntu for a good while, and this is my first time ever having this problem.  I have a Radeon X800XL with fglrx 8.16.20 drivers installed from the Ubuntu repos.  uname -r returns 2.6.12-10-386.  Any help would be appreciated!

---

### Post by Roybotnik on 2005-12-03
;_;

---

### Post by Roybotnik on 2005-12-03
Last bump...I really need help with this, it's making linux pretty much completely unusable for me..anytime something crashes and messes up my desktop(i.e. games) I have to hard reboot.

---

### Post by aysiu on 2005-12-03
This topic has had eleven views, apparently.

It's not as if eight people thought, "Hey, I think I can solve that, but... I'm going to ignore it instead."

I may be making incorrect assumptions, but I'm going to assume the other seven people who viewed the thread and didn't answer thought, like me, "I wish I could help, but I have no idea what that problem is."

If someone can jump in and fix it, that's great. If not, it's probably just because your problem is obscure.

---

### Post by [Jedi] on 2005-12-04
Same problem for me, Kubuntu 5.10, kernel 2.6.12-10 and fglrx 8.19.10.
I've tryied a lot of different xorg.conf files, but still found no solution. Switched back to Kubuntu ati embedded drivers without TV-Out.

I'm really disappointed...

---

### Post by zi99y on 2005-12-08
me too, I'm having the same problem with my laptop running the fglrx drivers. only I can reboot ok, it's just logging out or switching out of the gui using ctrl-alt-f1 or ctrl-alt-bkspace that crashes it. Real pain.

I'm having a lot of ubuntu disasters at the moment, and have been working very hard at getting it all working, but this may be the straw that breaks my hump if there's no fix for it :(

---

### Post by zi99y on 2005-12-09
Can anyone with this problem state whether it has always happened since Ubuntu install? As mine was fine to begin with, but have installed/configured so much I don't knwo where to start to troubleshoot it.

However I have tried replacing "fglrx" with "vesa" in the xorg.conf and the problem still persists.....

---

### Post by RSX311 on 2005-12-09
I've been having the same problem too with fglrx drivers, couldn't figure out what the problem was.  I think it's the drivers because when I switch to VESA it works fine.

---

### Post by rezzakilla on 2005-12-15
My system works fine, but get the same probleme, i have a same card....:confused:

---

