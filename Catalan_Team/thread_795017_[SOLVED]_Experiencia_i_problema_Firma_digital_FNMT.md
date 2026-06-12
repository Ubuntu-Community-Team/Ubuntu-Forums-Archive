---
title: "[SOLVED] Experiencia i problema Firma digital FNMT"
date: 2008-05-15
forum: Catalan Team
---

### Post by ilku on 2008-05-15
Hola companys:
L'altre dia per qüestions de feina vem demanar una signatura digital a FNMT (Fabrica de Moneda y Timbre). I ara explico, una mica el periple i un problema per si algú em pot donar un cop de mà.

1.- Per descarregar el certificat des de la web, nomes es pot fer des de el mateix ordinador que va fer la sol·licitud.
Com era una versió d'ubuntu antiga (dapper LTS) no podia descarregar-la, primer perquè la entitat certificadora FNMT no estava inclosa com a tal, sinó que vaig haver de posar-la (en versions posteriors, Gutsy i Hardy, ja esta inclosa). Després em donava un error en el aplicatiu Java (no se que cony necessita d'aquest) des de el Firefox. Total que el vaig descarregar mitjançant el Konqueror (cap problema).
2.- Un cop descarregat i instal·lat.
Faig les comprovacions a la mateixa web (firefox), i és correcte.
Provo la signatura de mails amb evolution signant amb s/mime correcte.

I aquí ve el problema:
Quan intent signar un document de openoffice no puc. Faig una cerca per sant Google i trobo que d'exportar una variable d'entorn.
$export MOZILLA_CERTIFICATE_FOLDER=/home/ilia/.mozilla/firefox/profile.default

On profile és el resultat de

$cat /home/ilia/.mozilla/firefox/profile.ini

Llavors executo

$ooffice

I FUNCIONA

Quin és el problema?? Doncs que si executes des de el menú o des de llançadora no funciona, ni tan sols si varies la llançadora original "ooffice -writer %U" per "ooffice".

Algú sap com solucionar-ho?

Gracies per endavant

---

### Post by papapep on 2008-05-15
mmm.....i jo pregunto....si un cop has exportat la variable d'entorn al terminal, tanques la sessió gràfica i la tornes a obrir (sense tancar l'ordinador, eh!) et funciona la signatura?

---

### Post by oriolsbd on 2008-05-15
Crec que no hauria de funcionar. L'export permet passar la variable al procés actual (el terminal) i els seus processos fills. Per això quan s'executa "ooffice" des del mateix terminal agafa la variable exportada, però quan s'executa des del menú (que no és un procés fill del terminal on s'ha exportat la variable) no funciona.

Podríes posar la línia d'export en el fitxer .profile del directori /home/ilia (gedit /home/ilia/.profile). Aquest fitxer .profile s'executa cada cop que et connectes amb l'usuari. Com a mínim és així en entorns Unix. Algú hauria de confirmar que en Linux també funciona així o si s'ha de posar en algun altre fitxer.

Per cert, perquè et funcioni el canvi en el .profile s'ha de reiniciar la sessió.

Salut!

---

### Post by papapep on 2008-05-15
A Ubuntu les variables globals es fiquen a /etc/environment.

---

### Post by ilku on 2008-05-15
Gracies per les vostres aportacions, dema al mati ho probare.

Aixi doncs si no ho entes malamet la exportacio de la variable queda anulada en reiniciar la maquina i l'exportacio global a de ser a /etc/environment

La següent pregunta obligada és, si utilitzo el mateix metode, es a dir:
$export .....  /etc/environment

o bé faig:

sudo gedit /etc/environment

i llavors fico a dins

export .....

Gracies

---

### Post by oriolsbd on 2008-05-15
Hola, Ilku.

Has d'utilitzar el segon mètode: editar el fitxer /etc/environment i en aquest fitxer afegir la línia de l'export.

Papapep, entenc que el fitxer /etc/environment aplicarà aquesta variable a tots els usuaris quan es connectin a l'ordinador. Si volem assignar la variable només a un usuari, quin fitxer seria el correcte?

Salut!

---

### Post by papapep on 2008-05-15
> Papapep, entenc que el fitxer /etc/environment aplicarà aquesta variable a tots els usuaris quan es connectin a l'ordinador. Si volem assignar la variable només a un usuari, quin fitxer seria el correcte?


Correcte, /etc/environment és global pel sistema. 

Per a un sol usuari es troba a /home/nom_d'usuari/.bashrc

---

### Post by ilku on 2008-05-16
Hola companys:

He provat les dues possibilitats i no funcionen, no sé si ho he fet bé. Ara vos faig cinc cèntims (d'euro :) )

Primer he probat a fer 
"sudo gedit /home/ilia/.bashrc"

i afegir al final el text
"export MOZILLA_CERTIFICATE_FOLDER=/home/ilia/.mozilla/firefox/9y127kex.default"

i res continua igual. Funciona amb crida desde terminal pero no desde menu

Després he provat a fer
"sudo gedit /etc/environment"

i afegir el text al final i a sota d'un altre export (una vegada cada una)
"export....." 

El sistema on ho he provat es un Dapper, em penso que no ha de canviar res.

Continuaré buscant haver-ha que trobo i per descomptat accepto suggerencies :)

---

### Post by papapep on 2008-05-16
Ja has reiniciat el sistema després de inserir les variables?

---

### Post by ilku on 2008-05-16
Si, he reiniciat per cada prova que he fet

---

### Post by oriolsbd on 2008-05-16
Un cop reiniciat, obre un terminal i fes:
echo $MOZILLA_CERTIFICATE_FOLDER

Què et retorna? Si et retorna el directori del certificat vol dir que s'ha agafat bé la variable. Si et retorna una línia en blanc, vol dir que no ha agafat bé la variable.

Salut!

---

### Post by ilku on 2008-05-16
Hola companys:

He provat en una altre maquina amb gutsy i FUNCIONA, però nomes quan es passa la variable de forma global.
Es a dir:

$sudo gedit /etc/environment

"export ...."

Si posem la variable a l'entorn usuari ($sudo gedit /home/nom_d'usuari/.bashrc) no funciona

Probare en una maquina amb hardy en quan tingui temps i vos diré quelcom

Una salutació

---

### Post by ilku on 2008-05-16
Em sap greu no haver provat això que em comentes oriol, ho probare demà.
Ho havia provat al tren i al veure que funcionava ho havia d'explicar urgentment i no havia llegit el teu post :lolflag:

---

### Post by ilku on 2008-05-19
Aquest cap de setmana he insta·lat la Hardy al portàtil per provar això de la firma (entre d'altres coses :)). I quina es la meva sorpresa que a funcionat a la primera, ni tan sols he hagut de reiniciar la maquina. Sorpresa perquè ja ho havia provat a una Hardy en el pc de sobretaula de casa i no havia funcionat pas. No se per què c.... ara funciona, però funciona. Ara només falta que actualitzi tota la xarxa a Hardy (ostres quina mandra 2 servers i 4 clients) i ja estarà.

Estic molt agraït a tots per la ajuda que m'heu donat.
Ara marcaré el fil com a resolt, tot i que hauria de provar que no sigui accessible des de un altre usuari.

---

