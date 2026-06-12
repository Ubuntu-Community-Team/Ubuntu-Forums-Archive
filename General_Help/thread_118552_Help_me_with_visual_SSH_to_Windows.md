---
title: "Help me with visual SSH to Windows"
date: 2006-01-17
forum: General Help
---

### Post by Perhaps on 2006-01-17
Hi, the question is: How can I open visual SSH tunnel to a Windows machine? Is possible?
I can reach the windows server by console, but I need to reach there visually. (I'm a rookie using KDE).

Thank you all.

---

### Post by schdefan on 2006-01-17
rdesktop lets you connect to a Windows machine in graphical mode. There are some option to do via SSH tunnel i think.

schdefan

---

### Post by kenweill on 2006-01-17
[QUOTE=Perhaps]Hi, the question is: How can I open visual SSH tunnel to a Windows machine? Is possible?
I can reach the windows server by console, but I need to reach there visually. (I'm a rookie using KDE).

Thank you all.[/QUOTE]

How did you reach the windows server by console? I thought thats impossible. Doing SSH to a windows machine.

---

### Post by schdefan on 2006-01-17
If you want to connect to windows machine via ssh this machine has to run a ssh server. I use this one [http://sshwindows.sourceforge.net/]("http://sshwindows.sourceforge.net/")
Here I found the steps using rdesktop with ssh. 
[http://www.engr.wisc.edu/computing/best/rdesktop-mac.html]("http://www.engr.wisc.edu/computing/best/rdesktop-mac.html")
Although it is described for mac the procedure is the same.

schdefan

---

### Post by Perhaps on 2006-01-17
[QUOTE=kenweill]How did you reach the windows server by console? I thought thats impossible. Doing SSH to a windows machine.[/QUOTE]


Type on console: ssh [-l USERNAME] ipaddress

If you have a windows SSH server you reach to MS-Dos prompt.

---

