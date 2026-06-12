---
title: "[SOLVED] Kdenlive"
date: 2008-02-23
forum: Catalan Team
---

### Post by prostata on 2008-02-23
Tinc més de 300 fotos fetes a Venezia amb motiu del Carnaval. Ara voldria fer un CD-Video però el Kdenlive no te una eina que permeti fer una importació massiva de fotos i s'ha de fer d'una en una, com per tallar-se les venes...¿amb podeu fer un cop de mà...??

Gràcies

---

### Post by CarlesOriol on 2008-02-23
Eps... 

[http://www.kde-apps.org/content/show.php/Manslide?content=72739](http://www.kde-apps.org/content/show.php/Manslide?content=72739)

mola no?

---

### Post by CarlesOriol on 2008-02-23
També pots obrir l'arxiu nomdelprojecte.kdenlive que hagis començat i afegir les imatges a sac.

Veuras que cada imatge té una entrada tipus:

**  <producer hide="audio" aspect_ratio="1.02431" transparency="0" type="5" duration="250" id="0" resource="/home/carles/Desktop/nomimatge.png" />**

Doncs amb el copia encola pots anar força ràpid sols canviant el nom dels arxius.

---

### Post by RainCT on 2008-02-23
> **CarlesOriol said:**
> Doncs amb el copia encola pots anar força ràpid sols canviant el nom dels arxius.

O bé si les tens totes en la mateixa carpeta fer servir un petit script que et generi totes les línies necessaries. Si obres la terminal, vas a la carpeta on tens les imatges ii hi copies el que et poso a continuació (i prems enter), et sortirà una línia per a cada imatge que hi tinguis:

```

for file in *; do echo "<producer hide="audio" aspect_ratio="1.02431" transparency="0" type="5" duration="250" id="0" resource="$(pwd)/file" />"; done

```

Salut

---

### Post by niculau on 2008-02-24
El Kdenlive permet fer presentació de diapositives d'una manera fàcil i còmode, hi ha una opció: 

                     projecte / crear clip de presentació amb diapositives,
 
s'obre una finestra amb diverses opcions, selecciones la carpeta on tens totes les fotos, el tipus d'arxiu, transició, etc... et crearà un clip amb totes les fotos de la carpeta, que només hauràs d'afegir a la línia de temps, un cop allà podràs posar-hi musica i editar-ho com vulguis. 

salut

es el meu primer post, estic molt content de poder ajudar :)

---

### Post by CarlesOriol on 2008-02-24
Benvingut niculau... ara passa a presentar-te al fil de benvinguda per que tots ens coneguem.

---

### Post by prostata on 2008-02-25
> **niculau said:**
> El Kdenlive permet fer presentació de diapositives d'una manera fàcil i còmode, hi ha una opció: 

                     projecte / crear clip de presentació amb diapositives,
 
s'obre una finestra amb diverses opcions, selecciones la carpeta on tens totes les fotos, el tipus d'arxiu, transició, etc... et crearà un clip amb totes les fotos de la carpeta, que només hauràs d'afegir a la línia de temps, un cop allà podràs posar-hi musica i editar-ho com vulguis. 

salut

es el meu primer post, estic molt content de poder ajudar :)

Moltes gràcies per la teva resposta. De fet ahir tarde toquinejant el soft, vaig descubrir per "xiripa" aquesta opció, opció que d'altre costat és prou clara en la seva descripció literal. Com et dic només vaig fer una aproximació, però el que he vist en principi s'acosta molt al que vull, si de cas en tinc més consultes ja les enviaré, però gràcies novament per el teu inestimable consell...

Salut

---

### Post by prostata on 2008-02-25
Bé doncs, ja he vist tot el que entenc jo que havia de veure del Kdenlive. Esta bé, però no és res de l'altre mon. Ho dic perquè a windows feia servir un programari dit Magix Video, no se si algú també el coneix, i crec honestament que es millor. Clar que és de pagament i clar que kdenlive és totalment gràtis, de franc i aquest sol fet ja és prou important, però entenc que poden haver situacions en les quals has de triar necessariament prescindint tot el possible de les teves estimacions entre S.O. i cercan lo més acuradament el resultat que vols obtenir.

Moltes gràcies per les vostres ajudes.

Salutacions

---

### Post by orestesmas on 2008-02-26
Doncs paga, home, paga. No és pas tan greu. Jo mateix he pagat en ocasions per programes puntuals: VMware (ara ja no, gràcies al VirtualBox) i, en èpoques pretèrites, algun compilador de Borland...

I si vols pagar força, potser hauries de comprar l'Adobe Premiere, que suposo que ho deu tenir tot.

---

### Post by niculau on 2008-02-26
pagar per pagar també n'hi ha opcions per linux, MainActor es un editor de vídeo que te versió per linux, jo no l'he provat però et pots baixar una demo a veure que tal, en la wikipedia el donen com a alternativa a cinelerra.

salut

---

### Post by prostata on 2008-03-13
> **orestesmas said:**
> Doncs paga, home, paga. No és pas tan greu. Jo mateix he pagat en ocasions per programes puntuals: VMware (ara ja no, gràcies al VirtualBox) i, en èpoques pretèrites, algun compilador de Borland...

I si vols pagar força, potser hauries de comprar l'Adobe Premiere, que suposo que ho deu tenir tot.


He trigat a respondre perque he volgut voluntariament rumiar molt el contigut de la resposta. Espero ser capaç i espero sobre tot no ferir susceptibilitats.

Jo vinc de l'arquitectura 360 de IBM, era el que havia aleshores tant a l'empressa com a la uni, això del PC ho vaig començar a descubrir durante la meva etapa a la Universitat de Costa Rica, una mica avans a la UNP. A leshores tot es feia a base de compiladors dels diferents llenguatges, fortran, pascal, PL1, cobol, asembler i algún altre, parlo d'aquesta arquitectura IBM, d'altres ja anaven ambl Unix. Jo mai ni he tocat Unix, crec que per circumstancies de la vida professional, les meves preferències professional mai han estat en làmbit de la programació. Va ser amb el pas del temps, que poc a poc vaig anar entrant amb molt de respecte a Unix. 

Jo entenc l'informàtica com quelcom molt obert, altre cosa és el negoci, i entenc que hi han productes que poden ser bons per a Unix i no tan bons per windows i a l'inreves, vull dir que lo bo de la vida és agafar alló que et convè en el moment en que ho necessites, hi que no és una cursa quin SO és millor o pitjor, haurerm de reconeixer que gràcies windows molts dels participant d'aquest fòrum poden anar una mica més bé amb linux, però que segurament sense la experiència previa amb windows, els costaria més comprendre tot això,  tú i jo sabem que comparativametn parlant linix és infitament més SO que windows però aquest és pa mollat per als usuaris, i sovint confonem el nivell usuari del nivell professional.  Vull dir, i dic, que em de ser més obert, que ni linux és la panacea per a tot ni windows és el dimoni, que cadascu, busqui, compari i que agafi alló que més li convingui segons les seves circumstancies, les seves aptituds i els seus gustos.

Salutacions i disculpes per la demora i el rotllo, o no.

---

### Post by orestesmas on 2008-03-13
No estic pas en desacord amb el que dius. Quan jo afirmava que havia pagat per tot això ho deia seriosament. En aquell moment no tenia alternativa pràctica lliure.

El que a vegades em molesta (**i no és pas el teu cas**) és que hi ha gent que va pel món dient que tal o qual programari privatiu té més funcionalitats, però obvien el petit "detall" del preu (sovint molt elevat) que haurien d'haver pagat per aquell programari. I és que acaben interioritzant l'ús il·legal de programari com una cosa natural.

Per tant sempre que puc destaco que els programes privatius "professionals" acostumen a tenir un preu elevat.

---

### Post by prostata on 2008-03-14
> **orestesmas said:**
> No estic pas en desacord amb el que dius. Quan jo afirmava que havia pagat per tot això ho deia seriosament. En aquell moment no tenia alternativa pràctica lliure.

El que a vegades em molesta (**i no és pas el teu cas**) és que hi ha gent que va pel món dient que tal o qual programari privatiu té més funcionalitats, però obvien el petit "detall" del preu (sovint molt elevat) que haurien d'haver pagat per aquell programari. I és que acaben interioritzant l'ús il·legal de programari com una cosa natural.

Per tant sempre que puc destaco que els programes privatius "professionals" acostumen a tenir un preu elevat.

Molt bé, company; ja saps que de vegades les persones parlem amb la boca plena, i és cert que el programari privatiu és molt car, per això els p2p, i que de vegaes en tingui més funcionalitats, però tant en un sentit com en altre, lo millor de tot és poder exercir l'opció personal per sobre del programari i del maquinari, en el moment de elegir un determinat SO i un determinat programari.

Per aquest motiu mai he acabat de entendre aquest plantejament:

Un diseñador de programari cobra un salari.
El seu patrò te la propietat intel-lectual del diseny i a més cobra els corresponents royaltis...¿com s'enten això??

Salutacions

---

### Post by patrickfromspain on 2008-03-16
Igual que en qualsevol empresa:

un treballador cobra el seu sou i el patró ven el producte i es queda la quasi totalitat dels beneficis a final d'any... xD

---

### Post by kukat on 2008-03-17
Algú ha editat alguna vegada un vídeo amb Pinnacle Studio (de pagament) que dure més de 10 minuts? Amb el Kdenlive un vídeo de 2 hores pots editar-lo perfectament, amb Pinnacle rebenta l'ordinador abans de que vaja....jejeje:)
Era tan sols una reflexió. Està molt bé el Kdenlive...encara es pot millorar molt, però temps al temps...:popcorn:

---

