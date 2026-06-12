---
title: "an audio format converter"
date: 2009-01-25
forum: General Help
---

### Post by Dustin2128 on 2009-01-25
what's a good converter that could take WMA files I found on my brothers MP3 player and turn them in to mp3s

---

### Post by mb_webguy on 2009-01-25
You can do it with MPlayer.  If you haven't already, add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and install the extra codecs and mplayer.

Then you can use the following script to convert wma files to mp3s.
```
#!/bin/bash
for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm:waveheader "$i" && lame -m j -h --vbr-new -b 160 audiodump.wav -o "`basename "$i" .wma`.mp3"; done; rm -f audiodump.wav
```

Make a bin directory under your home directory (e.g. "mkdir ~/bin"), and save this script there as something like "wma2mp3", and make sure to chmod the file to make it executable (e.g. "chmod u+x ~/bin/wma2mp3").

Now just navigate in the terminal to a directory where you have a bunch of wma files and enter "wma2mp3", and it will convert all of the wma files in that directory to mp3s.

---

### Post by sefs on 2009-01-25
Also google for WinFF.  It's a gui, and nice.

Tutorial: [http://www.youtube.com/watch?v=mr-QbiZPHU8](http://www.youtube.com/watch?v=mr-QbiZPHU8)

The tutorial is for windows but you can get the download instructions for the deb from [http://winff.org/html/](http://winff.org/html/) as is made for linux as well.

---

### Post by lswb on 2009-01-25
If mb_webguy's script doesn't work you probably need to install the "lame" package  also. (Search & install from synaptic, or from cli "sudo apt-get lame" )

---

