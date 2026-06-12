---
title: "open ports"
date: 2005-09-30
forum: Desktop Environments
---

### Post by lomomo on 2005-09-30
i'm checking the open ports on my system and i see there are 4 ports open.

tcp port 631 (Internet printing protocol?) do i need this one to be open? which service opens this port and how can i disable it?

then i have port tcp 4662 but i don't know what service is it running, same with udp ports 4665 and 4672. What are these ports running? are this services necessary?

---

### Post by Teren on 2005-09-30
631 = cupsd
4662, 4665, 4672 = emule

---

### Post by lomomo on 2005-09-30
OK, i know how to close these emule ports :rolleyes: 

is cupsd a necessary service or can i remove it?

---

### Post by Teren on 2005-09-30
cupsd is a printing daemon, but I don't really know if the internet part is really needed, last time I used my printer was 4 years ago, and when I installed Ubuntu, I didn't even bother setting the printer up :)

---

### Post by lomomo on 2005-09-30
well, since i haven't any printer there shouldn't be any problem removing this service.

---

