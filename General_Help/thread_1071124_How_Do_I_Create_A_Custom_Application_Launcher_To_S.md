---
title: "How Do I Create A Custom Application Launcher To Start Lampp?"
date: 2009-02-15
forum: General Help
---

### Post by ajr901 on 2009-02-15
I have installed lampp and everything is good. But i dont wanna have to go into terminal everytime i need to start lampp. the command to start lampp is: "sudo /opt/lampp/lampp start".

Ok so now i right click on the panel > Click "+Add to Panel" > Then Click "Custom Application Launcher" > After i set the name and description, what is the command?

---

### Post by mcduck on 2009-02-16
"gksudo /opt/lampp/lampp start"
(gksudo instead of sudo because you need to get a graphical dialog asking for your password)

---

