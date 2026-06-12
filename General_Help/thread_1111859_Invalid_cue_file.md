---
title: "Invalid cue file???"
date: 2009-03-31
forum: General Help
---

### Post by GabrielWolff on 2009-03-31
I'm trying to split a big mp3 file with a cue sheet, but mp3splt states the cue sheet is invalid:```
gabriel@gabriel-laptop:~/Sch_Win----Chr_Pre_-_And_Sta.part1/Output$ mp3splt -c "Christoph Prégardien - Andreas Staier - Schubert Winterreise.cue" "Christoph Prégardien - Andreas Staier - Schubert Winterreise.mp3"
mp3splt 2.2.3 (18/01/09) - using libmp3splt 0.5.4
	Matteo Trotta <mtrotta AT users.sourceforge.net>
	Alexandru Munteanu <io_fx AT yahoo.fr>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
 Processing file 'Christoph Prégardien - Andreas Staier - Schubert Winterreise.mp3' ...
 reading informations from CUE file Christoph Prégardien - Andreas Staier - Schubert Winterreise.cue ...

  Artist: Christoph Pr&#65533;gardien - Andreas Staier"
  Album: Schubert Winterreise"
  Tracks: 1

 cue error: invalid cue file 'Christoph Prégardien - Andreas Staier - Schubert Winterreise.cue'
gabriel@gabriel-lapt
```

To my humble eyes it seems perfect... can anyone spot the problem?
```
REM DISCID 44115518

REM COMMENT "ExactAudioCopy v0.95b4"

PERFORMER "Christoph Prégardien - Andreas Staier"

TITLE "Schubert Winterreise"

FILE "Christoph Prégardien - Andreas Staier - Schubert Winterreise.mp3" MP3

  TRACK 01 AUDIO

    TITLE "Gute Nacht"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 00:00:00

  TRACK 02 AUDIO

    TITLE "Die Wetterfahne"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 06:08:72

  TRACK 03 AUDIO

    TITLE "Gefrorne Tränen"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 07:48:02

  TRACK 04 AUDIO

    TITLE "Erstarrung"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 10:02:30

  TRACK 05 AUDIO

    TITLE "Der Lindenbaum"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 12:44:45

  TRACK 06 AUDIO

    TITLE "Wasserflut"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 17:38:25

  TRACK 07 AUDIO

    TITLE "Auf dem Flusse"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 21:53:62

  TRACK 08 AUDIO

    TITLE "Rückblick"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 25:28:27

  TRACK 09 AUDIO

    TITLE "Irrlicht"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 27:33:70

  TRACK 10 AUDIO

    TITLE "Rast"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 30:31:50

  TRACK 11 AUDIO

    TITLE "Frühlingstraum"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 33:52:60

  TRACK 12 AUDIO

    TITLE "Einsamkeit"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 38:23:17

  TRACK 13 AUDIO

    TITLE "Die Post"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 41:32:07

  TRACK 14 AUDIO

    TITLE "Der greise Kopf"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 43:55:65

  TRACK 15 AUDIO

    TITLE "Die Krähe"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 47:09:42

  TRACK 16 AUDIO

    TITLE "Letzte Hoffnung"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 49:13:55

  TRACK 17 AUDIO

    TITLE "Im Dorfe"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 51:32:60

  TRACK 18 AUDIO

    TITLE "Der stürmische Morgen"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 54:48:57

  TRACK 19 AUDIO

    TITLE "Täuschung"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 55:36:17

  TRACK 20 AUDIO

    TITLE "Der Wegweiser"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 57:00:42

  TRACK 21 AUDIO

    TITLE "Das Wirthaus"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 61:08:22

  TRACK 22 AUDIO

    TITLE "Mut!"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 66:12:72

  TRACK 23 AUDIO

    TITLE "Die Nebensonnen"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 67:34:02

  TRACK 24 AUDIO

    TITLE "Der Leiermann"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 70:20:30

```

---

### Post by ukblacknight on 2009-04-30
> **GabrielWolff said:**
> I'm trying to split a big mp3 file with a cue sheet, but mp3splt states the cue sheet is invalid:```
gabriel@gabriel-laptop:~/Sch_Win----Chr_Pre_-_And_Sta.part1/Output$ mp3splt -c "Christoph Prégardien - Andreas Staier - Schubert Winterreise.cue" "Christoph Prégardien - Andreas Staier - Schubert Winterreise.mp3"
mp3splt 2.2.3 (18/01/09) - using libmp3splt 0.5.4
	Matteo Trotta <mtrotta AT users.sourceforge.net>
	Alexandru Munteanu <io_fx AT yahoo.fr>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!
 Processing file 'Christoph Prégardien - Andreas Staier - Schubert Winterreise.mp3' ...
 reading informations from CUE file Christoph Prégardien - Andreas Staier - Schubert Winterreise.cue ...

  Artist: Christoph Pr&#65533;gardien - Andreas Staier"
  Album: Schubert Winterreise"
  Tracks: 1

 cue error: invalid cue file 'Christoph Prégardien - Andreas Staier - Schubert Winterreise.cue'
gabriel@gabriel-lapt
```

To my humble eyes it seems perfect... can anyone spot the problem?
```
REM DISCID 44115518

REM COMMENT "ExactAudioCopy v0.95b4"

PERFORMER "Christoph Prégardien - Andreas Staier"

TITLE "Schubert Winterreise"

FILE "Christoph Prégardien - Andreas Staier - Schubert Winterreise.mp3" MP3

  TRACK 01 AUDIO

    TITLE "Gute Nacht"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 00:00:00

  TRACK 02 AUDIO

    TITLE "Die Wetterfahne"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 06:08:72

  TRACK 03 AUDIO

    TITLE "Gefrorne Tränen"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 07:48:02

  TRACK 04 AUDIO

    TITLE "Erstarrung"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 10:02:30

  TRACK 05 AUDIO

    TITLE "Der Lindenbaum"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 12:44:45

  TRACK 06 AUDIO

    TITLE "Wasserflut"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 17:38:25

  TRACK 07 AUDIO

    TITLE "Auf dem Flusse"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 21:53:62

  TRACK 08 AUDIO

    TITLE "Rückblick"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 25:28:27

  TRACK 09 AUDIO

    TITLE "Irrlicht"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 27:33:70

  TRACK 10 AUDIO

    TITLE "Rast"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 30:31:50

  TRACK 11 AUDIO

    TITLE "Frühlingstraum"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 33:52:60

  TRACK 12 AUDIO

    TITLE "Einsamkeit"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 38:23:17

  TRACK 13 AUDIO

    TITLE "Die Post"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 41:32:07

  TRACK 14 AUDIO

    TITLE "Der greise Kopf"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 43:55:65

  TRACK 15 AUDIO

    TITLE "Die Krähe"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 47:09:42

  TRACK 16 AUDIO

    TITLE "Letzte Hoffnung"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 49:13:55

  TRACK 17 AUDIO

    TITLE "Im Dorfe"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 51:32:60

  TRACK 18 AUDIO

    TITLE "Der stürmische Morgen"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 54:48:57

  TRACK 19 AUDIO

    TITLE "Täuschung"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 55:36:17

  TRACK 20 AUDIO

    TITLE "Der Wegweiser"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 57:00:42

  TRACK 21 AUDIO

    TITLE "Das Wirthaus"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 61:08:22

  TRACK 22 AUDIO

    TITLE "Mut!"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 66:12:72

  TRACK 23 AUDIO

    TITLE "Die Nebensonnen"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 67:34:02

  TRACK 24 AUDIO

    TITLE "Der Leiermann"

    PERFORMER "Christoph Prégardien - Andreas Staier"

    INDEX 01 70:20:30

```

I'm having this same problem with a different mp3/cue sheet.  I wish mp3splt would state the reason why it's invalid!  There are no line gaps in my cue sheet though.

---

### Post by logos34 on 2009-04-30
Mine look slightly different:

> REM GENRE Avantgarde
REM DATE 1998
REM DISCID 5310B706
REM COMMENT "ExactAudioCopy v0.95b4"
PERFORMER "RCO, Chailly"
TITLE "Edgard Var&#65533;se: The Complete Works (Disk 1)"
FILE "Varese Complete Works. CD1 - RCO, Chailly.wav" WAVE
  TRACK 01 AUDIO
    TITLE "Tuning Up"
    PERFORMER "RCO, Chailly"
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "Ameriques original version"
    PERFORMER "RCO, Chailly"
    INDEX 00 05:00:12
    INDEX 01 05:06:59
  TRACK 03 AUDIO
    TITLE "Poeme Electronique"
    PERFORMER "Edgard Var&#65533;se"
    INDEX 00 29:44:20
    INDEX 01 29:54:39

...



Or
> 
REM GENRE Classical
REM DATE 2008
REM DISCID A311F40A
REM COMMENT "ExactAudioCopy v0.99pb4"
PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
TITLE "CD1 - Turangal&#65533;la Symphonie"
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\01 - Turangalila-Symphonie -I- Introduction.wav" WAVE
  TRACK 01 AUDIO
    TITLE "Turangalila-Symphonie -I- Introduction"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    PREGAP 00:00:32
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "Turangalila-Symphonie -II- Chant d'amour 1"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 06:19:63
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\02 - Turangalila-Symphonie -II- Chant d'amour 1.wav" WAVE
    INDEX 01 00:00:00
  TRACK 03 AUDIO
    TITLE "Turangalila-Symphonie -III- Turangal&#65533;la 1"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 07:58:50
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\03 - Turangalila-Symphonie -III- Turangal&#65533;la 1.wav" WAVE
    INDEX 01 00:00:00
  TRACK 04 AUDIO
    TITLE "Turangalila-Symphonie -IV- Chant d'amour 2"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 05:56:00
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\04 - Turangalila-Symphonie -IV- Chant d'amour 2.wav" WAVE
    INDEX 01 00:00:00
  TRACK 05 AUDIO
    TITLE "Turangalila-Symphonie -V- Joie du sang des &#65533;toiles"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 11:11:00
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\05 - Turangalila-Symphonie -V- Joie du sang des &#65533;toiles.wav" WAVE
    INDEX 01 00:00:00
  TRACK 06 AUDIO
    TITLE "Turangalila-Symphonie -VI- Jardin du sommeil d'amour"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 06:18:38
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\06 - Turangalila-Symphonie -VI- Jardin du sommeil d'amour.wav" WAVE
    INDEX 01 00:00:00
  TRACK 07 AUDIO
    TITLE "Turangalila-Symphonie -VII- Turangal&#65533;la 2"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 11:40:25
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\07 - Turangalila-Symphonie -VII- Turangal&#65533;la 2.wav" WAVE
    INDEX 01 00:00:00
  TRACK 08 AUDIO
    TITLE "Turangalila-Symphonie -VIII- D&#65533;veloppement de l'amour"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 03:44:50
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\08 - Turangalila-Symphonie -VIII- D&#65533;veloppement de l'amour.wav" WAVE
    INDEX 01 00:00:00
  TRACK 09 AUDIO
    TITLE "Turangalila-Symphonie -IX- Turangal&#65533;la 3"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 10:43:25
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\09 - Turangalila-Symphonie -IX- Turangal&#65533;la 3.wav" WAVE
    INDEX 01 00:00:00
  TRACK 10 AUDIO
    TITLE "Turangalila-Symphonie -X- Finale"
    PERFORMER " Messiaen - Orchestral & Chamber Works; Song Cycles"
    INDEX 00 05:17:25
FILE " Messiaen - Orchestral & Chamber Works; Song Cycles - CD1 - Turangal&#65533;la Symphonie\10 - Turangalila-Symphonie -X- Finale.wav" WAVE
    INDEX 01 00:00:00

---

### Post by optimix on 2009-05-02
Some critical bugs have been fixed with CUE files in the version released today.
Please try libmp3splt 0.5.5 & mp3splt 0.5.4 :
[http://mp3splt.sourceforge.net/mp3splt_page/downloads.php](http://mp3splt.sourceforge.net/mp3splt_page/downloads.php)

---

### Post by ukblacknight on 2009-05-02
Cheers optimix, the upgrade fixed it!

---

