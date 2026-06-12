---
title: "Can't convert flv to avi or anything else."
date: 2008-12-16
forum: General Help
---

### Post by miked860 on 2008-12-16
I download YouTube videos regularly and have tried  a few programs to download then convert the videos to avi/mp4/mp3. avi and mp4 will not work because of some ffmpeg error.

FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from 'People = **** - Slipknot lyrics.flv':
  Duration: 00:03:35.3, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240 [PAR 0:1 DAR 0:1], 25.00 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Output #0, avi, to 'People = **** - Slipknot lyrics.avi':
    Stream #0.0: Video: 0x0000, yuv420p, 320x240 [PAR 0:1 DAR 0:1], q=2-31, 200 kb/s, 25.00 tb(c)
    Stream #0.1: Audio: mp2, 22050 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.0

Any help would be appreciated.

---

### Post by anjilslaire on 2008-12-16
> 
Unsupported codec for output stream #0.0


Do you have all of the needed codecs installed? Also, try avidemux from the repositories.

---

### Post by Jose Catre-Vandis on 2008-12-16
try
```
sudo apt-get install ubuntu-restricted-extras ffmpeg
```
then
```
ffmpeg -i original_file.flv new_file.mpg
```

---

### Post by miked860 on 2008-12-16
> **Jose Catre-Vandis said:**
> try
```
sudo apt-get install ubuntu-restricted-extras ffmpeg
```
then
```
ffmpeg -i original_file.flv new_file.mpg
```

That worked. Thank you very much!

---

### Post by FakeOutdoorsman on 2008-12-16
You could have also tried:
```
sudo apt-get install libavcodec-unstripped-51
```
and skipped all of the other ubuntu-restricted-extras fluff.

---

### Post by thestig_992 on 2008-12-16
You might also like a script that converts files easily, without any terminal use. Got it from a member of this forum...

```
#!/bin/bash

# Separate list with newline rather than spaces
IFSBAK=$IFS
IFS=$'\n'

EXTENSION=`zenity --entry --title="Convert Script" --text="What file type do you want to convert to?"`

for NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    # If a file
    if [ -f "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
        # Get file name minus extension
        FILEBASENAME=`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | awk -F . '{print $1}'`
        # Convert file
        mplayer -dumpaudio "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" \
            -dumpfile "$FILEBASENAME.$EXTENSION"
    #
    # If a directory
    elif [ -d "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
        for FILE in `ls "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`; do
            FILEBASENAME=`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS/$FILE"|awk -F . '{print $1}'`
            mplayer -dumpaudio "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS/$FILE" \
                -dumpfile "$FILEBASENAME.$EXTENSION"
        done
    fi
done

IFS=$IFSBAK

```

---

### Post by Jose Catre-Vandis on 2008-12-20
> **miked860 said:**
> That worked. Thank you very much!

Please mark as solved :)

---

