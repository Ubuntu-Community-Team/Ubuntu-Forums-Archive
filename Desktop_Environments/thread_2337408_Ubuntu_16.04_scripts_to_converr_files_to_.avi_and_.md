---
title: "Ubuntu 16.04 scripts to converr files to .avi and delete files"
date: 2016-09-17
forum: Desktop Environments
---

### Post by deepakdeshp on 2016-09-17
Hello,

1.I was trying to create scripts for following ```
[COLOR=#2E8B57][FONT=Monaco]ffmpeg -i myvideo.mp4 -codec: copy myvideo.avi[/FONT][/COLOR]
``` input .mp4 file names should be taken from a text file and the converted video should be saved  with same names as the input file with .avi extension. The above basic command does work.

2. Find 10 biggest file in a directory and interactively delete them. I wasnt able to combine find command with -exec rm -i (find . -type -f  -name ".file-to-delete"  -exec rm {} \;) . 

What I was trying ```
command |(find . -type -f  -name ".file-to-delete"  -exec rm -i {} \;
``` where command finds 10 biggest files. I dont want to delete any directories.

Thank you for your help .

---

### Post by TheFu on 2016-09-17
'-f' isn't correct.

BTW, mp4 and avi are containers, not codec types. When avi files are popular, mpeg4 (divx or xvid) were popular codecs, not h.264 which is probably what would be put inside an mp4 file.

You can't pipe the ffmpeg output into a find in this way. What you need is a loop that 
* takes the inputs - I usually use file globbing as inputs, but the output from a find-cmd can work too.
* swaps the extension
* runs the transcode command ... ffmpeg, avconv, handbrakeCLI, mencoder, whatever
* does whatever checks you feel are needed to ensure the converted file is "reasonable" - not all conversions work
* remove the originally input file.

So ... to give you an idea, here's one of my little scripts ... 
filename: 2mkv-720
```
#!/bin/sh

FF_OPTS="-vcodec libx264 -crf 19 -vf scale=-1:720 -preset veryfast -strict experimental -c:a libvorbis -qscale:a 6"

for filename in "$@"; do

   IN="$filename"
   ROOT=`echo "$filename"| sed -e 's/...$//' `
   OUT="$ROOT.mkv"

   nice ffmpeg -y -i "$IN" $FF_OPTS  "$OUT"

done
```

If you use bash, there is a construct to convert the extensions. I can't assume bash exists always.

Hope that clears things up a little.  As you see, I'm looping over a list of files that are input to my script. Each filename is processed one at a time. My filenames never have spaces or other _funny_ characters. Filenames with spaces require extra work in the scripting, so I don't let that happen.

---

### Post by deepakdeshp on 2016-09-18
Thank you. The find command I was using is for the 2nd problem thatvis find 10 biggest files in the pwd and interactively delete the fikes with rm -i

---

