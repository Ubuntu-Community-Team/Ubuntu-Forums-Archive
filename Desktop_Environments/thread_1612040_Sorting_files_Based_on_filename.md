---
title: "Sorting files Based on filename?"
date: 2010-11-02
forum: Desktop Environments
---

### Post by valuntahr on 2010-11-02
I'm currently trying to organize a media server so that things will be in some kind of logical order rather than the current setup of dumping everything of a certain content type into a single folder. However, the size and diversity of content within these disorganized folders precludes me doing things manually. Does anyone know of a program or script that could sort the files into folders based on part of a filename? 

So a file named [abc]def.avi would go into a folder called def, etc.

Any help would be greatly appreciated.

---

### Post by Barriehie on 2010-11-02
> **valuntahr said:**
> I'm currently trying to organize a media server so that things will be in some kind of logical order rather than the current setup of dumping everything of a certain content type into a single folder. However, the size and diversity of content within these disorganized folders precludes me doing things manually. Does anyone know of a program or script that could sort the files into folders based on part of a filename? 

So a file named [abc]def.avi would go into a folder called def, etc.

Any help would be greatly appreciated.

I can think of a start to this.  I've got a daemon that gets launced at boot and it waits for the creation of a .jpg file in a specific folder and then renames and moves it.  If you like I'll post it; might be a good start.

---

### Post by valuntahr on 2010-11-02
That would be a very useful script to have. Please post it. Even if I can't use it as a starting point for another script I can think of a couple of other places where it would come in handy.

---

### Post by Barriehie on 2010-11-02
> **valuntahr said:**
> That would be a very useful script to have. Please post it. Even if I can't use it as a starting point for another script I can think of a couple of other places where it would come in handy.

Have to have inotifytools or whatever the equivalent is in your distro.  If you ```

aptitude search . | grep notify
``` you should find it.

Here's /etc/init.d/picsdaemondctl
```

#!/bin/bash

### BEGIN INIT INFO
# Provides:          picsdaemondctl
# Required-Start:    $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: picsdaemond start/stop control file.
### END INIT INFO


case "$1" in
    start)
        echo "Starting picsdaemond."
        /usr/local/bin/picsdaemond &
    ;;
    stop)
        echo "Shutting down picsdaemond."
        killall -s 9 picsdaemond inotifywait
    ;;
    *)
        echo "Usage: $0 {start|stop}"
        exit 1
esac
exit 0

#######################################################

```

And here's the actual daemon:
/usr/local/bin/picsdaemond
```

#!/bin/bash
#


if [ -e /var/run/picsdaemond.* ]
then
    rm /var/run/picsdaemond.*
else
    echo > /var/run/picsdaemond.$$
fi


OLDDIR="/home/barrie/Desktop/temp/pics/"
NEWDIR="/home/barrie/Pictures/SS/moved/"
declare -a CHARSARRAY=('a' 'A' 'b' 'B' 'c' 'C' 'd' 'D' 'e' 'E' 'f' 'F' 'g' 'G' 'h' 'H' 'i' 'I' 'j' 'J' 'k' 'K' 'l' 'L' 'm' 'M' 'n' 'N' 'o' 'O' 'p' 'P' 'q' 'Q' 'r' 'R' 's' 'S' 't' 'T' 'u' 'U' 'v' 'V' 'w' 'W' 'x' 'X' 'y' 'Y' 'z' 'Z' '0' '1' '2' '3' '4' '5' '6' '7' '8' '9')
declare -a CHARS
declare -i NUMBER=0
declare -i LOOPCOUNTER=0


#
# Shutdown after 30 minutes
#
#if [ $1 ]
#then
#                               /home/barrie/bin/picsdaemond-timer &
#fi


inotifywait -mq --format '%f' -e create /home/barrie/Desktop/temp/pics/ | while read line
do
file=$line

  while [ $LOOPCOUNTER -lt 10 ]
  do
    RANDOM=$(date +%N)
    NUMBER=$((RANDOM%62+1))
    CHARS[$LOOPCOUNTER]=${CHARSARRAY[$NUMBER]}
    LOOPCOUNTER+=1
  done
  LOOPCOUNTER=0         # ----------------------------- Reset name length counter
  NEWFILENAME=${CHARS[0]}${CHARS[1]}${CHARS[2]}${CHARS[3]}${CHARS[4]}${CHARS[5]}${CHARS[6]}${CHARS[7]}${CHARS[8]}${CHARS[9]}.jpg

        sleep 3

  mv $OLDDIR$file $NEWDIR$NEWFILENAME

  declare -a CHARS=  # ----------------------------- Reset CHARS array

done

```

Edit: I'm more familiar with php but this script could be used to call a php program to do the actual renaming / dir. creation etc.  I've never had the use of slicing up a file name into segments via bash.

---

### Post by valuntahr on 2010-11-03
I know that sed can be used to manipulate text in that manner, but I can't think of a good way for it to work with filenames of different lengths. A possible solution is to compare two different files and create a directory based on the text that is the same in both, but that has it's own problems.

---

### Post by Barriehie on 2010-11-03
You say this is a media server so aren't the file extensions in a predictably small set?

---

### Post by valuntahr on 2010-11-04
Yes, the file extensions themselves are fairly standard, so that does eliminate part of the problem, as I could use a for or case loop to deal with that part of the file name. 

Hmm, that gave me an idea. Wouldn't it be possible to write a command (possibly using sed) that would say, read everything from a set start point (beginning of the file or just past the bracket) until the last period and use that as the basis for the folder name?

The code logic would probably go something like this

Initial scan of filename
Extension check
Bracket Check
Has the directory been created?

then it would do a file move based on the outcome of those parameters.

When it's laid out like that it seems to be pretty straightforward. I could conceivably do without the extension check if I just wanted to run the program within a certain folder, but it would probably be worth it to include that functionality so then I could just run the program from the root of the drive and forget about it. Though of course, the only problem with running the program from the root of the drive is getting the program to realize if it's moved the file before or not. But that could be easily fixed by temporarily appending an extension to the moved file which could then be removed in either another script or at the end of the current script.

Now my main problem is figuring out how to actually write the script as It's been far too long since I've done any sort of scripting/programming, and even then the programs that I made weren't very complex.

---

### Post by Barriehie on 2010-11-04
I'm leaning in the direction of something more using php or some other language that's similar.  I'm not versed enough in bash/gawk to even start to think about slicing/dicing filenames and creating directories from them!  The script provided earlier could be used to 'trigger' the processing.

I don't fully understand your filename / create dir. scenario.  What's wrong with /avi /flv /mpg ... etc.?

Barrie

---

