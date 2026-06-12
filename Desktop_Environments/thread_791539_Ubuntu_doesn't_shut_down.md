---
title: "Ubuntu doesn't shut down"
date: 2008-05-12
forum: Desktop Environments
---

### Post by vocs on 2008-05-12
Now every time I try to shut down or reboot the system from gnome, the menus disapear and on the screen there are only the wallpaper and the mouse cursor. Ubuntu isn't able to complete the halt process. So I always have to press ctrl+alt+f1 and shut down my system with "sudo halt". How can I solve this problem?

---

### Post by hermes0710 on 2008-05-12
Are you running on a fresh installation or upgrade?

---

### Post by vocs on 2008-05-12
Fresh installation. It was all fine some days ago, maybe a service doesn't close properly now, but the system shut down correctly by the terminal ctrl+alt+f1

---

### Post by hermes0710 on 2008-05-12
When you turn to ctrl+alt+f1 doesn't it have any log on what it's doing?

---

### Post by vocs on 2008-05-12
At the top of the screen it's written:

kinit: name_to_dev_t(dev/disk/by-uuid/....I don't remember.....) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/......I don't remeber.....
kinit: No resume image, doing normal boot...

---

### Post by hermes0710 on 2008-05-12
Ok. Let's try this. Create a new user (let's say "bob") and login as "bob". Try to shutdown. Is this still happening? If not then it's definitely a setting in you home folder.

---

### Post by vocs on 2008-05-12
I've just created the new user "bob" and everything works fine if I login with that. How can I fix my current user home folder?

---

### Post by hermes0710 on 2008-05-12
Check if there are differences between the two users in:

"System>Preferences>Sessions". Other than that, you will have to wait until i get home so i have my box to work on...

---

### Post by vocs on 2008-05-12
In "System>Preferences>Sessions" there are no differences between the users in the first and third tab. In the second tab there are some differences since I don't use compiz and graphical effects with my main user.

---

### Post by hermes0710 on 2008-05-12
Try using compiz and g.effects with your main to see if that is the problem

---

### Post by vocs on 2008-05-12
I enabled compiz and g.effects but the problem still remains. However some days ago the halt process was running fine even with compiz and g.effects disabled

---

### Post by vocs on 2008-05-12
If I type "sudo reboot" or "sudo halt" by the terminal in gnome, the system shut down properly. The problem occurs only when I use the menu System>Exit. Can anybody help me?

---

### Post by afilios on 2008-05-12
Same situation here. Fresh installation of 8.04. The other users shut down normally, Me only using Ctrl-Alt-F1.

---

### Post by vocs on 2008-05-13
bump

---

### Post by hermes0710 on 2008-05-13
Without shutting down, go to the terminal: ctrl+alt+f1 and type ```
sudo /etc/init.d/gdm stop
``` and post the output if any and then ```
sudo /etc/init.d/gdm start
``` to have it started again

---

### Post by vocs on 2008-05-13
There isn't any strange output when I stop the gdm service

---

### Post by vocs on 2008-05-14
bump

---

### Post by Ozzin on 2008-05-18
Did you install Keytouch? Might be the cause; see [https://bugs.launchpad.net/ubuntu/+bug/186713](https://bugs.launchpad.net/ubuntu/+bug/186713)

---

### Post by vocs on 2008-05-19
Thank you very much! The problem was caused by keytouch

---

