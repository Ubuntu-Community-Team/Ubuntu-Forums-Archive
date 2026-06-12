---
title: "`whoami`"
date: 2007-07-17
forum: Dell  Ubuntu Support
---

### Post by pepage on 2007-07-17
I am getting ready to install third party drivers for my new Epson Perfection V100 scanner. According to instructions, I am to first enter the command: sudo addgroup `whoami` scanner

I understand the new group name will be scanner and I ASSUME the username, `whoami`, is a wildcard for all users. My problem is I can find no documentation  on `whoami` so I can understand   what I am doing. Can someone explain or point me to a document that explains `whoami`?

---

### Post by yabbadabbadont on 2007-07-17
```
/home/daffy $ whoami
daffy
```
All that command does is return the username of the person who is running the command.  The back-tick marks tells the shell to run the whoami command first, then return the value so that it can be used with the addgroup command.  Run "man addgroup" without the quotes in a terminal window for details on that command.

---

### Post by yabbadabbadont on 2007-07-17
Actually, after having read the addgroup manpage, I doubt that the command will work the way that the scanner provider thinks that it will.  You'll have to try it and see.  You may want to post the full set of instructions so that others can look them over and see if there are any obvious problems.

---

### Post by fjgaude on 2007-07-17
I would think the "whoami" means you should put your username there, and of course, without the quote marks.

frank

---

### Post by fjgaude on 2007-07-17
BTW, where do the third party drivers come from? Scanners, along with printers, have always been an issue with Linux, especially if you wish to get full function out of them.

frank

---

