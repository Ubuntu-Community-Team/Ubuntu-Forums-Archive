---
title: "[SOLVED] No puc accedir a arxius d'una carpeta"
date: 2008-09-07
forum: Catalan Team
---

### Post by PequeMayol on 2008-09-07
Hola,

a veure us explico... És que tinc un problema i el meu germà m'ha dit que ell no sabia què fer-hi i que ho preguntés aquí...


A */home/peque/USB* hi tinc els arxius que tenia en el meu pendrive abans de canviar-los (ve a ser una còpia de seguretat del que hi ha al pen). Però quan he intentat entrar-hi he trobat que els arxius i carpetes interns tenen dos simbolets taronjes: un cadenat i un quadrat amb una "x" (veure arxius adjunts) i a més no em deixa obrir els arxius ni accedir a les carpetes. El meu germà (en ***LitusMayol***) m'ha dit que potser era un problema de permisos i que ho mirés. Però en tots surt com a propietari la meva sessió...Jo diria que està bé, però us adjunto una captura perquè veieu com estan (la 2a captura). A veure si algú sap com m'ho he de fer...

A més a més... He "*mogut a la paperera*" una carpeta (per error) i ara vull recuperar-la i no està a la meva paperera! :S Algú sap com desfer aquesta opció?

Algú em pot ajudar? 
Merci!!

---

### Post by papapep on 2008-09-07
Fes a un terminal:

```
sudo chmod -R 744 /home/peque/USB 
```

amb això donaràs permisos totals al propietari, suposo que tu, i de lectura  a la resta d'usuaris del món mundial.

---

### Post by thedavis on 2008-09-07
Per mirar de recuperar la carpeta borrada:

Quan elimines un archiu d'un PenDrive aquets es queden "amagats" dins del mateix dispositiu a una carpeta que es diu .Trash (fixa't amb el puntet del davant). Per veure aquets fitxers amagats fes CONTROL+H i així pots veure aquets fitxers ocults

Sort!!!!

---

### Post by PequeMayol on 2008-09-07
Ja està solucionat. 

**papapep** he posat les comandes que m'has dit i ja va moltíssimes gràcies.

---

