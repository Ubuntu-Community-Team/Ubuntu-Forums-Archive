---
title: "El disc extern fa que Ubuntu no responga"
date: 2008-02-04
forum: Catalan Team
---

### Post by Bensy on 2008-02-04
Fa ja vora dues setmanes que l'Ubuntu començà a calar-se'm de tant en tant, al més pur estil Windows 95. De sobte el ratolí no respon, tampoc el teclat (el primer que vaig fer va ser ctrl+alt+retrocés, ctrl+alt+supr), i per més que espere no torna a respondre.

Al principi no sabia massa bé què passava, però he arribat a la conclusió de que el problema té a vore amb el disc dur extern per diverses raons:

Primer vaig pensar que el problema era de l'Amarok, perquè després que em va passar dues o tres vegades vaig començar a buscar coses que sempre estiguera fent quan passava, i vaig notar que només em passava quan estava sentint música (que llig des del disc dur extern), a banda del que he descrit adés la cançó que sona en eixe moment fa efecte de CD ratllat. Vaig provar de desinstal·lar l'Amarok i tornarlo a reinstal·lar, però seguia fent-ho.

Després m'ha passat un parell de vegades mentre estava passant grups d'arxius des de l'ordinador al disc,i una altra vegent una pel·lícula (també feia el disc ratllat). I una vegada, tot i que no estava fent res, acabava de sentir el cruix-cruix de quan el ordinador li fa "ei, què encara vius?".

De moment no m'ha passat amb el disc connectat però desmuntat, i passe hores i hores sense cap problema quan no el tinc connectat. També he provat de connectar-lo directament (normalment el tinc connectat a un lladre de 4 USB).

La versió d'Ubuntu que tinc és la 7.10, amb totes les actualitzacions al dia.

L'ordinador és un Amilo Pi 2515, link a les especificacions oficials ací: [http://www.fujitsu-siemens.es/home/products/notebooks/amilo_pi_2515.html](http://www.fujitsu-siemens.es/home/products/notebooks/amilo_pi_2515.html)

El disc dur és un Philips de 500 GB, USB 2.0, prou nou, el vaig comprar en novembre si no recorde mal. El sistema d'arxius l'he deixat en NTFS perquè el faig servir també amb l'ordinador de ca els meus pares i amb el del meu company de pis, que duen WinXP.

Vaig intentar passar-li l'scandisk de windows des de la màquina virtual que tinc al virtualbox, però després de tres hores encara anava per la fase 1, i no havia eixit ni un miserable quadret a la barra de progrés, així que si m'ho puc estalviar, estaria prou bé. He pensat de fer-ne particions més menudes, com ara 5 de 100 GB cadascuna per poder passar l'scandisk d'una en una encara que siga una per dia, però així sabria que puc tenir els resultats abans de l'apocalipsi. Ho trobeu recomanable? Preferisc no haver de reformatar el disc amb sistemes de fitxers nadius de GNU/Linux per les raons que he donat més amunt.

Moltes gràcies per llegir-vos la parrafada. Si necessiteu cap altra informació només heu de demanar-la (no sé si Ubuntu desa cap informació quan es cala, ni on trobar-la), i editaré si trobe cap altra pista.

---

### Post by jodufi on 2008-02-05
És difícil que se t'hagi penjat el Linux, i és molt més probable que se t'hagin penjat les "X". Quan es pengen les "X" el ratolí, teclat... deixen de funcionar, però encara et podries connectar remotament mitjançant una sessió remota SSH i mirar què està fallant. No sóc gaire expert en el tema i potser estic dient una bajanada, que em rectifiquin els "sabis" del fòrum :)

El que si que et puc recomanar és no utilitzar el NTFS i intentar utilitzar FAT32. La compatibilitat amb Ubuntu és molt més bona i també funciona amb WinXP.

---

### Post by CarlesOriol on 2008-02-05
Mira si al disc NTFS hi ha arxius comprimits (a nivell del sistema d'arxius) en windows.
A veure si pot ser això.

Si el ubuntu troba un problema en el disc el que farà serà desmuntar-lo i si és intern remuntar-lo en mode de sols escriptura.

Prova també de canviar el cable usb a vegades et fan tornar boig. (tipus error de memòries ;-) )

---

### Post by lluisalguero on 2008-02-05
És el mateix error que tinc jo amb el meu portàtil, amb la diferència que jo no tinc cap disc extern connectat.
Al post que vaig ficar em vau dir que podria ser un defecte del disc dur intern del portàtil. No podria ser el mateix?

---

### Post by guillemsola on 2008-02-05
Crec q podries provar més coses:

- Suposo que es queda penjat i no pots tornar a fer servir l'ubuntu per molt que esperis. Has provat a fer ctrl+alt+F1 i connectar-te a través de terminal? Tb està penjada aquesta opció?

- Si pots entrar a la terminal fes 
> dmesg | tail
a veure que hi diu.
També podries fer un 
> top 
per veure si algun procés esta menjant molts recursos.

La meva experiència és que el gnome si que té tendència tornar-se molt lent amb problemes de disk. Si desconectes el disc de manera brusca un cop penjat, que fa?

Un problema molt "divertit" que vaig trobar amb el meu portàtil és que si no hi havia un CD a dins de la unitat cada X minuts es penjava l'ordinador... El vaig solucionar actualitzant el firmware del DVD i oli en un llum. Cada vegada que això passava després consultava el dmesg i hi havia missatges d'error.

Salut!

---

### Post by Bensy on 2008-02-05
Moltes gràcies. Hui el deixaré connectat i a vore què passa.

---

