---
title: "Suavizat al dibuixar en kde"
date: 2007-12-23
forum: Catalan Team
---

### Post by CarlesOriol on 2007-12-23
Acabo de veure el programa filelight que recomanava l'Orestes en un altre post. (i és un gran programa tipus baobab però millor, amb una opció que val un imperi que és el poder obrir el konqueror directament en la carpeta seleccionada -si es pogués fer en nautilus ja seria la *st*a )

Però m'ha sortit un dubte al veure'l. No és un programa vell i el dibuixat de línies produeix dents de serra al no estar suavitzades (o antialiasejades... - destralejant el català-).

En gnome des de la versió de l'edgy la presentació gràfica es realitza en la majoria dels programes usant les llibreries cairo que produeixen una sortida de gran qualitat... fins i tot en hasefrog el gdi+ realitza aquesta funció... però... en kde 3.5 (el darrer 3) veig que encara hi ha programes que usen tècniques antigues de presentació gràfica.

La meva pregunta als mestres kdeaires és si això és una deficiència concreta d'aquesta aplicació o si no això no està implementat en les llibreries gràfiques de kde 3?

---

### Post by CarlesOriol on 2007-12-23
De fet estic provant d'altres programes i no m'havia fixat però el renderitzat gràfic és bastant pobre.

Això canvia en kde4?

---

### Post by lluisanunez on 2007-12-23
Les imatges que jo he vist s'*antialiasejaven* bé. Aquesta de la Wikipedia és de maig 2006, no hi havia KDE4:
[http://en.wikipedia.org/wiki/Filelight](http://en.wikipedia.org/wiki/Filelight)

PS. M'explicareu d'on surt això del hasefrog? Si cerco a google només veig pàgines linuxeres en català o castellà

---

### Post by papapep on 2007-12-23
hhehehe, això va sortir originalment dels de [Bulma]("http://bulma.net/body.phtml?nIdNoticia=1613"). I, realment, és "hasefroch", per això no ho devies trobar.

També, com no, hi ha un petit article a la [wikipedia]("http://es.wikipedia.org/wiki/Hasefroch").

---

### Post by CarlesOriol on 2007-12-23
No, no optimitzen el resultat ni la mescla.

Us adjunto un retall de la mostra que comenta la lluisa de la wikipedia i una imatge de mida similar realitzada amb el gnome + cairo + baobab.

Fixeu-vos en els separadors, en la línia negra diagonal. La imatge cairo és ferma. La kde és escalonada i l'intent d'antialias (ja que el programa intenta alguna cosa) sols aconsegueix esborronar les linies divisories però no fer-les consistents. 

Les dues imatges tenen la mateixa mida i no estan escalades. La de kde tenim la sensació que hem agafat un tros més petit.

---

### Post by lluisanunez on 2007-12-23
Sí, tens raó
Deu ser per això que el KDE em mareja una mica :-P

Per cert, el baobab sí que t'obre els directoris, però no des de la imatge sinó desde el panel lateral

---

### Post by eselma on 2007-12-23
Efectivament, he instal·lat el *filelight* (no el coneixia) i he comprovat que la presentació gràfica és suficient per al seu propòsit, però molt pobra per a ser un programa actual (traçat de diagonals i corbes).

No sóc mestre ni en KDE ni en res, però per sort els altres programes en KDE (tant si són gràfics com si no) els veig molt bé, i amb el seu corresponent antiàlies, llevat que els tregui específicament (no és el cas). En canvi, la versió 1.2X d'audacity (un programa Gnome) es veia penós en KDE, fins que a la versió 1.3X ja usa les biblioteques adients, i ara es veu tan bé com els altres. És l'únic cas recent que recordo de mala presència entre entorns diferents.

---

### Post by CarlesOriol on 2007-12-23
No. 

Son problemes diferents. El que comentes a l'audacity era degut al renderitzador de fonts fet que segueix passant en alguns programes en tcl/tk.

El que jo comento és en el funcionament de les eines de les comandes bàsiques de dibuix.

---

### Post by orestesmas on 2007-12-23
Si, això que comentes de l'antiàlies és interessant. La veritat és que a mi no em molesta pas, però si et poses a comparar efectivament la presentació del baobab és més suau.

No conec prou la programació en Qt com per dir si això és una qüestió de les llibreries subjacents o no. Gairebé et puc assegurar que les Qt4 porten de sèrie el suport per SVG i antiàlies, però desconec si el tema de l'antiàlies ja venia de sèrie en les Qt3 o s'ho havia de muntar el programador. Qui sap, potser són coses de la multiplataforma. Ho podem preguntar a l'Albert Astals...

De tota manera, també podria ser el Filelight. La funcionalitat d'aquest programa és interessant, però els seus "acabats" estan poc polits. Fins a la Feisty, sense anar més lluny, l'aplicació petava sistemàticament en tancar-se. A la Gutsy ho han corregit, però no pas l'estètica, que continua essent la mateixa.

---

