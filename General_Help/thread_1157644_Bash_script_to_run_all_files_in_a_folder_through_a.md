---
title: "Bash script to run all files in a folder through a command"
date: 2009-05-12
forum: General Help
---

### Post by SentientFluid on 2009-05-12
I know very little about shell scripting so I'm looking for some help finding information on how to write a shell script that will run a HandBrakeCLI command on all the files in a folder.  I've used the HandBrake GUI to create a preset so their is less chance of me making an error when I type out the command.

When first run, I would like to be prompted for the path (not the fileame) to the output file and I would like the filename to match the original filename.

I've got all but the barest start of a script:
```
#! /bin/sh

HandBrakeCLI -i /path/to/inputfile -o /path/to/outputfile --preset="My Preset"
```

I know, not really much at all so far. :(

Can anyone point me to where I can find out how to process all the files in a directory and how to get the script to prompt me once for the output path?

---

### Post by KyleBrandt on 2009-05-13
Hints:
Within bash, 'help read' and 'help for'.

Basically you will want to get ask for the output folder, and put that into a variable like folder.  Then a for loop like ```
for i in *; do ... -o "${folder}/${i}"
```

Any more would be spoon feeding, and this is such a common place thing you should take the time to learn it I think.  Take a look at [http://wooledge.org:8000/BashGuide](http://wooledge.org:8000/BashGuide)

-Kyle

---

### Post by SentientFluid on 2009-05-21
Thanks Kyle!

So this what I've come up with, any critiques/suggestions?

```
#!/bin/bash

tmpifs=$IFS
IFS="
"

SRCFLDR=
DESTFLDR=

read -p "Where are the original files? " SRCFLDR
read -p "Where are we saving the new files? " DESTFLDR

cd "$SRCFLDR"
echo "Converting files from $SRCFLDR and saving to $DESTFLDR"
echo

for file in `ls --format=single-column *`; do
    if [ ! -d file ]
        then HandBrakeCLI -v --input "$SRCFLDR/$file" --output "$DESTFLDR/$file" --preset="mypreset"
    fi
done

IFS=$tmpifs
```

Is there a better method than using *`ls --format=single-column *`* to grab the filenames from the folder?

Also, some of the folders also have sub-folders in them so I wanted to only run the command on the files.  *[ -f file ]* kept giving false for the files but testing for "not a directory" seems to work.  Is there a way to test just for video files (miscellaneous extensions ie .avi, .mov, .mpg, etc)?  Some folders have text and other files in them and if possible I'd like to avoid running the command on them.

Any suggestions on cleaning it up or error trapping?

---

### Post by KyleBrandt on 2009-05-21
Doing a for loop over command substation with ls is bad idea.  The shell splits its arguments based on IFS , so any file name with spaces, tabs, or newlines will be interpreted as being multiple files.  So, it should just be ```
for file in /home/foo/*; do ...
```
Also, for this same reason, it is a good practice to put your variables in double quotes (which you did do): ```
"$file"
```

You don't need to declare the variables before:
```
SRCFLDR=
DESTFLDR=
```

Lastly, I don't really think setting IFS is probably needed, but I guess some people recommend it...

-Kyle

---

### Post by SentientFluid on 2009-05-21
Thanks again, Kyle.

```
for file in "$SRCFLDR"; do
``` So this should work fine to replace the command substitution?  By the way, setting IFS was supposed to work around the spaces in filenames, etc but I couldn't get it to work right abd forgot to remove it.  Formatting ls to list in single-column worked though. :)

I originally declared the variables with the intent of setting a couple of folders as defaults but couldn't get it to work.  Thinking of it at work just now, though, I suppose testing to see if either variable is returned empty and then setting it to a default location if it is empty would be the way to go.  Would this work:

```
if [ "$SRCFLDR" = ""]
then SRCFLDR=/default/path
```

And is there a way I could test for video files to avoid running handbrake on text and other files?

---

### Post by geirha on 2009-05-21
> **SentientFluid said:**
> Thanks again, Kyle.

```
for file in "$SRCFLDR"; do
``` So this should work fine to replace the command substitution?

That will only loop once, and with file being $SRCFLDR. Either change to $SRCFLDR, then loop through *
```
cd "$SRCFLDR"
for file in *; do

```
or loop through "$SRCFLDR"/*
```
for file in "$SRCFLDR"/*
```

It's important that the * is not inside quotes, because if it is inside quotes, it becomes a literal asterisk. Try the following in a terminal to see the differences: (set SRCFLDR to an actual path)
```

SRCFLDR="/path/to/src"
echo "$SRCFLDR/*"
echo "$SRCFLDR"/*
cd "$SRCFLDR"
echo "*"
echo *

```

> **SentientFluid said:**
> 
```
if [ "$SRCFLDR" = ""]
then SRCFLDR=/default/path
```


Make sure you have a space after [ and before ]
```
if [ "$SRCFLDR" = "" ]
# Alternatively
if [ -z "$SRCFLDR" ]   # if variable is empty or unset

```
> **SentientFluid said:**
> 
And is there a way I could test for video files to avoid running handbrake on text and other files?

If they are all .avi for instance, you can do 
```
for file in "$SRCFLDR"/*.avi; do
```
If they are of random extensions, you can use the file command to figure out what type of file they are. The file command reads a few bytes of the file looking for known patterns.

```
for file in "$SRCFLDR"/*; do
  case `file -bi "$file"` in
    video/*)  # If it starts with video/, it's a video file
      do_something_with "$file"
      do_some_more
      ;;
    audio/*)
      do_some_audio_stuff "$file"
      ;;
    *) # Anything else
      continue   # go to the start of the for-loop and try the next $file
      ;;
  esac   # case backwards ends the case block
done

```

---

### Post by SentientFluid on 2009-05-23
Thanks gheira!

Here's what I have now:
```
#!/bin/bash

dfltSRC="$PWD"		# make current working directory the default source folder
dfltDEST="$HOME"	# make user's home folder default destination

read -p "Where are the original files? (default: $dfltSRC) " SRCFLDR

if [ -z "$SRCFLDR" ] # a source path is not entered
	then		# assume script is run in folder with files to convert
		SRCFLDR="$dfltSRC"
		echo "Using $SRCFLDR as source"
		echo
fi

read -p "Where are we saving the new files? (default: $dfltDEST) " DESTFLDR

if [ -z "$DESTFLDR" ] # a destination path is not entered
then		# save files to users home folder
	DESTFLDR="$dfltDEST"
	echo "Saving to $DESTFLDR"
	echo
fi

echo "Converting files in $SRCFLDR and saving to $DESTFLDR"

cd "$SRCFLDR"
for file in *; do
	case `file -bi "$file"` in
		video/*)  # Convert video files
			echo "Starting $file"; echo
	      	HandBrakeCLI --input "$SRCFLDR/$file" --output "$DESTFLDR/$file" --preset="iPod"
	      ;;
		audio/*)  # Convert audio files
			# possibly add an audio conversion option later
			echo "$file is an audio file. Audio conversion not implemented yet."
	      ;;
		*) # Anything else
			echo "$file can't be converted with this script"
			continue   # go to the start of the for-loop and try the next $file
		;;
	esac
done

clear
echo "Finished processing $SRCFLDR"
cd "$DESTFLDR"
echo "All files can be found in $DESTFLDR"
echo "Type ls to list the new files."
echo
echo
```

Would this be a good way to prompt to continue...

```
echo "Converting files in $SRCFLDR and saving to $DESTFLDR"
echo
read -n 1 -p "Press Y to accept or N to quit without converting: " CNFRM

if $CNFRM = "n"
	then exit 0
fi
```

That would only work for a lowercase n though, wouldn't it?

---

### Post by geirha on 2009-05-23
> **SentientFluid said:**
> Thanks gheira!

Here's what I have now:

Looks good!

> **SentientFluid said:**
> 
Would this be a good way to prompt to continue...

```
echo "Converting files in $SRCFLDR and saving to $DESTFLDR"
echo
read -n 1 -p "Press Y to accept or N to quit without converting: " CNFRM

if $CNFRM = "n"
	then exit 0
fi
```

That would only work for a lowercase n though, wouldn't it?

You forgot the [ ]: ```
if [ "$CNFRM" = "n" ]
``` But otherwise, yes, it would only match lowercase. With case you can easily check for both though.
```

case "$CNFRM" in
  y|Y) echo "answered yes" ;;
    *) echo "not y or Y, assuming the answer is no" ;;
esac

```

---

### Post by SentientFluid on 2009-05-23
```
case "$CNFRM" in
  y|Y)  # insert my "for file in *; do" loop here
  ;;
  *) echo "Script canceled by user."
     echo
     exit 0
  ;;
esac
```

So this would run the for loop to check and convert the files if y or Y are pressed but would exit the script if any other key is pressed.  Is there a way to point to the for loop if Y is pressed instead of moving the appropriate code into this case block?

---

### Post by geirha on 2009-05-23
When it reaches the y|Y part, and $CNFRM is indeed y or Y, then it will execute everything between y|Y) and ;;, and then exit the case block, so just put the for-loop after it. 

```

case "$CNFRM" in
  y|Y) ;;
    *) exit 0 ;;
esac

cd "$SRCFLDR"
for file in *; do
  ...

```

---

### Post by SentientFluid on 2009-05-24
Ahhh.. that's perfect! Thanks again!

---

### Post by SentientFluid on 2009-05-25
One last thing... how can I strip off the extension from $file before I pass it on to HandBrakeCLI?

---

### Post by geirha on 2009-05-25
With parameter substitution [http://tldp.org/LDP/abs/html/parameter-substitution.html](http://tldp.org/LDP/abs/html/parameter-substitution.html)
```
"${file%.*}"
```

---

