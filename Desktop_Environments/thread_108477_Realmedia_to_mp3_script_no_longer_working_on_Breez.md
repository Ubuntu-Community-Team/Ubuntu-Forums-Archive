---
title: "Realmedia to mp3 script no longer working on Breezy"
date: 2005-12-26
forum: Desktop Environments
---

### Post by Dafydd on 2005-12-26
Hello,
I upgraded to Breezy and now a script I used to convert realmedia to mp3 does not work. I used it everyday to listen to my favorite radio programs on my mp3. Does anyone know what to do? Here's the script. The thing just dies now after opening up a terminal. Or does someone know an easier way to convert to mp3?

Thanks
Dafydd
----------- SCRIPT -----------------------

#!/bin/bash
# transcodes realmedia (RM) audiofiles to MP3 audio files.
# Version 0.1
# Author: Arjen
# Usage: rm2mp3 <input-dir>

### Configuration

#This is where the temporary wav files will be stored
TMPDIR="/tmp"

#This is where the MP3 files will end up
OUTPUTDIR="/media/usbdisk"

#Path to mplayer binary. Don't change unless you know what you're doing.
MPLAYER="/usr/bin/mplayer"

#Path to lame binary. Don't change unless you know what you're doing.
LAME="/usr/bin/lame"

#Options for rm to wav decoding
MPLAYER_OPTS="-ao pcm -aofile"

#Options for lame encoding
LAME_OPTS="-f"

#Define working directory
WORK="$TMPDIR/rm2mp3.$$"

#Define working name for tracks
WAV="$WORK/track.wav"

### End configuration

# Get absolute directory paths
INPUTDIR="$1" #you can change this to an absolute path
cd "$INPUTDIR"
INPUTDIR="$PWD"

# Setup work directory, clean and create
rm -rf "$WORK"
if [ -e "$wORK" ]; then
	echo "Couldn't delete $WORK"
	exit 1
fi
mkdir "$WORK"
	if [ ! -d "$WORK" ]; then
	echo "Couldn't create $WORK"
	exit 1
fi

# Transcode the files
cd "$INPUTDIR"
OLDIFS="$IFS"
IFS=$'\n'
for filepath in $(find . -type f -name '*.rm' -print \
	| sort | sed -e 's/^\.\///' -e 's/\.rm$//'); do
	IFS="$OLDIFS"
	filedir="$(dirname "$filepath")"
	filename="$(basename "$filepath")"
	if [ ! -d "$OUTPUTDIR/$filedir" ]; then
		mkdir -p "$OUTPUTDIR/$filedir"
	fi
	if [ ! -f "$OUTPUTDIR/$filepath.mp3" ]; then
		#Create wav file
		$MPLAYER "$INPUTDIR/$filepath.rm" $MPLAYER_OPTS "$WAV"

		# Encode MP3
		$LAME $LAME_OPTS "$WAV" "$OUTPUTDIR/$filepath.mp3"
	fi
done

# Clean up
rm -rf "$WORK"
exit

---

### Post by adamkane on 2006-04-08
I tested the script with:

```

mplayer filename.rm -ao pcm -aofile track.wav

``` 
I got this message:

> 
-aofile is deprecated. Use -ao pcm:file=<filename> instead.
 
So I tried this, and it worked:

```

mplayer filename.rm -ao pcm:file=track.wav

``` 
So the following lines need to be changed from:

```

MPLAYER_OPTS="-ao pcm -aofile"
$MPLAYER "$INPUTDIR/$filepath.rm" $MPLAYER_OPTS "$WAV"

``` 
to:

```

MPLAYER_OPTS="-ao pcm:file="
$MPLAYER "$INPUTDIR/$filepath.rm" $MPLAYER_OPTS${WAV}

```

I'm going

---

