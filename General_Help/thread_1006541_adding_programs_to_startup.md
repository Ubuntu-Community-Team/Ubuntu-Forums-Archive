---
title: "adding programs to startup"
date: 2008-12-09
forum: General Help
---

### Post by ShaolinF on 2008-12-09
hi guys

how can I add files to the startup folder via terminal in ubuntu 8.10?

---

### Post by oldos2er on 2008-12-09
System, Preferences, Sessions, Startup Programs.

---

### Post by ShaolinF on 2008-12-09
I know that and I tried it but it didnt work. So thats why I want to try via terminal instead. Any ideas?

---

### Post by oldos2er on 2008-12-09
Can you give more details beyond "it didn't work"? What exactly did you do, did you see any error messages and if so, what were they?

---

### Post by ShaolinF on 2008-12-09
I didnt see anything. I have setup a mysql server and added the mysql.server script to the session program and when I restarted it doesnt start the mysql server.. There are no errors or anything being outputted.

---

### Post by binbash on 2008-12-09
add your commands/scripts before exit : 

nano -w /etc/rc.local

---

### Post by ShaolinF on 2008-12-09
thanks the rc.local didnt work either :/

Here is the error from the log files:

> Dec  9 22:41:49 moe-desktop x-session-manager[4612]: WARNING: Could not launch application 'mysql.server.desktop': Unable to start application: Failed to execute child process "/usr/local/mysql/source/support-files/mysql.server" (Permission denied) 

Looks like a permission error, but Im not sure where and what needs changing..

---

### Post by binbash on 2008-12-09
please post the script or command

---

