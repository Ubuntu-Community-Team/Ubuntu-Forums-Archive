---
title: "What player or converter do I use to play/convert a 'bin' and 'cue' video file?"
date: 2012-01-06
forum: Desktop Environments
---

### Post by rocksockdoc on 2012-01-06
What player plays 'bin' and 'cue' video files on Ubuntu?

If none, what is the best way to convert a bin & cue set of files to something playable (e.g., avi or mp4)?

---

### Post by cybergalvez on 2012-01-06
> **rocksockdoc said:**
> What player plays 'bin' and 'cue' video files on Ubuntu?

If none, what is the best way to convert a bin & cue set of files to something playable (e.g., avi or mp4)?

I thought bin/que was a cdrom format

---

### Post by rocksockdoc on 2012-01-07
> **cybergalvez said:**
> I thought bin/que was a cdrom format

Oh. I did not realize that. I thought 'iso' was a CDROM format. To play an 'iso', I would have to mount it first.

If 'bin' and 'cue' are CDROM formats, then I've been googling for the wrong keywords. I'll google for how to 'mount' (rather than 'play') bin/cue files and let you know the results.

---

### Post by rocksockdoc on 2012-01-07
> **TeoBigusGeekus said:**
>  the bin file is not an executable but a disc image...
Ubuntu can't mount bin files, but it can mount iso files.
Have a look at [bchunk]("http://www.howtodothings.com/computers-internet/how-to-convert-cue-bin-nrg-img-mdf-files-to-iso-files-on-ubuntu-linux") for converting the bin/cue files to an iso image.
Then the easiest way to mount it, is to install gmountiso (it must be in the software center).

It looks like 'bchunk' will convert bin/cue to iso/cdr format.

So then I would just need mount iso files instead of bin/cue files.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210385&stc=1&d=1325926897[/IMG]

---

### Post by rocksockdoc on 2012-01-07
It looks like Furius will mount bin/cue files (in addition to iso files) so I'll try that and report back.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210386&stc=1&d=1325927142[/IMG]

---

### Post by rocksockdoc on 2012-01-07
Now that I know I need to MOUNT the bin/cue files, I have better search terms.

For example, these should tell me how to mount bin/cue files:

[LIST]
[*][COLOR=#980101]**[ubuntu]**[/COLOR]                          [iso,bin cue and other files mounting software, wayne1980]("http://ubuntuforums.org/showthread.php?t=1753758&highlight=mount+bin+cue")
[*][COLOR=#980101]**[ubuntu]**[/COLOR]                          [mount .bin file directly?]("http://ubuntuforums.org/showthread.php?t=1720920&highlight=mount+bin+cue"), jiapei100
[/LIST]
And, these should show me how to convert the bin/cue to iso files:

[LIST]
[*][COLOR=#980101]**[ubuntu]**[/COLOR]                          [need help converting .ISO to .BIN/.CUE]("http://ubuntuforums.org/showthread.php?t=1630042&highlight=mount+bin+cue"), branscombe_richmond
[*][COLOR=#980101]**[ubuntu]**[/COLOR]                          [.cue + .bin  ->  .iso or avi]("http://ubuntuforums.org/showthread.php?t=1691599&highlight=mount+bin+cue"), Acheron3
[/LIST]
And, interestingly, this shows other people are as confused as I was:

[LIST]
[*][SOLVED]                          [How to play .bin/.cue movies]("http://ubuntuforums.org/showthread.php?t=1369981&highlight=mount+bin+cue"), Mr Nemo
[/LIST]
Gimme a few minutes to check these out ...

---

### Post by rocksockdoc on 2012-01-07
One approach, apparently, is to convert the bin/cue files to iso & then either mount the iso or load it directly with VLC player according to this post:

> **lykeion said:**
> You can use *bchunk* command to convert bin/cue to iso
Open a terminal and install it with:
```
sudo apt-get install bchunk
```...
To convert to iso:
```
bchunk "cd 1.bin" "cd 1.cue" "cd 1"
```You should be able to  open the resulting "cd 1.iso" with VLC directly (VLC > Media >  Open File)

This seems like the basic approach most seem to use:
> **gsmanners said:**
> A "cue" file stores the layout of a CD and the  "bin" file stores the data. That is to say, it is the container for your  movie's container.

This will convert the bin/cue files to iso:

```
bchunk movie.bin movie.cue movie
```At this point you can use  something like isomaster to extract the actual movie files.

Incidentally, many said you can play bin/cue files with VLC but I was unable to do so:
> **handy said:**
> I can play .bin/.cue movies with vlc.

You just choose the .bin file & away it goes. 

Of course, there is confusion whether VLC plays the bin or the cue ... 

> **lykeion said:**
> ... VLC should be able to play SVCD cue/bin directly. Just make sure you **select the cue file** (not the bin file), see: [http://www.afterdawn.com/guides/archive/how_to_play_bin___cue_files.cfm](http://www.afterdawn.com/guides/archive/how_to_play_bin___cue_files.cfm)

But, for me, VLC played neither.

---

### Post by rocksockdoc on 2012-01-07
I used bchunk as shown above to convert the bin/cue to iso and I was surprised how quickly that ran (just a couple of minutes).

Now I have three files:

[LIST=1]
[*]Movie.bin
[*]Movie.cue
[*]Movie.iso
[/LIST]
I was able to mount the iso using Gmount-iso (after creating an empty directory mount point). This created a round disc image that I could doubleclick on to open and browse. 

And I was able to mount the bin file using Furius ISO mount tool. This created a square disk images that I could doubleclick on to open & browse.

Both worked just fine.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210388&stc=1&d=1325930288[/IMG]

---

### Post by rocksockdoc on 2012-01-07
I'm going to mark this solved since I can now mount the bin/cue files and/or convert the bin/cue files to an iso image (which I can also mount).

Looking at the threads I referenced prior, I'll also update the relevant ones ... especially since multiple people asked the same question I asked and none of them came up with the simplest idea of all - which was to use Furius to mount the bin/cue files.

Thanks for pointing me in the right direction!

I hope this thread serves as a reference for the next person who runs into a bin/cue file and needs to figure out what to do with it to access the data inside.

---

### Post by rocksockdoc on 2012-01-10
I'm liking Furius over the other bin-mounting tools.

Yesterday it mounted an ISO file and today it mounted an IMG file:
- [**How to mount a video *.img file in Ubuntu so that you can use it**]("http://ubuntuforums.org/showthread.php?t=1907182")

So, Furius ISO mount tool version 0.11.1.2 is now my favorite bin/img/iso mounter!

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=210605&stc=1&d=1326249078[/IMG]

---

