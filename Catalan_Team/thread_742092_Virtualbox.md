---
title: "Virtualbox"
date: 2008-04-01
forum: Catalan Team
---

### Post by lo gambusí on 2008-04-01
Salut!

continuo amb la inst·lació de l'ubuntu al company. esta vegada estic amb el virtualbox. .l'he instal·lat i he creat una màquina per a windows xp, però a l'hora d'iniciar-la amb el cd dins per instal·lar el güindos, me dóna[ lo següent ]("http://img132.imageshack.us/img132/9924/capturact5.png")error.

Alguna idea? 
gràcies!

---

### Post by papapep on 2008-04-01
Sí, que li fiquis el cd dins :-D

Ja has configurat, i detecta, correctament la unitat de cd/dvd al Virtualbox?

---

### Post by lo gambusí on 2008-04-01
Me dirigixo a configurar-lo i me surt [això]("http://img182.imageshack.us/img182/2923/captura1vm3.png"). li dono a  acceptar i sí, tinc lo dvd configurat.

---

### Post by lo gambusí on 2008-04-01
He reiniciat l'ordinador per una altra cosa, i a l'iniciar lo virtualbox me dóna un nou [missatge.]("http://img409.imageshack.us/img409/3894/capturabf5.png")O_O

---

### Post by papapep on 2008-04-01
> **lo gambusí said:**
> He reiniciat l'ordinador per una altra cosa, i a l'iniciar lo virtualbox me dóna un nou [missatge.]("http://img409.imageshack.us/img409/3894/capturabf5.png")O_O

Jo no sóc capaç de veure aquesta última imatge...:-/

---

### Post by lo gambusí on 2008-04-01
[http://img520.imageshack.us/img520/4737/capturaur4.png](http://img520.imageshack.us/img520/4737/capturaur4.png) ara?

---

### Post by papapep on 2008-04-01
Ara sí! :-D

Doncs ja t'ho diu. Has d'afegir l'usuari que esteu fent servir al grup vboxusers :-)

Ara ve la pregunta del milió, oi?? Com!?

Doncs fas:

```
sudo nano /etc/group
```

Busques una línia on et surti:

```
vboxusers:x:1001:
```

i hi afegeixes el nom de l'usuari, per exemple:

```
vboxusers:x:1001:papapep
```

(evidentment hi ha manera de fer-ho gràficament, però passo :-P)

Tornes a engegar el Virtualbox i a veure què fa...

---

### Post by Kururu on 2008-04-01
més fàcil encara: 
sudo gpasswd -a nomd’usuari vboxusers
Evindentment substitueix nomd’usuari pel teu usuari.

---

### Post by jodufi on 2008-04-01
Quina mania amb el terminal
Sistema -> Administració -> Usuaris i grups...
Ves a «Gestiona els grups» i assegura't que el grup vboxusers té el teu usuari

L'error«No s'ha pogut accedir al subsistema USB» em sona que em va passar. Diria que ho vaig solucionar utilitzant els repositoris de virtualbox (els que no són lliures). Has d'afegir aquesta linia a /etc/apt/sources.list
[INDENT]deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free[/INDENT]
Ho pots fer per terminal o «Sistema -> Administració -> Gestor d'actualitzacions»

Salut

---

### Post by lo gambusí on 2008-04-02
Moltes gràcies als tres. Ara ja no tinc el problema dels permisos.
Tinc encara, però, [este.]("http://img132.imageshack.us/img132/9924/capturact5.png") i lo de l'usb.

---

### Post by kukat on 2008-04-02
Per al dels USB pegali una miradeta a aquest atre fil, que vam aconseguir solucionar. Però crec que necessites la verssió no lliure del Virtualbox per a fer anar els USB, si no recorde mal.... De totes formes, com diu Carles, per a fer anar un sistema privatiu (supose) igual dona!! jejeje


[http://ubuntuforums.org/showthread.php?t=663567](http://ubuntuforums.org/showthread.php?t=663567)

Salut!!

---

### Post by lo gambusí on 2008-04-02
He pogut arreglar-ho, crec (com a mínim no me surt la pantalla d'error de l'usb...) però seguix fallant-me lo primer error, [este.]("http://img132.imageshack.us/img132/9924/capturact5.png")

---

### Post by lFossil on 2008-04-02
Ei hola sóc el company del Gambusí i si em podeu ajudar amb el tema del virtualbox us u agrairé molt. Sóc nou en l'ubuntu i espero adaptar-me el millor possible. Gràcies.:)

---

### Post by jodufi on 2008-04-02
El que et falta es inserir el CD del windows per a instal·lar-lo.

Ves a «Dispositius -> Munta el CD» i assegura't que hi hagi muntat el CD del windows. Després reinicia la màquina virtual «Maquina -> Reinicia»

---

### Post by lFossil on 2008-04-02
Ei, sóc jo atre cop. He intentat el que em dius però em continua igual i crec que em surt com si no reconegués el cd que troves?¿

---

### Post by papapep on 2008-04-02
lFossil, benvingut al fòrum.

Estaria bé que ens possessis exactament els missatges que et mostra l'ordinador, ja que les teves suposicions ens poden portar, sense voler, per un camí equivocat.

T'aconsello llegir-te el fil pels nouvinguts: [http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

També estaria bé que passessis [pel fil de benvinguda]("http://ubuntuforums.org/showthread.php?t=562776") a explicar-nos una mica la teva vida ;-)

EDITO: Has provat a ficar qualsevol altre cd arrencable (per exemple un live-cd de Ubuntu) al lector a veure si el detecta correctament?

---

### Post by orestesmas on 2008-04-03
Jo penso que la finestra del VirtualBox ens està tapant la de sota, que és on hi deu haver el desllorigador de tot plegat.

Com tens configurat el CDROM? És una imatge ISO o és el CD real de la màquina host?

Pots posar una captura de pantalla de la configuració de la màquina virtual, please?

---

### Post by lFossil on 2008-04-03
A veure, el cd està configurat com a imatge iso i la cosa s'em queda així [http://reg.imageshack.us/content.php?page=blogpost&files=img510/9268/capturagestordediscsvirov2.png](http://reg.imageshack.us/content.php?page=blogpost&files=img510/9268/capturagestordediscsvirov2.png)

---

### Post by jodufi on 2008-04-03
Aquest CD no té el windows....

Has de ficar una imatge del CD del windows, per a poder instal·lar-lo.

---

### Post by lFossil on 2008-04-03
Sí que hi ha el windows xp, però no entenc aiò que em dius de la imatge iso.  Em surt  això.

---

### Post by lFossil on 2008-04-03
Sí que hi ha el windows xp, però no entenc aiò que em dius de la imatge iso. Em surt això. [http://reg.imageshack.us/content.php?page=blogpost&files=img20/6632/capturagestordediscsvirlo5.png](http://reg.imageshack.us/content.php?page=blogpost&files=img20/6632/capturagestordediscsvirlo5.png)

---

### Post by patrickfromspain on 2008-04-03
ja ho he dit alguna que altra vegada, pero em sembla que hi ha gent que pregunteu per sistema i no us pareu ni 5s a buscar solucions..

Com tu mateix pots veure, aquesta imatge iso es diu Vboxguesadditions.iso i NO es el windows XP. 

Suposant que tinguis una imatge ISO del windows XP (ja sigui baixada de la mula, o feta per tu mateix d'un cd d'XP), el que has de fer es posar afegeix, buscar la imatge, triar-la i aleshores t'apareixera junt amb la de Vboxguestadditions que ja tens. La selecciones i muntes i ja t'hauria d'arrancar.

salut

---

### Post by jodufi on 2008-04-03
Em sembla que hi ha un problema de comprensió.

Pots enviar una captura de «Paràmetres -> CD/DVD-ROM»?

Si ho tens com la captura que adjunto i tens el CD de windows a la unitat que especifiques, t'hauria de funcionar.

---

### Post by patrickfromspain on 2008-04-03
ara que ho dius.. segurament ha configurat per arrancar per una imatge iso i té posat el cd del win XP al lector.. aixo ho explicaria tot xD

---

### Post by papapep on 2008-04-03
Nois, tots hem estat novells i tots hem hagut d'aprendre, fins i tot, què era o no era una imatge iso. O sigui que tranquilitat...

IFossil, tens configurat el Virtualbox per a que utilitzi com a CD un fitxer que és el que faries servir per crear un cd. A més, tens configurat amb una imatge iso que no és la que et caldria per arrencar l'Ubuntu, ja que és un afegit que es pot instal·lar al Virtualbox per a fer-lo més empàtic a Windows...

Si et fixes en la impressió de pantalla que t'ha posat el jodufi, hauries de tenir-ho igual, o semblant considerant que no deveu tenir el mateix model de lector-gravador de Cd/DVD.

---

### Post by lFossil on 2008-04-08
Ei hola cracks, ja fa temps que vaig preguntar per si em podíeu ajudar perquè no puc fer anar la màquina virtual. Hem vau dir que tenia alguna cosa malament de la imatge iso però no ho entenc i no sé com trobar-ho. Ja fa temps que intento de tot, però res fructífer, si hem podeu tirar un cable...:)

Us adjunto aquesta imatge: [http://img366.imageshack.us/my.php?image=capturanh6.png](http://img366.imageshack.us/my.php?image=capturanh6.png)

---

### Post by papapep on 2008-04-08
Molt millor ;-)

Mira, el que jo faria és començar de nou. Esborra aquesta màquina virtual i comencem de cap i de nou, creant-ne una altra. Què et sembla?

---

### Post by lFossil on 2008-04-08
D'acord, però no sé com fer-ho ja que va ser el gambusí qui m'ho va fer tot.
Necessitaria un poc d'ajuda...:)

---

### Post by papapep on 2008-04-08
Evidentment, per això t'ho dic. El que passa és que estava preparant això :-D,

- Cliques a Nova, 
- Cliques a "Següent"
- Fiques el nom que et sembli i tries la versió de sistema operatiu que vas a instal·lar i  cliques damunt "Següent".
- Assignes la ram que vulguis i cliques a "Següent"
- Cliques damunt "Nou" per crear un disc dur virtual nou, cliques "Següent".
- Marques "Imatge de mida fixa", cliques "Següent".
- Deixes el nom i la mida per defecte (per fer la prova ara), cliques a "Següent".
- Cliques a "Finalitza".

Quan tinguis això fet, seguim amb la resta.

---

### Post by lFossil on 2008-04-08
val, ja està.:)

---

### Post by papapep on 2008-04-08
Bé, ara què tens per instal·lar el sistema operatiu (per cert, quin és?), un cd o només el fitxer d'extensió .iso?

---

### Post by lFossil on 2008-04-08
És un cd amb el windows xp.

---

### Post by patrickfromspain on 2008-04-08
Maquina -> Parametres -> CD/DVD-ROM i selecciones Munta la unitat CD/DVD i Controlador de CD/DVD de l'amfitrio i la teva unitat de CD/DVD

---

### Post by papapep on 2008-04-08
Doncs ara, 

- cliques damunt la màquina virtual que s'ha creat a la part esquerra del Virtualbox, i després cliques a la dreta on posa "CD/DVD-ROM".
- Cliques a "Munta la unitat CD/DVD" i verifica que tens marcat "Controlador de CD/DVD de l'amfitrió" (i que a la dreta et reconeix el teu dispositiu".
- Cliques a "D'acord".
- Fiques el cd a la unitat.
- Cliques damunt "Inicia"

I ja hauria d'estar...fàcil, oi? ;-)

---

### Post by lFossil on 2008-04-08
No, em surt el mateix error desde el principi
[http://reg.imageshack.us/content.php?page=blogpost&files=img180/426/captura1kz0.png](http://reg.imageshack.us/content.php?page=blogpost&files=img180/426/captura1kz0.png)

---

### Post by papapep on 2008-04-08
1.- Ensenya'ns la configuració de on li has dit que fes servir el cd del teu pc.
2.- Estàs segur que el cd que fas servir és executable i està en bon estat?

---

### Post by lFossil on 2008-04-08
Sí, està en bon estat i és executable.7
Aquí tens: 
[http://reg.imageshack.us/content.php?page=blogpost&files=img525/5921/capturainnotekvirtualbozs6.png](http://reg.imageshack.us/content.php?page=blogpost&files=img525/5921/capturainnotekvirtualbozs6.png)

---

### Post by papapep on 2008-04-08
> Sí, està en bon estat i és executable

Quan el fiques al lector, es munta la unitat automàticament? És que això de Virtualbox és massa fàcil, i ha d'haver alguna cosa tonta que s'escapa...

---

### Post by lFossil on 2008-04-08
A vere, quan dic que és executable em refereixo a que l'he instal·lat prèviament tot el sistema operatiu, no sé si es munta sol com ho he de veure?

---

### Post by patrickfromspain on 2008-04-08
Dono per suposat que no tens 2 lectors i l'estas posant al que no es.

Proba el següent:

Maquina -> Parametres -> General -> Pestanya avançat i comprova que on hi diu ordre d'inici hi tinguis marcat Disc durs i CD/DVD rom

salut!

---

### Post by papapep on 2008-04-09
> **lFossil said:**
> A vere, quan dic que és executable em refereixo a que l'he instal·lat prèviament tot el sistema operatiu, no sé si es munta sol com ho he de veure?

Doncs, en principi, hauries de veure la imatge d'un cd amb el nom de winxp o el que sigui a l'escriptori. Però fes el que t'ha comentat el Patrick, per verificar que el tens configurat per a automuntar-se.

---

### Post by lFossil on 2008-04-09
Referent al que m'ha dit el Patrick, sí, tink marcats els cd i disc dur dins de paràmetres > general > avançat  , i com tu dius Papapep, em surt una imatge d'un cd on posa " WXP PRO SP2" a l'escritori.

---

### Post by papapep on 2008-04-09
Curiós...el que jo faria és reiniciar l'ordinador amb el cd posat, i a veure si inicia el procés d'instal·lació (no segueixis, eh!!! :-D), per verificar que no hi ha cap problema lector/disc de cd.

---

### Post by lFossil on 2008-04-09
sí, sí, el cd està en perfecte estat i no hi ha cap problema.
No està rallat ni res

---

### Post by papapep on 2008-04-09
Doncs no ho entenc....:-(

A veure, anem al principi (de tot plegat :-D). Fes a un terminal:

```
sudo aptitude search virtualbox | grep \ i 
```

Fixa't en que entre la barra inclinada i la "i" i ha un espai. Enganxa el que et surti aquí, si us plau.

---

### Post by patrickfromspain on 2008-04-09
Quan dius si si, ho has provat ara o ho havies provat "fa uns mesos"? De totes formes, ens podries fer el favor de probar algun cd d'ubuntu, a veure si aixo arranca? I una altra cosa, proba a treure la disquetera de la seqüència d'inici, no fos cas que...


gracies!

PD: i ja per ultim, enganxan's una imatge de la pantalla principal del virtualbox.

---

### Post by lFossil on 2008-04-10
A veure Papapep, he repetit tots els passos que em vas dir a la pàgina 4 i al iniciar la màquina aquesta vegada m'ha aparegut això 
[http://img402.imageshack.us/my.php?image=capturasx9.png](http://img402.imageshack.us/my.php?image=capturasx9.png)
No m'havia aparegut mai

---

### Post by papapep on 2008-04-10
I quan ha acabat, funciona?

---

### Post by lFossil on 2008-04-10
No, no funciona.

---

### Post by patrickfromspain on 2008-04-10
> **patrickfromspain said:**
> Quan dius si si, ho has provat ara o ho havies provat "fa uns mesos"? De totes formes, ens podries fer el favor de probar algun cd d'ubuntu, a veure si aixo arranca? I una altra cosa, proba a treure la disquetera de la seqüència d'inici, no fos cas que...


gracies!

PD: i ja per ultim, enganxan's una imatge de la pantalla principal del virtualbox.
m'auto cito..

---

### Post by Diegstroyer on 2008-04-14
Prova de crear una imatge ISO del CD del WXP amb algun programa de copia de CD i prova de muntar-lo com a imatge al VirtualBox a la màquina que vols instal·lar. L'error està en que no et reconeix el CD com a arrencable, d'aquesta manera no deuries tenir el problema.

Salutacions.

---

### Post by lFossil on 2008-04-26
He provat el que m'has dit però no consegueixo res. Estic igual des de el principi ja no se que fer més:(

---

