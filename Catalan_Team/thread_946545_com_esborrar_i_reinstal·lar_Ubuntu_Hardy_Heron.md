---
title: "com esborrar i reinstal·lar Ubuntu Hardy Heron"
date: 2008-10-13
forum: Catalan Team
---

### Post by Carles_BE on 2008-10-13
Hola novament

m'agradaria esborrar completament Ubuntu de la meva màquina (però tranquils que no és que vulgui passar-me novament al costat fosc :))

Fa uns dies intentant connectar una VirtualBox a la xarxa vaig "tocar" alguna cosa que no tocava (estava treballant des de la consola i sóc molt inexpert) i des d'aleshores tinc una mica de problemes de connexió a la xarxa (es connecta i desconnecta a voluntat d'ella)
La causa podria ser alguna altra, evidentment, però no vull perdre el temps investigant perquè ja m'anava pel cap que, si ficava la pota (o sense ficar-la), reinstal·laria Ubuntu de cap i de nou per a practicar i tindre ben clar com es fa 

He estat mirant per forums i m'ha semblat entendre que ho puc fer directament amb el LiveCD (el fico al lector i segueixo les instruccions com el dia que vaig fer la primera instal·lació)

La pregunta és: vaig bé i amb el LiveCD podré reinstal·lar Ubuntu i esborrar al mateix temps la distribució que tinc ara o la cosa és més complexa? (no vull guardar cap de les dades que tinc)
Algú s'hi ha trobat en aquest cas?

Gràcies per endavant

---

### Post by enricXIII on 2008-10-13
Suposo que tens instalat l'ubuntu com a unic sistema operatiu al teu ordinador..si es aixi no hi ha cap problema. Amb el live cd fas una instalacio normal i corrent, a tot el disc i t'esborrarà tot el que tenies fins ara.

---

### Post by Carles_BE on 2008-10-13
Oops ... també tinc el Windows ... però vaja ... si s'ha d'esborrar cap problema ... que estem amb proves:)

Gràcies

---

### Post by Rubunter on 2008-10-13
> **Carles_BE said:**
> Oops ... també tinc el Windows ... però vaja ... si s'ha d'esborrar cap problema ... que estem amb proves:)

Gràcies

En aquest cas, per conservar el windows, dins els menus del LiveCD quan toqui particionar el disc, tria la opció manual. un cop alla, tries la particio on tens instal·lat l'ubuntu i selecciones modificar la partició. En el menú que t'apareixerà:

1.com a sistema de fitxers tries ext3 que és el predeterminat(o qualsevol altre depenent de l'us que en fagis)

2. Com a punt de muntatge, si no m'equivoco, tries / 

3. El tamany de la partició no cal que el canviis si ja t'estava be com ho tenies

4. Selecciones la casella pq et formategi la particio (si no fas aixo crec que instal·laria el sistema a sobre, però tampoc n'estic 100% segur pq no ho he fet mai)

5.Apliques els canvis i llestos!

Si m'he equivocat en algun pas (o en tots) o m'he deixat alguna cosa important que algú em corregeixi si us plau.

---

### Post by enricXIII on 2008-10-14
Be, suposo que tal com a dit el company Rubunter ja estaria be, pero jo el que faria en aquest cas (amb pindows instalat), seria esborrar la particio on tinc ubuntu amb el Gparted, desde el live cd, i deixar neta aquesta particio. Despres nomes cal iniciar sessio amb el live cd i a l'hora d'instalar, indicar que ho fagi a la particio que has deixat neta. Es sencill quan ho fas un cop i ho veus...pero ja se que fa por! a mi m'en feia molta quan començava amb linux..tenia pànic a particionar!

---

