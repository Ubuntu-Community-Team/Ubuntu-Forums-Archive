---
title: "Muliple sessions from Ubuntu OS"
date: 2010-10-04
forum: Desktop Environments
---

### Post by hisanju81 on 2010-10-04
Hello,
 
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Will it be possible to maintain multiple sessions from Ubuntu?[/SIZE][/FONT]
 
[SIZE=2][FONT=Helv][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Actually we are working on one open source application and we have setup this application on one of our Ubuntu machine and this would act as a server for other developer's windows machine. [/SIZE][/FONT]
 
[SIZE=2][FONT=Helv]Is any utility available(preferable open source) using which we will be able to access the Ubuntu server from all 4-5 developer's Windows machines?[/FONT][/SIZE]
 
[SIZE=2][FONT=Helv][FONT=Helv][SIZE=2][FONT=Helv][SIZE=2]Our requirement will be to access the whole system including console and GUI (same like remotely access) by using different sessions so that all 4-5 developers can start work together on the same Ubuntu machine.[/SIZE][/FONT]
 
[SIZE=2][FONT=Helv]Thanks in advance.[/FONT][/SIZE]
Sanjay[/SIZE][/FONT][/FONT][/SIZE][/SIZE][/FONT][/FONT][/SIZE][/SIZE][/FONT]

---

### Post by macanudo on 2010-10-07
You can easily start multiple x sessions via ssh and use something like vnc to access them.

-Set up a user profile for each user
-Install ssh client/server on the Ubuntu box
-Use cygwin w/ ssh on the windows boxes
-Install vncserver on the Ubuntu box, and get the client for the windows boxes
-ssh from the windows box to ubuntu, run vncserver
-run the vnc client, and access the x session you just started on the ubuntu box

---

