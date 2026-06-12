---
title: "[fluxbox] Slit questions"
date: 2008-03-02
forum: Desktop Environments
---

### Post by Epic Plecostomus on 2008-03-02
First off I should have posted here.   Mods, wanna merge/move/delete my thread in beginner talk with this one?

I just installed Fluxbox, and set up the right click menu...   and I realized the "slit" is either non-operational or not installed.      

I'm betting I have something set wrong, or I'm just plain overlooking something,  can ya'll point me in the right direction?

---

### Post by spupy on 2008-03-02
The slit is not visible if there is nothing in it. It is not a toolbar, rather just a place. 
[http://dockapps.org/](http://dockapps.org/)    you can find some apps for the slit. Most of them are in the ubuntu repositories. You just run them from the command line with a & at the end and they appear in the slit.

Edit: Type 
```
fluxbox -i
```
to see if you have SLIT in the compile options, but i think it's there by default.

---

### Post by Epic Plecostomus on 2008-03-02
Yeah I got that answer in the other thread I started.

Now how do I automate the load process so the apps in question will be there when I boot?

---

### Post by spupy on 2008-03-02
Put their commands somewhere in ".fluxbox/startup", but before the last exec command. And make sure to add "&" at the end of the command.

---

### Post by Epic Plecostomus on 2008-03-02
YAY!   Thank you.

---

