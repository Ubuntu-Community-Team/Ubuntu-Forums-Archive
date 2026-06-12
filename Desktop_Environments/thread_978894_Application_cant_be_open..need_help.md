---
title: "Application cant be open..need help"
date: 2008-11-11
forum: Desktop Environments
---

### Post by AznPat on 2008-11-11
i recently update to the new version of ubuntu 8.10,but for some reason when i am trying to open the application tab it doesn't work at all..i can't even scroll down..can someone help me i just need it to work because thats the only way i can get my compiz to start..if someone can tell what i need to do i would appreciate it..thank you

---

### Post by anando on 2008-11-11
Maybe you have a screwed-up gnome configuration file. In your situation, I would try to move all my previous gnome stuff to a backup directory and try logging in again. 

In a tty session (Ctrl+Alt+F1), 

```
login 
cd $HOME
mkdir -p gnomeBkup/
mv .gnome* gnomeBkup/
mv .gconf* gnomeBkup/
mv .compiz gnomeBkup/
mv .config gnomeBkup/
mv .gtk* gnomeBkup/
```

Nw logout, go to the gdm screen by pressing Ctrl+Alt+F7 and login. Hopefully, it will sort things out for you.




> **AznPat said:**
> i recently update to the new version of ubuntu 8.10,but for some reason when i am trying to open the application tab it doesn't work at all..i can't even scroll down..can someone help me i just need it to work because thats the only way i can get my compiz to start..if someone can tell what i need to do i would appreciate it..thank you

---

