---
title: "M'ha desaparegut l'escriptori"
date: 2008-03-10
forum: Catalan Team
---

### Post by Agustí on 2008-03-10
Hola bona gent

Resulta que no tinc escriptori. No tinc ni el fons de pantalla ni les carpetes que hi tenia. Ho he reiniciat però res de res. A més, si vaig a "Llocs" i li dic que m'ensenyi la carpeta d'inici no m'ensenya res tampoc. No sé com sortir-me'n. Agraïria que em diguéssiu com recuperar l'escriptori (tinc Gutsy i l'escriptori és GNOME) però amb paciència, perquè no sé gaire com va tot plegat, fa poc que tinc Ubuntu. Per cert, un cop s'hagin donat ordres al Terminal, com es tanca la sessió?

Moltíssimes gràcies.

Agustí

---

### Post by papapep on 2008-03-10
Prova amb:

```
sudo apt-get --reinstall install ubuntu-desktop
```

---

### Post by Agustí on 2008-03-10
Gràcies Papa Pep!!

A veure, he posat l'ordre que em deies al terminal amb un copy and paste, ha treballat, m'ha dit que hi ha una llibreria del brasero que no val però no ha fet res. Quina ordre li dono per tancar el terminal? M'haig d'esperar o haig de reiniciar? Perdona però sóc totalment novell.

Gràcies un altre cop.

Agustí

---

### Post by orestesmas on 2008-03-10
Per sortir d'una sessió de terminal cal fer

```
logout
```

però això no et durà al mode gràfic. Abans hauries d'activar-lo:
```
sudo /etc/init.d/gdm restart
```

El "problema" és que això et commutarà a l'entorn gràfic deixant oberta la sessió que tenies en el terminal. Però no pateixis: pots commutar a la sessió de terminal amb Alt+Ctrl+F1, fer el "logout", i tornar a l'entorn gràfic amb Alt+Ctrl+F7

---

### Post by CarlesOriol on 2008-03-10
Explica'ns com obres el terminal.

---

### Post by Agustí on 2008-03-10
Gràcies Carles i Orestesmas!!

Obro el terminal anant a Aplicacions-Accessoris-Terminal. Ho faig bé?

Agustí

---

### Post by jodufi on 2008-03-10
Per a tancar el terminal hi ha tres maneres:
[LIST]
[*]Fitxer -> Tanca la finestra
[*]Escriure «exit» al terminal
[*]Fer clic en la creu que hi ha a la bada superior dreta
[/LIST]

Realment, el que has obert és una emulador de terminal, no una sessió de terminal.
L'Orestes explica com iniciar una sessió de terminal. Tot i que pel teu problema no fa cap falta. En tens de sobre amb el que has obert.

El que ens aniria bé per a resoldre el teu problema és que ens enganxis el resultat de la instrucció que et diu en papapep.

També estaria bé una captura de l'escriptori. Aquestes es fan prement la tecla «Impr» o «Aplicacions -> Accessoris -> Feu una captura de pantalla»

---

### Post by Agustí on 2008-03-11
baba@baba-desktop:~$ sudo apt-get --reinstall install ubuntu-desktop
[sudo] password for baba:
Sorry, try again.
[sudo] password for baba:
S'està llegint la llista de paquets... Fet 
S'està construint l'arbre de dependències       
Reading state information... Fet           
The following packages were automatically installed and are no longer required:
  libgpod1 brasero
Use 'apt-get autoremove' to remove them.
0 actualitzats, 0 nous a instal·lar, 1 reinstal·lats, 0 a eliminar i 4 no actualitzats.
E: No s'ha pogut blocar /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: No és possible blocar el directori de descàrrega

---

### Post by papapep on 2008-03-11
> E: No s'ha pogut blocar /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: No és possible blocar el directori de descàrrega

Això diu que tens algun altre programa o instància de programa intentant accedir simultàniament a la base de paquets amb el que tu has llençat, i això no és possible. Tanca la resta de programes que tinguis oberts, i si no és possible (no està bé però funcionarà) reinicia a "lo cafre" l'ordinador i torna a executar la ordre.

---

### Post by CarlesOriol on 2008-03-11
Prova al terminal d'escriure:

metacity --replace

si et funciona desactiva els efectes d'escriptori.

---

### Post by Agustí on 2008-03-12
Ep! Ahir un ubuntuaire em va dir que no m'ha desaparegut l'escriptori, sinó que en realitat m'ha desaparegut el GNOME.

Així que fent cas al Papapep vaig fer

sudo apt-get --reinstall install gnome

Va obrir-me i instal·lar-me un munt de paquets, però finalment no se'm va obrir el GNOME, sinó que estava a l'espera d'una altra ordre. Li vaig dir que "logout" i "exit" però em tornava a demanar el login i el password. No sé perquè no acaba les ordres. El que sí crec és que se m'ha desinstal·lat el GNOME.

em van dir que fes

sudo /etc/initd/gdm stop
i després

sudo /etc/initd/gdm start

però em diu que no sap el que és /etc

Se us acut res?

Moltes gràcies per endavant.

Agustí

---

### Post by patrickfromspain on 2008-03-12
sudo /etc/init.d/gdm restart

init.d: fixa't que hi ha un punt! 

salut!

---

### Post by papapep on 2008-03-12
Disculpa Agustí, però la ordre que et vaig indicar jo era exactament:

```
sudo apt-get --reinstall install ubuntu-desktop
```

No t'aconsello seguir indicacions de gent diferent simultàniament, et pot portar problemes seriosos.

A veure, t'has de centrar en el problema i seguir un fil d'actuació:

1.- Quan s'engega l'ordinador arribes a la finestra gràfica on et demana usuari i contrassenya o no?

2.- 

> em van dir que fes

sudo /etc/initd/gdm stop
i després

sudo /etc/initd/gdm start

T'has oblidat un punt. És:

```
sudo /etc/init[COLOR="Red"]**.**[/COLOR]d/gdm stop
```

```
sudo /etc/init[COLOR="Red"]**.**[/COLOR]d/gdm start
```

Tingues pel clar que l'ordinador és tonto a rematar, i li has de dir tot exactament i correctament si vols que funcioni com cal. Així doncs, espais, comes, punts i demés, s'han de respectar al màxim a fi de executar les ordres correctament.

---

