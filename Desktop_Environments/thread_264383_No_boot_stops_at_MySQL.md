---
title: "No boot: stops at MySQL"
date: 2006-09-24
forum: Desktop Environments
---

### Post by HakanS on 2006-09-24
I ran Adept to install a game and got an error message that something got wrong (I don't remember the message). I then tried to start Adept again but a got another message saying that it couldn't start.
After that I can't start the computer. The boot stops with the text:
Starting MySQL database server: mysqld

Nothing more happens.
Please help me solve this.

---

### Post by henriquemaia on 2006-09-25
Have you tried booting in recovery mode?

---

### Post by HakanS on 2006-09-25
Yes, and it works.
But what shall I do then?

---

### Post by HakanS on 2006-09-25
Solved
It wasn't a problem with MySQL.
It was the partition /var (/var/cache/apt/archives) that was full.

---

### Post by henriquemaia on 2006-09-25
When I asked that, I was thinking that if you could boot in recovery mode, you could then turn off mysql init script to check its problem later. But it's good to know you solved that.

---

