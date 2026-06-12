---
title: "[SOLVED] Desapareixen les vores de les finestres al instal·lar el compiz en l'Intrepi"
date: 2008-10-13
forum: Catalan Team
---

### Post by lo gambusí on 2008-10-13
Salut!

He estat instal·lant el compiz en la beta de l'Intrepid, i em passa el problema típic de que desapareixen les vores de les finestres. Quan m'havia passat altres cops instal·lava l'emerald i desapareixia el problema, però esta vegada no ha estat així. He seguit els passos de guia-ubuntu.org, i em diu de fer això:>  Instalé todo, pero desaparecen los bordes de mis ventanas

Si desaparecen los bordes de tus ventanas puede ser por muchos motivos:

    * Porque no has instalado un decorador de ventanas compatible con Compiz Fusion. Si es eso te recomiendo que instales el paquete emerald mediante tu gestor de paquetes preferido (Synaptic) o mediante la terminal: 

sudo aptitude install emerald

    * Porque la configuración de tu xorg.conf no es la correcta, para corregirlo editamos el archivo tecleando en la terminal: 

$ sudo gedit /etc/X11/xorg.conf

Imagen:Nota clasica.png 	Si usas Kubuntu (KDE) el editor de textos predeterminado es el kate.

Y añadimos esto al final del archivo:

Section "DRI"
Mode 0666
EndSection
 
però no ho arregla.

Alguna idea? 

Gràcies! :-)

---

### Post by lo gambusí on 2008-10-13
Arreglat. Solució: no tenia el plugin "decora les finestres" activat. Aix...

---

### Post by tanreb20 on 2008-10-13
Hostres oriol!!!!

Vas perdent facultats nanu!!!! A vere si a l'estiu hauras de portar els windows eh!!!!!

---

### Post by lo gambusí on 2008-10-13
Cobraras, bernat... ¬¬

---

