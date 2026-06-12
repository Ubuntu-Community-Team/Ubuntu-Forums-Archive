---
title: "Dolphin drag and drop behaviour problem"
date: 2008-04-29
forum: Desktop Environments
---

### Post by kirys on 2008-04-29
Hi all, today I've noticed a strange behavior problem of Dolphin under Kubuntu 7.10.

It is realated to the scrolling
Here is how I can reproduce it
Create a directory with a lot of subdirectory, enough to have 4 or more lines of dirs into a dolphin window.

Now scroll a little down, enough to have have some lines hidden by the scrolling (2 should suffice) leaving at least the same numbers of lines plus one of dirs visible (so if you have hidden 2 lines you should have at least 3 visible lines).

Now copy, using drag and drop, a file to one of the directory of the visible lines, it should not copied to the dir you've dropped it into but on the dir that is located x lines over that column (where x is the number of lines hidden by the scrolling)

Do anyone have the same problem?
Thank you
Kirys

---

### Post by kirys on 2008-05-02
no one can reproduce this problem?

---

### Post by Xiong Chiamiov on 2008-05-03
Hmm, that could possibly be the problem I've been having.  I noticed that sometimes I lose my files because they get put in random folders other than the ones I thought.  You should probably file a report on Launchpad.

---

### Post by kirys on 2008-05-03
OK 
I'll report it.

---

### Post by kirys on 2008-05-03
It seems a known problem since 2007-10... strange noone find a solution yet.

---

### Post by Xiong Chiamiov on 2008-05-04
For those interested, the launchpad bug report is [here]("https://bugs.launchpad.net/ubuntu/+source/dolphin/+bug/152788").

---

