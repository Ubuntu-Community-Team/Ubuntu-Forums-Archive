---
title: "Problema en actualitzar a 8.04"
date: 2008-06-05
forum: Catalan Team
---

### Post by FloiT on 2008-06-05
Vaig intentar actualitzar a la versi'o 8.04 d-Ubuntu seguint el gestor d-actualitzacions. Recordo que al final em va dir que hi havia algun error, per[o no recordo quin era (perdo, ara se que hauria estat important fixar-mhi). 
El resultat es que l-Ubuntu de vegades es carrega i de vegades no (a la pagina inicial on surt el logo i la barra horitzontal a sota, el rectangle taronja va d-una banda a l-altra eternament). Quan si es carrega, ho fa amb una resoluci'o de pantalla de 640x480, que no puc canviar anant a Preferencies-> Resoluci'o de pantalla, perque de les opcions que em dona, 640x480 es la mes gran(les altres son 512x384...320x240). He habilitat els controladors restringits de la meva targeta grafica, una Nvidia Geforce 8600GT, pero continua igual. He intentat anar als nvidia-settings mitjansant el Terminal, i em deia que no estava instalat, l-he instalat pero no em deixa accedir a l-apartat de la resoluci'o, ja que faig clic a sobre el boto pero se m-obre una altra cosa.
Disculpeu l-extensio de la historia i tambe la manca d-accents, pero aquest es un altre dels problemes que tinc.
 
Finalment, tambe he intentat reinstalar Ubuntu amb un CD Live de 8.04 que vaig fer servir per instalar el Gutsy en un portatil (i que va anar be), pero ara em surt aquest missatge d-error:

[INDENT][B]BusyBox v1.1.3 (Debia 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter help for a list of built-in commands
(initrams)
[97.810397] ata1.00: revalidation failed (errno=-5)[/B][/INDENT]

Algu sap com puc sortir d'aquest embolic on m-he ficat?

---

### Post by papapep on 2008-06-05
...tens un bon pitafi, eh! :-)

Abans que res cal atacar els problemes d'un en un, sinó ens ofegarem:

a) 
> de vegades es carrega i de vegades no

b)
> si es carrega, ho fa amb una resoluci'o de pantalla de 640x480, que no puc canviar anant a Preferencies-> Resoluci'o de pantalla

c)
> he intentat reinstalar Ubuntu amb un CD Live de 8.04 que vaig fer servir per instalar el Gutsy en un portatil (i que va anar be), pero ara em surt aquest missatge d-error

Problema a): caldria veure els missatges que van passant quan arrenca l'ordinador. Per a això, caldria esborrar del fitxer /boot/grub/menu.lst les següents coses:

**ATENCIÓ, CAL ANAR AMB MOLT DE COMPTE EN EDITAR AQUEST FITXER**, per si no ho tenies clar :-)

Per això, primer en fem una còpia de seguretat. Fes Ctrl+Alt+F1 i aniràs a un terminal virtual. Allà posa (després d'identificar-te amb el teu usuari i contrasenya):

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

ara sí que l'editem:

```
sudo nano /boot/grub/menu.lst
```

busques un apartat on posi (la versió de kernel pot diferir):

```
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=26e88827-d6e5-4bd4-b596-6f662b8d66b6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

```

i esborres les paraules "quiet" i "splash" de la línia que comença per "kernel".

Fas Ctrl+X i deses.

Ara tornes a iniciar l'ordinador i estigues ben atent als missatges que va  mostrant (pots parpallejar de tant en tant, però...:-D).
Quan es mostrin missatges d'error, intenta anotar-los o fer-ne fotos, o el que sigui.

---

### Post by FloiT on 2008-06-05
d-acord, moltes gracies per la resposta. Ara ho fare, pero nomes una puntualitzacio que no se si es important: al meu ordinador hi tinc convivin el Windows XP i l-Ubuntu (l-XP funciona perfectament).

Sabut aixo, canvia alguna cosa del que m-has posat que haig de fer? Continuo el pla previst?

Moltes gracies

---

### Post by papapep on 2008-06-05
Només canvia en el sentit de que has de ser més acurat encara en no pifiar-la :-)

Però si fas estrictament el que t'he comentat, no ha de passar res de dolent.

---

### Post by FloiT on 2008-06-05
Ja ho he fet.
Gràcies per la resposta.

Allò de fer fotos, no sé si era broma, però jo ho he fet en sèriu... les adjunto aquí sota (disculpeu per la qualitat). Són 5 ja que no sé ben bé amb què m'havia de fixar. No paraven de sortir lletres i números (que curiós). Al final, quan m'ha semblat que la cosa havia entrat en un bucle infinit i no passava res de nou, he reiniciat (al cap d'uns 10 minuts més o menys, espero no haver-me precipitat).

[FloiTPitafiCaption01]("http://www.collonada.com/imatges/FloiT_Pitafi_01.jpg")
[FloiTPitafiCaption02]("http://www.collonada.com/imatges/FloiT_Pitafi_02.jpg")
[FloiTPitafiCaption03]("http://www.collonada.com/imatges/FloiT_Pitafi_03.jpg")
[FloiTPitafiCaption04]("http://www.collonada.com/imatges/FloiT_Pitafi_04.jpg")
[FloiTPitafiCaption05]("http://www.collonada.com/imatges/FloiT_Pitafi_05.jpg")


PS: No em vull avançar als esdeveniments, però jo diria que la clau de la cosa és a la foto núm 05...

---

### Post by papapep on 2008-06-05
I amb les altres dues versions de kernel que tens instal·lades et passa el mateix, o només amb la 24-18?
Has provat a entrar en "recovery mode"?

---

### Post by FloiT on 2008-06-06
Doncs sí que funciona a la tercera versió, la **2.6.22-14**. 

Però la segona no (tampoc el recovery mode) ni la primera (tampoc el recovery mode). El que passa quan provo els recoveries modes és: és que surt text semblant (o igual?) al de la captura de pantalles que he penjat (tant a la primera opció (**2.6.24-18**) com a la segona (**2.6.24-17**)).

Com deia, la tercera versió funciona aparentment tot bé (**els accents** continuaven sense sortir però ho he arreglat anant a Sistema-Preferencies-Teclat i hi he posat l'Spanish (Catalan variant) enlloc de l'USA que hi havia, i et voilá). **La resolució de pantalla** també és la correcta (això ha sortit bé sense que ho hagués de cnaviar jo).

Moltes gràcies, sr. Papapep, no sé si ja es pot considerar com a SOLVED el meu problema... sempre entro amb el tercer kernel i ja està, no?

---

### Post by ilku on 2008-06-06
No esta solved, simplement ja sabem que el problema el tens amb els últims kernels, es a dir a canviat alguna cosa que a tu no t'acaba de d'anar bé.
Però amb una mica d'esforç per part d'en papapep :) i potser d'algú més, finalment ho farem rutllar.

D'entrada podries donar una mica de pistes de maquinari (lspci) dels moduls (lsmod) un de missatges (dmesg), i a veure que en trèiem.

(Jo no et podré ajudar gaire, soc molt novell):lolflag:

---

### Post by FloiT on 2008-07-16
Faig un recordatori d'un problema que fa temps que tinc (mirar a baix), que és que no em funcionen els dos primers kernels que surten al Grub. Des d'aleshores vaig tirant amb el tercer kernel (i l'XP), però agrairia que algú m'ajudés a arreglar els altres dos. 
Si cal, puc reinstal·lar l'Ubuntu a partir d'un cd de la 8.04 (tinc totes les dades gravades)... però la veritat és que tampoc sé ben bé com ho hauria de fer això (a part d'eliminar la partició i començar de zero).

Gràcies

---

