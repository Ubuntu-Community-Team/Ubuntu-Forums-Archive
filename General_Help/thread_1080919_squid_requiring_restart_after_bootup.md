---
title: "squid requiring restart after bootup??"
date: 2009-02-25
forum: General Help
---

### Post by ddigler on 2009-02-25
I'm running 8.10 & I finally have a transparent proxy setup using Dansgaurdian and Squid for content filtering and it works very well.

Prob I'm having is that my internet never works after booting up the system until I restart squid in the terminal.

Also, after system startup, if I status squid it says its already running and gives a process ID #. Yet internet WILL NOT work until a manual restart is performed.

Why is this happening?

---

### Post by Hobgoblin on 2009-02-25
How are you restarting Squid, perhaps this will give a clue.

Post the exact command line.

---

### Post by ddigler on 2009-02-25
sudo /etc/init.d/squid restart

---

### Post by ddigler on 2009-02-25
FYI. The tutorial I followed was a 3 step process:

Install and conf squid
Install and conf DG
Create an exec file with a single ip table redirection command
Update init.d to include redirection command

Upon restart both dg and squid show running when I 'status squid'

But no internet until I use the restart command post above.

---

### Post by ddigler on 2009-02-26
Would the fact that my network connection is wireless matter? thought I saw somewhere that squid has problems if connections are not established in time. 

Its always 10 secs or so after I log on until my connection is established.

---

### Post by ddigler on 2009-02-26
Problem solved; had to add dns_nameservers entry to squid.conf from data found in /etc/resolvconf

---

### Post by dragonfoundry on 2009-04-30
ddigler:- Spot on. Thanks! Squid was driving me mad on Jaunty.

---

