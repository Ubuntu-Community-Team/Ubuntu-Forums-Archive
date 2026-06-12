---
title: "Strange terminal behaviour"
date: 2008-08-22
forum: Desktop Environments
---

### Post by festerwim on 2008-08-22
Hi,

I'm seeing some strange behaviour in the Terminal and I was wondering if this is to be expected or some kind of bug. I have tested this on Ubuntu 8.04 but my colleague also tested this on his SUSE and it was the same.

Steps to reproduce:

1) Create a directory 'testdir'
2) Create a file in that dir called 'test.txt' and put 'Hello' in there.
3) Open a terminal and 'cd' into testdir
4) Delete testdir through nautilus. This succeeds without problems (In Windows XP, you get an error that the directory cannot be deleted as long as there is a dos-box open)
5) Do an ls in the terminal, still in that deleted dir
6) Create 'testdir' again (through Nautilus) and put an empty file in there called 'test.txt' again.
7) Do 'ls' again. You will see that there is a file 'test.txt' in there.
8) Now do 'gedit test.txt' from the terminal. The file is not empty!
9) Do 'cd ..' and 'cd testdir' again
10) Now do 'gedit test.txt' again. The file is empty!

I find this very strange. I encountered this problem when I updated a .sh file but I never saw my changes.

Is there anybody who has a clue why this happens or have I just found a bug after using Linux for 3 days :)

regards,

Wim

---

