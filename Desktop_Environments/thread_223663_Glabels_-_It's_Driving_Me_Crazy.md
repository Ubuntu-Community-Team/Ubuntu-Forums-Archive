---
title: "Glabels - It's Driving Me Crazy"
date: 2006-07-26
forum: Desktop Environments
---

### Post by mpierce on 2006-07-26
I think there's a song in that title.

Problem: Using glabels & glabels-data 2.1.2-2ubutntu1 on both my laptop and my server.

Printing works fine on both machines with an exception. Glabels cannot print to the HP Colorlaserjet 2550L. The printer hangs everytime. If I print the same file from my laptop, no problem. 

Obviously, the printer is correctly installed; samba is working properly as the printer is connected to the server (my laptop dual boots Kubuntu and XP pro). 

Any suggestions as to what might be causing this? All help appreciated.

---

### Post by mpierce on 2006-07-27
Solution found: Glabels will only print UTF-8 fonts and nothing else. 

Otherwise, it won't print or it will hang the printer. 

Issue resolved!

---

