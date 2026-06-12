---
title: "Undo change in Unity done with CCSM"
date: 2016-02-22
forum: Desktop Environments
---

### Post by deatinor on 2016-02-22
Good afternoon,

by mistake I've made some changes to Unity with CCSM. In particular before:
[LIST]
[*]dragging a window to the top caused it to magnify, now nothing happens
[*]the shortcut super+left/right caused it to magnify to the left/right, now nothing
[*]with alt+tab before I had all the windows of an application grouped together and with a big icon on screen, now I have all windows opened and very little icons
[*]The shotcut alt+~ doesn't work anymore
[/LIST]

I don't know what caused it, I tried uninstalling CCSM but nothing happened. I've searched on many posts but I didn't find any solution.
I use Ubuntu 12.04

Do you have an idea of the problem and what can I do to solve it?

Thank you very much!


[EDIT]
Then I noticed that the problem was not caused by CCSM, but by missing drivers that caused Ubuntu to run Unity 2D.
See my last answer for detail.
[\EDIT]

---

### Post by grahammechanical on 2016-02-22
Compiz Configuration Settings Manager (CCSM) is just a tool. As you have found out, uninstalling CCSM does not revert the changed configuration files back to their default values. But, CCSM does have options to reset to default values. 

Regards.

---

### Post by deatinor on 2016-02-23
Thank you for your answer.
I've tried to reset CCSM to the default values following some guides. I think I've done it, but nothing changes.
I'm starting to think that it may be something else, but it seems strange.

---

### Post by mc4man on 2016-02-23
The first 2 mentioned are from the grid plugin, haven't used 12.04 in so long don't know about the tab switcher.

---

### Post by deadflowr on 2016-02-23
12.04 also uses unity2D.
Perhaps you are running that,
which doesn't use those features. (Me thinks)
Just a guess, though.

---

### Post by deatinor on 2016-02-25
I finally solved. I was really running unity2D thank you for the suggestion.
In my case the problem is that there where some missing drivers of the graphic card, I followed the first reply of this post to solve: [http://askubuntu.com/questions/325037/installing-nvidia-drivers-on-ubuntu-12-04](http://askubuntu.com/questions/325037/installing-nvidia-drivers-on-ubuntu-12-04)

I change the first post, since CCSM didn't cause the problem.

---

