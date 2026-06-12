---
title: "Awn Manager: problema amb l'arrencada"
date: 2008-04-22
forum: Catalan Team
---

### Post by lo gambusí on 2008-04-22
Sempre que carrego l'ordinador m'apareix així:
[IMG]http://img442.imageshack.us/img442/4840/capturazt2.png[/IMG]

Llavors surto de la sessió, torno a entrar i se'm carreguen bé les icones.:?

---

### Post by papapep on 2008-04-22
Culpa del gatet, segur, segur....

---

### Post by SiscoGarcia on 2008-04-22
> **papapep said:**
> Culpa del gatet, segur, segur....

o dels .doc que es veuen a l'escriptori :)

---

### Post by lo gambusí on 2008-04-23
los .doc no són meus :(

Alguna resposta útil? xD

---

### Post by jaume69 on 2008-04-23
Bé,suposo que no cal dir que ja deus tenir els Efectes d´Escriptori activats!.

Si no és això,pot ser que algun Applet que necessita de connexió,i suposo que con que primer es carrega l´Avant,doncs no te temps a carregar amb la connexió ja connectada.

O algun Applet que et doni problemes...

No sé...

:lolflag:

(Tot i que aquest gat te pinta de ser una mica entremaliat...)

---

### Post by SiscoGarcia on 2008-04-23
> **lo gambusí said:**
> los .doc no són meus :(

Alguna resposta útil? xD

Era una broma, perdó :oops:

---

### Post by lo gambusí on 2008-04-23
:p

Algú pot ajudar-me, però?

---

### Post by pespin on 2008-04-24
Has provat de tancar el dock i tornar-lo a borir sense tancar la sessió? amb quin resultat?

---

### Post by lo gambusí on 2008-04-24
Sí, també em funciona.

---

### Post by pespin on 2008-04-24
Una solució així ràpida que veig al tema és buscar el script que arranca el dock i posar-li un per exemple 'sleep 20' davant, per a que carregui les altres coses necessàries abans. Si l'arrancada l'has configurat des d'algun panell del gnome mira si hi ha alguna opció per a que el carregui més cap al final :)

---

### Post by lo gambusí on 2008-04-24
Això com ho faig? Des de sistema/administració/...?:?

---

### Post by pespin on 2008-04-24
Prova a 'Sistema->Preferencies->Sessions' si l'inicia el gnome o potser trobes l'script d'arrancada a /etc/init.d/ ¿?

---

### Post by lo gambusí on 2008-04-24
Seria [això]("http://img151.imageshack.us/img151/6295/capturawh6.png")? On posa 50 posar-ho a 20?

---

### Post by pespin on 2008-04-25
Al contrari, en aquest cas posa-hi un nombre més alt per a que ho carregui després (51? 60?)

---

