---
title: "Problema en reproduïr vídeos format flash [Era: Youtube]"
date: 2008-06-02
forum: Catalan Team
---

### Post by judit_judoca on 2008-06-02
Hola amics,

sóc nova des d'avui al Ubuntu. Em trobo que no puc veure els vídeos de youtube, he instal·lat el flash player per ubuntu, però no funciona. Què he d'instal·lar?

Algun altre programa o aplicació que hagi d'instal·lar?

Salut!

Judit

---

### Post by Joan Marc on 2008-06-02
Fa un temps també tenia problemes amb pàgines tipo youtube...
Vaig obrir un  [fil]("http://ubuntuforums.org/showthread.php?t=643103"), amb la versió 7.10 Gutsy Gibbon, però suposo que sera el mateix problema... per cert, que tens la versio de 64bits? es que jo enia els problemes amb 64, i va ser passarme a 32bits i solucionat xD

---

### Post by Joan Marc on 2008-06-02
per cert benvinguda al fòrum :)

---

### Post by patrickfromspain on 2008-06-02
comprova que tens instal·lat el flashplayer-nonfree i no el gnash. 

Salut!

---

### Post by judit_judoca on 2008-06-03
Moltes gràcies, de fet crec que la solució és el Firefox 32 bits. Però he estat mirant i no sé com és fa. Algú em pot donar una instrucció. Estic aprenent :(

Salut!

Judit

---

### Post by papapep on 2008-06-03
Benvinguda al fòrum, Judit.

Abans que res, seria molt interessant que passessis pels dos fils destinats als nouvinguts. 

Un per fer una mica de presentació: [http://ubuntuforums.org/showthread.php?t=562776](http://ubuntuforums.org/showthread.php?t=562776)

i l'altre per a entendre com intentem funcionar:
[http://ubuntuforums.org/showthread.php?t=599965](http://ubuntuforums.org/showthread.php?t=599965)

Si llegeixes el segon, veuràs que necessitem una mica més d'informació per poder-te ajudar amb el suficient coneixement de causa.
Estaria bé saber quina versió tens d'Ubuntu: (Feisty, Gutsy, Hardy...7.04, 8.04...) quin "sabor": Ubuntu, Kubuntu, Xubuntu... i quina arquitectura de màquina tens, 32 o 64 bits.

---

### Post by Joan Marc on 2008-06-03
> **judit_judoca said:**
> Moltes gràcies, de fet crec que la solució és el Firefox 32 bits. Però he estat mirant i no sé com és fa. Algú em pot donar una instrucció. Estic aprenent :(

Salut!

Judit
Em sembla que tens un error de concepte: No és el Firefox el que te 64 o 32 bits, sinó que és el Sistema Operatiu (en aquest cas Linux/Ubuntu) que pot ser de 32bits o de 64bits.
L'única solució per canviar-ho és desinstal·lant l'Ubuntu de 64bits i instal·lant l'Ubuntu de 32bits (fet que comportarà haver de formatejar la partició on tinguis l'Ubuntu disposat, i en conseqüència la supressió de tots els teus arxius).
Però avans de fer res, deixa't aconsellar pels sàbis del fòrum, que segur que et donaran motius més ben direccionats al respecte.

Un salut!

---

### Post by judit_judoca on 2008-06-03
Bé, moltes gràcies a tots.

Descriuré doncs el meu ordinador: és un portàtil Acer Aspire 1690; la targeta gràfica és ATI (la pitjor per Ubuntu... ja sé). La verisó és Ubuntu 8.04, de "sabor també ubuntu :) Pel que fa a l'arquitectura, només he trobat que és PCI Express... no sé res més. La verisió me la va instal·lar l'informàtic, o sigui que espero que no s'equivoquessin amb la versió d'Ubuntu.

Els detalls sobre el que em passa a l'obrir el un video de youtube: simplement surt en negre la pantalla i després passa a blanc, com si no hi hagués res. També he probat webs de música com [www.deezer.com](www.deezer.com) i em fa pampallegues. Tot el que requereix del flash player no em funciona...

Espero que aquest cop ho hagi fet bé, disculpeu les molèsties...

Judit

---

### Post by papapep on 2008-06-03
> disculpeu les molèsties...


Nop, de molèsties cap ni una, però cal aprendre coses noves cada dia, oi? ;-)

Tens els efectes d'escriptori activats? prova a desactivar-los totalment a veure com veus els vídeos.

---

### Post by judit_judoca on 2008-06-03
Uis, ja no ho vaig ni activar això dels efectes, perquè no m'ho van recomanar gens amb la meva targeta gràfica...

---

### Post by papapep on 2008-06-03
Anem a posar-nos en feina. Fes a un terminal:

```
sudo aptitude search flashplugin-nonfree
```

Enganxa aquí el que et surti, si us plau.

---

