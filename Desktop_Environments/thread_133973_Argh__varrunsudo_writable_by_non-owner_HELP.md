---
title: "Argh : /var/run/sudo writable by non-owner HELP"
date: 2006-02-21
forum: Desktop Environments
---

### Post by mpozzi on 2006-02-21
Hy everybody ! Maybe someone can help me.. :-k 

I made a mistake and changed the permissions on my /var/run folder to 777.
the problem is that now I cannot get it back to 700, expecially because sudo is not working anymore.. how I can do this ?

[B]mpozzi@muletto:/var/run$ sudo chmod -R 700 /var/run/
sudo: /var/run/sudo writable by non-owner (040777), should be mode 0700[/B]

Argh...

---

### Post by Marshall2day on 2006-02-21
You could try booting a live cd and then change the permissions

---

### Post by mpozzi on 2006-02-21
Thanks I will try it !

---

### Post by mpozzi on 2006-02-21
In any case... Mmmh... without the live cd (that i have to download and burn) is there any other chance ?

---

### Post by mpozzi on 2006-02-21
Well I managed to solve the problem by booting in recovery mode with the root account. :-D 

I changed with **chmod 777 -R /var/run/sudo** and the sudo command now works again.

As a matter of fact at the moment also all the other directory in **/var/run** are set to be permission 777 (free for all), what is the general suggestion, do I have to switch all of them to 700 or leave like it is now ? Any comments people ?

Bye

---

