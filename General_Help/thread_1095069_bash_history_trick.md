---
title: "bash history trick"
date: 2009-03-13
forum: General Help
---

### Post by neoguy on 2009-03-13
Hi, dudes!

Some time and somewhere (maybe freebsd) I've seen such trick.

**##Trick Description**

If you press "Up arrow" button several times you will browse through you command history: 
[FONT="Courier New"]%
% ls
% ssh localhost -u root
% exit[/FONT]

But if you type several chars of command (for example [FONT="Courier New"]'ss'[/FONT]) and press UP key - you will browse throw command from history filted by this chars:
[FONT="Courier New"]% ss
% ssh localhost -u root
% ssh localhost
% ssh localhost -u fry[/FONT]

**##End of Trick Description**


Is it possible turn this feature in bash (defalt shell in Ubuntu family distros)?

Thank you a lot!

--
Sergei O. Udalov

---

### Post by roccivic on 2009-03-13
```
man history
```

---

### Post by neoguy on 2009-03-13
thanks! i'll try :)

---

### Post by heindsight on 2009-03-13
have a look at [thread=1024973]this thread[/thread]

---

### Post by neoguy on 2009-03-13
This one is the solution:
[http://ubuntuforums.org/showpost.php?p=6461999&postcount=7](http://ubuntuforums.org/showpost.php?p=6461999&postcount=7)

heindsight, thank you very much! my dreams came true

---

