---
title: "Firefox 3 Won't Start on Jaunty"
date: 2009-06-22
forum: General Help
---

### Post by rich1939 on 2009-06-22
All of a sudden, Firefox won't even start on my laptop. I have probably changed my home page on my Windows computer to a custom iGoogle theme and when I try to start Firefox on Ubuntu Jaunty it grinds away and then won't even start.

I tried to re-install Firefox, but I'm not sure that I was able to do that correctly...and then maybe the problem has something to do with my new home page.

In any event, Firefox tries to start then just gives up and nothing happens. I have re-booted several times and get the same situation.

Any suggestions on how to recover? I don't have a CD of Jaunty, I just upgraded from Intrepid and it has worked just fine since the launch of Jaunty...until today.

What to do??

---

### Post by fooman on 2009-06-22
try deleting (or just renaming in case you want it back) the hidden .mozilla directory which contains your firefox config files. 

first backup your bookmarks/favorites!

then open your home folder and in the taskbar,  click view.  put a check next to "show hidden files".  then scroll down and find the .mozilla folder....right click on it and either rename it or send it to the trash (firefox will create a new one when it restarts).

 then try to start firefox....hope that helps.

---

### Post by Maheriano on 2009-06-22
Common error that everyone is seeing. Do a search, there are fixes.

---

### Post by hyperdude111 on 2009-06-22
run firefox in terminal, what is the output.

I get a syntax error in firefox 3.5 which i cant fix.

---

### Post by rich1939 on 2009-06-22
> **hyperdude111 said:**
> run firefox in terminal, what is the output.

I get a syntax error in firefox 3.5 which i cant fix.

I tried renaming the **.mozilla** folder and restarting Firefox, but that didn't help...so I uninstalled Firefox and then re-installed it and it now runs again fine.

Don't know what happened, but now it seems okay.

---

