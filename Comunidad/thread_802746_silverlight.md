---
title: "silverlight"
date: 2008-05-21
forum: Comunidad
---

### Post by euzkoarima on 2008-05-21
Che alguien sabe algo de este "silverlight" que está apareciendo en varias páginas (en mi caso cuando navego el site de la nba) ?

1. Es de microsoft y creo que no tiene version linux (dice que la van a hacer a traves de novell y el acuerdo que tienen con ellos)
2. Viniendo de quien viene no terminaré rompiendo nada ?
3. Hay modo de sustituírlo ?

Igual aclaro que no me importa demasiado si no veo esos contenidos.

Gracias.

---

### Post by WanderingKnight on 2008-05-21
Silverlight es básicamente la competencia de Flash que sacó Microsoft hace poco. Novell y el equipo de Mono (port del framework .NET para Linux) están desarrollando Moonlight, que supuestamente es una implementación de ese formato para Linux.

Obviamente me parece una movida completamente monopolista. Microsoft empezó agregando bocha de contenido en Silverlight a su página web, y ahora cuando abrís el IE por primera vez en Windows te aparece un cartelito que te dice que podés instalar Silverlight. Supongo que las próximas versiones de Windows lo incluirán por defecto, con lo cual cualquier posible batalla ya está perdida.

Es triste, pero así funcionan estas cosas.

---

### Post by vk-cdg on 2008-05-22
En el XP que tengo virtualizado (al igual que en la PC del laburo) ya bajó un componente de Silverlight vía WindowsUpdate, así que en XP también ya está implementado (al menos para los que lo tengan legal).

---

### Post by margori on 2008-05-22
Veamos si puedo ayudar. Estoy metiéndome por laburo en el uso de esta tecnología y esto es lo que se:
> **euzkoarima said:**
> 1. Es de microsoft y creo que no tiene versión linux (dice que la van a hacer a través de novell y el acuerdo que tienen con ellos)
Si, es de Microsoft y trabaja sobre .Net framework. Novell está impulsando Moonlight sobre Mono (.Net para linux open source, aunque .Net esta por la versión 3.5 y Mono todavía no ha llegado a soportar la 2.0).

> **euzkoarima said:**
> 2. Viniendo de quien viene no terminaré rompiendo nada ?
No tengo noticias de que rompa algo. Aunque puede tener vulnerabilidades como cualquier producto cerrado.

> **euzkoarima said:**
> 3. Hay modo de sustituirlo ?
Y no hay como sustituirlo, pero si tiene competencia.

Silverlight (año 2007) es una versión muy depurada, aunque no necesariamente basada en esta, de una tecnología de Mozilla, XUL (año 1998).
Silverlight pide al servidor un archivo XML, XAML, que le indica como mostrar el contenido en pantalla. Trabaja sobretodo con modelos vectoriales, basados a esta vez en la forma de construir las imágenes SVG (estándar w3c 2001). Conclusión, Microsoft tomo idea de varias personas, las unio, depuro, se adelanto y creo un soft comercial.


Acá tienen un par de paginas con mejores descripciones:
- [http://www.xul.fr/comparison-user-interface-markup-languages.html](http://www.xul.fr/comparison-user-interface-markup-languages.html) (ingles)
- [http://www.free-ebooks-download.org/free-ebook/dotnet/Framework/essential-silverlight.php](http://www.free-ebooks-download.org/free-ebook/dotnet/Framework/essential-silverlight.php) (libro en ingles)

Están orientadas a desarrolladores, pero tiene la posta sobre Silverlight.

Espero sirva. Nos vemos.

---

### Post by euzkoarima on 2008-05-22
Gracias a todos!!
Me dieron el panorama que necesitaba para saber de que se trata.

---

### Post by oktubrer on 2008-05-22
> **margori said:**
> Conclusión, Microsoft tomo idea de varias personas, las unio, depuro, se adelanto y creo un soft comercial.

O sea, lo mismo de siempre.

---

### Post by margori on 2008-05-23
> **margori said:**
> Conclusión, Microsoft tomo idea de varias personas, las unio, depuro, se adelanto y creo un soft comercial.

Silverlight es un producto comercial, competencia directa de Adobe Flex. Flex salio en Mar-2004 y Silverlight en Dic-2006 y hacen lo mismo conceptualmente, y cuando digo lo mismo, es lo mismo.

Flex SDK esta liberado con licencia Mozilla Public License (MPL) compatible con el concepto de Open Source.


Mas datos en [http://es.wikipedia.org/wiki/Adobe_Flex](http://es.wikipedia.org/wiki/Adobe_Flex)

---

