---
title: "Compilar kernel i altres productes del temps lliure"
date: 2008-04-01
forum: Catalan Team
---

### Post by raukonak on 2008-04-01
Hola!

Simplement tinc curiositat sobre tot això de compilar i tal. Segons tinc entés (jo d'informàtica nanai, tot és autodidacta) compilar és passar del codi (o sigui si passa menganito fés fulanito, o copia la memoria 1 a la memoria 2 i despres el que toqui...) a 0 i 1 per a que la màquina ho executi. El que tu baixes amb el apt son paquets que han estat compilats per a que funcionin amb tota una serie d'arquitectures i altres paranoies, com ara ix86, o el del powerpc o el del lowlatency. Però al ser més generic vol dir que no s'adapta tant bé al hardware que tu puguis tenir, per exemple, tens un kernel generic per a i386 i tu tens un i686, no? o li vols posar suport per a un driver de ves a saber què com ara un wifi o algo, o li has de desactivar el Acpi (que no se ni que és) perquè l'has d'instalar  en un pIII. Llavors hi han aquelles distribucions que venen precompilades com l'Arch per a una arquitectura, o la Gentoo, que pel que tinc entés cal compilar-ho tot.

Llavors, per simple curiositat, com funciona compilar? he llegit que cal posar uns flags que son les opcions amb les quals vols compilar el que sigui. Llavors, puc compilar el nucli i treure el que no necesiti i posar-hi el que si, per exemple, treure el suport per a bluetooth (no se si és un modul) i posar el driver de la targeta ati. La questió és, val la pena? 

I una altra cosa, si compilo qualsevol cosa, desprès per desinstalar com és fa? perque si no és un paquet no em sortira al apt, haig de fer el paquet jo mateix?

---

### Post by orestesmas on 2008-04-01
Tu ens vols mal, company. Respondre tota aquesta tira de preguntes requereix un llibre sencer, com a mínim.

L'avantatge és que no vas gens desencaminat. Jo diria que en essència has comprès bé el procés. Per tant, a veure si et guio una mica:

1) Com funciona compilar?
  - Obre un editor de textos i escriu el següent:

```

#include <stdio.h>

int main()
{
 printf("Hola a tothom\n");
}

```

 - Desa el fitxer amb el nom "prova.c" (acabes d'escriure un programa en llenguatge "C").
 - Obre un terminal, situa't al mateix directori on has desat el fitxer i compila'l amb:
```

gcc -o prova prova.c

```

(nota: has de tenir instal·lat un compilador de C, com ara el GCC)
Això et generarà un executable anomenat "prova", que pots executar des del mateix terminal teclejant
```

./prova

```

2) Marranejar i compilar el kernel, al teu nivell, no val la pena. No és cap comentari despectiu, és perquè probablement els beneficis seran molt inferiors als maldecaps.

Ara bé, a vegades el maquinari del teu PC no et deixa altra opcíó que compilar mòduls si vols que tal o qual cosa funcioni. Si és aquest el cas, molta paciència.

3) Quan compiles no instal·les res. El programa anterior simplement el pots desinstal·lar esborrant el fitxer resultant. Tots els programes "seriosos" tenen un sistema per instal·lar els executables resultants de la compilació als directoris on han d'anar. Malauradament, no tots tenen una ordre similar per desinstal·lar-los, de manera que no hi ha una forma genèrica per fer-ho.

Per sort, la majoria de programes compilats per l'usuari s'instal·len sota el directori de l'usuari que els compil·la, o bé sobre /usr/local, i per tant com que allí no hi acostuma a haver gran cosa, és fàcil anar allí a mirar i esborrar allò que calgui.

No sé si això respon els teus dubtes.

Orestes.

---

### Post by raukonak on 2008-04-01
ostres, merci per la paciencia, m'ha aclarit moltes coses però segueixo tenint uns quants dubtes:

1.) Tot això de compilar amb e gcc ho havia vist quan un company meu que fa química feia una cosa semblant amb el fortran ( que ell li deia "fotran" perquè li fotia bastant), però què té a veure amb lo típic del configure i el make?

2) Merci per l'advertiment, pel què he vist hi ha gent que té dies l'ordinador sencer per compilar no se què, però des que vaig fer el salt a linux he descobert un cantó friki que no sabia que tenia, m'ho passo bé instalant ves a saber què i carregant-me l'ordnador i haver de tornar-lo a formatejar. O sigui que potser si algun dia no tinc res a fer ho provo i ja us diré què tal. Saps on podria trobar informació sobre tot això? Un amic meu (el mateix del "fotran") té un pIII i diu que me'l deixa per a que li faci marranades. A part té una xbox vella i potser m'aniria bé saber quatre cosetes. I per cert, els del Gentoo com s'ho fan? es passen 2 dies per compilar-ho tot?

3)Es podria compilar un programa i empaquetar-lo per així poder-lo fer anar des del apt, i així poder desinstalar-lo o guardar-lo si formateges l'ordinador?

Moltes gràcies una altra vegada per contestar.

Carles

---

### Post by pespin on 2008-04-01
> 1.) Tot això de compilar amb e gcc ho havia vist quan un company meu que fa química feia una cosa semblant amb el fortran ( que ell li deia "fotran" perquè li fotia bastant), però què té a veure amb lo típic del configure i el make?

El configure i el make són els scripts/arxius d'instal·lació utilitzats per la majoria de programadors per a fàcilitat el treball a l'usuari a l'hora de compilar i instal·lar el programa.

El configure és un script que busca al teu ordinador que tinguis instal·lades les dèpendencies de llibreries i altres factos per a que la compil·lació és porti a terme correctament.

El make és una ordre de consola que llegeix un arxiu creat pel 'configure' previament (anomenat Makefile) i a partir d'aqui compila el programa estalviant molts mals de cap al usuari. Utilitzant 'make install' la ordre llegeix al Makefile i copia els arxius necesaris als directoris que toquin.
> 

3)Es podria compilar un programa i empaquetar-lo per així poder-lo fer anar des del apt, i així poder desinstalar-lo o guardar-lo si formateges l'ordinador?
Sí, però no és molt fàcil de fer diria (jo segueixo esperant cert llibre que en RainCT va dir que escriuria... xD)

---

### Post by RainCT on 2008-04-01
> **pespin said:**
> Sí, però no és molt fàcil de fer diria (jo segueixo esperant cert llibre que en RainCT va dir que escriuria... xD)

Haha. Vaig dir «potser», i al final resulta que el que faré serà sobre com muntar un servidor amb Ubuntu i serà com a treball de recerca :P.

Això sí, el 26 d'abril organitzem un (mini-)curs pràctic d'introducció a la creació i manteniment de paquets, així que si t'interessa ja saps. Aquí hi ha tota la informació al respecte:: [HolaHardy/PackagingJam (wiki)]("https://wiki.ubuntu.com/CatalanTeam/HolaHardy/PackagingJam").

---

### Post by orestesmas on 2008-04-03
> **raukonak said:**
> ostres, merci per la paciencia, m'ha aclarit moltes coses però segueixo tenint uns quants dubtes:

2) I per cert, els del Gentoo com s'ho fan? es passen 2 dies per compilar-ho tot?


Doncs en essència si. Dos o els que calgui, en funció de la potència de l'ordinador. L'avantatge és que si és hivern et pots estalviar l'estufa, perquè amb la calor que desprèn el processador ja n'hi ha prou.

De tota manera la Gentoo té un sistema d'instal·lació que et permet utilitzar parts precompilades per tal d'accelerar el procés (només durant la instal·lació del sistema, insisteixo, i sempre pots no usar-ho i compilar-ho tu tot).
També cal dir que he llegit en alguna banda que la Gentoo està caient en desús, perquè la feinada de compilar-ho tot no compensa els beneficis que s'obtenen, oimés quan avui en dia ja hi ha distribucions senceres optimitzades pels processadors més actuals.

> **raukonak said:**
> 
3)Es podria compilar un programa i empaquetar-lo per així poder-lo fer anar des del apt, i així poder desinstalar-lo o guardar-lo si formateges l'ordinador?


Ja t'han contestat això: és com una mena de màgia negra. Bé, tampoc no és impossible, però has de tenir al cap moltes coses:
 a) De quins altres paquets depèn el teu paquet.
 b) Quines accions s'han de fer en els següents casos:
   - Abans d'instal·lar-lo
   - Després d'instal·lar-lo.
   - Abans de desinstal·lar-lo
   - Després de desinstal·lar-lo.
  i crear uns "scripts" amb les ordres necessàries
 c) On cal ubicar tots els fitxers de què consta el teu paquet, seguint la política de la distribució

Tota aquesta informació s'ha d'ubicar en una sèrie de fitxers seguint una estructura de directoris especial, comprimir això, signar-ho digitalment i penjar-ho en alguna banda.

També sé que ubuntu té un sistema ([https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)) que facilita que els usuaris de "a peu" facin els seus paquets, però jo no ho he provat mai.

---

### Post by pespin on 2008-04-04
> Això sí, el 26 d'abril organitzem un (mini-)curs pràctic d'introducció a la creació i manteniment de paquets, així que si t'interessa ja saps. Aquí hi ha tota la informació al respecte:: HolaHardy/PackagingJam (wiki).

Doncs a veure si ho graveu i ho penjeu a algun lloc que malauradament tinc el cap de setmana ocupat >.<

---

