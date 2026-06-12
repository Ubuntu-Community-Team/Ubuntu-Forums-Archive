---
title: "APIC error on CPU: 40(40)"
date: 2008-10-31
forum: Catalan Team
---

### Post by KiKuX on 2008-10-31
Hola, aquest és un dubte plantejat a latres llocs pero de moment l'unica solucio que m'han donat, és consultar un parell de bugs, una mica antics, i jo voldria saber alguna cosa mes del tema.
Si em podeu ajudar... que algu em digui si el que dic aqui es cert o vaig errat:

estic forgant en un error que m'apareix als missatges del kernel i a syslog, soc bastant novell en linux pero faig el què puc.
Ara mateix faig servir ubuntu hardy amb el nucli 2.6.24-21
Tinc un ACER espire 7720g
intel core duo T7100
El dubte es el seguent
corregiu-me en el que jo digui:
APIC és el control d'interrupcions del CPU que rep les ordres d'interrupcions desde els diferents canals  IRQ,  m'apareix en el registre del kernel i  a  syslog, l'erro seguent:

[ "una serie de nombres" ]  APIC error on CPU0: 40(40)

l'error es repeteix indefinidament i dins els claudators sempre hi ha un nombre diferent pero creixent.

Que vol dir en general?
Que es aquest 40 ?
Potser és un canal IRQ?
Alguna possible idea de solució?

M'han proposat de arrenacar el kernel amb la opcio "noapic", no se com es fa pero si no m'equivoco es afegir "noapic" al menu de grup en la linia on es carrega el kernel. Però aquesta es la solucio???
si jo tinc dos nuclis a la CPU (cuore duo) i faig "noapic", no estic tallant la comunicacio entre ells???

Gracies per tot...
Salut i força LinuX !!!!

---

