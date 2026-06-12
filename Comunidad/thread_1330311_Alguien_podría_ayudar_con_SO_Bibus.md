---
title: "Alguien podría ayudar con SO Bibus"
date: 2009-11-18
forum: Comunidad
---

### Post by guillermon on 2009-11-18
Hola a todos. Mi ayuda es algo inespecífica, lo sé. Ocurre que estoy comenzando mi tesis de grado en Psicología. Soy militante de Software Libre, pero lego total en conocimientos profundos de computación. Como pienso hacerlo con openoffice, debo prever algunas cosas de antemano. Entre ellas cómo manejaré las bibliografías, que son muchas y complejas. He visto un aplicativo libre Bibus, pero no le encuentro la vuelta, y lo que está como explicaciones no me resulta claro, o no da cuenta de la practicidad (o lo impractico). El wiki: [http://bibus-biblio.sourceforge.net/wiki/index.php/Bibus_base_de_datos_bibliograficos](http://bibus-biblio.sourceforge.net/wiki/index.php/Bibus_base_de_datos_bibliograficos)

   Se me ocurrió postear mi cuestión, a lo mejor alguien con buena disposición me ayuda, o tiene el mail de alguien que sí lo sepa ["No importa tanto saber, sino tener el teléfono del que sabe"]. No hago más largo el post. Muchas gracias desde antemano. Felicitaciones a la comunidad por todo el laburo

Guillermo

---

### Post by guillermolisi on 2009-11-18
No es un SO, es un aplicativo.
Su home page dice:
> Bibus es un programa para manejar referencias bibliográficas. Como otras herramientas de este tipo, Bibus nos permite buscar, editar y ordenar los datos bibliográficos. Ademas, Bibus posee otras características que lo hacen único entre el software libre, aun entre bases de datos bibliográficos propietarios y de pago

---

### Post by gmunioz on 2009-11-18
Hola guillermon:

Bibus es una base de datos bibliográfica que se desarrolló con OpenOffice.org en mente. Puede insertar citas directamente y dar 
formato al índice bibliográfico en un documento abierto con OpenOffice.org Writer. 

Sus principales características son:

 * Organización jerárquica de las referencias con claves definidas por 
el usuario.
 * Diseñado para entornos multiusuario (compartir bases de datos entre
   usuarios).
 * Un mecanismo de búsqueda permite realizar búsquedas instantáneas.
 * Acceso en línea a PubMed y eTBLAST.
 * Importación de registros desde PubMed (Medline), EndNote/Refer, RIS y
   BibTeX.

Bibus utilizará de forma predeterminada una base de datos SQLite para el almacenamiento (mediante el módulo SQLite2 disponible en Python 2.5). Pero también permite utilizar bases de datos MySQL. Si desea utilizar 
una base de datos MySQL, asegúrese de tener el paquete python-mysqldb instalado.

Implementado en: Python 
Interface de usuario: X Window System
Rol: Programa científico bibliográfico
Propósito: Organización de datos
Formatos soportados: BibTeX, ODF, Open Document Format

Instalación
Gráfica desde synaptic 
Consola: sudo apt-get install bibus

---

### Post by guillermon on 2009-11-18
Muchas gracias Guillermo y Gabriel. Pero lo que me dicen en realidad lo sé, pues lo he instalado, incluso he agregado datos bibliograficos, insertándolos desde Bibus a mi documento de Ooo. He hecho búsquedas de PubMed; pero no resulta claro en el manejo de los datos bibliográficos. Digamos, si solo sirva para hacer la bibliografía de los autores, pues lo hago a mano al final del texto. Pero se supone que serviría para hacer manejos complejos de citas... y eso es lo que no me doy cuenta cómo funciona. 
```
Perez y Luque (1995) reportaron que el desempeño de sus participantes mejoro bajo estas condiciones mientras que otros observadores notaron un decremento en el desempeño (Alderete, 1950; Avila y Samar, 1943).
```
   En este ejemplo se introducen 3 citas, con diferente formato... Es por eso pensé en ponerme en contacto con alguien que lo haya usado, y preguntarle... 
   Gracias de todos modos, aunque espero nuevas ideas! Un abrazo

Guillermo

---

