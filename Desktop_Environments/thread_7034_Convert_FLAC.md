---
title: "Convert FLAC"
date: 2004-12-03
forum: Desktop Environments
---

### Post by mattyh on 2004-12-03
I have a large collection of FLAC and M4A files that I want to move to my ipod.  My issue is that I want to convert the FLAC files to either m4a, or mp3, preferably m4a.  I am curious if anyone has found some good programs to do that under Linux as I have never done this before.  Also, does anyone know of a good program that will read the tag information on these files and build a directory structure for me, or rename the files, or both?  Thanks.

---

### Post by rolfpal on 2004-12-04
Hi,

I use Naudilus, it is a nautilus script.

Get it here., download it, put it in ~.gnome2/nautilus-scripts, make sure it is executable and right click on a file or a group of files and it lets you transpose it or them to mp3 (if you have lame installed), ogg, or wave.  You could probably tinker with it to transform them to other formats too.

Get it here - [Naudilus script is here](http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Naudilus)

Cheers,

Rolf

---

### Post by beerorkid on 2005-03-04
Nice script it worked like a charm.  Although I was not able to go from flac to mp3.  I just used sound recorder to save the recording into .ogg format.

Thanks

---

### Post by Gekoskate on 2005-07-03
this version works correctly with flac, good luck
```

# Geko Audio Converter 0.3

# Basado en codigo de convert_to_jpeg (David Westlund)
# Basado en codigo de Archiver/Unarchiver (Patrick Largey & David Westlund)
# Basado en codigo de Naudilus - audio conversion (Rafael Rigues)
# agrega el script a ~/.gnome/nautilus-scripts, y aplicale un chmod +x

# Lista de cosas que faltan para hacer
# 2 copiar los tags entre los formatos
# 3 convertir de formato flac a wav y viceversa
# 4 agregar conversion formato wma

# Uso:
# * Para convertir 1 archivo o varios, seleccionas con el mouse los archivos a convertir presionas click derecho
# en el menu entras a scripts y seleccionas este script.
# * Para convertir todo el directorio sin seleccionar ningun archivo presionas click derecho en el directorio  # en el menu entras a scrips y selecionas este script.

# PORFAVOR ESCRIBAN LOS BUGS O MEJORAS QUE SE LE PUEDA HACER A ESTE CODIGO, Y ASI MEJORARLO

#OPCIONES

directorio="/home/geko/Convertidos/"

#INICIO

if [ ! -f `which gdialog` ]
then
   echo "No se ha encontrado gdialog, necesitas gnome-utils"
   exit 1
fi

#FUNCION PARA CODIFICAR

fcodificar()
{
	if [ "`file -b "$1" | grep 'MP3'`" != "" ] || [ "`echo $1 | grep -i '\.mp3$'`" != "" ]
	then
		if [ "$3" = ".ogg" ]
		then
			lame --quiet --decode "$1" - | oggenc - -q6 -o "$2"
		else
			lame --quiet --decode "$1" "$2"
		fi
		break
	fi
	if [ "`file -b "$1" | grep 'Vorbis'`" != "" ] || [ "`echo $1 | grep -i '\.ogg$'`" != "" ]
	then
		if [ "$3" = ".mp3" ]
		then
			ogg123 -q --device=wav "$1" -f - | lame -m j -b 192 -s 44.1 - "$2"
		else
			ogg123 -q --device=wav "$1" -f "$2"
		fi
		break
	fi
	if [ "`file -b "$1" | grep 'WAVE'`" != "" ] || [ "`echo $1 | grep -i '\.wav$'`" != "" ]
	then
		if [ "$3" = ".mp3" ]
		then
			lame --quiet -m j -b 192 -s 44.1 "$1" "$2"
		else
			oggenc "$1" - -q6 -o "$2"
		fi
		break
	fi
	if [ "`file -b "$1" | grep 'WMA'`" != "" ] || [ "`echo $1 | grep -i '\.wma$'`" != "" ]
	then
		if [ "$3" = ".mp3" ]
		then
			mplayer -ao pcm -aofile "$2.wav" "$1"
			lame --quiet -m j -b 192 -s 44.1 "$2.wav" "$2"			
		else
			mplayer -ao pcm -aofile "$2.wav" "$1"
			oggenc "$2.wav" - -q6 -o "$2"
		fi
		rm -f "$2.wav"
		break
	fi
	if [ "`file -b "$1" | grep 'Flac'`" != "" ] || [ "`echo $1 | grep -i '\.flac$'`" != "" ]
	then
		ARTIST=`metaflac "$1" --show-tag=ARTIST | sed s/.*=//g`
		TITLE=`metaflac "$1" --show-tag=TITLE | sed s/.*=//g`
		ALBUM=`metaflac "$1" --show-tag=ALBUM | sed s/.*=//g`
		GENRE=`metaflac "$1" --show-tag=GENRE | sed s/.*=//g`
		TRACKNUMBER=`metaflac "$1" --show-tag=TRACKNUMBER | sed s/.*=//g`
		DATE=`metaflac "$1" --show-tag=DATE | sed s/.*=//g`
		if [ "$3" = ".mp3" ]
		then
			flac -c -d "$1" | lame - -m j -b 256 -s 44.1 "$2" 
			id3 -t "$TITLE" -T "$TRACKNUMBER" -y "$DATE" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" "$2"
		else			
			flac -c -d "$1" | oggenc - -q6 --artist "$ARTIST" --album "$ALBUM" --tracknum "$TRACKNUMBER" --date "$DATE" --genre "$GENRE" --title "$TITLE" -o "$2"
		fi
		break
	fi
}

#FUNCION PARA CONVERTIR

fconvertir()
{
		psalida=`echo "$entrada" | sed 's/\.\w*$/''/'`
		salida=`echo "$entrada" | sed 's/\.\w*$/'$formato'/'`		
		echo "# Convertiendo archivo: $entrada"
		i=`echo $i | sed 's/"//g'`
		while `true`
		do
			if  [ "$entrada" = "$salida" ]
			then
				zenity --error --title="Geko Audio Converter 0.3 - ATENCION!!" --text="El archivo \"$entrada\" ya se encuentra en el formato que selecciono \"$formato\", la conversion no seria necesaria para este archivo!!"
				break
			fi		
			if [ "`ls "$directorio$salida" | grep -v "^ls"`" != "" ]
			then
				if !(`gdialog --title "Geko Audio Converter 0.3 - ATENCION!!" --yesno "El Archivo:  \"$directorio$salida\" ya existe, deseas remplazarlo?" 200 100`)
				then
					break
				fi
			fi			
			salidaf="$directorio$salida"
			fcodificar "$entrada" "$salidaf" "$formato"
		break
		shift
		done
		let "contador += 1"
		let "progress = contador*100/archivos"
		echo $progress
}

#PREGUNTA PARA CONVERTIR TODO EL DIRECTORIO 

todo=0
if [ $# -eq 0 ]
then
	if !(`gdialog --title "Geko Audio Converter 0.3 - ATENCION!!" --yesno "Se convertiran todos los archivos del directorio, estas seguro?" 200 100`)
	then
		exit 1
	fi
	todo=1
fi

#MENU PARA SELECCIONAR FORMATO

sformato=""
if which lame 2>/dev/null
then
	sformato=".mp3"
fi
if which oggenc 2>/dev/null
then
	sformato="$sformato .ogg"
fi		
while [ ! "$formato" ]
do
	formato=`zenity --title "Geko Audio Converter 0.3" --list --column="Formatos disponibles" $sformato .wav --text "A que formato deseas convertir?"`
	if  [ $? != 0 ]
	then
		exit 1
	fi
	[ $? -ne 0 ] && exit 2
done

#CONVIERTE LOS ARCHIVOS SELECCIONADOS

let "archivos = $#"
(while [ $# -gt 0 ]
do
	for i in $formato
	do
		entrada=$1
		fconvertir
	done
	shift
done

#CONVIERTE TODO EL DIRECTORIO

if  [ "$todo" = "1" ]
then
	for a in *.*
	do
		let "nfile = nfile+1"
	done
	let "archivos = $nfile"
	for a in *.*
	do
		entrada=$a
		fconvertir
	done
	shift
fi

#TERMINA

) |
zenity --progress --title="Geko Audio Converter 0.3" --auto-close --percentage=0
```

---

### Post by gammyhand on 2005-08-28
The link to the Naudilus script doesn't work. And if I do:

sudo gedit .gnome2/nautilus-scripts

and paste in the example above it won't let me save the file.

---

### Post by nszabolcs on 2005-09-10
[http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Audio/Naudilus](http://g-scripts.sourceforge.net/nautilus-scripts/Multimedia/Audio/Naudilus)

---

### Post by maxfacta on 2007-01-01
I used this little loop, at the bash prompt. It'll just create mp3 files out of all flac files in the current directory. You could adjust it to move the output to a different directory, or delete the flac files once you're done, etc...

```
bash# for i in *flac ; do flac -dc "$i" | lame -h - "${i%flac}mp3" ; done
```

The quotes are required just in case your filenames have spaces etc. in them.

---

### Post by pizpot on 2007-03-19
I guess it is time to post the real answer now that everyone had tried the hard ways.

--> it is called SoundConverter

Read it's blurb in Add/Remove Programs. It says what it does and what you need.

Thank you, thank you.

---

### Post by Jose Catre-Vandis on 2007-04-29
soundconverter works a treat :-)

```
sudo aptitude install soundconverter
```

---

### Post by citybird on 2007-11-11
does sound converter have a number of songs limit? I am just asking because my FLAC directory has over 2000 songs and when I hit the convert button sounConverter says:
```
file xxxx of yyyy (333 minutes remaining)
```

I am guessing that there is some sort of overflow happening...

---

### Post by Spike-X on 2007-11-12
> **pizpot said:**
> I guess it is time to post the real answer now that everyone had tried the hard ways.

--> it is called SoundConverter

Read it's blurb in Add/Remove Programs. It says what it does and what you need.


As long as you don't **need** your converted tracks to have accurate track times, sure it does.

---

### Post by Spike-X on 2007-11-12
Addendum to previous post:

I just did some experimenting. I thought the problem might be with the conversion from Flac straight to MP3, so I converted to .wav first. No problem so far, the .wav file had the same track time as the .flac file. I then converted the .wav file to MP3 - not so good. The track time got screwed up.

Then I figured the problem might be because I was converting to VBR MP3. Perhaps the track time is taken from the total amount of bits divided by the bitrate? So I tried converting both the .wav file and the .flac file to CBR MP3. This time, the track time was the right length.

Summary - SoundConverter screws up the track time when converting to VBR MP3. Time to file a bug report!

---

