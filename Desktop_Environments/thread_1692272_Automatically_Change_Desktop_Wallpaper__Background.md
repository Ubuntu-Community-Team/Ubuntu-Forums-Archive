---
title: "Automatically Change Desktop Wallpaper / Background to Random Image ( Gnome )"
date: 2011-02-21
forum: Desktop Environments
---

### Post by rocuan on 2011-02-21
I am running Ubuntu Lucid( 10.04 ) w Gnome & I quickly tire of my wallpaper.
I wanted to set another random HD image as the desktop background  :
    - immediately from a bash shell 
    - whenever with a hot-key.

After surfing the forums & hacking away at it for awhile 
i came up with this bash script. You are welcome to cut n paste it.

[COLOR=DarkRed]EDIT:[/COLOR] This code will NOT accept files with spaces in the name -> (i.e.) [COLOR=DimGray]late night debauchery.jpg [/COLOR]
but these TWO will : 
- simple but usually effective bash script : [http://ubuntuforums.org/showthread.php?t=329164](http://ubuntuforums.org/showthread.php?t=329164)
- my more robust perl script : [http://ubuntuforums.org/showthread.php?p=10654538](http://ubuntuforums.org/showthread.php?p=10654538)
         
if you are unfamiliar with shell scripts here's a tutorial : [http://www.freeos.com/guides/lsst/ch02sec01.html](http://www.freeos.com/guides/lsst/ch02sec01.html)
```

#!/bin/bash
DIR="$HOME/Pictures/Wallpaper" 
GCONF="gconftool-2 -t str -s /desktop/gnome/background" 
TYPE="-iname *.png -or -iname *.jpg"
new_pic=( $(find $DIR/ \( $TYPE \) ! -type d | sort -R) )
random=$[ ( $RANDOM % ${#new_pic[@]} )  ]
$GCONF/picture_filename "${new_pic[$random]}"
$GCONF/picture_options zoom

```This script : 
   - searches the given directory and its sub-dirs for all .png & .jpg 
   - uses $RANDOM to generate a "random" image selection 
   - sets the background image & *zooms *in using gconftool-2

Obviously you'll need to substitute the $HOME/Pictures/Wallpaper for your local path
```

DIR="path_to_your_images" 

```To ignore the sub-directories use 
```

new_pic=( $(find $DIR/ [COLOR=DarkRed]-maxdepth 1[/COLOR] \( $TYPE \) ! -type d | sort -R) )

```To tie it to a Hot-Key / Keyboard Shortcut :
- **System->Preferences->Keyboard Shortcuts**
- click [B]add
[/B]- give it a name
- in the **command **box use full path to your script ( e.g. /home/user/bin/wallswitch.sh )
- give it a memorable hot key combo. ( i use **alt-shift-w** )

[COLOR=DarkRed]Remember : [COLOR=Black]
- make your script executable [/COLOR][/COLOR]from the command line -> chmod a+x yourscript.sh
- put your scripts in the right place: $HOME/bin -> [http://ubuntuforums.org/showthread.php?t=368125](http://ubuntuforums.org/showthread.php?t=368125)

---

### Post by rothalem on 2011-02-25
Awesome Script. I have been fiddling with it a bit today, I tried to add command line arguments to it. Its still a little WIP but as long as your arguments are never invalid it should work.

I find that sometimes after the script runs it doesn't display a Picture, so all I get is a plain purple background (the Gnome default background colour I think). I think this has more to do with my file structure than the script. Im not sure if its because the file the script chose is not supported by nautilus (or whatever actually draws the wallpaper) or something else.

CLI Arguments:
-d folder/ : sets DIR=$HOME/Pictures/wallpapers/folder/ #wallpaper directory
-pd folder/ : sets DIR=$HOME/Pictures/folder/ #Pictures directory
-ad /folder/ : sets DIR=/folder/ #Absolute directory

-r #: Sets the recursive depth. (if you don't set -r, it will go infinitely deep.)
-nr : non-recursive. Sets the recursive depth to 1.

-l : sets the script to loop (indefinitely)
-t # : specifies the time between changes, in seconds. Using -t without -l is useless, but won't cause errors.

If you supply more than one directory argument (ie. -d and -pd) then the argument you supplied last should over-ride all previous arguments of the same type. The same applies for -nr and -r.

I hope that makes sense to you.

```

#!/bin/bash
# Parse command line args. (Please understand that there are no 'fail safes' for incorrect arguments.)
while [[ -n "$1" ]] ; do
	case $1 in
		"-d")  DIR="$HOME/Pictures/wallpapers/$2"; shift 2;; #directory
		"-pd") DIR="$HOME/Pictures/$2"; shift 2;; #Pictures directory
		"-ad") DIR=$2; shift 2;; #absolute directory
		"-nr") depth=1; shift;; #no recursive
		"-r")  depth=$2; shift 2;; #specify recursive depth
		"-l")  loop=true; shift;; #loop
		"-t")  time=$2; shift 2;; #set time between changes, in seconds.
	esac
done

if [[ -z ${DIR} ]] ; then
	DIR="$HOME/Pictures/wallpapers"
fi
if [[ -z ${time} ]] ; then
	time=2
fi
#if [[ -n "$1" ]] ; then
#	DIR="$HOME/Pictures/wallpapers/$1"
#else
#	DIR="$HOME/Pictures/wallpapers" 
#fi

GCONF="gconftool-2 -t str -s /desktop/gnome/background"
TYPE="-iname *.png -or -iname *.jpg"


while true ; do
	if [[ -n "${depth}" ]] ; then	
		# To ignore the sub-directories use
		new_pic=( $(find $DIR/ -maxdepth $depth \( $TYPE \) ! -type d) )
	else
		new_pic=( $(find $DIR/ \( $TYPE \) ! -type d) )
	fi

	random=$[ ( $RANDOM % ${#new_pic[@]} )  ]
	$GCONF/picture_filename "${new_pic[$random]}"
	$GCONF/picture_options zoom
	if [[ -z "${loop}" ]] ; then
		break
	fi
	sleep $time
done

```

EDIT: I was thinking, that if you set it to loop (using -l) then it should see if another (prior) instance already exists using ps -C $0 (or something) and kill itself, otherwise, just continue (that would create a new instance). Im just not sure how to differentiate between a prior instance on loop, and the current instance that was just created. If that makes sense?

---

### Post by rocuan on 2011-02-26
I had fun with this little hack & I am stoked u tweaked it for your box rothalem!
I will freely admit that my above example script [COLOR=DarkRed]does no error checking[/COLOR] either.
My intent was to post only the meat of the code & skip the potatoes. ;)
> 
I tried to add command line arguments to it. Its still a little WIP
try **getopts** for arguments/flags it does alot of the dirty work for you : [http://aplawrence.com/Unix/getopts.html](http://aplawrence.com/Unix/getopts.html)

> 
I find that sometimes after the script runs it doesn't display a Picture, so all I get is a plain purple background 
Are there spaces in your image file names? odd symbols? spaces in the folder name?

If your jpg has spaces like[COLOR=DarkGreen] spelunking for trolls.jpg[/COLOR], the array will be delineated at each word, the first being  : [COLOR=DarkGreen]spelunking[/COLOR]*. *
When **gconftool** tries to set [COLOR=DarkGreen]spelunking[/COLOR] as the background image, it will fail & reset the wallpaper to the purple default.

You may want to define a folder with spaces thru[COLOR=DarkGreen] **getopts**[/COLOR]. Throw a flag & set it. e.g. [I]./wallswap.sh -f
[/I]```

while getopts ":d**[COLOR=DarkGreen]f[/COLOR]**rt:" o; do 
     ..
     f) DIR="$HOME/pictures/[COLOR=DarkGreen]fun\ with\ a\ flame\ thrower[/COLOR]";;                               

```> I was thinking, that if you set it to loop then it should see if another (prior) instance already existsGood idea. That is why the sleep hack is sketchy. 
Either of these *should* hunt down & kill previous processes
```

# KILL previous script processes
name=( $( pgrep "wallswitch.sh" ) )
for (( i = 0 ; i < ${#name[@]} - 1 ; i++ )); do
    kill -9 ${name[$i]}
done

```or
```

# KILL previous script processes
killall -gqo 1s $( echo "$0" | awk -F\/ '{ print $NF }' )

```note: brute force killing can be unpredictable and to *Kill with Care* : [http://linux.byexamples.com/archives/157/kill-process-with-care/](http://linux.byexamples.com/archives/157/kill-process-with-care/)

Using sleep can result in sloppy code but this will flip the background every 15 min.[FONT=Georgia][COLOR=DarkSlateGray]
[/COLOR][/FONT] ```

#!/bin/bash

# KILL previous script processes
name=( $( pgrep "[COLOR=Purple]wallswitch.sh[/COLOR]" ) )
for (( i = 0 ; i < ${#name[@]} - 1 ; i++ )); do
    kill -9 ${name[$i]}
done

DIR="$HOME/[COLOR=DarkRed][COLOR=Purple]Pictures/Wallpape[/COLOR]r[/COLOR]" 
GCONF="gconftool-2 -t str -s /desktop/gnome/background" 
TYPE="-iname *.png -or -iname *.jpg -or -name *.jpeg"
DEPTH="-maxdepth 1"
TIME="900"

# catch command line FLAGS
while getopts ":d:rt:" o; do 
  case $o in
    d) DIR=$(echo "${OPTARG}" | sed -e "s/\/*$//");;   # set Dir & cut trailing slash
    r) DEPTH="";;                                      # search recursively
    t) TIME=$OPTARG;;                                  # sleep time in sec
  esac
done

# LOOP
while true; do
    new_pic=( $(find $DIR/ $DEPTH \( $TYPE \) ! -type d | sort -R) )
    random=$[ ( $RANDOM % ${#new_pic[@]} )  ]      
    $GCONF/picture_filename "${new_pic[$random]}"
    $GCONF/picture_options zoom
    sleep $TIME;
done

```again no error checks. if you feed it garbage it will die. 

now you can run the script at startup & change whenever you want with hotkey etc
either of the following will change the background to a random image from the parent dir /home/user/Pictures & all of its sub-dirs once every minute:
```

./wallswap.sh -r -t 60 -d /home/user/Pictures &
./wallswap.sh -d /home/user/Pictures/ -rt 60 &

```notice if your a TAB-complete junkie either ../Pictures or /Pictures/ will work

---

### Post by rothalem on 2011-02-27
Thanks. I will play with it later today, I don't exactly have time right now.

Neat getopts. I was hoping that there was something like that, I think it was a perl script I once tweaked which did something similar.

I am a tab complete junkie. I love linux, and I think Im starting to like bash.

Thanks again.

---

### Post by rothalem on 2011-03-26
If I am in (so my presentWorkingDir is) a dir that has a *.jpg or *.png or *.jpeg filetype then the wildcards expand and bug out the find command with the following error:

find: paths must precede expression: linuxVSvista.jpg
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
/home/knoppies/scripts/wallswitch.sh: line 64: ( 12462 % 0 )  : division by 0 (error token is ")  ")

linuxVSvista.jpg is the second image I have in wallpapers, If I am in a subdir, then it tends to pick the second image of that subdir)
I know that division by 0 is caused because find returns an error, rather than pictures.
Does anybody know of possible causes/solutions? I have fiddled with it and I am unable to work it out.
EDIT: I have worked something out: bash/find tends to auto-expand *.jpg like so:
++ find /home/knoppies/Pictures/wallpapers/cars/ '(' -iname '*.png' -or -iname fireSkellaton.jpg linuxVSvista.jpg noise-brands-3450.jpg turntable.jpg xbmcwallpaper.jpg -or -iname '*.jpeg' ')' '!' -type d

To fix the problem I used "cd /" to change my working dir to one that I am certain exists, and almost certain contains no .jpg/,png/.jpeg files in it.

My new code (the following code has been fixed of the above error, and should work):

```

#!/bin/bash

# add -x to the shabang for some more debug info.

# http://ubuntuforums.org/showthread.php?p=10602790

# WARNING: This script does no sanity checks on CLI arguments: Garbage in=Garbage out
# Known bugs:
#	I find that sometimes after the script runs it doesn't display a Picture, so all I get is a plain purple background (the Gnome default background colour I think). I think this has more to do with my file structure than the script. I suspect that if it chooses a file in a Directory that has a space in the name, or a file with a space in the name, then the script fails. After cleaning up my wallpapers directory/file names, I no longer get any 'purple backgrounds'


#	CLI Arguments:
#	-d folder/ : sets directory(relative to working dir) to search for wallpapers.
#	-D folder/ : sets directory(absolute) to search for wallpapers.
#	-w folder/ : sets directory(relative to wallpapers) to search for wallpapers.
#	-m #: Sets the maxdepth of the recursive search.
#	-r #: recursive. (default)
#	-R  : non-recursive. Sets the recursive depth to 1.
#	-t #: specifies the time between changes, in seconds. Loops indefinitely
#	-h  : TODO: prints help text.

# -f to disable globbing
# -f
# KILL previous script processes
name=( $( pgrep "wallswitch.sh" ) )
for (( i = 0 ; i < ${#name[@]} - 1 ; i++ )); do
    kill -9 ${name[$i]}
done
 
DIR="$HOME/Pictures/wallpapers"
depth=""
verbose=0
option="zoom"
# I need to implement some type of help.
# catch command line FLAGS (Please understand that there are no 'fail safes' for incorrect arguments.)
while getopts ":d:D:w:m:rRt:hvo:" o; do 
	case $o in
		d) # TODO: if first character is / then (absolute) else
				DIR=`pwd`/$(echo "${OPTARG}" | sed -e "s/\/*$//");; # set DIR(presentWorkingDir) & cut trailing slash
			#fi
			#;;
		D) DIR=$(echo "${OPTARG}" | sed -e "s/\/*$//");; # set Dir(absolute) & cut trailing slash
		w) DIR=$HOME/Pictures/wallpapers/$(echo "${OPTARG}" | sed -e "s/\/*$//");; #set DIR (wallpapers) & cut trailing slash
		m) depth="-maxdepth $OPTARG";;	# Set MaxDepth 
		R) depth="-maxdepth 1";;      # Set MaxDepth=1, no recursive
		r) depth="";; # Searches files recursively (default behaviour)
		t) time=$OPTARG;;		# sleep time in sec; loops indefinitely.
		v) verbose="1";; # OBVIOUSLY sets verbose to true. Prints out the chosenPic:
		o) option=$OPTARG;;
		h) # echo "I should echo some command line help here."
		default) echo "Usage: $0 [-d path -D path -w path -m # -r -R -t # -h -v -o option"
			echo "-d path (relative from present working dir (pwd) )"
			echo "-D path (absolute)"
			echo "-w path (relative from $HOME/Pictures/wallpapers/ )"
			echo "-m # max depth"
			echo "-r recursive (default behaviour)"
			echo "-R non-recursive. sets maxdepth=1"
			echo "-t # time (in seconds) between updates. If omitted then updates once and quits"
			echo "-h prints this help text"
			echo "-v sets verbose to true. Prints out the filename of the file that has been selected."
			echo "	Please understand that if you have spaces in your filestructure, it will confuse this script, and your wallpaper will return to the default colour"
			echo "-o option WHERE option takes on the values: 'none', 'wallpaper', 'centered', 'scaled', 'stretched', 'zoom', 'spanned'."
			echo "Created and edited by rocuan AND rothalem (on ubuntuforums)."
			echo "http://ubuntuforums.org/showthread.php?p=10602790"
	esac
done
cd / # an attempt at fixing a bug. Bash auto-expands *.png *.jpg *.jpeg when find tries to use them as $TYPE. It messes with my script. This (mostly) fixes the issue (assuming / contains no such files) 
# echo $verbose # DEBUG
GCONF="gconftool-2 -t str -s /desktop/gnome/background"
TYPE='-iname *.png -or -iname *.jpg -or -iname *.jpeg'
#TYPE='-iname \*.png -or -iname \*.jpg -or -iname \*.jpeg'
#TYPE='-iname "*.png" -or -iname "*.jpg" -or -iname "*.jpeg"'


while true ; do
	# echo "find $DIR/ $depth \( $TYPE \) ! -type d" #DEBUG
	if [[ -n "${depth}" ]] ; then	# specify a maxdepth
		new_pic=( $(find $DIR/ $depth \( $TYPE \) ! -type d) )
	else
		new_pic=( $(find $DIR/ \( $TYPE \) ! -type d) )
	fi

	random=$[ ( $RANDOM % ${#new_pic[@]} )  ]
	# echo "ChosenPic:" #DEBUG
	# echo ${new_pic[$random]} #DEBUG
	if test ${verbose} -gt 0 ; then # If verbose, print out the chosenPic:
		echo "ChosenPic: ${new_pic[$random]}"
	fi
	$GCONF/picture_filename "${new_pic[$random]}"
	$GCONF/picture_options $option # Possible values are "none", "wallpaper", "centered", "scaled", "stretched", "zoom", "spanned". Default = zoom
	if [[ -z "${time}" ]] ; then #If time is not set, break loop (so the script finishes).
		break
	fi
	if test ${time} -lt 0 ; then #If time is negative (illegal), break loop (so the script finishes).
		echo "ERROR: Time (-t) needs to be set to a positive number (in seconds). EXITING!"
		break
	fi
	sleep $time
done

```

---

### Post by sflitman on 2011-04-04
I found a better way using Perl which allows files and directories with spaces in them.  Make sure you install File::Random from CPAN first:

```
sudo cpan File::Random
```

The script:

```
#!/usr/bin/perl
# SSF 040311 Change Gnome2 wallpaper to something random 

use strict;
use File::Random qw/random_file/;

my $dir="$ENV{HOME}/Pictures";             # put your wallpaper folder here
my $gconf="gconftool-2 -t str -s /desktop/gnome/background";
my $file=random_file(-dir=>$dir,-recursive=>1,-check=>qr/\.(?:jpg|jpeg|png)$/i);
print "Selected $dir/$file\n";
system qq{$gconf/picture_filename "$dir/$file"};
system qq{$gconf/picture_options scaled};  # put other options here, I think scaled works best
exit;

```

You can call it from cron if you want to rotate on a schedule.

Hope that helps,
SSF

---

### Post by rocuan on 2011-04-04
Like it sflitman !! 
This line is silky smooth :
```
my $file=random_file(-dir=>$dir,-recursive=>1,-check=>qr/\.(?:jpg|jpeg|png)$/i);

```I took it and ran with it : [http://ubuntuforums.org/showthread.php?p=10654538](http://ubuntuforums.org/showthread.php?p=10654538)

rothalem, I don't know if you fixed your problems yet. If not, I'll drop some suggestions.

There is a slim chance it could be as simple as your script folder location.
It is good coding practice to have all your personal programs in your [COLOR=DarkGreen]$HOME/bin[/COLOR] folder 
How to export that path to your [COLOR=DarkGreen].bashrc[/COLOR] : [http://ubuntuforums.org/showthread.php?t=368125](http://ubuntuforums.org/showthread.php?t=368125)
That way all of your scripts are accessible from anywhere & you don't need the [COLOR=DarkGreen]./[/COLOR] every time
( I personally also get annoyed with the [COLOR=DarkGreen].sh[/COLOR] on the end of my script name, so I never use it )

As you know, you are getting two errors :
**1. Find Fails**
 > 
 find: paths must precede expression: linuxVSvista.jpg
 Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]
 **2. Division by Zero**
> /home/knoppies/scripts/wallswitch.sh: line 64: ( 12462 % 0 )  : division by 0 (error token is ")  ")Working backwards :
When the calculator tries dividing 12462 by 0 it dies.
The error is thrown here :
```
random=$[ ( $RANDOM % ${#new_pic[@]} )  ]

```[COLOR=DarkGreen]12462[/COLOR] is the RANDOM number [COLOR=DarkGreen]
              0 [COLOR=Black]is the count of items in the array [COLOR=DarkGreen]new_pic[][/COLOR][/COLOR][/COLOR]

The array [COLOR=DarkGreen]new_pic[/COLOR] is filled with the image files retrieved by the [COLOR=DarkGreen]find [COLOR=Black]command[/COLOR][/COLOR] 
If find fails, the array stays empty, & the item count is zero which throws the division by zero error.

easy error check :
```

# is directory empty
if [ ${#new_pic[@]} == "0"  ]; then
     exit 1;
fi

```So the main question is, why does find fail?
I think part of the problem is the delcaration of [COLOR=DarkGreen]$TYPE[/COLOR]
> 
TYPE='-iname *.png -or -iname *.jpg -or -iname *.jpeg'
This most likely should be [COLOR=DarkRed]"double quoted"
[/COLOR]I suspect bash gets confused at the [COLOR=DarkGreen]\( [COLOR=Black]and [COLOR=DarkGreen]\) [/COLOR][/COLOR][/COLOR]
Bash can be sketchy about literal substitution within a script calling a system command
Try changing the single quotes to double, but, You might have better luck skipping this substitution all together
```

new_pic=( $(find $DIR/ $DEPTH \( -iname *.png -or -iname *.jpg -or -name *.jpeg \) ! -type d | sort -R) )

```[COLOR=DarkGreen][COLOR=Black][COLOR=DarkGreen]
[/COLOR][/COLOR][/COLOR]All that being said, I am not exactly sure why find bails here : 
> find: paths must precede expression: linuxVSvista.jpgBut, most likely, the [COLOR=Black]script is sending bad data to find.[/COLOR]
which could mean [COLOR=Purple]$DIR is not set correctly at some point in your code[/COLOR]
With all the substitutions/calls happening there ( [COLOR=DarkGreen]$DIR, $DEPTH, $TYPE, !-type d, sort -R [/COLOR]) it is easy to feed it garbage

- Happy Hacking

---

### Post by rocuan on 2011-04-04
rothalem, I was cruising your code again & realized you gave me a shout out !
Thanx man that's cool of you. :grin:
Since my name is attached to that code, I feel I can offer a few more suggestions :

Readability :
The functionality of the code is paramount but all codes need [I]style
[/I]A big part of style is how it READS in a terminal window to other coders : [http://ubuntuforums.org/showthread.php?p=10673262#post10673262](http://ubuntuforums.org/showthread.php?p=10673262#post10673262)

That being said, you may not want to indent your loops so far
You put all that work in to getting it running, make it look good too 8-)
It could be it is just a cut-n-paste problem on the forums, if it is i apologize.

Functionality: 
Your while loop needs a little love. You don't need this if / else
```

if [[ -n "${depth}" ]] ; then    # specify a maxdepth
    new_pic=( $(find $DIR/ $depth \( $TYPE \) ! -type d) )
else
    new_pic=( $(find $DIR/ \( $TYPE \) ! -type d) )
fi

```[COLOR=DarkGreen]$depth [COLOR=Black]is set to "" (an empty string by default) so find will pass right over it. promise.
[/COLOR][/COLOR]
It is good that your testing the validity of [COLOR=DarkGreen]$time
[COLOR=Black]You might dig this : [/COLOR][/COLOR]if time is a positive integer: sleep. else: break.[COLOR=DarkGreen]
[/COLOR] ```

if [[ $time =~ ^[0-9]+$ ]]; then
   sleep $time
else
   break
fi
```Tip: If u use getopts to "flip a switch" by setting a variable to true
```

v) verbose=1;;

```Then on most bash variants you can check if "the switch is on" simply by
```

if [ $verbose ]; then
   ...
fi

```all together now
```

while true ; do
    new_pic=( $(find $DIR/ $depth \( $TYPE \) ! -type d) )
    random=$[ ( $RANDOM % ${#new_pic[@]} )  ]
    if [ $verbose ]; then
        echo "ChosenPic: ${new_pic[$random]}"
    fi
    $GCONF/picture_filename "${new_pic[$random]}"
    $GCONF/picture_options $option
    if [[ $time =~ ^[0-9]+$ ]]; then
        sleep $time
    else
        break
    fi
done

```

[COLOR=DarkRed]EDIT: [COLOR=Black]was just thinking if you set time to negative one as the default, then the script would only run once unless you [/COLOR][/COLOR]defined a time.

For me, I find it easier to remember if I keep the [COLOR=DarkGreen]help[/COLOR] option standard on all my work
```
wallswap --help
```this is an easy way :
```

#!/bin/bash
if [ "$1" == "--help" ]; then
    echo " $0 <option> <arg> "
    ..
    exit 1
fi

```no reason to run thru the main body of code for a help statement :smile:
In your code you could write this as a usage function & call if from your [COLOR=DarkGreen]h) and default) [COLOR=Black]case in getopts.[/COLOR][/COLOR]
```

#!/bin/bash
usage()
{
    echo " $0 <option> <arg> "
    ..
    exit 1
}
..
while getopts ":d:D:w:m:rRt:hvo:" o; do 
    ..
    h) usage ;;
    default) usage ;;

```

---

### Post by .salo on 2011-04-15
rocuan, this doesn't supports spaces in the image file name, since 
```
 the array will be delineated at each word
```

I don't know how the array is generated (which part of script is responsible for it), so could you help me to solve this problem?

Thakns

---

### Post by rocuan on 2011-04-15
I had fun with this code but made a mistake when I posted it. :(
I don't use files with spaces so this code will not accept file names with spaces.

If you want to use a bash script that accepts file names with spaces try this : [http://ubuntuforums.org/showthread.php?t=329164](http://ubuntuforums.org/showthread.php?t=329164)
or check out the modified version I wrote in *perl* [http://ubuntuforums.org/showthread.php?p=10654538](http://ubuntuforums.org/showthread.php?p=10654538)

If your still interested in how this one works, I'll break it down :

The array is called new_pic and is filled with a list of images obtained from the **find **command( man pages for find : [http://ss64.com/bash/find.html](http://ss64.com/bash/find.html) ) 
It is defined here :
```
new_pic=( $(find $DIR/ \( $TYPE \) ! -type d | sort -R) )
```- The outer parentheses indicate that new_pic is an array : [COLOR=Gray]new_pic=( stuff )[/COLOR]
- The second parentheses tell bash to run the command & return the results: [COLOR=Gray]$( command )[/COLOR]
- The inner parentheses tell the command what type of file to look for: [COLOR=Gray]\( file extension \) [/COLOR]

[COLOR=Gray]! -type d[/COLOR] [COLOR=Black]tells find to ignore the directories( probably not needed if your folder names never contain png|jpg etc ) 
[COLOR=Gray]| sort -R [COLOR=Black]tells bash to sort the results randomly( helps make RANDOM more random when choosing a pic )[/COLOR][/COLOR]
[/COLOR] 
[COLOR=Gray]$DIR[/COLOR] is the directory to search
[COLOR=Gray]$TYPE[/COLOR] is the file extension to look for
```
TYPE="-iname *.png -or -iname *.jpg -or -iname *.jpeg"
```[COLOR=Black][COLOR=Gray]-iname [COLOR=Black]means ignore case( UPPER or lower case letters )

Basically, **find** runs off and locates all the images in the Wallpaper directory and prints a long list, we snag it & stuff it in the array.
[/COLOR][/COLOR][/COLOR]
Test it on your box by going to :
Main Menu -> Accessories -> Terminal

And type in the following( substitute Pictures for your directory full of photos )
```
cd Pictures/
find . -iname *.png -or -iname *.jpg

```You will get a long, vertical list of all the files that match anything.png or whatever.jpg

All I did was redirect that list into the array new_pic & select a random image from it.
[COLOR=DarkOliveGreen]
Where the code breaks down[/COLOR]: passing the results of find into the array.

As you know by now, basic Linux commands do not like names with spaces.
The array chops the results at every white space & the code donks out.

[COLOR=DarkOliveGreen]Fix ?: [/COLOR]There are bash solutions to this, but they are annoying. 

Try one of these instead ;)  
[U][http://ubuntuforums.org/showthread.php?t=329164](http://ubuntuforums.org/showthread.php?t=329164)
[http://ubuntuforums.org/showthread.php?p=10654538](http://ubuntuforums.org/showthread.php?p=10654538)
[/U]

---

