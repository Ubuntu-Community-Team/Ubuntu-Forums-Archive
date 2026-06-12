---
title: "Placa nvidia y Wolvix"
date: 2008-07-30
forum: Comunidad
---

### Post by madelaki on 2008-07-30
Primero que nada no estoy seguro de que pueda postear esto aca pero vi varios threads con preguntas sobre otras distros y nadie dijo nada asi que no creo que este mal. Al problema...

Tengo una GeForce 8400 GS y Wolvix Cub 1.1.0 no encuentra los drivers (nv). Por lo tanto no puedo activar 1440x900 que es la resolucion de mi monitor. Alguien tiene alguna idea de como solucionar esto? Wolvix casi no tiene documentacion asi que buscar en la wiki fue inutil, al igual que lo fue buscar con Google.

---

### Post by User21 on 2008-07-30
UUPS! Lei mal. 
Obvien o eliminen esta respuesta!

---

### Post by tzulberti on 2008-07-31
Seria raro que no te encuentre los drivers nv porque los mismos son los drivers libres para nvidia.

La verdad es que no tengo nada de idea de Wolviw pero en ese caso te recomiendo que te bajes los drivers de la pagina de nvidia y los instales.

---

### Post by madelaki on 2008-07-31
Me pide el paquete *binutils* para instalar el driver de nvidia, me fije en los repositorios y no esta. Alguna idea de donde lo puedo sacar?

---

### Post by luks911 on 2008-07-31
> **madelaki said:**
> Me pide el paquete *binutils* para instalar el driver de nvidia, me fije en los repositorios y no esta. Alguna idea de donde lo puedo sacar?

Como para que el thread todavía tenga algo que ver con Ubuntu :p , ¿[este]("http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.18.1~cvs20080103.orig.tar.gz")[0] debería servir no? (Sacado, claro, de Ubuntu Packages)

Saludos

[0] [http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.18.1~cvs20080103.orig.tar.gz](http://archive.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.18.1~cvs20080103.orig.tar.gz)

---

### Post by madelaki on 2008-07-31
Nunca habia instalado un paquete en un .tar.gz, en que carpeta tendria que descomprimirlo?

---

### Post by luks911 on 2008-07-31
Por lo que veo, tenés que descomprimirlo en tu home

```
tar zxvf nombre_de_paquete
```
 
Eso crea un directorio con el nombre del paquete. Te movés a ese directorio y ejecutás

```
./configure
```

Después 

```
make
```

Y como root

```
make install
```

Con eso debería quedar instalado. Confieso que de Wolvix no tengo la menor idea, pero el proceso de instalación es igual en Ubuntu y acabo de verlo en el foro de ellos. 
Ahora, no sé cómo responderán los drivers de nvidia. Ya te enterarás.

---

### Post by madelaki on 2008-07-31
> tar: binutils_2.18.1~cvs20080103.orig.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

Copado. Alguna idea de por que pasa eso cuando no deberia?

---

### Post by luks911 on 2008-07-31
¿Es posible que cuando ejecutás el tar no estés parado en la misma carpeta en la que está el binutils comprimido? Antes de ejecutarlo tirá un ls para confirmar que esté ahí.
Otra opción podría ser usar el programa que tengas similar al Nautilus, ir hasta el archivo y descomprimirlo con un click derecho.

---

