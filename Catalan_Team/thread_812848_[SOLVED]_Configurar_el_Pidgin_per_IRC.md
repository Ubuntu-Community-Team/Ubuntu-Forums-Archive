---
title: "[SOLVED] Configurar el Pidgin per IRC"
date: 2008-05-30
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-30
Bones!

Abans per conectar-me al IRC feia ús del *Kopete* però ara m'he avessat a fer servir el *Pidgin* i m'agradaria poder utilitzar-lo també per l'IRC.

El problema es que quan afegeixo el compte d'IRC, no hem deixa entrar al grup d'ubuntuCat...


Alguna idea?

Merci! ;)

---

### Post by papapep on 2008-05-30
> no hem deixa entrar al grup d'ubuntuCat

cal que expliquis una mica més com "no et deixa" entrar al canal d'ubuntu.cat. El canal és públic i completament obert a tothom, evidentment, o sigui que deu ser que no tens alguna cosa ben configurada al Pidgin.

---

### Post by LitusMayol on 2008-05-30
Perdó, no m'he explicat.

A veure...

Al Pidgin premo "*Crtl+A*" per afegir un nou compte. Allí premo "*Afegeix*". En la finestreta eixint em surten les opcions següents:

**-Protocol:** IRC
**-Nom d'usuari:** LitusMayol
**-Servidor:** irc.freenode.org
**-Contrasenya:** *********
**-Àlies Local:** LitusMayol
**-Recorda la contrasenya** (marcat)

Aleshores clicko a "*Desa*". Es conecta. 

Aquí ve el que no entenc... Se m'obre una finestreta de xat amb dues pestanyes. En una hi diu:

"*(16:43:22) freenode-connect: Received CTCP 'VERSION' (to litusmayol) from freenode-connect*"

I en l'altra:

"*(16:43:22) NickServ: (notice) LitusMayol is not a registered nickname.*"


Jo no he registrat re per entrar al IRC. Quan utilitzava el **Kopete** no vaig haver de registrar re... 



(**papapep**, millor? ;) Acabo de llegir l'altre i era nul de sentit xD Perdó. :D )

---

### Post by papapep on 2008-05-30
Ara perfecte Litus. És una bona pràctica rellegir-se els posts (i els correus) abans d'enviar-los. Hi ha cops que jo mateix em faig creus de les bestieses que puc redactar en una primera embranzida...

Doncs això té a veure amb els servidors de Freenode que fa uns anys, si no recordo malament, van canviar la seva operativa a fi d'evitar, o minimitzar, trolls i demés marranades que solen córrer per les xarxes d'irc (mirar irc-hispano per a més referències). Aleshores, no recordo exactament com, si registres el teu nick, un cop entris la contrassenya et dirà que t'ha reconegut i punt. Potser el problema és que no tens ben posada la contrassenya?
Quan tingui un moment miro el tema de com registrar el nick (si no ho trobes tu abans ;-))

---

### Post by RainCT on 2008-05-30
Pots registrar el teu nick fent:
```

/msg NickServ REGISTER <contrasenya> <e-mail>

```

Tot i que t'ho recomano, fer això no és necessari; si borres la contrasenya de la finestra de configuració deixarà de queixar-se (no sé quina contrasenya hi deus haver posat si dius que no t'has registrat... o_O).

---

### Post by LitusMayol on 2008-05-31
> **RainCT said:**
> Pots registrar el teu nick fent:
```

/msg NickServ REGISTER <contrasenya> <e-mail>

```

Tot i que t'ho recomano, fer això no és necessari; si borres la contrasenya de la finestra de configuració deixarà de queixar-se (no sé quina contrasenya hi deus haver posat si dius que no t'has registrat... o_O).

Si senyor... això ha sigut un cop bai, però útil! xD Especialment lo de "*no sé quina contrasenya hi deus haver posat si dius que no t'has registrat... o_O*". hehe. 

Perfecte, ara no es queixa... però com entro al canal ubuntu-cat?


Merci! ;)

---

### Post by RainCT on 2008-06-01
> **LitusMayol said:**
> Perfecte, ara no es queixa... però com entro al canal ubuntu-cat?

Molt fàcil, tens dues possibilitats:

a) En alguna de les finestres que se't obren, escriure-hi: «/join #ubuntu-cat» (sense les cometes i vigilant que no hi hagi cap espai abans de la barra invertida).

b) Fent-ho a la manera del Pidgin: A la finestra principal, «Amics» -> «Afegeix un xat». Tria el compte d'IRC, a Canal posa-hi «#ubuntu-cat» i la contrasenya deixa-la en blanc (el nostre canal no en té); a la resta de camps hi pots triar el que vulguis.

---

### Post by LitusMayol on 2008-06-01
> **RainCT said:**
> Molt fàcil, tens dues possibilitats:

a) En alguna de les finestres que se't obren, escriure-hi: «/join #ubuntu-cat» (sense les cometes i vigilant que no hi hagi cap espai abans de la barra invertida).

b) Fent-ho a la manera del Pidgin: A la finestra principal, «Amics» -> «Afegeix un xat». Tria el compte d'IRC, a Canal posa-hi «#ubuntu-cat» i la contrasenya deixa-la en blanc (el nostre canal no en té); a la resta de camps hi pots triar el que vulguis.

Merci! 

Solucionat! ;) Gràcies **RainCT**.

---

