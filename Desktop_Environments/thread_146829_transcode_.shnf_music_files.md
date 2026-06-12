---
title: "transcode .shnf music files?"
date: 2006-03-19
forum: Desktop Environments
---

### Post by bionnaki on 2006-03-19
how can play or encode .shnf/.shn (shorten) music files?

[http://userpages.umbc.edu/~hamilton/shnfaq.html](http://userpages.umbc.edu/~hamilton/shnfaq.html)

---

### Post by bionnaki on 2006-03-19
I have shntool installed but I'm not quite sure how to use it... any ideas?

---

### Post by RAOF on 2006-03-19
You should be able to **play** (and transcode from) shorten files using gstreamer.  You'll need the gstreamer-ffmpeg packages - check out the wiki: [wiki.ubuntu.com/RestrictedFormats](wiki.ubuntu.com/RestrictedFormats).

There doesn't seem to be an encoder (easily) available.

---

### Post by RAOF on 2006-03-19
[QUOTE=bionnaki]I have shntool installed but I'm not quite sure how to use it... any ideas?[/QUOTE]
Have you tried **shntool --help**?

Edit: Looking at the notes for the shntool package, I don't think it does what you hope it does.
I'd recommend encoding to FLAC if you want a lossless audio codec - it's well supported, and compresses about as well as all the other lossless encoders.

---

### Post by bionnaki on 2006-03-19
hmm - I downloaded some live sets from [http://bt.etree.org](http://bt.etree.org)

I dont know why I wrote encode - just want to convert the shorten files to wav.

> bill@ubuntu:~$ shntool -h
Usage: shntool mode ...
       shntool [OPTIONS]

Options:

  -m    shows detailed mode module information
  -f    shows detailed format module information
  -v    shows version information
  -h    shows this help screen

bill@ubuntu:~$ shntool -m
Supported modes:

    len  (displays length, size and properties of PCM WAVE data)
    fix  (fixes sector-boundary problems with CD-quality PCM WAVE data)
    md5  (computes the MD5 fingerprint of PCM WAVE data)
    pad  (pads CD-quality files not aligned on sector boundaries with silence)
   join  (joins PCM WAVE data from multiple files into one)
  split  (splits PCM WAVE data from one file into multiple files)
    cat  (writes PCM WAVE data from one or more files to stdout)
    cmp  (compares PCM WAVE data in two files)
    cue  (generates a CUE sheet or split points from a set of files)
   conv  (converts files from one format to another)
   info  (displays detailed information about PCM WAVE data)
  strip  (strips extra RIFF chunks and/or writes canonical headers)

  For help with any of the above modes, type:

    shntool mode -h

bill@ubuntu:~$ shntool -f
Supported file formats:

    wav  (RIFF WAVE file format)
         + audio format - supports input and output

   aiff  (Audio Interchange File Format (AIFF and uncompressed/sowt AIFF-C only))
         + audio format - supports input and output via 'sox'

    shn  (Shorten low complexity waveform coder)
         + audio compression format - supports input and output via 'shorten'

   flac  (Free Lossless Audio Codec)
         + audio compression format - supports input and output via 'flac'

    ape  (Monkey's Audio Compressor)
         + audio compression format - supports input and output via 'mac'

    ofr  (OptimFROG Lossless WAVE Audio Coder)
         + audio compression format - supports input and output via 'ofr'

   lpac  (LPAC - Lossless Predictive Audio Compression)
         + audio compression format - supports input only via 'lpac'

     wv  (WavPack Hybrid Lossless Audio Compression)
         + audio compression format - supports input via 'wvunpack' and output via 'wavpack'

   cust  (custom output format module)
         + audio format - supports output only

   null  (sends output to /dev/null)
         + audio format - supports output only
bill@ubuntu:~$ shntool -v
shntool 2.0.3
Copyright 2000-2004 Jason Jordan <shnutils@freeshell.org>

shorten utilities pages:

  [http://www.etree.org/shnutils/](http://www.etree.org/shnutils/)
  [http://shnutils.freeshell.org/](http://shnutils.freeshell.org/)

This program comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions.  See the file COPYING for details.

bill@ubuntu:~$



---

### Post by hw-tph on 2006-03-19
> cat (writes PCM WAVE data from one or more files to stdout)

Or, use **shncat**.


Håkan

---

### Post by bionnaki on 2006-03-19
apt-get install shncat does nothing...

---

### Post by RAOF on 2006-03-19
It looks like you're probably after the **conv** mode.  **shntool conv -h** should give help as to how to use that.

Alternatively, you could use the **cat** mode.  Again, **shntool cat -h**, but I would imagine that it would go something like:
**shntool cat *inputfile* > *outputfile.wav***

---

### Post by hw-tph on 2006-03-20
[QUOTE=bionnaki]apt-get install shncat does nothing...[/QUOTE]

**shncat** comes with the shntools package...


Håkan

---

### Post by RAOF on 2006-03-20
Alternatively, if you've got the gstreamer0.8-ffmpeg package installed you can use the magic of gstreamer and run
```
gst-launch-0.8 filesrc location=*/path/to/input* ! decodebin ! wavenc ! filesink location=*/path/to/output*
```

Edit: for bonus marks, transcode the input into flac:
```
gst-launch-0.8 filesrc location=*/path/to/input* ! decodebin ! flacenc quality=8 ! filesink location=*/path/to/output*
```
Transcoding into other formats is left as an exercise for the reader :)

---

