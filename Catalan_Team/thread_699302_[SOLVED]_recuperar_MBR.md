---
title: "[SOLVED] recuperar MBR"
date: 2008-02-17
forum: Catalan Team
---

### Post by Miquel Ubuntero on 2008-02-17
Bones.
He estat "jugant" amb u  PC i l'he cagat!
Involuntariament, tinc el GRUB a un PC on hi tinc Win'XP.
Voldria treure'l.
He provat de fer:
"sudo apt-get install ms-sys
ms-sys –mbr /dev/hdX"

Però no xuta, hem diu aixó:

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
E: No s'ha pogut trobar el paquet ms-sys
ubuntu@ubuntu:~$ 

Hem doneu un cop d ma, sisplau.

---

### Post by CarlesOriol on 2008-02-17
Engega amb el cd del hasefrog. Fes recuperació per consola i despres entra les comandes:

fixmbr i fixboot

---

### Post by PellRoja on 2008-02-17
[http://www.informatics.cat/wiki/index.php/Recuperaci%C3%B3_del_Sector_d%27Arranc_de_Windows_XP](http://www.informatics.cat/wiki/index.php/Recuperaci%C3%B3_del_Sector_d%27Arranc_de_Windows_XP)

---

### Post by Miquel Ubuntero on 2008-02-17
SOLVED :)
Moooooooooooooooltes gracies.
El link d'en Pelroja, molt fàcil, molt clar.
Estaba acollonit, era el ladtop, del curro!!!
Mai més. A partir d'ara el experiments, només a casa am gaseosa.
Gracies de nou.
Salut!

---

