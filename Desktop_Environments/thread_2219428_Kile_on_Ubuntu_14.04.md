---
title: "Kile on Ubuntu 14.04"
date: 2014-04-24
forum: Desktop Environments
---

### Post by Leandro_Ishi on 2014-04-24
Hello all,

I installed Ubuntu 14.04 and I really like Kile to edit latex documents. I tried some other editors, but I really think Kile is the best one by far. However, one thing in Kile is very annoying. On my machine, any changes I make in settings, like checking "Dynamic Word Wrap" or checking "Automatic Spell Checking", does not persist. In other words, these changes are applied while I have Kile opened. After closing and opening Kile again, all these changes are lost and I have to reconfigure Kile. I googled about this issue, but could not find a solution. I changed the owner of the ~/.kde to my user and gave permission to anyone to read and write to ~/.kde/share/config/kilerc (the file where kile stores his configurations). However, he always starts with his default config, like if it was the first run. I don't know what to do more, any help would be appreciated.

Thanks in advance.

---

### Post by ai.karanam on 2014-05-11
Hi, did you try to change the kile settings in settings > configure kile. In the dialog box, 
1. select editor > appearance option. Tick the dynamic word wrap in left pane. 
2. In the editing option, select spellcheck from left pane and check for "automatic spell checking enabled by default".
Click Ok. These change should persist. By the way, I am using Ubuntu 12.04 and kile version 2.1.0.

---

