---
title: "Kppp error"
date: 2005-04-17
forum: Desktop Environments
---

### Post by ludi on 2005-04-17
Apr 17 12:31:38 localhost pppd[9172]: The remote system is required to authenticate itself
Apr 17 12:31:38 localhost pppd[9172]: but I couldn't find any suitable secret (password) for it to use to do so.
Apr 17 12:31:38 localhost pppd[9172]: (None of the available passwords would let it use an IP address.)

Well, I can't connect with Kppp. My pon provider poff are working but I would like to use a graphical interface instead of the terminal.
What's the problem?

---

### Post by Glanz on 2005-04-17
[QUOTE=ludi]Apr 17 12:31:38 localhost pppd[9172]: The remote system is required to authenticate itself
Apr 17 12:31:38 localhost pppd[9172]: but I couldn't find any suitable secret (password) for it to use to do so.
Apr 17 12:31:38 localhost pppd[9172]: (None of the available passwords would let it use an IP address.)

Well, I can't connect with Kppp. My pon provider poff are working but I would like to use a graphical interface instead of the terminal.
What's the problem?[/QUOTE]
 I believe your setup is asking the ISP to verify itself also. It is rare indeed that an ISP will be bothered with a user asking for verification. As I am not using KDE and am not familiar with KPPP, try to find some check in its configuration (setup) interface where you can eliminate a user request to the ISP to verify. Only you need to verify yourself to the ISP. It's a one way handshake, or a case of "one hand clapping.":)

---

### Post by ludi on 2005-04-18
[QUOTE=Glanz]I believe your setup is asking the ISP to verify itself also. It is rare indeed that an ISP will be bothered with a user asking for verification. As I am not using KDE and am not familiar with KPPP, try to find some check in its configuration (setup) interface where you can eliminate a user request to the ISP to verify. Only you need to verify yourself to the ISP. It's a one way handshake, or a case of "one hand clapping.":)[/QUOTE]
The problem is the auth option in the options file of ppp '/etc/ppp/options'.
I've just replaced with noauth instead of auth, now everything works :)

---

### Post by brk3 on 2005-04-19
Ya i had this problem at first too. getting rid of the auth fixes it :) The answer is actually in the kppp manual, the manuals are actually starting to get good :) It tells you how to mod your init string aswell to get it to display your proper connection speed. Is there any plan to make a tips page for kubuntu like the one for ubuntu..? It was really helpfull when I used to use ubuntu. Maybe we could create a wiki page and when an answer is found it could be added

---

### Post by newmike on 2005-04-19
Hi All, I have same problem.Same msg. I do not understand where to go/ how to on your fix. I understand what you are saying, but where is all of that? KPPP Manual-WOW-wheres that? *When i 1st clicked KPPP I get msg."Have Adminitrator create(can be empty) file with appropriate r-w permissions. /etc/resolv.conf missing or cannot be read".  On install i created an Admin user login, but, where is root? Since root has all authority doesnt that clear-up some config.-setup things on the fly at 1st use? thanx 4your help. mike

---

