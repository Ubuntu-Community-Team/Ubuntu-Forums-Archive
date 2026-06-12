---
title: "crippled desktop environment  after a particular reboot"
date: 2011-05-21
forum: Desktop Environments
---

### Post by almy on 2011-05-21
_**xubuntu 11.4**_ . my **VLC** was still playing when i pressed "reboot",it didn't reboot till i closed the VLC window,then it rebooted  to a crippled desktop environment.(i regenerated the problem 3 times)

_description of the crippled environment _

[LIST=1]
[*]in the setting manager the "windows manager tweaks" and "windows manager" were empty(no settings in them)
[*]no full screen with videos and pictures
[*]no transparency effects
[*]windows didn't have the title bar,and can not be moved (except firefox)
[*]open windows didn't appear in the panel
[*]message boxes appeared embedded in the parent window
[*]alt+tab didn't work
[*]and more
[/LIST]

so i created a new user and his desktop was healthy

 i repeated the reboot procedure described above, and the same problem appeared  again and again.


thanks in advance ,and apologies for my poor English 
:)

---

### Post by Copper Bezel on 2011-05-21
By the sound of it, the "crippled desktop" doesn't have xfwm4, the window manager, running. What happens if you run xfwm4 --replace ?

---

### Post by almy on 2011-05-21
**yes ,it worked. **
many thanks copper

---

### Post by Copper Bezel on 2011-05-21
Excellent. = ) Please mark the thread as solved, if you would (thread tools in the upper right.)

---

