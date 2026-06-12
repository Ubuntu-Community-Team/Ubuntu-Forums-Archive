---
title: "Linux command for Create Launcher"
date: 2008-10-29
forum: Desktop Environments
---

### Post by lsutiger on 2008-10-29
I was wondering if there is a single command for the right-click-->Create launcher in the linux system or is it in 'the code'?

---

### Post by ddrichardson on 2008-10-30
The launcher in some desktops is a seperate thing or a wrapper for creating links but the command line equivalent is:
```
ln -s original link
```

---

### Post by lsutiger on 2008-10-30
Thanx for the reply. What I am doing is making a login remote server, but it needs to be locked down. The only 'problem' I have is with the mouse right-click still allows to create a launcher. The right person could cause a little chaos. I am not too worried, as most of the users are not too technically inclined.

For right-click Send Mail I just deleted the nautilus-sendto command. I was hoping to do the same thing with right-click create launcher.

---

### Post by ddrichardson on 2008-10-30
Ah OK, try [this]("http://ubuntuforums.org/showthread.php?t=309099") thread.

---

### Post by lsutiger on 2008-10-30
DUDE???!!???!! Where did you find that so quick? I googled my fingers to nubs looking for that answer!!! I googled "disable right click gnome" and things of that sort and you wouldn't believe how many ppl are looking for the answer. Many forums I went to had posting saying it was not possible...I knew it could be done :)

Thanx 1000 million times!!

---

### Post by ddrichardson on 2008-10-30
Just lucky I guess. Depends what you google for - its usually best to try things like nautilus rather than gnome or kde to narrow it down, hope it helps.

---

