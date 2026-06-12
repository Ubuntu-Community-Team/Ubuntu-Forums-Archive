---
title: "Per unes simples cometes"
date: 2008-02-11
forum: Catalan Team
---

### Post by Daerun on 2008-02-11
Per tal que l'aMSN em mostrés correctament els accents, la ç i aquestes coses, vaig seguir els consells d'[AQUEST]("http://ubuntuforums.org/showthread.php?t=529536") post, és a dir, a /home/daerun/.amsn canviar l'arxiu "langlist.xml" perquè hi posés utf-8 en comptes de iso8859-1 a la llengua catalana.

Després, per continuar, vaig fer també la modificació perquè l'idioma sigui català, i no variant valencià; és a dir, a */etc/default* modificar l'arxiu "locale", i a */etc* l'arxiu "environtment" per esborrar de tots dos el '@valencia' i deixar-ho en " LANG="ca_ES.UTF-8".

Ara tot funciona molt bé, i puc escriure correctament. Però el què volia comentar és que, inicialment, un cop fetes les modificacions, vaig apagar l'ordinador, i quan hi vaig tornar, va resultar que no s'havien muntat d'inici ni el disc dur de dades que tinc a part, ni la partició de windows que encara conservo. Vaig reiniciar per entrar en mode recuperació, per verure si el problema era que feia falta fer la comprovació d'arrencada, però no. Vaig tornar a entrar en mode gráfic i tot estava igual.
Aleshores vaig pensar "calla, no sé si tindrá res a veure, perquè només era una modificació que afectava l'idioma, però no podria ser que fos conseqüència que he fet alguna cosa malament en tot el procés d'abans?". Vaig repassar els dos arxius de la carpeta /etc... i efectivament, en un d'ells, no recordo quin, m'havia oblidat d'escriure-hi les cometes finals, de menera que, en comptes de:

" LANG="ca_ES.UTF-8"

hi tenia escrit

" LANG="ca_ES.UTF-8

Tot per unes cometes!!! :? :?

---

