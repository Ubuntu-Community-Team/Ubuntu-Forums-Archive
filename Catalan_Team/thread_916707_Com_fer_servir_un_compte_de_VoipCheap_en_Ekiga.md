---
title: "Com fer servir un compte de VoipCheap en Ekiga"
date: 2008-09-11
forum: Catalan Team
---

### Post by Urfe on 2008-09-11
Hola.

Tinc un compte de VoipCheap que faig servir quan entro al Windows. Per poder pasar del Windows haig de resoldre cosetes com les trucades (no tinc telèfon fixe).

El Ekiga és bastant poc intuitiu. He trobat en una pàgina en anglés l'explicació per configurar el compte de VoipCheap. Però no acaba de rutllar.

Em sembla molt estrany que si teclejo un número de telefon desprès de "sip:" em diu que està trucant al "numero@ekiga.net" ?????

Alguna pista sobre aquest estrany programa?

---

### Post by papapep on 2008-09-11
Hola Urfe,

No tinc idea del tema, però [aquí]("http://ubuntuforums.org/showthread.php?t=309218") sembla que ho tenen clar.

---

### Post by Urfe on 2008-09-11
Gràcies per contestar.

Aquestes són precisament les instruccions que deia que havia seguit.

Crec que ara el problema és que no entenc el problema. Com es truca a un telefon? O potser no és el millor programa per fer trucades?

Jo fico el número a la pantalla principal i surt el missatge "llamando a sip:6625362..@ekiga.net" No passa res i després surt el missatge "Error al abrir el dispositivo de video/dev/video0"

També he probat a fer herramientas/Cuenta-PC-to-phone

Surt una pantalla de configuració. Suposadament està bé i quan dono acceptar no passa res.

Gràcies.



Gràcies.

---

### Post by patrickfromspain on 2008-09-11
no sembla que hagi de tenir a veure amb el teu error, pero, recorda que si truques a un telefon normal, has de posar el prefix internacional (el 0034 en el cas d'espanya)

salut

---

### Post by Urfe on 2008-09-11
Si, és cert. Però efectivament no té a veure amb el/s problema/es que tinc amb l'Ekiga.

De fet al teclejar 0034656585... ja m'ha autocompletat el camp amb el número que havia ficat abans, però sempre surt: "00346525625...@ekiga.net" i no truca

---

### Post by patrickfromspain on 2008-09-11
En pots dir com ho tens configurat?

---

### Post by rroca1 on 2008-09-28
T'has de donar d'alta de servei telefònic i crec que HAS DE PAGAR PER TRUCAR A UN FIX O A UN MÒbil!!!!!

---

### Post by RainCT on 2008-09-28
> **rroca1 said:**
> i crec que HAS DE PAGAR PER TRUCAR A UN FIX O A UN MÒbil!!!!!

Clar, però és més barat que amb la majoria de companyies telefòniques normals, especialment per a les trucades internacionals (de fet, segons el que he sentit aquest és el principal motiu pel que la gent fa servir voip).

---

### Post by Urfe on 2008-11-19
Hola.

Ja he aconseguit trucar. Ara el tema és que no sento. Però segur que truca.

PatrickfromSpain: La configuració que tinc a preferències és la següent:

Dispositivo de sonido: Complemento de sonido ALSA
                       Dispositivo de salida Default
                       Dispositivo de entrada Default

Si provo a canviar els dipositius a HDA NVidia em diu que no pot obrir els canals d'audio. I si fico Ensoniq AudioPCI no diu res però tampoc se sent res.

Quant al complemento de sonido, no puc escollir res més que ALSA

Gràcies.

---

### Post by Urfe on 2008-11-19
D'altra banda, per si no em funcionés el Ekiga he vist instruccions per instal·lar el VoipCheap en el wine.

Diuen que he de col·locar dos arxius en el directori

~/.wine/drive_c/windows/system32

Però com trobo aquest directori en l'arbre de directoris d'Ubuntu?

Moltes gràcies.

---

### Post by papapep on 2008-11-19
~ és el camí fins el teu directori personal. O sigui, si el teu usuari es digués usuari, ~/.wine/drive_c/windows/system32 equivaldria a /home/usuari/.wine/drive_c/windows/system32

---

### Post by PatrickVogeli on 2008-11-19
jo crec que el tens mal configurat, ja que em sembla que no t'hauria de sortir ekiga.net.

salut

---

