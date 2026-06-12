---
title: "[SOLVED] Error gràfic"
date: 2008-07-30
forum: Catalan Team
---

### Post by Daerun on 2008-07-30
Hola nois, aquest matí, en encendre l'ordinador, m'he trobat que tenia la resolució de pantalla posada a 640x480 i que no tinc possibilitat de modificar-la; a més, està posat el tema predeterminat de quan t'instal·les l'Ubuntu.
He provat de desinstal·lar els controladors restringits de la targeta gràfica i tornar-los a instal·lar (per si sonava la campana :P ) però res.
El cas és que el controlador de la tarja (una nvidia, per cert) funciona perquè compiz+beryl segueixen funcionant  :confused:

---

### Post by Daerun on 2008-07-30
De vegades oblido que la comunitat ubuntaire és una mina on hi pots trobar la solució a tots els teus problemes :P
Bé,ho he pogut arreglar fent el següent: he obert un terminal i hi he escrit

sudo displayconfig-gtk

m'ha aparegut la finestra de Preferències de la pantalla i gràfics, on seguia sense poder posar una resolució més alta que 640x480, PERO clicant a la pestaña "Model" es pot seleccionar la resolució que tenia configurada originalment. Després calia reiniciar, i ara ja ho tinc solucionat :D

Per cert, que ara ja no em passa, però abans de reiniciar, quan escrivia la comanda aquella m'ha sortit el seguent missatge al terminal:

FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): No such device
FATAL: Error inserting battery (/lib/modules/2.6.24-19-generic/kernel/drivers/acpi/battery.ko): No such device

Tot i que he pogut operar normalment a la finestra de preferències. No está repetit, és que em sortia dos cops. Què podia indicar això?

---

