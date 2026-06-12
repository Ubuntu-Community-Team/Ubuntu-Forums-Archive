---
title: "[SOLVED] Portàtil amb Ubuntu en live"
date: 2008-02-15
forum: Catalan Team
---

### Post by Curial on 2008-02-15
Déu vos guard,

M'agradaria treballar en mode live amb un portàtil que és de l'empresa i que tinc prohibit instal·lar res :) .

És un hp6910p-Intel Core 2 Duo-2Gb RAM-ATI Mobility Radeon x2300

En un primer moment vaig pensar a engegar des d'un pendrive d'1G però no me n'he sortit. (no se si coneixeu alguna web que doni una bona explicació de com fer-ho).

No vull instal·lar res al disc dur que després no pugui esborrar.

Ja sé que és anar una mica amb les mans lligades, no tinc alternativa però.

Qualsevol recomanació serà benvinguda.

---

### Post by eduardsola on 2008-02-15
I en un disc dur extraíble?

N'hi ha de 80GiB que estan molt bé de preu, pensa que amb la Live no pots guardar res permanentment.

---

### Post by SiscoGarcia on 2008-02-15
> M'agradaria treballar en mode live amb un portàtil que és de l'empresa i que tinc prohibit instal·lar res  .
..I per què no ho fas? Vull dir, per què no poses un CD Live? Què m'he perdut?:confused:

---

### Post by papapep on 2008-02-15
Doncs [aquí]("http://www.vcubells.net/index.php/arxiu/2008/02/03/852/") crec que ho trobaràs prou ben explicat com fer-ho amb un pendrive USB.

Sisco: Jo assumeixo que deu voler fer-ho amb un pendrive per a poder desar el que faci amb l'Ubuntu (només m'ho imagino).

---

### Post by RafaelCarreras on 2008-02-16
L'altre dia vaig estar provant l'Slax ([http://slax.org](http://slax.org)) amb molt bon resultat perquè és molt senzill fer-la arrencable des del pendrive. Amb les ubuntus mai no ho he aconseguit, però jo sóc una mica patata per a aquestes coses.

Es pot descarregar la versió catalana per a pendrive des d'aquí: [ftp://ftp.slax.org/SLAX-6.x/multi-language/slax-catalan-6.0.0.tar](ftp://ftp.slax.org/SLAX-6.x/multi-language/slax-catalan-6.0.0.tar)

---

### Post by Curial on 2008-02-16
Gràcies per les webs, aquestes no les havia trobat. Ho provaré.

Bé el tema del disc dur extern, no se a quin preu van els petits pero estic fiscalitzat per la meua dona :) , a part que estic tot el dia amunt i avall i contra menys coses penjant millor. Ja ho valoraré.

Referent al Pendrive, és exactament per desar dades, tal com l'idioma i especialment havia pensat en l'Eina de configuració NTFS per a poder remenar si els arxius del disc dur.

Si per la banda del pendrive no me'n sortia havia pensat efectivament amb el CD en live per a Open Office.

De totes maneres m'he abaixat la versió catalanitzada per a funcionar amb la Gutsy perquè he intentat engegar amb la 7.04 i se'm queda penjat suposo que per qüestions de gràfics. Encara no l'he provat amb la Gutsy Gibbon. 

Salut.

---

### Post by papapep on 2008-02-16
Amb el pendrive i en cinc minuts he posat a funcionar una Slax, com en Rafael t'explicava:

Descarregues el fitxer .tar.

Amb el gparted (així ho he fet jo) crees la, o les, particions fat32 que et plagui al dispositiu usb.
Descomprimeixes el contingut del .tar al pendrive.

Executes (amb sudo) el fitxer bootinst.sh (que és dins el directori /boot)

I ja està!!!

---

### Post by Curial on 2008-02-16
He provat l'slax i ha estat molt fàcil de fer funcionar.
També he vist que El CDlive amb la Gutsy funciona força bé en aquest ordinador.

El fracàs l'he tingut quan he intentat seguir les pases que molt clarament exposa en Vicent Cubells en el seu blog:
No se on l'he errat perquè quan apareix el menú de la grub i selecciono el sistema operatiu instal·lat al pendrive em dona un error 7 i em diu que no pot muntar l'unitat.

Tinc tres duptes amb això:
1) No se si ha estat quan he executat el syslinux en l'instal·lació de l'slax que m'ha tocat la MBR.(no se si variant la partició queda diferent).

2) Abans de començar la prova amb la instal·lació de l'Ubuntu amb l'alternate, he suprimit la partició vfat i n'he creada partició per al total de la unitat i després la formatat a ext3.No se si hauria d'haver deixat una segona partició.

3) Al final de la instal·lació amb el CD-Alternate quan m'ha demanat d'instal·lar la grub he triat /dev/sdc en comptes de /dev/sdc5/ o partició estesa d'aquesta unitat com em deia l'enunciat.

Que n'opineu?

Seguiré provant.
Salut

---

### Post by papapep on 2008-02-16
> 1) No se si ha estat quan he executat el syslinux en l'instal·lació de l'slax que m'ha tocat la MBR.(no se si variant la partició queda diferent).

Si no recordo malament, quan executes l'script bootinst.sh ja t'ho diu ben claret això.

> 2) Abans de començar la prova amb la instal·lació de l'Ubuntu amb l'alternate, he suprimit la partició vfat i n'he creada partició per al total de la unitat i després la formatat a ext3.No se si hauria d'haver deixat una segona partició.

No cal. Amb una ext3 és suficient (sempre que sigui prou gran, clar).

> 3) Al final de la instal·lació amb el CD-Alternate quan m'ha demanat d'instal·lar la grub he triat /dev/sdc en comptes de /dev/sdc5/ o partició estesa d'aquesta unitat com em deia l'enunciat.


Li has de dir el nom de la partició que hagis creat. La mateixa que has creat i formatat. sdc serà un dispositiu, però no una partició.

---

### Post by Curial on 2008-02-16
> **papapep said:**
> Si no recordo malament, quan executes l'script bootinst.sh ja t'ho diu ben claret això.
.

I tant que ho deixa clar! No ho he dit bé, Em refereixo a que un cop he tocat l'MBR ja ha m'ha quedat fotuda (verb menys eufemístic :) he,he).
No sé si n'hi ha prou amb canviar la partició per tornar a deixar-la com abans.(no és quelcom que tingui massa clar en els meus coneixements) 

> **papapep said:**
> 
Li has de dir el nom de la partició que hagis creat. La mateixa que has creat i formatat. sdc serà un dispositiu, però no una partició.

Ok. Ho provaré el que no sé a què es refereix quan esmenta el principi de la partició ??

Gràcies

---

### Post by Curial on 2008-02-17
Doncs a base d'insistir al final s'ha instal·lat bé i ha arrencat des de l'usb.

Me quedat bastant decebut perquè m'he trobat un escriptori "debian" pelat.(per pelat no per debian).
Tenia el firefox i poca cosa més i només m'han quedat 12Mb lliures.

Si ho haig de comparar amb un CDlive ho tinc claríssim.

:(

Salut.

---

### Post by Miquel Ubuntero on 2008-02-17
Hola company.
1/ Si tens problemes amb l'MBR, pots fer un cop d'ull al post que vaig posar "Recuperar MBR". A mi hem va anar be l'ajuda.

2/ Referent a Ubuntu en un pendrive. Jo vaig fer el que a pendrive.com diuen i hem va be. Aixó si, està en anglès. [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Salut!

---

### Post by Miquel Ubuntero on 2008-02-17
He oblidat de comentar 2 coses.
El meu pendrive amb Ubuntu te l'escriptori Gnome al complet, te només 1GB , quedant lliures uns 250 MB. Prou be, no?
Si estàs interesat, i et pega l'anglès, fes-mo saber i amb molt de gust et faig una traducció.
Salut!

P.D.: Per menys de 20€ és fàcil trobar pendrives de 4GB.

---

### Post by Curial on 2008-02-17
Gràcies Miquel,

Resulta que vaig comprar la d'1Gb fa poc, si ho hagués sabut n'hagués triat una de més gran:(. 

En quant al link que m'has posat (n'hi ha uns quants que ho fan de manera similar), ja ho havia intentat però crec que no dec haver fet bé algun dels punts 16 li (poso cd /media/cdrom1) i 18 (no tinc cap directori /home/ubuntu ho he fet des de l'escriptori).

Aconsegueixo copiar els arxius a la pendrive pero mai no m'arrenca.Tot i que executo el el lilo -M /dev/sdc1 (en el meu cas).Quan he instal·lat el lilo m'ha demanat que fes alguna cosa que no he acabat d'entendre (ara no me'n recordo).

Quan torni a tenir una estona ho tornaré a provar per últim cop perquè ja començo ha pensar que hi he dedicat massa temps a aquest tema sense obtenir fruits.

De totes maneres gràcies per l'interes.:)

---

### Post by Miquel Ubuntero on 2008-02-18
Hei Curial.
Les coses bones es fan esperar. Anims!
Aquest vespre m´ho tornaré a mirar com ho vaig fer, crec que tinc per casa alguna xuleta. Intentaré de pasarte-la.
Se que vaig tindre algun problema de permisos. Quan ho provis de nou.
Mira de tenir permisos de "root".
Estem en contacte ...

---

### Post by Curial on 2008-02-18
Miquel al final hi ha hagut un desenllaç feliç!

Gràcies pels ànims: m'han ajudat a mantenir la concentració.:)

La meva equivocació inicial havia estat intentar fer-ho en un PC que ja el tenia amb l'ubuntu instal·lat i no des del portàtil amb un CD arrencat en live!!

De fet ho havia fet així per evitar/minimitzar qualsevol incident.

Malgrat això he tingut algun problema, suposo que amb la pendrive. També a la hora de descomprimir l'arxiu zip que he solucionat fent el procediment amb dos ordinadors al l'hora.(he fet trampa: ho he fet des de l'entorn gràfic però shihihih, no li diguis res a en Papapep.:):) )

Bé, això és tot.:popcorn:

Salut.

---

