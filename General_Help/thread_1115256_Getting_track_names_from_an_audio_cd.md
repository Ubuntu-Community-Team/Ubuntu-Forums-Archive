---
title: "Getting track names from an audio cd"
date: 2009-04-03
forum: General Help
---

### Post by spibou on 2009-04-03
When I use cdda2wav or cdparanoia to list the contents of an audio cd I get a list of track numbers and duration of each track but I do not get track and artist names although if I use sound-juicer with the same cd it presents on screen the names of the tracks. So I'm looking for a command line utility which will print not only the duration of each track but also its name if it's available on the disk. Also one which will allow me to create a copy of the cd including the track and artist names.

---

### Post by logos34 on 2009-04-03
try [ABCDE]("https://help.ubuntu.com/community/CDRipping#ABCDE")

- Track info only:

> abcde -a cddb

- Make bit-for-bit lossless (FLAC) copy of CD + CUE sheet:
> 
abcde Alternatively, abcde can also grab a CD and turn it into a single FLAC file with an embedded cuesheet which can be user later on as a source for other formats, and will be treated as if it was the original CD. In a way, abcde can take a compressed backup of your CD collection.

Options

-1

Encode the whole CD in a single file. The resulting file uses the CD title for tagging. If the resulting format is a flac file with an embedded cuesheet, the file can be used as a source for creating other formats. Use "-1 -M -o flac" for obtaining such a file.

If you want to burn an exact copy to CD, simply open the .cue sheet in an app like K3b

---

### Post by logos34 on 2009-04-04
on second thought, abcde cddb lookup doesn't printout track times.

i.e.:

> $ abcde -a cddb
Getting CD track info... Querying the CD for audio tracks...
Grabbing entire CD - tracks: 01 02 03 04 05 06 07 08 09 10 11 12
Checking CDDB server status...
Querying the CDDB server...
Obtaining CDDB results...
Retrieving multiple matches... done.
Which entry would you like abcde to use (0 for none)? [0-3]: 2
Selected: #2 (Daft Punk / Alive 2007)
---- Daft Punk / Alive 2007 ----
Year: 2007
Genre: Electronic
1: Robot Rock / Oh Yeah
2: Touch It / Technologic
3: Television Rules The Nation / Crescendolls
4: Too Long / Steam Machine
5: Around The World / Harder Better Faster Stronger
6: Burnin' / Too Long
7: Face To Face / Short Circuit
8: One More Time / Aerodynamic
9: Aerodynamic Beats / Forget About The World
10: Prime Time Of Your Life / Brainwasher / Rollin' And Scratchin' / Alive
11: Da Funk / Daftendirekt
12: Superheroes / Human After All / Rock'n Roll


You might try **[COLOR="Red"]Ripit[/COLOR]**

> RipIT is used to create MPEG-1 Layer 3 (mp3) using Lame, or uses Flac (flac), Ogg Vorbis (ogg) or Faac (m4a) to convert audio files (wav) extracted from an audio CD. It is a console based front-end (no fancy GUI here), written in Perl, for these excellent programs (which must be installed -- at least one from each category!):

        * dagrab, cdparanoia or cdda2wav (tosha and cdd are also supported) for ripping the audio CD tracks (I don't know if dagrab is still up to date, but it works!)
        * Lame, OggVorbis, Flac or Faac for encoding the wav files to mp3, ogg, flac or m4a (find some info and links)
        * CDDB_get 2.25 or higher, a Perl module for CDDB retrieval (info and links).

The program will do the following without user intervention:

  [COLOR="Red"]# gets the Audio CD Album/Artist/Tracks information from CDDB[/COLOR]
  # rips the Audio CD Tracks
  # encodes to flac, mp3 or ogg
  # id3 tags encoded songs
  # [COLOR="Red"]Creates an playlist (m3u) file
  # Can generate a toc (cue) sheet for nice DAO burning[/COLOR]
  # Can prepare and send a CDDB submission and save it locally
  # Can extract hidden songs and split ghost songs
  # May create md5sum files for all tracks
  # Run several encoder processes at the same time and same run

Example:

> 
**$ ripit**

RipIT version 3.6.0.



system: lame --version > /dev/null 2> /dev/null

Will create a cd.toc file.
Will create a playlist file.

Checking for a DB entry @ freedb.freedb.org...
This CD could be:

1: Daft Punk / Alive 2007
2: Daft Punk / Alive 2007
3: Daft Punk / Alive 2007

0: none of the above

Choose: 1
system: lame --genre-list | grep -i "Euro House" > /dev/null 

Genre Euro House is not ID3v2 compliant!
Use "lame --genre-list" to get a list!

Please enter a valid CDDB genre (or none): 124
system: lame --genre-list | grep -i "124" > /dev/null 


-----------------
CDDB and tag Info
-----------------
Artist: Daft Punk
Album: Alive 2007
Category: data
ID3-Genre: none
Year: 2007
Revision: 7
CD id: 8b11590c

01: [06:27.38] Daft Punk / Robot Rock / Oh Yeah
02: [05:29.49] Daft Punk / Touch It / Technologic
03: [04:50.63] Daft Punk / Television Rules The Nation / Crescendolls
04: [07:01.45] Daft Punk / Too Long / Steam Machine
05: [05:42.47] Daft Punk / Around The World / Harder Better Faster Stronger
06: [07:11.38] Daft Punk / Burnin' / Too Long
07: [04:55.17] Daft Punk / Face To Face / Short Circuit
08: [06:10.40] Daft Punk / One More Time / Aerodynamic
09: [03:31.57] Daft Punk / Aerodynamic Beats / Forget About The World
10: [10:22.36] Daft Punk / Prime Time Of Your Life / Brainwasher / Rollin' And Scratchin' / Alive
11: [06:36.73] Daft Punk / Da Funk / Daftendirekt
12: [05:41.08] Daft Punk / Superheroes / Human After All / Rock'n Roll



Do you want to edit or submit the CDDB entry?
To confirm each question type Enter!

1: Yes, and I know about the naming-rules of freedb.org!


---

### Post by spibou on 2009-04-25
> **logos34 said:**
> on second thought, abcde cddb lookup doesn't printout track times.
<S N I P>
You might try **[COLOR="Red"]Ripit[/COLOR]**

Ripit seems a bit too "heavy" for my needs. Combining abcde and cdparanoia I get all the information I want so I'll probably write a wrapper script which runs the two utilities and prints all I want.

Thanks for the suggestions.

---

### Post by logos34 on 2009-04-25
ok, good luck

feel free to share that script, because there are probably a few others beside myself who would be interested.

---

