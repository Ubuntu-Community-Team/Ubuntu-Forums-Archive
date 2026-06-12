---
title: "conexion de disco duro"
date: 2009-04-25
forum: Centroamerica Team
---

### Post by yariel on 2009-04-25
buensa tardes ante todo si es que tengo un server 2003 y  lo quieren pasar a linux y  no  me reconoce los disco duro como hago para que lo reconozca y no  borrar la informacion  de los disco 
los disco estan en formato nfts 

le agradeceria su ayuda

---

### Post by meldon12 on 2009-04-25
Hola yariel, puedes leerte [esta guía](http://www.cristalab.com/tips/montar-escribir-y-leer-particiones-ntfs-desde-ubuntu-c26881l/) para instalar el fuse y el ntfs-3g, aunque en el ubuntu 8.10 en adelante creo que no es necesario... o que alguien me corrija si me equivoco..

Saludos y espero que te sirva.

meldon12

---

### Post by eivar on 2009-04-27
> **meldon12 said:**
> Hola yariel, puedes leerte [esta guía](http://www.cristalab.com/tips/montar-escribir-y-leer-particiones-ntfs-desde-ubuntu-c26881l/) para instalar el fuse y el ntfs-3g, aunque en el ubuntu 8.10 en adelante creo que no es necesario... o que alguien me corrija si me equivoco..

Saludos y espero que te sirva.

meldon12

Es correcto meldon, en ubuntu 8.10 ya hay buen soporte para ntfs (me parece que usan ntfs-3g por defecto).
Me parece que el ntfs-3g está en los repositorios, por lo que se puede instalar usando synaptic.

Saludos.

---

