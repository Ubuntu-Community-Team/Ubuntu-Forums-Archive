---
title: "Need help with a sed command"
date: 2009-04-30
forum: General Help
---

### Post by detroit/zero on 2009-04-30
I have a script I wrote that creates a list of all videos in a folder and its' subfolders, calls on VLC to play six random videos, and then stops.

I've run into a problem with my list generation. I'm using the find command to make my list so it will include absolute paths to all my videos. The problem is that it's also including the folder names, subfolder names, and any other extra files that may or may not be present anywhere in the main folder.

Here's a sample of how the list looks:```
[COLOR=Blue]Simpsons[/COLOR]
[COLOR=Blue]Simpsons/Simpsons Season 10[/COLOR]
Simpsons/Simpsons Season 10/s10e10 - Viva Ned Flanders.avi
Simpsons/Simpsons Season 10/s10e03 - Bart the Mother.avi
Simpsons/Simpsons Season 10/s10e21 - Monty Can't Buy Me Love.avi
Simpsons/Simpsons Season 10/s10e01 - Lard of the Dance.avi
Simpsons/Simpsons Season 10/s10e11 - Wild Barts Can't Be Broken.avi
**[...]**
[COLOR=Red]Simpsons/episodes.txt[/COLOR]
[COLOR=Red]Simpsons/RandomVLC.bash[/COLOR]
Simpsons/The.Simpsons.S20E17.PROPER.HDTV.XviD-NoTV.avi
[COLOR=Blue]Simpsons/Simpsons Season 18[/COLOR]
Simpsons/Simpsons Season 18/The Simpsons [18x15] Rome-Old And Juli-Eh.avi
Simpsons/Simpsons Season 18/The Simpsons [18x01] The Mook, the Chef, the Wife, and Her Homer.avi
Simpsons/Simpsons Season 18/The Simpsons [18x18] The Boys Of Bummer.avi
**[...]**
[COLOR=Red]Simpsons/RandomVLC.bash~[/COLOR]
Simpsons/The.Simpsons.S20E16.HDTV.XviD-0TV.avi

```The blue items are the folder/subfolder names. The red items are examples of other files that also live in these folders - the list and the script itself (along with any backup files).

I'm pretty sure piping to *sed* before the list is written is the way to go to trim these kinds of things from this list, but since each filename includes the things I want cut from the list, I can't figure out how to structure the *sed* command.

I did have some luck piping to *grep*, and selecting only .avi files to be written, but not all my videos are .avi files - some are .flv, some .mpg, etc..

Having those extra lines in the list is causing some playback errors when I run this script. How can I use *sed* (or *grep*) to keep those items out of my playlist?

Here's a cat of the script itself. I know it's kind of messy, and I'm sure there's a better way to do some of the things I did, but hey - It's the first script I ever wrote - cut a guy some slack.

Thanks for any help.
```
#!/bin/bash
#
# Creates a list of all files in all Simpsons folders and then
# plays six random episodes with VLC Media Player.
# Created by Uncertain

# Filenames and paths.
path1=/media/disk/J/Videos
path2=/home/zero/Videos/Simpsons
list=/home/zero/Videos/episodes.txt
# Set the number of episodes to play.
repeat=6
cycles=0
while  [ $cycles -ne $repeat ]
 do
  echo $cycles
  cycles=$(( $cycles + 1 ))
# Check for the list. If it's in ~/Videos, fine.
# If it doesn't exist, create it in ~/Videos.
if [ -f $path1/vids ]
 then
  echo "Episodes list found in Videos folder!"
   else
    echo "Episodes list not found in Videos folder. Creating list..." && cd $path1 && find Simpsons > $list
fi
# Echo the filename of the list, just because.
echo "Done. Filename is:" 
echo $list
# Read the list, select one random line.
LowerBound=1
RandomMax=32767
UpperBound=$(cat $list | wc -l)
RandomLine=$(( $LowerBound + ($UpperBound * $RANDOM) / ($RandomMax + 1) ))
# Use sed to grab the random line.
episode=$(sed -n "$RandomLine{p;q;}" "$list")
# open the random line in VLC
vlc -vvv --fullscreen "$episode" vlc:quit
# Close the cycle count loop...
  done
# ...and exit the program.
exit
```

---

### Post by Brandon Williams on 2009-04-30
Instead of 'find Simpsons', try 'find Simpsons -type f -name "*.avi"'. If you have some videos that are not .avi files, you can use a slightly more complicated expression to match on multiple possible filename extensions.

---

### Post by detroit/zero on 2009-04-30
> **Brandon Williams said:**
> Instead of 'find Simpsons', try 'find Simpsons -type f -name "*.avi"'. If you have some videos that are not .avi files, you can use a slightly more complicated expression to match on multiple possible filename extensions.
> **detroit/zero said:**
> I did have some luck piping to *grep*, and selecting only .avi files to be written, but not all my videos are .avi files - some are .flv, some .mpg, etc..

Thanks for the reply. It'd be that "slightly more complicated expression" that I'd be looking for.

I'd kind of rather leave *find* as it is and use *grep* or *sed* to trim the extraneous info, but it's really six of one and a half dozen of the other.

Whichever way works is fine with me, as long as it does work.

---

### Post by lloyd_b on 2009-04-30
Here's another variant on the find command, that I think you can extend to do what you want:```
find . -regextype posix-egrep -regex ".*\.avi|.*\.mpg|.*\.flv"
```
What this is doing is changing the basis of the matching to something something like "egrep", and then using a suitable pattern for the match.

The above example will match any file that ends with ".avi", ".mpg", or ."flv".

To extend this, just add "|.*\.aaa" to the regex, where "aaa" is the three letter extension, for any other file types that you want to match.

(If I've got you thoroughly confused with that regex - the "|" is a logical OR, the ".*" = "any number of any characters", and "\." is a literal period (".").  
So that pattern translates to: any number of any characters ending in ".avi", OR any number of any characters ending in ".mpg", OR any number of any characters ending in ".flv")

Lloyd B.

---

### Post by kaibob on 2009-05-01
> **detroit/zero said:**
> ...I've run into a problem with my list generation. I'm using the find command to make my list so it will include absolute paths to all my videos. The problem is that it's also including the folder names, subfolder names, and any other extra files that may or may not be present anywhere in the main folder....

I did have some luck piping to *grep*, and selecting only .avi files to be written, but not all my videos are .avi files - some are .flv, some .mpg, etc..

Having those extra lines in the list is causing some playback errors when I run this script. How can I use *sed* (or *grep*) to keep those items out of my playlist?...
I would use the following. It yields absolute paths and includes only those files with the specified extensions (AVI and MPG and FLV as written):

```
find /target/directory -name '*.avi' -o -name '*.mpg' -o -name '*.flv' -type f
```

You have to change /target/directory to the full path to the target directory. To make the search case insensitive, use -iname rather than -name.

---

### Post by detroit/zero on 2009-05-01
Both of those work just fine.
 
Thanks for the help!

---

