---
title: "[SOLVED] Com traduir scripts del Gimp al català?"
date: 2008-03-27
forum: Catalan Team
---

### Post by rajoar on 2008-03-27
Fa uns pocs dies que estic introduïnt-me en el món dels scrips i voldria traduir les descripcions dels menús gràfics al català, però no m'en surto. Pensava que seria més fàcil... i traduínt només les definicions amb l'editor de textos, sense tocar res més em funcionaria, però no és així...
Em prodrieu explicar si això es pot fer i com i quins paràmetres s'han d'utilitzar...

---

### Post by papapep on 2008-03-27
A quina mena d'scripts et refereixes? Posa'ns un exemple, si us plau.

---

### Post by rajoar on 2008-03-27
Bona nit, papapep,
Per exemple aquest és un script pel al Gimp:
#!/usr/bin/env python

# -*- coding: latin-1 -*-



# Script para Gimp en Python

# Realizado por Fco. Javier Pérez Pacheco como ejercicio



# importamos los módulos necesarios

from gimpfu import *



import datetime



default_font = "Sans"



def Calendar(img, drawable, width, height, photo_porcent, month, year, font_month, size_font_month, color_month, font_number, size_font_number, color_number, color_festive, bg_weekdays, size_font_year):

	# comenzamos a agrupar el UNDO

	pdb.gimp_image_undo_group_start(img)



	old_background = pdb.gimp_context_get_background()



	pht_porcent = float(photo_porcent)/100.0



	cal_porcent = float( (100-photo_porcent) )/100.0

	

	layer_photo = drawable

	layer_photo.add_alpha()



	# SCALE IMAGE



	pdb.gimp_image_set_unit(img, UNIT_MM)

	pdb.gimp_image_set_resolution(img, 300, 300)



	w = width*118/9.99

	h = height*118/9.99



	#pdb.gimp_message(str(w) + " - " + str(h))



	pdb.gimp_image_resize(img, w, h, 0, 0)





	# CREATE BACKGROUND



	layer_bg = pdb.gimp_layer_new(img, w, h, RGB_IMAGE, "background", 100, NORMAL_MODE)

	layer_bg.add_alpha()

	img.add_layer(layer_bg, -1)

	pdb.gimp_image_lower_layer(img, layer_bg)



	pdb.gimp_context_set_background((255, 255, 255))

	layer_bg.fill(BACKGROUND_FILL)



	# SCALE PHOTO



	height_photo = h*pht_porcent - ((h*pht_porcent)/12)*2



	width_photo = (height_photo * pdb.gimp_drawable_width(drawable)) / pdb.gimp_drawable_height(drawable)



	pdb.gimp_layer_scale(layer_photo, width_photo, height_photo, True)



	layer_photo.set_offsets( (w-width_photo)/2, (h*pht_porcent)/12)



	# YEAR LAYER



	layer_year = pdb.gimp_text_fontname(img, drawable, 0, 0, str(year), -1, True,  size_font_year, POINTS, font_month)

	pdb.gimp_layer_set_lock_alpha(layer_year, 255)

	pdb.gimp_floating_sel_to_layer(layer_year)



	pdb.gimp_layer_set_opacity(layer_year, 20)



	#pdb.gimp_layer_scale(layer_year, (w/10)*3, ( ((w/10)*3) * pdb.gimp_drawable_height(layer_year) ) / pdb.gimp_drawable_width(layer_year), True)



	x = w - layer_year.width - (w/10)

	y = h - layer_year.height - (h/25)



	layer_year.set_offsets(x, y)



	# MONTH LAYER



	months = ['', 'Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio', 'Agosto', 'Septiembre', 'Octubre', 'Noviembre', 'Diciembre']



	layer_month = pdb.gimp_text_fontname(img, drawable, 0, 0, months[month], -1, True,  size_font_year, POINTS, font_month)

	pdb.gimp_layer_set_lock_alpha(layer_month, 255)

	pdb.gimp_floating_sel_to_layer(layer_month)



	pdb.gimp_layer_set_opacity(layer_month, 20)



	#pdb.gimp_layer_scale(layer_month, (w/10)*3, ( ((w/10)*3) * pdb.gimp_drawable_height(layer_month) ) / pdb.gimp_drawable_width(layer_month), True)



	x = (w/10)

	y = h - layer_month.height - (h/25)



	layer_month.set_offsets(x, y)



	# CALENDAR



	weekdays = ['Lunes', 'Martes', 'Miercoles', 'Jueves', 'Viernes', 'Sabado', 'Domingo']



	cont = 0

	sep_w = w/9

	sep_h = (h*cal_porcent)/8



	height_layer_weekdays = 20



	while(cont<7):

		px = (cont%7)*sep_w + sep_w + (sep_w/5)

		py = (h*pht_porcent)

		layer_txt = pdb.gimp_text_fontname(img, drawable, px, py, weekdays[cont], -1, True,  size_font_month, POINTS, font_month)

		height_layer_weekdays = layer_txt.height

		pdb.gimp_layer_set_lock_alpha(layer_txt, 255)



		if cont==6:

			pdb.gimp_context_set_background(color_festive)

		else:

			pdb.gimp_context_set_background(color_month)



		pdb.gimp_edit_fill(layer_txt, BACKGROUND_FILL)



		pdb.gimp_floating_sel_to_layer(layer_txt)

		if cont>0:

			pdb.gimp_image_merge_down(img, layer_txt, 0)



		cont = cont + 1



	# CREATE BACKGROUND WEEKDAYS



	layer_bg_weekdays = pdb.gimp_layer_new(img, w, height_layer_weekdays+16, RGB_IMAGE, "background weekdays", 100, NORMAL_MODE)

	layer_bg_weekdays.add_alpha()

	img.add_layer(layer_bg_weekdays, -1)

	pdb.gimp_image_lower_layer(img, layer_bg_weekdays)



	pdb.gimp_context_set_background(bg_weekdays)

	layer_bg_weekdays.fill(BACKGROUND_FILL)



	layer_bg_weekdays.set_offsets(0, (h*pht_porcent)-8)



	# DAYS



	day = datetime.date(year, month, 1)

	cont = 0

	dayofmonth = datetime.date.weekday(day)



	nextmonth_year = year

	nextmonth_month = month+1

	if nextmonth_month>12:

		nextmonth_year = year+1

		nextmonth_month = 1		



	ndaysofmonth = datetime.date(nextmonth_year, nextmonth_month, 1) - day



	while(cont<ndaysofmonth.days):

		px = (dayofmonth%7)*sep_w + sep_w + (sep_w/5)

		py = (dayofmonth/7)*sep_h + (h*pht_porcent) + + sep_h

		layer_txt = pdb.gimp_text_fontname(img, drawable, px, py, str(cont+1), -1, True,  size_font_number, POINTS, font_number)

		pdb.gimp_layer_set_lock_alpha(layer_txt, 255)



		if dayofmonth%7==6:

			pdb.gimp_context_set_background(color_festive)

		else:

			pdb.gimp_context_set_background(color_number)



		pdb.gimp_edit_fill(layer_txt, BACKGROUND_FILL)



		pdb.gimp_floating_sel_to_layer(layer_txt)

		if cont>0:

			pdb.gimp_image_merge_down(img, layer_txt, 0)



		cont = cont + 1

		dayofmonth = dayofmonth + 1



	pdb.gimp_context_set_background(old_background)

	

	# agrupamos UNDO

	pdb.gimp_image_undo_group_end(img)



# función principal

if __name__ == '__main__':



	# llamada a función register

	register(

		"calendar",

		"Calendario",

		"Calendario",

		"Javi Pacheco",

		"Javi Pacheco",

		"2007",

		"<Image>/Python-Fu/Crear calendario de imagen",

		"RGB*, GRAY*",

		[

			(PF_SPINNER, "width", "Ancho (mm)", 125, (0, 1000, 1)),

			(PF_SPINNER, "height", "Alto (mm)", 142, (0, 1000, 1)),

			(PF_SPINNER, "photo_porcent", "Procentaje foto", 60, (0, 100, 1)),

			(PF_SPINNER, "month", "Mes", 1, (1, 12, 1)),

			(PF_SPINNER, "year", "Anio", 2008, (1900, 2999, 1)),

			(PF_FONT, "font_month", "Fuente Letras", default_font),

			(PF_SPINNER, "size_font_month", "Tam. Meses", 30, (8, 120, 1)),

			(PF_COLOR, "color_month", "Color Meses", (0,0,0)),

			(PF_FONT, "font_number", "Fuente Numeros", default_font),

			(PF_SPINNER, "size_font_number", "Tam. Numeros", 50, (8, 120, 1)),

			(PF_COLOR, "color_number", "Color numeros", (0,0,0)),

			(PF_COLOR, "color_festive", "Color festivo", (0,0,0)),

			(PF_COLOR, "bg_weekdays", "Fondo dias semana", (200,200,200)),

			(PF_SPINNER, "size_font_year", "Tam. Anio y Mes", 120, (40, 200, 1))

		],

		[],

		Calendar)

	main()


Si tradueixo totes les definicions del castellà al català, deso els canvis i activo els permisos, no em funciona...¿...?

---

### Post by papapep on 2008-03-27
Per provar he descarregat i instal·lat el glass-text.scm, després l'he traduït i funciona perfectament (vull dir que surt en català).
Alguna cosa se't deu escapar. On deses el fitxer traduït? Quin propietari i permisos té?

```
sudo ls -la /usr/share/gimp/2.0/scripts/nom_del_fitxer_traduït.scm
```

---

### Post by rajoar on 2008-03-27
El fitxer està a: /home/ramon/.gimp-2.4/plug-ins, o bé a: /home/ramon/.gimp-2.4/scripts, tal i com aconsellen el creadors dels scripts que he provat i que funcionen perfectament abans de la seva traducció.
Faig doble clic sobre el fitxer corresponent i s'obre el menu: Voleu executar «calendar.py», o mostrar-ne el contingut? Premo mostrar-ne el contingut i s'obre amb el gedit..., edito el text en castellà, el tradueixo al català i deso el fitxer. Comprovo els permisos i... no funciona... (no apareix al menú corresponent junt amb els altres)...

---

### Post by papapep on 2008-03-27
Fins aqui no hi arribo. Jo he baixat l'script, l'he posat on ja has vist i tot va de perilles. El que comentes ni flowers. Prova a preguntar a algun fòrum específic de Gimp.

---

### Post by rajoar on 2008-03-27
papapep,
Ja he descobert per què no funciona... No es poden posar accents...
Ho he provat sense accentuar i tot va com una seda... És una llàstima però ens haurem de conformar, si no és que algú ens explica com poder utilitzar els accents i d'altres caracters especials...

---

### Post by papapep on 2008-03-27
En el meu cas si que funcionen

---

### Post by rajoar on 2008-03-28
Sí papapep, però fixa-t'hi bé hi veuràs que tu has fet servir un fitxer *.scm i en el meu cas és un *.py, i a més, al començament del meu fitxer diu: # -*- coding: latin-1 -*-
Crec que aquí rau el problema dels accents, el que passa és que no tinc ni idea de què ni com s'ha de fer per editar l'script i que passi a utilitzar UTF-8, per exemple, perquè així agafi tots els accents...

---

### Post by papapep on 2008-03-28
Tinc perfectament clar que estem parlant de coses diferents. Els .scm són scripts fets en llenguatge [Scheme]("http://schemers.org/") (dialecte del [LISP]("http://ca.wikipedia.org/wiki/Lisp")), i el teu és un programa, ni que sigui curt, fet amb [Python]("http://www.python.org/"). Ambdós són interpretats, però són llenguatges de programació amb tots els ets i uts.

Sobre com fer que el Gimp et faci servir l'script en Python amb utf-8, prova a editar-lo amb el Gedit (o qualsevol altre editor que sigui capaç de fer-ho) i digues-li que el desi com a utf-8,  a veure si funciona.

---

### Post by rajoar on 2008-03-28
Valgam Déu papapep! he fet servir l'expresió fixat-hi bé des de un punt de vista visual, no pretenia pas res més... Encara que ja sóc una mica grandet, sóc molt neòfit amb l'Ubuntu i no faig res més que aprendre cada dia amb les teves explicacions i d'altres persones que com tu ens ajudeu dia rere dia.
Tornant al tema..., efectivament fent servir l'anomena i desa i com a UTF-8 tot funciona perfectament, amb accents inclosos... 
O sigui que ja puc continuar traduïnt els scripts del Gimp, Nautilus, etc. al català amb tots els ets i uts com cal...
Per tant, una vegade més, moltes gràcies per la teva predisposició..
Salut a tots!

---

