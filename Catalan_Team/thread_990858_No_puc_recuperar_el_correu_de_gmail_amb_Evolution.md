---
title: "No puc recuperar el correu de gmail amb Evolution"
date: 2008-11-23
forum: Catalan Team
---

### Post by Omit7 on 2008-11-23
Be, doncs això, després de molt googlejar, revisar el wiki i buscar algun post al forum que m'ajudés, no ho aconsegueixo.

He trobat diferents pagines on indica com configurar l'Evolution per tal de rebre i enviar correu d'un compte Gmail. A l'hora de enviar, cap problema tot va com la seda. A l'hora de rebre no hi ha manera. Per si serveix d'ajuda les instruccions que trobo son totes com les d'aquest link

[http://tuxlink.wordpress.com/2007/10/31/gmail-en-evolution-ubuntu/](http://tuxlink.wordpress.com/2007/10/31/gmail-en-evolution-ubuntu/)

Si algú em pot ajudar...

Gràcies

---

### Post by papapep on 2008-11-23
Edita > Preferències > (Marques el compte que vols editar) Edita > pestanya "Recepció de correu" :

Tipus de servidor: pop
Servidor; pop.gmail.com
Nom d'usuari: la teva adreça de correu completa
Empra una connexió segura: Xifratge SSL
Tipus d'autentificació: Contrasenya

i deses amb "D'acord".

---

### Post by Omit7 on 2008-11-23
Gràcies, però això es exactament el que he fet i no funciona. També he probat (com  indica en alguns blogs) ha indicar el número de servidor:

Servidor: pop.gmail.com:995

Tampoc em funciona. He comprobat repetides vegades la configuració del compte de gmail:

Configuracio > Reenviament i POP/IMAP > Baixada POP > 1. Estat: _El correu POP està habilitat per a tots els missatges rebuts des del 14:23_

No hi ha manera, Evolution no em dona cap missatge d'error però no recupera els missatges de Gmail.

Alguna altra idea?

---

### Post by PatrickVogeli on 2008-11-23
el problema que tens diria que te a veure a que només has habilitat el POP per als missatges que has rebut avui a partir de les 14:23...

Ves a la web de gmail, i a configuració de POP selecciona la opció per rebre tots els missatges, inclosos el que ja s'han descarregat.

salut

---

### Post by Omit7 on 2008-11-23
> **PatrickVogeli said:**
> 

Ves a la web de gmail, i a configuració de POP selecciona la opció per rebre tots els missatges, inclosos el que ja s'han descarregat.

salut

Sembla que hem avançat una mica però encara no del tot. M'explico:

Faig el que em dius i efectivament quant li dono a recuperar el correu des de Evolution ja els recupera...però només els que tinc en aquell moment. Els que m'envien a posteriori d'haver fet el canvi a gmail ja no m'arriben.

Si torno a dir-li a gmail que els vull tots un altre cop, ja els torno a tenir i així cada vegada. Suposo que el normal seria que una vegada fet el canvi m'arribesin tots i no haver de refer la configuració cada vegada...oi?

Si se't acut alguna cosa, soc tot orelles ;)

---

