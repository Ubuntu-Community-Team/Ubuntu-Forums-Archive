---
title: "Això està que crema !!!"
date: 2008-04-27
forum: Catalan Team
---

### Post by lluisalguero on 2008-04-27
No sé que pot passar al meu portàtil...avui sense més ni més, s'està escalfant a 3 de fondo...

```
-Temperatures-
temp1		: 97,00°C
temp1		: 97,00°C
-Voltage Values-
-ACPI Thermal Zone-
THRM		: 104°C
-Hard Disk Temperature-
SAMSUNG HM160JI (/dev/sda): 34°C
```

La CPU està constantment al voltant del 40-60% i només està obert el navegador.

Us adjunto un "pantallasu" del monitor del sistema, per si vosaltres veieu alguna cosa..

---

### Post by crazyserver on 2008-04-27
Ermmm has marcat en el menú, que et mostri tots els processos?

---

### Post by lluisalguero on 2008-04-27
> **crazyserver said:**
> Ermmm has marcat en el menú, que et mostri tots els processos?

Crec que si..però ho tornaré a mirar. He parat una estona el portatil, no sigui cosa que comensi a sucarrimar-se

Edito: si, es mostren tots el processos..

---

### Post by lluisalguero on 2008-04-27
Us deixo un altre pantallasu i dalt de tot podeu veure la simetria de l'us de la CPU, tot plegat ben extrany...

---

### Post by patrickfromspain on 2008-04-27
es ben estrany això. Deixant de banda si ubuntu funciona bé o no (no sembla que hi hagi problema en aquest sentit, segons els gràfiques adjuntades), el que veig clar es que el teu portatil no va bé.

M'explico: no va bé perque 97ºc... tela marinera! Es moltissim. Hi pot haver 2 problemes: o que ubuntu no engegui els ventiladors o que aquest no vagin bé. Mira a ver si els ventiladors van o fan quelcom estrany. Si sempre t'ha anat bé i ara de sobte no.. jo apostaria pel hardware.

salut!

---

### Post by lluisalguero on 2008-04-27
Els ventiladors funcionen correctament, ja que van a "tope" revolucions (o al menys això em sembla pel soroll que fan, que és molt).

Tinc una mala sort amb els pc's i la temperatura que no us podeu ni imaginar...un pc ja se'm va "rostir" per això

---

### Post by patrickfromspain on 2008-04-27
doncs bé, revisa-ho... Ubuntu pot ser una part del problema (en el sentit que igual esta estressant el processador sense motiu), però segur que el teu hardware té algun tipus de mal funcionament. El pc, si esta ben dissenyat, hauria de poder funcionar perfectament amb la CPU a tope, encara que sigui un portatil.

El fet que sentis molt de soroll dels ventiladors no implica necessariament que estiguin funcionant correctament. O potser, encara que funcionen correctament, els dissipadors estan taponats i no es pot refrigerar el conjunt.

salut!

---

### Post by Miquel Ubuntero on 2008-04-27
Bones.
Estic d'acord amb el Patrick, que els ventiladors facin molt soroll, no vol dir que funcionin correctament. De fet, pot ser, hi ha algun objecte intrús o 
excés brutícia. A les botigues de electrònica venen pots d'aire a pressió. Van molt be per netejar els ventiladors.
Salut!

---

### Post by lluisalguero on 2008-04-28
Si es un problema de hardware, com es que amb el finestres no passa això? Pot ser ens tindriem que decantar a algún tipus de problema amb l'ubuntu...no sé...dic jo

Tot i això miraré de netejar el disipador i ventilador de la CPU

Gràcies pels vostres consells

---

### Post by crazyserver on 2008-04-28
Fes una cosa (amb risc de que es pengi l'ordinador...)
procés que vegis que es passa de la ratlla per les bones, mata'l (si es alguna cosa que tu li has manat no el matis!XD)

Abans però podries mirar de fer el següent:
- canviar el driver de la gràfica
- Funcionar sense compiz: metacity --replace

---

### Post by patrickfromspain on 2008-04-28
aaamigo, aixo no ho habies dit ;)

No se, en principi per a mi nomes hi ha 2 opcions:
A) Que ubuntu no activi els ventiladors quan toca
B) Que ubuntu requereixi més processador que el windows, i per tant encara que els ventiladors no vagin bé, en windows "no es nota"

salut!

PD: es possible saber la temperatura del processador a windows, així com l'us?

---

### Post by CarlesOriol on 2008-04-28
A veure... jo veig a la gràfica que hi ha sempre un nucli "xupant" el 100% i d'aquí el simetrisme que comentes que es perfectament normal.
Per tant estem parlant d'un procés que està fregint la màquina. Si al windows fem anar un process també al 100% crec que estariem en la mateixa situació per tant jo descartaria un problema inicialment de programari (tot i que caldrà resoldre que és el que està prenent tant de temps) i tornaria a la idea inicial del maquinari.

Comprova que el teu ordinador no sols tingui els ventiladors correctament, sinò que el fluxe intern de l'aire sigui el correcte. Una màquina muntada amb els ventiladors de caixa malament acostuma a portar problemes d'aquest tipus.

Comprova 
1. L'aire calent ha de sortir per dalt de l'ordinador (normalment pel ventilador del transormador, un ventilador superior, o unes bones obertures no taponades. Si tens un ventilador al costat del micro a la caixa extraient aire pot estar "ofegant" el disipador del procesador.
2. El recorregunt intern de l'aire és possible i no està bloquejat per seccions de caixa, cables gegants, un merder de cables o plaques que tallin la circulació de l'aire. 
3. Un mal contacte pot produir que un dispositiu s'escalfi i això es propagui a tota la màquina. Comprova-ho i assegura't que l'origen de la temperatura sigui el micro. També pot ser que algun component malgrat estar correctament connectat s'escalfi en excés (pot ser la gràfica), llavors et caldrà cercar una altra forma de refrigerar-lo.

---

### Post by CarlesOriol on 2008-04-28
Llegint encara una mica més quan parles de la teva "mala sort" em fa pensar que no tinguis l'ordinador en un lloc tancar o bloquejant les entrades i sortides d'aire. Moles taules de disseny estan mal parides i tot pot ser que tinguis una taula assassina.

---

### Post by patrickfromspain on 2008-04-28
carles, es un portatil.. per tant es redueixen bastant les opcions. O bé, més que reduir-se, es compliquen.

salut!

---

### Post by CarlesOriol on 2008-04-28
vaja... amb això que els fils es parteixen de diverses pàgines no ho havia vist.

No he caigut que fos un portàtil per que és normal que la bios dels portàtils els aturi en cas de sobreescalfament del micro i això a diferencia dels sobretaula no acostuma a ser modificable.

Bé... doncs anem per feina... insisteixo en que primer cal mirar per que arriba a aquesta temperatura i despres ja veuras quin proces t'està saturant la màquina. (que per cert a mi m'ho fa sovint el tracker amb un ordinador que tinc quan escaneja una partició ntfs).

Agafa el portàtil i per tot arreu on vegis forats comença a BUFAR com un desesperat. COM SI FOS UNA HARMÒNICA. Dic buffar per que el problema acostuma a ser un taponament de dins cap a fora per tant tornem la merda a origen per desbloquejar-la. Cerca sobretot l'opertura que es poden veure unes ragletes de coure a l'interior.
Un cop fet això i amb el nas ple de polsim que no et deixa respirar agafes l'aspirador i ara si, treus tota la porqueria.

Si el portàtil arriba a aquesta temperatura probablement els sensors s'hauran espatllat i be del tot no tornarà a anar mai. Ara (i sols si ja tens la màquina a unes temperatures altes però raonables 40-60º) ves a comprar una plataforma amb ventiladors.

Digues com han anat les proves.

---

### Post by lluisalguero on 2008-04-29
Gràcies pels vostres consells. Tenia un pot d'aire comprimit i està esgotat, pasaré per la botiga a per un altre i a veure que pasa.

Així a primer cop d'ull, no sembla que les reixetes estiguen molt brutes, però ves a saber...

Per cert, això em farà parar boig...ara la CPU gairebé no té activitat, la temperatura es la correcta (51ºC a la CPU) i lo més extrany...es que no estic fent res que no hagui fet altres vegades...obert el thunderbird i el flock...ja us dic...tot ben extrany

---

### Post by CarlesOriol on 2008-04-29
Desactiva el tracker.

---

### Post by lluisalguero on 2008-04-30
> **CarlesOriol said:**
> Desactiva el tracker.

Et faré cas...si trobo com fer-ho :lolflag:

---

### Post by CarlesOriol on 2008-04-30
A sistema > Preferencies > Sessions

---

