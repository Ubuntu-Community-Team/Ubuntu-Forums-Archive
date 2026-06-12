---
title: "[SOLVED] Necessito ajuda urgent!!"
date: 2008-06-15
forum: Catalan Team
---

### Post by Satboy on 2008-06-15
Hola,
 Ahir mentre mirava un PowerPoint via PowerPointViewer (Wine) l'ordinador se'm va penjar.Com que no responia a cap acció vaig prémer Ctrl+Alt+Sup i el vaig reiniciar.Des d'aleshores l'he reiniciat 4 vegades i no em surten les barres superior ni inferior de l'escriptori.Algú se li acut que puc fer? Si us plau expliqueu'm-ho pas a pas.

 Gràcies per endavant!

A10!:wink:

---

### Post by papapep on 2008-06-15
Podríes provar un:

```
sudo dpkg-reconfigure ubuntu-desktop
```

Per cert, recorda ficar quin és el problema a l'assumpte del fil, si us plau.

---

### Post by Satboy on 2008-06-15
> **papapep said:**
> Podríes provar un:

```
sudo dpkg-reconfigure ubuntu-desktop
```

Per cert, recorda ficar quin és el problema a l'assumpte del fil, si us plau.

 Hola Papapep,
 He fet el què tu m'has dit i he obtingut la següent resposta:

 /usr/sbin/dpkg-reconfigure: ubuntu-desktop no està instal·lat

 A10!:wink:

---

### Post by papapep on 2008-06-15
Hi ha dues opcions, o fas servir KUBUNTU (amb KDE) o has desinstal·lat el Gnome. Quina és la bona?

---

### Post by orestesmas on 2008-06-15
S'ha de llegir entre línies, papapep. No estic massa familiaritzat amb Gnome però em sona que per omissió és l'únic que porta una "barra" superior i una inferior a l'escriptori.

Per tant, el que hauria de fer és provar de reinstal·lar el paquet ubuntu-desktop (o, encara millor, el kubuntu-desktop :-) ). Vés a saber perquè se li haurà desinstal·lat!

Per cert, em pregunto com s'ho haurà fet per executar el sudo dpkg-reconfigure ubuntu-desktop, si no tenia els panells de l'escriptori i per tant no devia poder tenir menús... Se n'ha de saber una mica...

---

### Post by Satboy on 2008-06-16
> **orestesmas said:**
> S'ha de llegir entre línies, papapep. No estic massa familiaritzat amb Gnome però em sona que per omissió és l'únic que porta una "barra" superior i una inferior a l'escriptori.

Per tant, el que hauria de fer és provar de reinstal·lar el paquet ubuntu-desktop (o, encara millor, el kubuntu-desktop :-) ). Vés a saber perquè se li haurà desinstal·lat!

Per cert, em pregunto com s'ho haurà fet per executar el sudo dpkg-reconfigure ubuntu-desktop, si no tenia els panells de l'escriptori i per tant no devia poder tenir menús... Se n'ha de saber una mica...

 Hola,
 Bona observació **Orestes**, tinc la drecera de la cònsola a l'escriptori.
  Intentaré de fer el què em dius aquesta tarda, ara sóc a la feina i treballo amb el **Finstres XP**.

 A10 i gràcies!:wink:

---

### Post by CarlesOriol on 2008-06-16
Prova també a la consola d'executar el gnome-panel a veure que diu.

---

### Post by Satboy on 2008-06-17
Hola Tothom,
 Gràcies a la vostra sapiència ho he pogut resoldre, no sé pas què hauria fet sense el vostre ajut!!
 El que he fet ha estat executar el Synaptic des del Terminal ( sudo synaptic) i un cop a dins he reinstal.lat l'ubuntu-desktop.
 Un cop més gràcies a tots els "cracks" del fòrum.

 A10!;-)

---

### Post by CarlesOriol on 2008-06-19
Pots deixar un titol més descriptiu per si algú cerca informació?

---

