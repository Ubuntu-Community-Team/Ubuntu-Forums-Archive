---
title: "Una pregunta acerca de sistemas de archivo"
date: 2009-09-04
forum: Centroamerica Team
---

### Post by Nugar on 2009-09-04
Hola Todos,

Tengo una pregunta acerca del sistema de archivos, todo en el marco de que en algun momento de este año estaré armando otra PC (que mejor no les digo como bautizaré) pero bueno, estoy divagando...

Yo en estos momentos, tengo un disco, relativamente pequeño formateado como ext3, y dos discos internos formateados como NFTS (fuera de uno externo formateado como FAT32).

Tengo la intención de probablemente formatear uno de 160gb que tengo como ext4, dejar uno de 320gb como NTFS (y probablemente de hecho instale Win7 allí), pero quiero entre otras cosas comprar uno de al menos 1 ó 1.5TB interno y formatearlo a su vez como ext4.

La pregunta es la siguiente, con mi poco conocimiento de sistemas de archivos, punto de montaje, etc:

Puedo fijar la maquina de manera que todo mi directorio ~home este en el disco de 1.5TB? Eso me permitiria si fuera necesario por upgrade, formatear completamente el disco principal sin preocuparme de los datos que tengo en ~home/user

Si se fija asi, el sistema lo reconoce como un solo sistema, como si en esencia fuera un solo disco duro mas grande? Mi pregunta viene a resultar de que planeo que lo poco que use de Windows lo usare probablemente a traves de VMware (de hecho, quizas en esa línea ni instale Windows en un disco físico...)

Gracias de antemano por cualquier datillo que me puedan dar,

---

### Post by eivar on 2009-09-04
Hola Nugar,
Tu puedes configurar tu sistema para que tu home (/home) se monte en una partición u otro disco duro diferente.
De hecho yo tengo mi home en una partición especial separada del resto y en media monté un disco bastante grande que compre luego, donde guardo mis archivos más pesados.
Todo esto en GNU/Linux es tratado como un único arbol de archivos.

Saludos.

---

### Post by Nugar on 2009-09-04
Excelente, gracias.

O sea que para el sistema, esto es transparente. Y respecto a la velocidad de acceso, etc?

Recientemente aprendi algo por experiencia que normalmente no se ve en los tutoriales y es que por problemas de espacio, meti una maquina VMware, o mas bien el disco duro virtual (vdx si mal no recuerdo) en el disco NTFS, porque tenia mas espacio libre.

El resultado fue que la VM a cada rato se ponia gris, igual que pasa cuando alguna applicacion de Linux esta temporalmente ocupada.

Pasaria esto con este sistema de dejar por ejemplo mi ~home en otro disco?

---

### Post by eivar on 2009-09-04
El tema de la VM debe ser algo relativo al propio VMWare, porque llevo mucho tiempo usando esta configuración que menciono y funciona bien y tengo entendido que es muy común eso de montar distintas carpetas (no solo home) en varios discos/particiones.
Saludos.

---

### Post by Nugar on 2009-09-04
Yo mas bien pienso que el tema era relativo a que lo monte en una particion NTFS y no ext3

---

### Post by dan_06 on 2009-09-08
Hola nugar 
como estaba leyendo q comenstas sobro los sistemas de archivos **tenia una pregunta.**
si se puede hacer para que windows vista detecte una particion que tengo con archivos ext3 q es donde quiero instalar ubuntu

---

### Post by eivar on 2009-09-08
Hola dan_06, no tengo idea si es posible que vista detecte una partición con ext3.
Como esta es una pregunta distinta deberías crear un hilo nuevo de esa manera hay más posibilidad de que alguien te responda.
Saludos.

---

### Post by Nugar on 2009-09-08
Es verdad lo que dice eivar de crear un hilo distinto, pero de todos modos, supuestamente hay un programa para que windows lea ext3 y creo que ext2 tambien, pero yo lo instale y nunca pude leer nada.

Segun Ubuntu, tengo 4 discos duros. Segun Windows, tengo 3, pues no ve el ext3

---

