---
title: "Converting everything in the Music folder to mp3"
date: 2009-05-10
forum: General Help
---

### Post by davidism on 2009-05-10
I'm trying to organise all my music, and as part of that I want to convert all of it to a single format.  How can I automatically locate and convert all non-mp3 files?  Either a terminal command or a program is fine.

---

### Post by spiderbatdad on 2009-05-10
ffmpeg works for conversion. There is a script here for mass conversion.
[http://goinggnu.wordpress.com/2007/08/13/mass-conversion-using-ffmpeg/](http://goinggnu.wordpress.com/2007/08/13/mass-conversion-using-ffmpeg/)
You will obviously have to modify the input file type for whatever formats you have, and run the command for each format.

---

### Post by davidism on 2009-05-10
I'll need some more help with this one.  While that code is a good start, how do I modify it to:
a) Find all files that **aren't **mp3 since there are some that are wma, some that are ogg, etc.?
b) Convert sound files, not video files?

---

### Post by spiderbatdad on 2009-05-10
lets say I had a number of .flv file in my home directory I wanted to convert to .mp3 
I create a directory called bin in my home directory. I create a document in there named convert.sh and paste in ```
#!/bin/bash
$IFS=$&#8217;\n&#8217; ;for f in `ls *.flv`; do FILE=$(basename $f .flv) ;ffmpeg -i $FILE.flv -target ntsc-dvd $FILE.mp3; done
```Then open terminal. I need to be in the directory containing the files. So , if they are in Music i run ```
cd Music
convert.sh
```convert.sh needs to be made executable. chmod +x convert.sh or the gui properties>>permissions...allow executing...If I am converting ogg, I need to change each instance of .flv to .ogg in the script.

---

### Post by Yellow Pasque on 2009-05-10
Converting from one lossy format to another will decrease audio quality. Whether this is noticeable/relevant is a matter of personal aural ability and the audio equipment used.

I would recommend keeping copies of the original files for comparison until you listen to the resulting mp3's and make sure they're okay.

---

### Post by mc4man on 2009-05-10
@ davidism
Just as an observation, there are a few things you didn't mention

Do you wish to encode to mp3 using a variable bitrate? (ffmpeg uses cbr

Are your tracks tagged and if so do you want the mp3's to be also?

Is there a directory structure you wish to preserve or you want to just dump them all into one directory?

---

### Post by spiderbatdad on 2009-05-10
As a note, the above script will not overwrite or remove the existing files, only create copies in the new format. Also looking at man ffmpeg will show you how to customise the conversion to suit your needs.

---

