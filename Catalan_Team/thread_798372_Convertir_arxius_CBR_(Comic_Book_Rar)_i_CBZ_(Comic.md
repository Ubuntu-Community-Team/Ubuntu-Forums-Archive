---
title: "Convertir arxius CBR (Comic Book Rar) i CBZ (Comic Book Zip) a pdf"
date: 2008-05-18
forum: Catalan Team
---

### Post by pixatintes on 2008-05-18
He estat buscant una aplicació per passar arxius de còmic digital(cbr o cbz) a pdf. Pensant particularment en els dispositius portàtils i/o ebooks readers a vegades és més pràctic aquest format que no el format imatge (jpg o png).

Com que no he trobat res prou practic he anat fent aquest script pel Nautilus que us deixo aquí.

Permet les següents opcions al passar a pdf:
- Conversió normal
- Convertir a grisos sense escalar les imatges
- Escalar les imatges per Irex Iliad (XGA-768x1024)
- Convertir a grisos i escalar les imatges per Irex Iliad (XGA-768x1024)
- Escalar les imatges per Sony eBook Reader (VGA-600x800)
- Convertir a grisos i escalar les imatges per Sony eBook Reader (VGA-600x800)

Per instal·lar-lo només cal descomprimir l'arxiu al directori /$HOME/.gnome2/nautilus-scripts/ i donar-li permís d'execució.
I per executar-lo, sel·leccionar l'arxiu o arxius dins el Nautilus i amb el menu del botó dret -> Scripts --> Cbr2Pdf.

L'script no és cap meravella .. i de ben segur que es pot millorar molt.. però sembla que fa bé la seva funció..

Nota: El consum de CPU en la conversió és considerable.

Espero que sigui de utilitat per algú..

Us deixo algunes utilitats més per eCòmics a [aquí]("http://pixatintes.freeprohost.com/?page_id=319").

Versió 0.21b

---

### Post by pixatintes on 2008-05-18
Versió 0.2b

```

#!/bin/bash

# cbr2pdf
# Convert cbr/cbz files to pdf.
#
# pixatintes@gmail.com 
#
#		15.05.2008 : v0.2b	
# Install
# 		Put on ~/.gnome2/nautilus-scripts/
#		In a console : chmod +x ~/.gnome2/nautilus-scripts/cdr2pdf
# Dependency
#		unrar
#		unzip
#		ImageMagick
#		
version="0.2b"
#########################################################################
#!/bin/bash

	###### Default = English #####
	title="Cbr2Pdf "$version""
	pleasesel="Please select a file."
	noselec=""$title" convert cbr/cbz files. "$pleasesel""
	select="Select a format:"
	Standard="No resize images" 
	Standard_grey="Convert to Grey-scale without resize images"
	Iliad="Resize images for Irex Iliad (XGA-768x1024)"
	Iliad_grey="Convert to Grey-scale and resize images for Irex Iliad (XGA-768x1024)"
	Sony="Resize images for Sony eBook Reader (VGA-600x800)"
	Sony_grey="Convert to Grey-scale and resize images for Sony eBook Reader (VGA-600x800)"
	warning="Warning"
	proceed="is already exist. Overwrite?"
	conversion="Converting files.."
	end="Complete :P"

case $LANG in
	######## Spanish ########
	ca* )
	title="Cbr2Pdf "$version""
	pleasesel="Sel·leccina almenys un arxiu."
	noselec=""$title" converteix cbr/cbz arxius. "$pleasesel""
	select="Sel·lecciona un format:"
	Standard="No escalar les imatges" 
	Standard_grey="Convertir a grisos sense escalar les imatges" 
	Iliad="Escalar les imatges per Irex Iliad (XGA-768x1024)"
	Iliad_grey="Convertir a grisos i escalar les imatges per Irex Iliad (XGA-768x1024)"
	Sony="Escalar les imatges per Sony eBook Reader (VGA-600x800)"
	Sony_grey="Convertir a grisos i escalar les imatges per Sony eBook Reader (VGA-600x800)"
	warning="Warning"
	proceed="ja existeix. Sobreescriure?"
	conversion="Convertint arxius.."
	end="Complert :P"
esac

#################################################
#	FUNCIONS
ext() # funció "convert file"
{
	#### Extreure cbr/cbz arxius a ~/tempcbr/

	O=`echo "$1" | sed 's/\.\w*$/''/'`	

	if [ "`file -b "$1" | grep 'RAR'`" != 0 ]
	then
		mkdir tempcbr
		unrar e -y "$1" tempcbr/
	fi

	if [ "`file -b "$1" | grep 'Zip'`" != 0 ]
	then
		unzip "$1" -d tempcbr/
	fi

	#### Crear pdf

	if [ "$2" = "Standard" ]
	then # Standard
		convert tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O".pdf
	fi

	if [ "$2" = "Standard_grey" ]
	then # Standard
		convert -modulate 100,0 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O".pdf
	fi

	if [ "$2" = "Iliad" ]
	then # Iliad
		convert -resize 768x1024 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O".pdf
	fi

	if [ "$2" = "Iliad_grey" ]
	then # Iliad
		convert -resize 768x1024 -modulate 100,0 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O".pdf
	fi

	if [ "$2" = "Sony" ]
	then # sony
		convert -resize 600x800 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O".pdf
	fi

	if [ "$2" = "Sony_grey" ]
	then # sony
		convert -resize 600x800 -modulate 100,0 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O".pdf
	fi

	##### borrar temp directori ~/tempcbr/
	rm -R tempcbr
}


#### No hi ha fitxers sel. ###
			
if [ $# -eq 0 ]; then
	zenity --error --title="$warning" --text="$noselec"
	exit 1
fi		

######## Finetra principal ########
while [ ! "$formatout" ] # Preguntar el format de sortida
do	
	formatout=`zenity --list --title="$title" --text="$select" --width=680 --height=270 --column="Format" --column="Description" Standard "$Standard" Standard_grey "$Standard_grey" Iliad "$Iliad" Iliad_grey "$Iliad_grey" Sony "$Sony" Sony_grey "$Sony_grey"`

	[ $? -ne 0 ] && exit 2 # Cancelar
done

(while [ $# -gt 0 ]; do
	for i in $formatout; do
		O=`echo "$1" | sed 's/\.\w*$/'.pdf'/'`			

		while `true`; do
			########## Mirar si el fitxer existeix, sobreescriu ? ##########
			if [ "`ls "$O" | grep -v "^ls"`" != "" ]
			then
				if !(`gdialog --title "$warning" --yesno "$O $proceed" 200 100`)
				then
					break
				fi
			fi
			ext "$1" "$formatout" # Convertir
		break
		shift
		done
	done
	shift
done
echo "# "$end"" ; sleep 1
echo "100" ; sleep 1
) |
#### Barra de progrés ####
zenity --progress --percentage=0 --title="$title" --text="$conversion" --pulsate --width=400 


```

---

### Post by Curial on 2008-05-19
Ja fa temps que no em miro el aquest tema amb els còmics d'aquests formats i jo de sempre també els he preferit en pdf.

Jo el que feia per aquella època era descomprimir-los amb rar i un cop obtingudes les imatges passar-les a pdf amb l'Adobe Acrobat. El que no recordo és si ho he arribat a fer amb el PDFeditor o amb gscan2pdf des que faig anar l'ubuntu.(amb un dels dos segur)

Al sinàptic surten el cbrpager i el comix que no he provat, ho he anat deixant i encara estic igual.

Els scrips no els controlo, però ja va bé que hagis tocat el tema dels còmics:popcorn:.

Salut

---

### Post by pixatintes on 2008-05-19
Per linux hi ha el [comix]("http://comix.sourceforge.net/"), el trobaràs als repositoris.És de collonut però per formats cbr/cbz.

De totes formes un cop hagis provat els cbr/cbz amb un programa com el comix veuràs que són molts millors que no en format pdf, almenys al meu gust. El programa està dissenyat per llegir còmics i un lector de pdf és un lector genèric.

Jo prefereixo el format cbr/cbz però és que en alguns casos és millor passar-lo a pdf, sobretot per dispositius portàtils (lector de llibres electrònics, pda,..) ja que solen dur un lector de pdfs millor que lectors de imatges.

Els scripts són molt pràctics per automatitzar petites coses, serien un equivalent als *.bat de l'MSdos però amb la potència de l'interpret de comades de linux (tb es poden programar amb llenguatges més potents però ja no hi arribo :P ).
Els scripts al Nautilus s'apliquen seleccionant sobre un o varis arxius i amb el botó dret del mouse seleccionant l'script a executar.
Per instal·lar-los només cal còpiar l'arxiu al directori /$HOME/.gnome2/nautilus-scripts/ i donar-li permís d'execució.

Aquí deixo un parell d'enllaços interesants sobre el tema:
[http://g-scripts.sourceforge.net/]("http://g-scripts.sourceforge.net/")
[http://nautilus-scripts.javielinux.com/]("http://nautilus-scripts.javielinux.com/")

fins ara,

---

### Post by Curial on 2008-05-19
> **pixatintes said:**
> Per linux hi ha el [comix]("http://comix.sourceforge.net/"), el trobaràs als repositoris.És de collonut però per formats cbr/cbz.

De totes formes un cop hagis provat els cbr/cbz amb un programa com el comix veuràs que són molts millors que no en format pdf, almenys al meu gust. El programa està dissenyat per llegir còmics i un lector de pdf és un lector genèric.

Jo prefereixo el format cbr/cbz però és que en alguns casos és millor passar-lo a pdf, sobretot per dispositius portàtils (lector de llibres electrònics, pda,..) ja que solen dur un lector de pdfs millor que lectors de imatges.

Els scripts són molt pràctics per automatitzar petites coses, serien un equivalent als *.bat de l'MSdos però amb la potència de l'interpret de comades de linux (tb es poden programar amb llenguatges més potents però ja no hi arribo :P ).
Els scripts al Nautilus s'apliquen seleccionant sobre un o varis arxius i amb el botó dret del mouse seleccionant l'script a executar.
Per instal·lar-los només cal còpiar l'arxiu al directori /$HOME/.gnome2/nautilus-scripts/ i donar-li permís d'execució.

Aquí deixo un parell d'enllaços interesants sobre el tema:
[http://g-scripts.sourceforge.net/]("http://g-scripts.sourceforge.net/")
[http://nautilus-scripts.javielinux.com/]("http://nautilus-scripts.javielinux.com/")

fins ara,

Ei! Moltes gràcies, No havia vist l'script abans.

Jo ho provaré.:)

---

### Post by albert-I on 2008-05-22
Pero els fitxers CBR no son fitxers rar amb l'extensió canviada? 

Si li poses la extensió rar queda com un conjunt de fotografies comprimides amb un rar.

---

### Post by pixatintes on 2008-05-23
> **albert-I said:**
> Pero els fitxers CBR no son fitxers rar amb l'extensió canviada? 

Si li poses la extensió rar queda com un conjunt de fotografies comprimides amb un rar.

Dons sí.

La idea era que l'script descomprimís l'arxiu, ja fos Rar o Zip, i de les imatges que hi ha dins en crees un pdf.
A més, amb l'opció de canviar el tamany de les imatges o convertir-les a escala de grisos..

Està pensat de cares a poder llegir comics, principalment manga (per la mida de paper) en un ebook reader (sony, irex iliad,..), que duen un bon lector de pdfs.

En principi funciona, i els puc veure al PC amb l'evince sense problemes. Però en el ebook reader, el pdf em provoca errors i es penja.. Déu ser cosa de ImageMagick.. :(

---

### Post by pixatintes on 2008-05-23
Bé, trastejant una mica he trobat l'aplicació 'pdftk', que repara pdfs.
És molt ràpida i l'he afegit al final de l'script, ara sembla que funciona bé.

```

#!/bin/bash
# cbr2pdf
# Convert cbr/cbz files to pdf.
#
# pixatintes@gmail.com 
#
#		15.05.2008 : v0.21b	
# Install
# 		Put on ~/.gnome2/nautilus-scripts/
#		In a console : chmod +x ~/.gnome2/nautilus-scripts/cdr2pdf
# Dependency
#		unrar
#		unzip
#		ImageMagick
#		pdftk
#		
version="0.21b"
#########################################################################
#!/bin/bash

	###### Default = English #####
	title="Cbr2Pdf "$version""
	pleasesel="Please select a file."
	noselec=""$title" convert cbr/cbz files. "$pleasesel""
	select="Select a format:"
	Standard="No resize images" 
	Standard_grey="Convert to Grey-scale without resize images"
	Iliad="Resize images for Irex Iliad (XGA-768x1024)"
	Iliad_grey="Convert to Grey-scale and resize images for Irex Iliad (XGA-768x1024)"
	Sony="Resize images for Sony eBook Reader (VGA-600x800)"
	Sony_grey="Convert to Grey-scale and resize images for Sony eBook Reader (VGA-600x800)"
	warning="Warning"
	proceed="is already exist. Overwrite?"
	conversion="Converting files.."
	end="Complete :P"

case $LANG in
	######## Spanish ########
	ca* )
	title="Cbr2Pdf "$version""
	pleasesel="Sel·leccina almenys un arxiu."
	noselec=""$title" converteix cbr/cbz arxius. "$pleasesel""
	select="Sel·lecciona un format:"
	Standard="No escalar les imatges" 
	Standard_grey="Convertir a grisos sense escalar les imatges" 
	Iliad="Escalar les imatges per Irex Iliad (XGA-768x1024)"
	Iliad_grey="Convertir a grisos i escalar les imatges per Irex Iliad (XGA-768x1024)"
	Sony="Escalar les imatges per Sony eBook Reader (VGA-600x800)"
	Sony_grey="Convertir a grisos i escalar les imatges per Sony eBook Reader (VGA-600x800)"
	warning="Warning"
	proceed="ja existeix. Sobreescriure?"
	conversion="Convertint arxius.."
	end="Complert :P"
esac

#################################################
#	FUNCIONS
ext() # funció "convert file"
{
	#### Extreure cbr/cbz arxius a ~/tempcbr/

	O=`echo "$1" | sed 's/\.\w*$/''/'`	

	if [ "`file -b "$1" | grep 'RAR'`" != 0 ]
	then
		mkdir tempcbr
		unrar e -y "$1" tempcbr/
	fi

	if [ "`file -b "$1" | grep 'Zip'`" != 0 ]
	then
		unzip "$1" -d tempcbr/
	fi

	#### Crear pdf

	if [ "$2" = "Standard" ]
	then # Standard
		convert tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O"_.pdf
	fi

	if [ "$2" = "Standard_grey" ]
	then # Standard
		convert -modulate 100,0 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O"_.pdf
	fi

	if [ "$2" = "Iliad" ]
	then # Iliad
		convert -resize 768x1024 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O"_.pdf
	fi

	if [ "$2" = "Iliad_grey" ]
	then # Iliad
		convert -resize 768x1024 -modulate 100,0 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O"_.pdf
	fi

	if [ "$2" = "Sony" ]
	then # sony
		convert -resize 600x800 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O"_.pdf
	fi

	if [ "$2" = "Sony_grey" ]
	then # sony
		convert -resize 600x800 -modulate 100,0 tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G "$O"_.pdf
	fi

	##### borrar temp directori ~/tempcbr/
	rm -R tempcbr
}


#### No hi ha fitxers sel. ###
			
if [ $# -eq 0 ]; then
	zenity --error --title="$warning" --text="$noselec"
	exit 1
fi		

######## Finetra principal ########
while [ ! "$formatout" ] # Preguntar el format de sortida
do	
	formatout=`zenity --list --title="$title" --text="$select" --width=680 --height=270 --column="Format" --column="Description" Standard "$Standard" Standard_grey "$Standard_grey" Iliad "$Iliad" Iliad_grey "$Iliad_grey" Sony "$Sony" Sony_grey "$Sony_grey"`

	[ $? -ne 0 ] && exit 2 # Cancelar
done

(while [ $# -gt 0 ]; do
	for i in $formatout; do
		O=`echo "$1" | sed 's/\.\w*$/'.pdf'/'`			
		while `true`; do
			########## Mirar si el fitxer existeix, sobreescriu ? ##########
			if [ "`ls "$O" | grep -v "^ls"`" != "" ]
			then
				if !(`gdialog --title "$warning" --yesno "$O $proceed" 200 100`)
				then
					break
				fi
			fi
			ext "$1" "$formatout" # Convertir

                        pdftk "$O"_.pdf output "$O".pdf
                        rm "$O"_.pdf
		break
		shift
		done
	done
	shift
done

echo "# "$end"" ; sleep 1
) |
#### Barra de progrés ####
zenity --progress --percentage=0 --title="$title" --text="$conversion" --pulsate --width=400 

```

---

### Post by barx on 2008-09-14
:: English ::

Hi :KS :

 I can't understand it all your langague, I imagine that is French, but I'm not sure . . . anyway I tried to modify your script to include the cbt format, you know with compresion tar, tat.gz and tar.bz2, but I couldn't  . . . So I changed into Spanish Language kind of properly. I hope you can check it and see if there's a modification to cbt to linuxaize it around the internet

:: Español ::

Hola :KS :

No entendí en que idioma esta pero imagino que esta en Francés, pero no estoy seguro . . . de todos modos traté de modificarlo para ponerlo en formato cbt,tu sabes con compresión tar, tar.gz y tar.bz2, pero espero lo veas y agregar un cambio a cbt para linuxizarlo en internet.

Saludos desde México

---

### Post by papapep on 2008-09-14
Hi Barx,

I don't get what you are saying in your post, neither in english or in spanish.
Our language is not french, its [catalan]("http://en.wikipedia.org/wiki/Catalan_language"), as our forum name states, and this is the regular language in this forum.

---

### Post by barx on 2008-11-08
:D haha, maybe it's  common language in Europe, well in America is more used Spanish, well, but if English we understand us, much better, isn't it?:popcorn:

---

### Post by papapep on 2008-11-08
As I said before, this is the **catalan speakers subforum**. To post in english you've got plenty of places.

---

### Post by pixatintes on 2008-11-10
Hi barx, thanks for your mod, I promise you that I'm going to add your code, when I have a moment.

The page where I have the script is [http://pixatintes.freeprohost.com/?page_id=319](http://pixatintes.freeprohost.com/?page_id=319) 

No hay problema con el español tampoco. Saludos desde Catalunya.

Thanks, see u, 
pixatintes

---

### Post by zakhooi on 2009-01-04
I'm looking for the opposite, something to convert PDF TO CBR.

Can anyone advice please?

---

### Post by papapep on 2009-01-04
En aquest fòrum en anglès NO, si us plau.

---

### Post by barx on 2009-05-13
Yes, there's a pack of Nautils scripts that put in folders the images of the pdf, then you can rar it again.

Download from [this]("http://nautilus-scripts.javielinux.com/pdf.php") page 

It's a Deb that you can install and have many pdf tools, enjoy it

Sorry, I knew it time ago, but I thinks isn't too late :P

---

### Post by barx on 2009-05-13
> **papapep said:**
> Hi Barx,

I don't get what you are saying in your post, neither in english or in spanish.
Our language is not french, its [catalan]("http://en.wikipedia.org/wiki/Catalan_language"), as our forum name states, and this is the regular language in this forum.

Perdón, no lo noté en el comienzo, paso de nuevo por este post y de verdad pido disculpas, es solo que, el script es tan bueno que lo encontre en este subforo de catalán. Recomende el script a un blog, espero que no te moleste.

Jeje, bueno, ahora se como se escribe el Catalán :popcorn:

---

### Post by Camulus on 2010-01-15
Hola a tots. m'he descarregat aquest interessant script però no aconsegueixo que funcioni. copio la sortida a veure si algú em pot ajudar. em seria de gran ajuda un script com aquest o algun que fes quelcom semblant.
Gracies

```
camulus@Miko:~/Escriptori/v$ ./cbr2pdf_v0.30b Las_Rubias_1de4.cbr
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::visited-link-color' of type `GdkColor' from rc file value "((GString*) 0x1150b80)" of type `GString'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::visited-link-color' of type `GdkColor' from rc file value "((GString*) 0x12334c0)" of type `GString'
ls: no se puede acceder a Las_Rubias_1de4.pdf: No existe el fichero ó directorio
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkWidget::visited-link-color' of type `GdkColor' from rc file value "((GString*) 0x1778d60)" of type `GString'
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  Las_Rubias_1de4.cbr may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of Las_Rubias_1de4.cbr or
        Las_Rubias_1de4.cbr.zip, and cannot find Las_Rubias_1de4.cbr.ZIP, period.
identify: unable to open image `tempcbr/*G': No such file or directory @ blob.c/OpenBlob/2439.
identify: unable to open image `tempcbr/*G': No such file or directory @ blob.c/OpenBlob/2439.
convert: unable to open image `tempcbr/*G': No such file or directory @ blob.c/OpenBlob/2439.
convert: missing an image filename `tempcbr/*G' @ convert.c/ConvertImageCommand/2775.
identify: unable to open image `tempcbr/*/*g': No such file or directory @ blob.c/OpenBlob/2439.
identify: unable to open image `tempcbr/*/*g': No such file or directory @ blob.c/OpenBlob/2439.
convert: unable to open image `tempcbr/*/*g': No such file or directory @ blob.c/OpenBlob/2439.
convert: missing an image filename `tempcbr/*/*g' @ convert.c/ConvertImageCommand/2775.
identify: unable to open image `tempcbr/*/*G': No such file or directory @ blob.c/OpenBlob/2439.
identify: unable to open image `tempcbr/*/*G': No such file or directory @ blob.c/OpenBlob/2439.
convert: unable to open image `tempcbr/*/*G': No such file or directory @ blob.c/OpenBlob/2439.
convert: missing an image filename `tempcbr/*/*G' @ convert.c/ConvertImageCommand/2775.
identify: unable to open image `tempcbr/*/*f': No such file or directory @ blob.c/OpenBlob/2439.
identify: unable to open image `tempcbr/*/*f': No such file or directory @ blob.c/OpenBlob/2439.
convert: unable to open image `tempcbr/*/*f': No such file or directory @ blob.c/OpenBlob/2439.
convert: missing an image filename `tempcbr/*/*f' @ convert.c/ConvertImageCommand/2775.
identify: unable to open image `tempcbr/*/*F': No such file or directory @ blob.c/OpenBlob/2439.
identify: unable to open image `tempcbr/*/*F': No such file or directory @ blob.c/OpenBlob/2439.
convert: unable to open image `tempcbr/*/*F': No such file or directory @ blob.c/OpenBlob/2439.
convert: missing an image filename `tempcbr/*/*F' @ convert.c/ConvertImageCommand/2775.
./cbr2pdf_v0.30b: línea 75:  3080 Fallo de segmentación  convert tempcbr/*g tempcbr/*G tempcbr/*/*g tempcbr/*/*G tempcbr/*/*f tempcbr/*/*F "$O"_.pdf
Error: Failed to open PDF file: 
   Las_Rubias_1de4_.pdf
Errors encountered.  No output created.
Done.  Input errors, so no output created.
```

---

### Post by boulesis on 2012-07-17
¡Saludos!
En primer lugar, disculparme por publicar en español, pero espero que me podáis ayudar. He ejecutado el script y todo parece funcionar sin problemas, pero no localizo el archivo pdf que debería crear. ¿Podríais indicarme en qué carpeta coloca el archivo?
¡Gracias!

---

