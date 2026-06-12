---
title: "jaunty giving me mysql issues"
date: 2009-05-30
forum: General Help
---

### Post by abhinav90 on 2009-05-30
I recently upgraded from intrepid ibex to jaunty. When i did i saw for some strange reason that my mysql was no longer accessible using my standard username "root" and leaving the password blank. So i was forced to do sudo dpkg reconfigure mysql-server-5.0 which allowed me to change my password. Now when i change it back to no password using phpmyadmin i get an access denied error and if i use the other above mentioned method my password simply does not change. I need to make the password blank since a lot of the development work i do with my team uses these configurations which would then require me to constantly change the password everytime i run their code on my machine. I have even tried removing mysql and reinstalling it using sudo apt-get remove mysql-server-5.0 but the password does not get changed. Pls help!

---

