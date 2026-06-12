---
title: "lame wav2mp3 encoding help"
date: 2005-11-06
forum: Desktop Environments
---

### Post by cinematography on 2005-11-06
I have a directory of wav files that I would like to encode into mp3s, and this command doesn't seem to work:

lame -V3 *.wav *.mp3

Does anyone know what the problem could be? Does lame not support batch processing like oggenc? And if it doesn't, is there another good wav to mp3 encoder I could use?

---

### Post by belda on 2007-12-01
bash script?

---

### Post by earlra on 2008-03-21
You need a script to loop through the files in the directory and perform the conversion.

Here is a script that will get the job done (borrowed from [http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux):](http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_aac/mp4_to_wav/mp3/ogg_on_Linux):)

#!/bin/bash 
# 
# wav2mp3
# 
for i in *.wav; do
    #out=$(ls $i | sed -e 's/.wav//g')
    #out=$(echo $i | sed -e 's/.wav$//')
    #lame -h -b 192 "$i" "$out.mp3"
    lame -h -b 192 "$i" "${i%.wav}.mp3"
done

If you need help on running scripts (setting permissions, path, etc.), try: [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

I just did this myself and converted my files successfully.

---

### Post by logos34 on 2008-03-21
It's astonishing that lame doesn't have a command-line option for this, and you have to make a script

---

### Post by logos34 on 2008-03-21
Oh wait--there IS a lame script for batch conversion called **mlame**:).  Just found it. It's included in the lame zip folder download. (> lame-3.97/misc/mlame). Just stick it in /usr/bin, make it executable (mine was already), and call it:

> $ mlame --version

This script runs the LAME mp3 encoder on multiple files: 

    /usr/bin/mlame [options] <file 1> ... <file n>

  options:
    -?                  this help text
    -r                  remove files after encoding
    -f                  force overwrite of destination if exists
    -l                  low quality settings
    -h                  high quality settings
    -o "<lame options>" overrides script default options

  example:
    /usr/bin/mlame  -r  -f  -o "-v -V 0 -b 112" a*.wav z*.aif g*.mp?

Worked great on a few test .wavs:

> $ mlame -o "-v -V 2" *.wav

Learn something new every day!

[http://stommel.tamu.edu/~baum/linux-music.html#makemp3](http://stommel.tamu.edu/~baum/linux-music.html#makemp3)
[http://ubuntuforums.org/showthread.php?t=468548](http://ubuntuforums.org/showthread.php?t=468548)

---

### Post by chochem on 2008-06-16
Yeah, thanks for mlame tip, logos34. I did however find a few annoying things in the script, e.g. the line that gets the source files reads:
```
for src in "$@"; do
```
which means that it won't work recursively (trawl subdirectories and subdirs of subdirs etc. for files). Try substituting this line:
```
find "$@" -type f | while read src; do
```
and you can just point it to the top level directory.

(to substitute: comment out the previous line by adding a '#' in front and copy paste the new one on a line underneath)

---

