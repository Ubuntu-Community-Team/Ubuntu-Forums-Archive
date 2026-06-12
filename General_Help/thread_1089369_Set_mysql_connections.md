---
title: "Set mysql connections"
date: 2009-03-07
forum: General Help
---

### Post by jonwcode on 2009-03-07
Okay, so I've setup my ubuntu server just the other night and I got the apache server working and I got mysql server running but there is one problem that I've been having, and that is connecting to mysql server from my computer. I know that its possible to set mysql up so that you can login into your database without being on localhost. How is this done?

Thanks,
Jon W

---

### Post by bluefrog on 2009-03-07
my.cnf bind-address

you'd better access your server via ssh.

---

### Post by jonwcode on 2009-03-07
I have a DNS not a static IP, how would I set this up with a DNS?

Edit: And what do you mean by "you'd better access your server via ssh." What is ssh stand for? Sorry, I'm new to linux servers.

---

### Post by jonwcode on 2009-03-07
Does anyone know how I can set up the mysql database so I can to it from any computer using a DNS?

---

### Post by jonwcode on 2009-03-07
I've went into /etc/mysql/my.cnf file and changed the bind-address to my IP address and my DNS both, and on each one I try whenever I go to restart Mysql server it fails to restart. What am I dong wrong?

---

### Post by john8765 on 2009-03-07
Make sure your not passing --skip-networking into the command that starts mysqld, also you can check out [mysql examples]("http://www.examplenow.com/mysql") if you not sure about general mysql syntax.

good luck

---

### Post by jonwcode on 2009-03-07
What I type in to restart mysql is: sudo /etc/init.d/mysql restart


And that restarts it. I'm not to sure if I'm following what your saying. I'm just simply trying to setup the mysql server so that I can connect from my other PC here at home and not have to be on my localhost ubuntu server.

---

### Post by jonwcode on 2009-03-07
Anyone?

---

