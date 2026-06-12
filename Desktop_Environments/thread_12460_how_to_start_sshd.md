---
title: "how to start sshd?"
date: 2005-01-24
forum: Desktop Environments
---

### Post by akurashy on 2005-01-24
i been wondering how can i start sshd O_o

---

### Post by albersag on 2005-01-24
[QUOTE=akurashy]i been wondering how can i start sshd O_o[/QUOTE]
 Easily via apt-get

sudo apt-get install ssh

---

### Post by akurashy on 2005-01-24
ok installed now how to use it?
i need it up for my friend =/

---

### Post by albersag on 2005-01-24
[QUOTE=akurashy]ok installed now how to use it?
i need it up for my friend =/[/QUOTE]
 To connect you must have port 22 opened via NAT on router, if you are using a broadband connection.

On /etc/ssh/ssh/ you have all the configuration files.

To understand them please read the manual (man ssh man sshd) or search at google tutorials

To connecto your own ssh server, type on shell "ssh user@ipserver" and accept the security adverstisement. Then type your "password" and you will be inside , as a shell window but remote . 

I hope this helps.

Next step could be vnc , search at this forum. There are documentation about it.

---

### Post by gt500 on 2005-01-24
[QUOTE=akurashy]i been wondering how can i start sshd O_o[/QUOTE]
 Some people are just too lazy too look for 2 seconds ...

greetz

---

### Post by albersag on 2005-01-24
[QUOTE=gt500]Some people are just too lazy too look for 2 seconds ...

greetz[/QUOTE]
 :mrgreen:

---

### Post by DynamicMouse on 2008-07-15
what a childish answer to a simple question.
to start sshd try  /etc/init.d/ssh start

---

