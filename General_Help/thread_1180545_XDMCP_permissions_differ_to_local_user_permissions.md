---
title: "XDMCP permissions differ to local user permissions"
date: 2009-06-06
forum: General Help
---

### Post by ouchmyhand on 2009-06-06
I have an Ubuntu 9.04 server and log into it via XDMCP from my OSX machine. I dont want to use a monitor keyboard etc for the Ubuntu box, nor do i want to use VNC.
When i log in via XDMCP, the same user does not have the same permissions as if i were to log in locally. I.e. i can change users/groups in local but ot remotley.
Can some one please help?

---

### Post by ouchmyhand on 2009-06-08
Anyone???

---

### Post by ouchmyhand on 2009-06-09
Can anyone redirect me to somewhere that could help? I'm so new i don't know where to look. I thought the Ubuntu forums would be a good start but so far no assistance.

---

### Post by ouchmyhand on 2009-06-10
any help? Surely someone else has come across this before?

---

### Post by rapchee on 2010-11-11
i believe this is because the user id in osx is different from the id on ubuntu, but xdmcp uses osx`s id, so the user won`t get the proper rights. even though i`ve solved this somehow back in my earlier workplace i`m not sure how i did it. i remember one solution was to change the id on ubuntu, but there might be other solutions/workarounds

---

