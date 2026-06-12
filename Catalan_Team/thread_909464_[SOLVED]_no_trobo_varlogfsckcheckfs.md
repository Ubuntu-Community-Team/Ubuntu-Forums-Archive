---
title: "[SOLVED] no trobo /var/log/fsck/checkfs"
date: 2008-09-03
forum: Catalan Team
---

### Post by manelfus on 2008-09-03
Hola de nou tinc un petitet problemo a l'hora d'obrir el portatil quant esta boteixant es queda amb:

*File system check failed.
A log is being saved in /var/log/fsck/checkfs if that location is writable.
Please repair the file system manually.
*A maintenance shell will now be started.
CONTROL-D will terminate this shell and resume system boot.
bash: no job control in this shell
bash: groups:command not found
bash: lesspige: command nhot found
bash: Command: command not found
bash: The: command not found
bash: dircolors: command not found
bash: Command: command not found
bash: The: command not found
root@manel3:~#

de fet li dono al ctrl+d i es torna a iniciar be, però veien  lo que diu de que repari el sistema manualment a traves del /var/log/fsck/checkfs

ves aquí on es el problemo aquest arxiu no el trobo algú sap res de aquests???? 


mercès des de ja  

salut

---

### Post by papapep on 2008-09-03
> A log is being saved in /var/log/fsck/checkfs if that location is writable.

Això vol dir que, _si s'hi pot escriure_ (if that location is writable), et desa un registre del problema al fitxer que t'esmenta. No que sigui la manera d'arreglar el problema. La manera és com ja ho has fet tu, Ctrl+D i fer la reparació manual.

---

### Post by manelfus on 2008-09-03
De fet ja he trobat l'arxiu però no entenc el que diu, lo que si se es que no estare sempre  donant-hi al ctrl+d (quin rotllo no?),aquí et deixo allo que diu:


root@manel3:/home/manel# cd /var/log/fsck/
root@manel3:/var/log/fsck# cat checkfs 
Log of fsck -C -R -A -a 
Thu Sep  4 01:02:44 2008

fsck 1.40.8 (13-Mar-2008)
open UUID=085E-5099:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
fsck.ext2: Unable to resolve 'UUID=fbe5001d-8977-441b-9334-b73a88061ca7'
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda3: 6867 files, 892816/1481313 clusters
open UUID=48AA-A306:No such file or directory
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
fsck.ext2: Unable to resolve 'UUID=676c3f7f-be0a-492e-b8f9-1bbbece20efb'
fsck died with exit status 9

Thu Sep  4 01:02:55 2008
----------------
root@manel3:/var/log/fsck# 

A lo millor es solucionava fent un fsck? , però sempre ho faig servir com a ultim recurs .
Per lo que sembla ser te a veure amb ell i amb alguna cosa d'un Fat32  i d'una  ext2.
I l'únic que recordo d'algú així es de fer-hi una partició a una microSD 
amb el gparted, pot ser-hi que sigui aquest el problema ? I com puc estalviar me  de fer sempre el ctrl+d?

---

### Post by papapep on 2008-09-03
> A lo millor es solucionava fent un fsck? , però sempre ho faig servir com a ultim recurs 

....un cop apareix un problema al sistema de fitxers, i no es resol automàticament, s'ha de resoldre sempre amb un fsck...no he vist mai que remiteixi espontàniament. Sinó entres com a root i executes l'fsck manualment, com ja has vist, seguirà sortint sempre el missatge del CtrlD, com és normal...
Si t'ha passat més cops assegura't de tenir còpia de la informació que t'importi que sigui dins el disc dur que genera l'error. Té els dies comptats (dies comptats = temps indeterminat entre demà i ves-a-saber-quan).

Quan esmenta fsck.ext2, t'està dient que no és capaç de vincular la uuid del disc dur amb cap partició. Has tocat alguna cosa del fstab?

---

### Post by manelfus on 2008-09-04
Quan esmenta fsck.ext2, t'està dient que no és capaç de vincular la uuid del disc dur amb cap partició. Has tocat alguna cosa del fstab?


No no ja te dit l'únic que vaig fer-hi fa un parell de dies va ser particionar una targe SD micró amb dues extensions una de FAT 32 i l'altre amb ext2 que es de lo que es queixava ell.
 He fet un fsck i ja arrenca normalment , pero aixos del fsck cada vegade que ho fem,no estem carregant-nos inodes del disc dur? quant acaba de fer-ho diu algo d'un % de non-contagiosus o algo semblant.

Ep que m'ha tornat a passar:Warnig !!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Do you really want to continue (y/n)?

li dic que yes   i  pim pam .... fsck.ext2 unable to resolve= incapaz de resoldre-ho???
No hem podre lliurar d'aquest maleit ctrl+d??

---

### Post by papapep on 2008-09-04
Abans que res, _calma_.

A veure, enganxa l'fstab.

---

### Post by manelfus on 2008-09-04
Mercès papapep tenies raó amb lo del fstab es una serie de particions que vaig fer-hi a una SD i amb el Disck Manager de fet lo que he fet es desmontarles o millor dit "remove" amb el mateig Disck Manager i apa s'acabat el problem.

merces per tot
 salut

---

### Post by papapep on 2008-09-04
"U" s'alegra d'haver estat útil ;-)

---

