---
title: "[SOLVED] configurar no-ip"
date: 2008-01-04
forum: Catalan Team
---

### Post by Brunilda on 2008-01-04
Estic intentant muntar un servidor ftp en un ordinador amb una connexio adsl amb ip dinàmica.

He llegit en alguns fòrums que la manera de convertir la ip dinàmica a estàtica és amb el programa no-ip.

Quan l'he descarregat dels repositoris m'ha donat el següent missatge d'error:

> 
jordi@brunilda:~$ sudo apt-get install no-ip
[sudo] password for jordi:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
S'instal·laran els següents paquets NOUS:
  no-ip
0 actualitzats, 1 nous a instal·lar, 0 a eliminar i 0 no actualitzats.
Es necessita obtenir 0B/23,9kB d'arxius.
Després de desempaquetar s'usaran 139kB d'espai en disc addicional.
S'està seleccionant el paquet no-ip prèviament no seleccionat.
(S'està llegint la base de dades ... hi ha 169404 fitxers i directoris instal·lats actualment.)
S'està desempaquetant no-ip (de .../no-ip_2.1.3-3build1_amd64.deb) ...
S'està configurant no-ip (2.1.3-3build1) ...
Starting dynamic address update: Can't locate configuration file /etc/no-ip.conf. (Try -c). Ending!

no-ip.


i quan intento configurar-lo em passa el següent:

> 
jordi@brunilda:~$ sudo no-ip -C
[sudo] password for jordi:

Auto configuration for Linux client of no-ip.com.

Please enter the login/email string for no-ip.com  [email]jovemont@jazzfree.com[/email]
Please enter the password for user 'jovemont@jazzfree.com'  *********

You have entered an incorrect username
        -or-
an incorrect password for this username.


He de dir que la primera vegada que he entrat el login el missatge que m'ha sortit  és:

Content Type: text/HTML

He buscat informació a d'altres fòrums però a tots els que he llegit expliquen que es tant fàcil de configurar.

No sé que estic fent malament, si algú pot donar-me un cop de ma us ho agrairé.

---

### Post by papapep on 2008-01-04
> You have entered an incorrect username
-or-
an incorrect password for this username.

Doncs que no li estàs introduint el nom d'usuari o contrassenya correcte del teu compte que has creat prèviament a no-ip.com

---

### Post by Brunilda on 2008-01-04
Novament gràcies papapep, amb tantes claus i contrassenyes un ja para boig. De totes maneres el problema important és que tampoc havia acabat de configurar el host a [www.no-ip.com](www.no-ip.com), només m'havia donat d'alta i m'he quedat tant ample com llarg. ara l'he configurat i puc continuar amb el projecte de ftp.

---

