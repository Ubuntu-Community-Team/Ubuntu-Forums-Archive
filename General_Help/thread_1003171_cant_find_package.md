---
title: "cant find package"
date: 2008-12-05
forum: General Help
---

### Post by jackattack99 on 2008-12-05
im new and i ned help...i just got ubuntu 7.10  for my ps3...i hav no internet connection so i put znes (for linix) on a usb stick and i try to install it but nothing... i type   sudo apt-get update   then  sudo apt-get install znes..and nothing  i also tried   the folder name...znes_1.5 i think it was called and still nothing it gives me a error cant find package...can sum1 help me install this??

---

### Post by oldos2er on 2008-12-05
Is this a *deb file? Copy it to your home directory, and double-click it to install, or open a terminal and run "sudo dpkg -i [filename].deb

 apt-get only looks in Ubuntu's repositories for packages.

---

### Post by zvacet on 2008-12-06
Maybe you want to try [keryx.]("http://keryx.betaserver.org/")

---

### Post by jackattack99 on 2008-12-06
okay ...i go applications>  add/remove > search zsnes it pops up but i cant check it off... it says that i require additional software??

---

### Post by zvacet on 2008-12-06
You can not install that package with add/remove if you don´t have internet connection.That is why I suggested to use keryx.You can download package from [here]("http://packages.ubuntu.com/intrepid/zsnes") if you use Interpid or from [here]("http://packages.ubuntu.com/hardy/zsnes") if you use Hardy.You have to download packages marked with red ball(they are dependencies) and install them first.Do it like **oldos2er** described.

---

