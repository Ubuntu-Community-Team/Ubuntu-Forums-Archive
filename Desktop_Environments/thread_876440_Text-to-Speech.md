---
title: "Text-to-Speech"
date: 2008-07-31
forum: Desktop Environments
---

### Post by notlim_hardy on 2008-07-31
Is there a text-to-speech software for Ubuntu 8.04? I'm using OSS 4 1016 and Gnome. Tankan.

---

### Post by notlim_hardy on 2008-08-02
Anyone?

---

### Post by lswb on 2008-08-02
I believe espeak is installed by default in 8.04, if not it is in the repositories. The festival speech synthesizer was default with earlier versions of ubuntu and is available in the repos. as well.

Just try 

  espeak "hello"

from a terminal to see if it's installed, then man espeak for more info.

---

### Post by everthonvaladao on 2008-08-26
espeak is a really great software, and easier to use than festival or mbrola... I use it with lame to convert my ebooks to mp3, so i can hear them as audiobooks on the school bus... :)

Here is a small script I made to make the process easier:

```

#!/bin/sh
# txt2mp3 - convert text files to mp3 audio files (aka audiobooks)
# v0.1
#
# (c) 2008 Everthon Valadão <everthonvaladao@gmail.com> under the GPL
#          http://www.gnu.org/copyleft/gpl.html
#
# OBS.: install some pre-requisites first, with
#       sudo apt-get install espeak lame xpdf-utils odt2txt antiword

TXT_FILE="$1"
BASENAME=`echo "$TXT_FILE" | sed 's/\(.*\)\(\....$\)/\1/g'`

echo "TTS (text-to-speach) ${TXT_FILE}"

ext=${1##*.}

# if it isn't a TXT file, convert it first
if [ "$ext" != "txt" ] ; then
    TMP_FILE="/tmp/espeakfile-$$.txt"

    # PDF
    if [ "$ext" = "pdf" ] ; then
        echo "converting from PDF to TXT"
        pdftotext "${TXT_FILE}" "${TMP_FILE}"
    fi

    # ODT
    if [ "$ext" = "odt" ] ; then
        echo "converting from ODT to TXT"
        odt2txt --subst=all "${TXT_FILE}" > "${TMP_FILE}"
    fi

    # DOC
    if [ "$ext" = "doc" ] ; then
        echo "converting from DOC to TXT"
        antiword "${TXT_FILE}" > "${TMP_FILE}"
    fi

    TXT_FILE="${TMP_FILE}"
fi

rm -f /tmp/voice.wav

# create a FIFO "named pipe" to save space
mkfifo /tmp/voice.wav

# espeak write output to a pipe while lame encodes the file on the fly
nice espeak -f "${TXT_FILE}" -w /tmp/voice.wav & \
xterm -e nice lame -a --resample 16 -V 9 --vbr-new --lowpass 8 -f /tmp/voice.wav -o "${BASENAME}_VBR.mp3"

echo "...done! Voice saved as ${1}.mp3"

```
source: _[txt2mp3 - Como converter eBooks pra audioBooks]("http://my.opera.com/everthonvaladao/blog/txt2mp3-como-converter-ebooks-pra-audiobooks")_

P.S.: epseak supports a lot of languages other than english, as you can check with `espeak --voices`

P.S.2: se você fala português como eu, pode adicionar um argumento ao espeak para utilizar uma voz na nossa língua pátria:
```

nice espeak -v brazil+f3 -p 25 -f "${TXT_FILE}" -w /tmp/voice.wav & \

```
no início é um pouco esquisito, mas com pouco tempo você se acostuma e passa a entender tudo ^^

---

### Post by RequinB4 on 2008-08-26
Fyi, the program "pdftotext" doesn't have its own package, it's in the package xpdf-utils.

---

### Post by everthonvaladao on 2008-08-27
> **RequinB4 said:**
> Fyi, the program "pdftotext" doesn't have its own package, it's in the package xpdf-utils.

@RequinB4: you're rigth, thanks! (i've updated my post)

---

### Post by RequinB4 on 2008-08-27
Fyi, to anyone who cares, I've changed the pdf section of that script to instaed of using pdftotext use this: [http://ubuntuforums.org/showthread.php?t=882899](http://ubuntuforums.org/showthread.php?t=882899)

Takes longer, but decreases the need for the user to check if there is embedded text in the pdf file (if there is, it should work fine anyway)

---

### Post by go_beep_yourself on 2008-09-26
Anybody have ebooks in chm that they convert to text?

---

### Post by binbash on 2008-09-27
You should try festival with high quality sounds.There is a howto at tutorials section

---

### Post by everthonvaladao on 2008-09-30
I tried festival and mbrola, but they are too much complicated to get work with brazilian portuguese... (and yes, i followed the tutorial)

---

### Post by gardengxc on 2008-11-20
its not designed for Linux, but NaturalReader 7 works under wine and has a free version.
I like it better than orca.

---

### Post by go_beep_yourself on 2008-11-20
I like 2nd Speech Center and Speakonia (free) under wine.

---

