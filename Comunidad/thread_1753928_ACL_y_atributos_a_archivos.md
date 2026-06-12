---
title: "ACL y atributos a archivos"
date: 2011-05-09
forum: Comunidad
---

### Post by z37a on 2011-05-09
Gente, dejo este mensaje aca a ver si alguno puede sacarme de una duda que me esta generando dolores de cabeza!

Como puedo hacer que SAMBA me permita compartir una carpeta que solo me permite agregar archivos y modificarlo, pero NO eliminarlos. Algo bastante complicado creo, y que la verdad me estoy volviendo loco buscando, asi que dejo mi pregunta a ver si hay alguno que sepa de esto!

---

### Post by guillermolisi on 2011-05-09
Desde el punto de vista de auditoria, si hay un repositorio comun donde muchos pueden acceder, editar un documento para generar otro (asi sea un punto de diferencia), lo aconsejable es que siempre se mantenga el documento/archivo original y que el nuevo documento/archivo sea una nueva version del primero, que no lo reemplace. Es decir, un sistema que permita gestionar archivos versionados.

De esta forma podes evitar dar permisos de escritura en forma grupal y cada usuario solo podra borrar aquellos documentos/archivos que le son propios.

Clero que todo esto si no interprete mal las necesidades que planteas.

---

### Post by juancarlospaco on 2011-05-09
Proba con el bit pegajoso:

sudo chmod --verbose 1777 cosa

donde cosa es el directorio, archivo, whatever.

Sino otra es meter un sistema de versionado 
(como los que se usan para programar) 
en el mismo directorio que usa el samba.

Si funciona, habria que cronear un script para que elimine archivos vacios.

---

### Post by z37a on 2011-05-10
Es que la idea es que un grupo de gente, todo usando el mismo usuario de samba suban unas fotos a una carpeta, pero estos mismos no puedan borrarlas. Por otro lado también es necesario que puedan subir unos archivos, puedan editarlos, pero tampoco puedan borrarlos. El problema es que si lo hago mediante las ACLs de samba de MS hay una propiedad que me deja, pero no se como hacer lo mismo desde el lado samba linux!

---

### Post by granjero on 2011-05-10
hola, probaste con poner en la llave de la compartición samba lo siguiente:

```
force user = z37a
create mask = 1770
```

así todos los archivos que se guardan allí van a ser de z37a y ademas tendrán el stickybit y solo los podrá borrar z37a.

salud!

---

### Post by z37a on 2011-05-10
> **granjero said:**
> hola, probaste con poner en la llave de la compartición samba lo siguiente:

```
force user = z37a
create mask = 1770
```

así todos los archivos que se guardan allí van a ser de z37a y ademas tendrán el stickybit y solo los podrá borrar z37a.

salud!

La carpeta es de z37a grupo z37a por así decirlo. esa carpeta tiene permisos 1770 y en samba esta configurado el force user = z37a con el create mask = 1770

Ahora entro con samba a la carpeta usando al usuario pepito, voy a la carpeta en cuesto, guardo un archivo y lo edito sin problemas, pero al borrarlo, me lo borra, y justo eso es lo que no necesito que suceda. Es algo muy complicado no se si se podrá o no hacer, pero no se pro que no lo logro ni encuentro que debo hacer!

---

### Post by granjero on 2011-05-10
una consulta, cuando escribís a través de samba con el usuario pepito y hacés un ls -la en esa carpeta que te sale sobre los permisos?

salud!

---

### Post by z37a on 2011-05-10
> **granjero said:**
> una consulta, cuando escribís a través de samba con el usuario pepito y hacés un ls -la en esa carpeta que te sale sobre los permisos?

salud!

me sale que el propietario es z37a, esta haciendo un force user, por ende cada cosa que haga lo hace con ese usuario, por eso creo que le deja borrar, también esta haciendo uso del usuario owner para borrarlo.

---

### Post by granjero on 2011-05-10
entonces hasta ahí llego yo.

:-({|=

si lo solucionás avisá como.

saludos!

---

### Post by z37a on 2011-05-11
> **granjero said:**
> entonces hasta ahí llego yo.

:-({|=

si lo solucionás avisá como.

saludos!

La verdad que si es una verdadera complicación, por que ya tengo andando todo lo demás y me quedo solo esto pendiente, si ya logre crear usuario de solo lectura en samba y demás, pero esto la verdad no encuentro como, ni encuentro alguien que halla querido hacer lo mismo.

---

