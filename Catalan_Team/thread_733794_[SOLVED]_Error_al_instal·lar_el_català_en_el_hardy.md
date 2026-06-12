---
title: "[SOLVED] Error al instal·lar el català en el hardy"
date: 2008-03-24
forum: Catalan Team
---

### Post by rajoar on 2008-03-24
A veure..., en un segon ordinador que tinc estic jugant amb el hardy (he instal·lat la beta)... La instal·lació la he iniciada en castellà i tot a anat força bé però, quan vull instal·lar el català em dona aquest missatge d'error i no sé com solventar-ho... No puc reinstal·lar el paquet trencat de cap manera... En sabeu quelcom?

E: /var/cache/apt/archives/language-pack-gnome-ca_1%3a8.04+20080317_all.deb: intentando sobreescribir `/usr/share/locale-langpack/ca/LC_MESSAGES/shared-mime-info.mo', que está también en el paquete language-pack-ca

---

### Post by rajoar on 2008-03-24
...quan intento arreglar-ho des de la cònsola:
ramon@ramon-desktop:~$ sudo apt-get install -f
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalarán los siguientes paquetes extras:
  language-pack-gnome-ca
Se instalarán los siguientes paquetes NUEVOS:
  language-pack-gnome-ca
0 actualizados, 1 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se necesita descargar 0B/1633kB de archivos.
Se utilizarán 6021kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
(Leyendo la base de datos ...  
101886 ficheros y directorios instalados actualmente.)
Desempaquetando language-pack-gnome-ca (de .../language-pack-gnome-ca_1%3a8.04+20080317_all.deb) ...
Reemplazando ficheros del paquete antiguo language-pack-gnome-ca-base ...
dpkg: error al procesar /var/cache/apt/archives/language-pack-gnome-ca_1%3a8.04+20080317_all.deb (--unpack):
 intentando sobreescribir `/usr/share/locale-langpack/ca/LC_MESSAGES/shared-mime-info.mo', que está también en el paquete language-pack-ca
Se encontraron errores al procesar:
 /var/cache/apt/archives/language-pack-gnome-ca_1%3a8.04+20080317_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ramon@ramon-desktop:~$

---

### Post by patrickfromspain on 2008-03-24
jo el que faig fer, una mica bestia, es baixar-me els 2 paquets de packages.ubuntu.com i instal·lar-los amb sudo dpkg -i --force-overwrite language-pack-gnome-ca*.deb languange-pack-gnome-ca-base*.deb

salut!

---

### Post by rajoar on 2008-03-24
patrickfromspain,

Crec que el "marro" deu ser massa gran..., tampoc ha funcionat... Hauré de fer una nova instal·lació...

ramon@ramon-desktop:~$ sudo dpkg -i --force-overwrite language-pack-gnome-ca*.deb languange-pack-gnome-ca-base*.deb
(Leyendo la base de datos ...  
101999 ficheros y directorios instalados actualmente.)
Preparando para reemplazar language-pack-gnome-ca 1:8.04+20080317 (usando language-pack-gnome-ca_8.04+20080317_all.deb) ...
Desempaquetando el reemplazo de language-pack-gnome-ca ...
Preparando para reemplazar language-pack-gnome-ca-base 1:8.04+20080301 (usando language-pack-gnome-ca-base_8.04+20080301_all.deb) ...
Desempaquetando el reemplazo de language-pack-gnome-ca-base ...
Reemplazado por ficheros en el paquete instalado language-pack-gnome-ca ...
dpkg: error al procesar languange-pack-gnome-ca-base*.deb (--install):
 no se puede acceder al archivo: No existe el fichero ó directorio
Configurando language-pack-gnome-ca (1:8.04+20080317) ...
Configurando language-pack-gnome-ca-base (1:8.04+20080301) ...
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
                                                                         [ OK ]

Se encontraron errores al procesar:
 languange-pack-gnome-ca-base*.deb
ramon@ramon-desktop:~$

Salut i gràcies...

---

### Post by papapep on 2008-03-24
Hauries d'escriure correctament el nom del paquet:

> sudo dpkg -i --force-overwrite language-pack-gnome-ca*.deb langua**[COLOR="Red"]n[/COLOR]**ge-pack-gnome-ca-base*.deb

---

### Post by rajoar on 2008-03-24
Ostres papapep,
Estàs en tot!!!...
De moment "solved"...
Gràcies

---

