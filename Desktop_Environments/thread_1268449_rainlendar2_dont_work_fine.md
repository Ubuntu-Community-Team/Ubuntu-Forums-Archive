---
title: "rainlendar2 dont work fine"
date: 2009-09-17
forum: Desktop Environments
---

### Post by ulissess on 2009-09-17
hi, i have ubuntu 08.10.02, i've installed this version rainlendar2-lite_2.3.b54 but each time i exec in user (or root) mode each skins dont work. i mean, it's work but it's like transparent!! i must just refresh for see the skin. anyone have the same problem?? thank u (sorry for my english)

---

### Post by ulissess on 2009-09-17
i have solved!! create a file rainlendar.sh 


> #!/bin/bash
sleep 2
rainlendar2 --execute='Rainlendar_Refresh()'


chmod 700 rainlendar.sh

put rainlendar.sh in a startup command and the programm will auto-refresh!!!!

---

