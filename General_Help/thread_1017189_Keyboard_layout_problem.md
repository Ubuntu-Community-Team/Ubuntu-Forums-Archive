---
title: "Keyboard layout problem"
date: 2008-12-20
forum: General Help
---

### Post by simonlugi on 2008-12-20
Using Ubuntu 8.04 has been fine until a couple of days ago. Every time I boot up the keyboard setting is changed to a different setting (appears to be Greek alphabet). I have to go into System Preferences Keyboard and restore default setting.

Can anyone let me know in simple language how to fix this problem.

---

### Post by monkeyking on 2008-12-21
I would add

[PHP]setxkbmap us[/PHP]
in some startup script

That is if you want the amarican layout.
Otherwise change the last 2 chars to some thing else

---

### Post by simonlugi on 2008-12-21
Hi Thanks for the reply however not sure where I need to insert or change the script. Can you be e bit more specific Thanks

---

### Post by drs305 on 2008-12-21
> **simonlugi said:**
> Hi Thanks for the reply however not sure where I need to insert or change the script. Can you be e bit more specific Thanks

What monkeyking is suggesting is to put it into your Sessions Startup list. Open System > Preferences > Sessions > Add. Make a name like "setxkbmap_us" and in the command type: **setxkbmap us **  Click Add, then Close.

At startup this command would run and may reset your keyboard. You will just have to try it.

---

### Post by simonlugi on 2008-12-27
Thanks
That appears to have solved the problem.

---

