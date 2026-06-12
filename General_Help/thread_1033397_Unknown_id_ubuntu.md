---
title: "Unknown id: ubuntu"
date: 2009-01-07
forum: General Help
---

### Post by Skwire on 2009-01-07
After I upgrade from 8.04 to 8.10 (for ubuntu & kubuntu), I restarted my computer. Which I`m guessing should be normal. Instead of giving a GUI, I get errors and then sais Unknown id: ubuntu. After words, I have a text based login screen, then something like a terminal. I looked everywhere for a solution, but couldn't find anything. Any help would be greatly appreciated.

---

### Post by Skwire on 2009-01-08
Bump

---

### Post by aloshbennett on 2009-01-08
Are you able to log in using the terminal?

---

### Post by Skwire on 2009-01-08
I think it's the terminal, so I can still put command lines.

---

### Post by bodhi.zazen on 2009-01-08
Boot to recovery mode. This will give you a root terminal

What is your user name ? Are you using ubuntu as a user name ?

If so you will need to edit /etc/passwd and confirm your user name and id in that file.

[http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/](http://www.cyberciti.biz/faq/understanding-etcpasswd-file-format/)

---

### Post by hyperdude111 on 2009-01-08
that happened to me once and "sudo startx" took me to a login screen, it may work for you.

---

### Post by Skwire on 2009-01-09
Thanks for your help, but I formatted my computer and now it works perfectly.

---

