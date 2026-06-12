---
title: "Funcionament continuo del ventilador de la CPU, que pot estar passant?"
date: 2008-02-18
forum: Catalan Team
---

### Post by lluisalguero on 2008-02-18
Hola companys,
ja fa dies que tinc la mosca darrera l'orella. Resulta que el ventilador de la CPU del meu portàtil, està més estona a tope de revolucions que no a poques.
Precisament no es que l'estigui exprimint ni molt menys. Normalment faig anar el Firefox i Thunderbird, apart del aMSN.
He estat mirant al monitor del sistema i ni de lluny la CPU està al 100% i es que no se com veure la temperatura del sensor de la CPU, vaig provar lmsensors, però no me'n vaig poder sortir.
Puc veure d'alguna forma què o perquè aquestes acceleracions del ventilador?

Gràcies,
Lluís

---

### Post by SiscoGarcia on 2008-02-18
Fa un temps [es va parlar]("http://ubuntuforums.org/showthread.php?t=464286&highlight=temperatura+cpu&page=3") al fòrum sobre com conèixer la temperatura del sistema, és a l'estil papapep, però com el seu nom indica funciona;)

---

### Post by lluisalguero on 2008-02-18
Ara ja sé perquè funciona continuament el ventilador...

[B]lluis@lluis-laptop:~$ cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             71 C
lluis@lluis-laptop:~$

[/B]

Gràcies per l'informació

---

### Post by papapep on 2008-02-18
Però la qüestió és el perquè s'escalfa tant. Potser s'ha fet malbé el conductor de calor que hi ha entre el disipador i el processador. En aquest mateix fòrum hi ha hagut gent que ha comentat que els havia passat això, i se'ls posava la màquina com per a fer-hi pizzes.

---

### Post by lluisalguero on 2008-02-18
Gràcies papapep, pel consell. El que faré será anar on el vaig comprar i com que encara està en garantia que me'l mirin. He fet la meteixa comprovació al WXP i els resultats son similars.

Ara em sorgueix una pregunta. S'escalfen més els portàtils que els de torre?

---

### Post by papapep on 2008-02-18
No depèn del format, depèn de què li facis fer. A igual feina també, evidenment, de com estan fabricats. Em refereixo a que si mires una caixa d'una torre de marca i d'un clònic, veuràs la diferència de disseny interior on fins i tot es veu que es preocupen del flux de l'aire dins per a que dissipi millor la calor. Aleshores puc creure que tampoc tots els fabricants, o ensambladors, de portàtils s'hi miren per igual en aquesta qüestió.
Si veièssiu per dins el nou servidor que hem posat a la feina (una bèstia parda) al·lucinarieu (jo ho vaig fer) de com està dissenyada, pensada i repensada la distribució dels elements a l'interior (prometo que si l'haig d'obrir li faré fotos).
Ja no sé si he respost el que preguntaves o no :-)

---

### Post by guillemsola on 2008-02-18
Hola,penso que per exemple si fos el sensor que estigués danyat aleshores l'aire que sortiria estaria fred. Si és veritat que la CPU està a 71º aquest aire sortirà  bastant calent. Amb això crec que podríem decantar-nos per si falla el sistema de ventilació o realment s'està escalfant molt.

Si l'aire està calent i no està la CPU a tope potser ja és cosa de que no ventila gaire bé.

Recordo un portàtil que tenia la sortida d'aire a sota i si te'l posaves sobre les cames no respirava bé i es resetejaba sol.

---

### Post by rajoar on 2008-02-19
Encara que potser sembli una tonteria..., a vegades els ordinadors generen un munt de pols interna... A mi em va passar i després de fer una bona neteja amb l'aspirador... Això sí, anant molt en compte!, el ventilador va tornar a funcionar com quan era nou!
No sé si pot ser aquest el teu cas?...

---

### Post by lluisalguero on 2008-02-19
> **rajoar said:**
> Encara que potser sembli una tonteria..., a vegades els ordinadors generen un munt de pols interna... A mi em va passar i després de fer una bona neteja amb l'aspirador... Això sí, anant molt en compte!, el ventilador va tornar a funcionar com quan era nou!
No sé si pot ser aquest el teu cas?...

Aprofitarem l'estona que passem l'aspirador per casa, per treureli la pols...gràcies per la suggerència.

---

### Post by eduardsola on 2008-02-19
> **lluisalguero said:**
> Aprofitarem l'estona que passem l'aspirador per casa, per treureli la pols...gràcies per la suggerència.

Jo ho faria amb un vaporitzador (es deia així? xD)

---

### Post by SiscoGarcia on 2008-02-19
Per treure la pols de l'ordinador, a part de fer-ho amb un aspirador, també es pot fer amb un assecador de cabell. És més brut perquè mou cap a fora tota la pols però potser és menys violent, no?

---

### Post by CarlesOriol on 2008-02-21
Res...

El millor és a la banyera. 25 litres d'aigua calenta, 1 pot de mistol i 1/2 litre de pintura "minio" per que no es rovelli, 1 sobret de cues de pansa dia per la memòria, colorant alimentari continente de tres colors per la gràfica i un sobre de colors de bàtic per tenir un salva pantalles ben xulo.

Deixes l'ordinador dins uns 25 minutets i ja veuras no torna a fer soroll mai més.

---

### Post by CarlesOriol on 2008-02-21
Ara sense conyes.

Sent un portàtil el pots agafar tipus armònica i per la reixa del dissipador fotre una bona bufada. Hi ha esprais d'aire a presió si ho vols fer més "profesionalment".

El problema és que la màquina no deu tenir un bon corrent d'aire intern per tant per molt que ventili no s'aturarà mai. Existeixen unes plataformes pels portàtils que bàsicament el que fan és que tingui més espai a sota i produeixen corrent d'aire. 

És un ventilador més però et pots aconseguir que la màquina et duri més anys.  Les parts més crítiques acostumen a ser el hdd, la pantalla i darrerament el procesador.

Jo en una reforma que vaig fer a casa va entrar pols i em va fondre la pantalla del portàtil... brutal!

---

### Post by lluisalguero on 2008-02-22
Carles, amb el portàtil que faig ara? L'estenc a la terrasa o el fico a l'assecadora?

L'opció aquesta del "dock station" amb els ventiladors també la tinc contemplada, però primer és passar pel servei tècnic...que encara té garantia !!!

---

### Post by CarlesOriol on 2008-02-22
Prova abans això de bufar, encara que et sembli una bestiessa.

Pel tema de secar-lo assegura't de treure la bola del mouse que amb la centrifugadora després van accelerats :-)

---

### Post by rroca1 on 2008-02-24
LA "MÈ": 

A mi em passava i vaig treure de dins del dissapador" una estoreta" de pols com les que surten de sota els radiadors de la calefacció. D'altra banda el tema de la temperatura és recurrent: Els processadors es dissenyen pensant en que cal que "xutin" i refredar-los no és el seu problema. Tinc un PIV de torre que amb el ventilador que duia de la intel no ens deixava treballar al despatx -de la fressa que feia - El vam canviar per un ple de llumetes blaves i el soroll s'ha acabat. Amb els portàtils el tema és més complicat.

(NETEJA'L O FES QUE ALGÚ EL NETEGI I ET CANVIÏ LA "POMADA" QUE PORTA EL PROCESSADOR I SEGUR QUE MILLORA)

Ricard:guitar:

---

