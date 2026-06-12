---
title: "muntar una carpeta compartida d'un XP a ubuntu"
date: 2008-04-18
forum: Catalan Team
---

### Post by uidb4056 on 2008-04-18
Hola, soc novell amb aixó del Ubuntu i vodria poder accedir a una carpeta compartida en un XP desde el terminal.
Desde el Nautilus - Xarxa puc accedir al grup de treball i veure la carpeta compartida amb els noms correctes (incloent accents, ñ y ç)
He provat de de posar una entrada al /etc/fstab perque amb munti la carpeta en un directori de /media diguen-li utilitzant smbfs i ho fa sense problemes, la questió es que llavors les lletres accentuades ó la ñ o ç no les enseña (hi posa ?)

Com ho puc fer per poder tindre la carpeta muntada i i veure els noms de fitxers i carpetas correctament com es veuen en el Nautilus - Xarxa?

---

### Post by CarlesOriol on 2008-04-19
*Una fòrmula ràpida: *a la barra d'adreça del nautilus. (jo accedeixo amb ctrl+L)

**smb://ipordinador **(o nom de l'ordinador)

*Una fòrumla persistent:* en comptes de **smbfs** usa **cifs**

---

### Post by papapep on 2008-04-19
> Una **fòrumla** persistent

Això què és?? una _fòrmula_ que et dónen en un _fòrum_???? :-D

---

### Post by uidb4056 on 2008-04-19
> **CarlesOriol said:**
> *Una fòrmula ràpida: *a la barra d'adreça del nautilus. (jo accedeixo amb ctrl+L)

**smb://ipordinador **(o nom de l'ordinador)

*Una fòrumla persistent:* en comptes de **smbfs** usa **cifs**

Gracies per la resposta pero el problema meu no es muntar la carpeta compartida sino que cuan navego per la carpeta compartida els noms de carpetas y fitchers que tenen accents ó la 'ñ' ó la 'ç' esl substitueix per '?'.

En canvi si obro la xarxa desde el nautilus i emb conecto al xp veig els noms correctament. La raó per la que vull tindra la carpeta muntada es per poder-hi accedir desde programas de linux com l'unison per poder sicronitar la carpeta compartida al XP amb una carpeta a l'Ubuntu, es per aixó que necessito que els noms de carpetas i fitchers es veigin tal com son al XP.

Deu haver-hi alguna manera de muntar un share en un XP i que es veigi sense distorsionar els noms tal com ho fa el mateix Nautilus.

---

### Post by CarlesOriol on 2008-04-19
Una fòrumla persistent: en comptes de **smbfs** usa **cifs**

---

### Post by SiscoGarcia on 2008-04-19
En què es diferencien les "fòrumles" de les fórmules? ;)

---

### Post by CarlesOriol on 2008-04-20
Les fòrumless funcionen sense estar connectat al fòrum. 

.. i evidentment fòrumla és el seu singular.

:-D

Saps... m'ha agradat la cagada. Podriem standaritzar-ho. Fòrumla: Solució que trobes al fòrum de com fer una cosa. (plurar: fòrumles)

---

### Post by SiscoGarcia on 2008-04-20
> Saps... m'ha agradat la cagada. Podriem standaritzar-ho. Fòrumla: Solució que trobes al fòrum de com fer una cosa. (plurar: fòrumles)

Fins i tot podríem fer un vocabulari català>ubuntaire-ubuntaire>català.

Per cert, fòrumles és el plura[COLOR="Red"]l[/COLOR] de fòrumla, no?

---

### Post by papapep on 2008-04-20
Jo li diria idioma Forumbuntí, per a més concreció (els de les llistes són uns avorrits i els de l'irc uns sms'eros...:-D)

---

### Post by SiscoGarcia on 2008-04-20
També es pot crear un wiki per votar quin nom se li dóna. A mi m'agrada forumtaire, més que res per portar la contrària ;)

---

### Post by uidb4056 on 2008-04-20
Be al final he trobat la manera d'aconseguir-ho, es tracta d'afegir 'iocharset=utf8' a les opcions de muntatge,

De totes formes gracies per la vostra col·laboració.

---

### Post by CarlesOriol on 2008-04-21
> **uidb4056 said:**
> Be al final he trobat la manera d'aconseguir-ho, es tracta d'afegir 'iocharset=utf8' a les opcions de muntatge,

De totes formes gracies per la vostra col·laboració.

Uops... disculpa. No havies dit res des de el darrer missatge.

En qualsevol cas per curiositat has usat smbfs o cifs?

---

### Post by uidb4056 on 2008-04-21
> **CarlesOriol said:**
> Uops... disculpa. No havies dit res des de el darrer missatge.

En qualsevol cas per curiositat has usat smbfs o cifs?

Si ho mires bé veuràs que tinc una resposta on deia que el problema no era muntar-ho sinó que no ensenyava els caràcters especials. Bé gracies de totes formes.

Ho he provat tan amb cifs com am smbfs i al final ho he deixat amb smbfs. L'únic problema que he tingut es un error al apagar i/o al re iniciar que he resolt posant un link al init.d

> ln -s /etc/init.d/umountnfs.sh /etc/rc0.d/K15umountnfs.sh
ln -s /etc/init.d/umountnfs.sh /etc/rc6.d/K15umountnfs.sh

---

### Post by CarlesOriol on 2008-04-22
> **uidb4056 said:**
> Si ho mires bé veuràs que tinc una resposta on deia que el problema no era muntar-ho sinó que no ensenyava els caràcters especials. 

Noi, això ja ho havia llegit... i diversos cops.

El cifs substitueix el smbfs i normalment (si funciona bé a la teva màquina/xarxa) molts d'aquests problemes tant de jocs de caràcters (iocharset) com de pàgines de codis (codepage= que veig que et falta). 
Per tant era lògic que et recomanes d'usar el cifs abans de forçar el iocharset no?

---

### Post by uidb4056 on 2008-04-22
Ja ho entenc pero llavors perque amb el cifs no amb funciona bé si no poso ei iocharset, es que amb falta configurar quelcom?, i aixó que dius del codepage, necessito configurar quelcom? a on?

Gracies

---

