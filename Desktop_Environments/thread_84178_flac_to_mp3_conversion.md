---
title: "flac to mp3 conversion?"
date: 2005-10-30
forum: Desktop Environments
---

### Post by PaganHippie on 2005-10-30
I'm trying to put music ripped from my CD collection into an iPod Shuffle. Sound Juicer extracts the CD tracks just fine, and saves them in flac format, which sounds great. But, of course, the iPod can't use flac.

I've tried using both lame and Audacity to convert my flacs to mp3s, but to no avail. Can anyone recommend a tool that will do the job? Graphical would be nice, but I'm not afraid of the command line.

Thanks....  :smile:

-----

Figured it out on my own.  Just in case anyone's interested:

```
flac -d -c infile.flac | lame - outfile.mp3
```

---

### Post by patbuntu on 2006-02-01
You could also try etree-scripts from here:

[http://etree-scripts.sourceforge.net/](http://etree-scripts.sourceforge.net/)

Theres a deb file you can download and install with synaptic.

Then just cd to the directory your flacs are in and do:

shn2mp3 .

or 

shn2ogg .

depending on the output format you want.  The scripts handle both shn and flac files, and give you get some output showing you whats going on.  If theres a text file in the directory it will also parse this and tag up your mp3s.  I've no idea what format this text file needs to be in, but a lot of the shows available from etree  have this already.

Description from the package file:
Useful scripts for handling lossless audio files.
Contains a number of handy utility scripts for dealing with
losslessly-compressed audio files (e.g. SHN and FLAC files).  Including:
md5check - recursively check md5sums on a directory tree
shn2mp3 - Convert a directory of SHN/FLAC files to nicely-tagged MP3/OGGs
flacify - Convert a directory of WAV/SHN/FLAC files to tagged FLACs.
unshn - Unpack a group of SHN or FLAC files.
burn-shns - Wrapper for unshn and cdrecord.  Used to un-SHN files and burn.
cdfill - Calculate optimal CD-filling for a set of SHN files and optionally
         rename them with disc and track indicators.
make-toc - Create a cdrdao TOC file from a directory of WAV files.
makehbx - Create a XML file with information about a directory of SHN files.

Hope this helps

-Pat

---

### Post by GrammatonCleric on 2006-02-25
Another way is to...

Install flac lame and id3..

```


sudo apt-get install flac lame id3


``` 

Open your favorite editor create a small shell script with the following in it...

```


for a in *

do
       OUTF=`echo "$a" | sed s/\.flac/.mp3/g`

       ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
       TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
       ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
       GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
       TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`

       flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1  - "$OUTF"
       id3 -t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" "$OUTF"

done


``` 
Save the script to a file (i.e. flac2mp3.sh).

Make the script executable

```


chomd 755 flac2mp3.sh


``` 
Copy the script into the directory of FLAC audio files that you want to convert.

```


cp flac2mp3.sh /some/directory/o/flac/


``` 
Change into that same directory.

```


cd /some/directory/o/flac/


``` 
Now run the script...

```


./flac2mp3.sh


``` 
And watch your flac files be converted to VBR mp3s.

- GC

---

### Post by Sigma on 2006-04-02
Thanks, GrammatonCleric, that was really helpful!

---

