---
title: "where is shutdown??"
date: 2007-05-11
forum: Desktop Environments
---

### Post by azray on 2007-05-11
Since going Kubuntu I find that my restart button is gone. I now have only log out, lock screen, switch user, suspend and hibernate.

What to do?

---

### Post by JonahBird on 2007-05-12
I'm a noob myself, but I have had the same thing when I accidentally logged in as root. also I felt I had to respond to a fellow in need here in Tucson.

when I cant shut down (for various reasons - usu. when I mess somthing up;) I go for 
ctrl+alt+sysRq+s followed by  
ctrl+alt+sysRq+u then
 ctrl+alt+sysRq+b
the first one synchs the something or other the second one unmounts the third reboots. I was told to always do those three and always in that order...
hope that helps

---

### Post by NikoC on 2007-05-12
I'm not really sure where to find it but you can always type in a terminal
```
sudo shutdown -h now
```

or

```
sudo shutdown -r now
```

Which are for shutdown and reboot respectively.

---

### Post by Obor on 2007-05-12
its a bug that is being worked on [https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695](https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695)
I believe there is a patch in the feisty proposed repo.

I had the same problem in Feisty when I installed both kde and gnome. Only one can control your session. Basically GDM is still your display manager. There is way to change it but I can't remember how I did it. 

I'll post back if I find it.

---

### Post by Obor on 2007-05-12
Found it
```
sudo dpkg-reconfigure gdm
```
and choose kdm as the default display manager (sudo dpkg-reconfigure kdm should do the same thing)

---

### Post by azray on 2007-05-12
obor
tried the reconfigure, still missing....

---

### Post by ernstblaauw on 2007-05-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695/](https://bugs.launchpad.net/ubuntu/feisty/+source/kdebase/+bug/64695/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I also experience this bug. It is already in Launchpad.

---

