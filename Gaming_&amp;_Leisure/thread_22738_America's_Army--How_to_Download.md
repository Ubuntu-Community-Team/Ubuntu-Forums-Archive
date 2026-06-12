---
title: "America's Army--How to Download?"
date: 2005-03-29
forum: Gaming &amp; Leisure
---

### Post by xNight Wraithx on 2005-03-29
Since there is no Linux Compatible version of Shockwave, how did you all get the download of America's Army? I went to the site and it was all in Shockwave. Thanks in advance.

---

### Post by arrizaba on 2005-03-29
What about?

[COLOR=Teal]http://aaotracker.4players.de/downloaddb.php?file=107[/COLOR]

You can download it from here. 
One more thing, you need to register in their page in order to advance in training and eventually play.
Enjoy  :mrgreen:

---

### Post by xNight Wraithx on 2005-03-29
Sweetness, many thanks for that and cool Avatar you have there. I will try it when I get home.

---

### Post by bored2k on 2005-03-29
[QUOTE=xNight Wraithx]Sweetness, many thanks for that and cool Avatar you have there. I will try it when I get home.[/QUOTE]
 arrizaba solved your problem but, I can see America's Army website with no problems, do you have Flash installed?

---

### Post by arrizaba on 2005-03-29
Good point., bored2k.
You should do then:  [COLOR=SandyBrown]sudo apt-get install flashplayer-mozilla[/COLOR]
I think it is in the multiverse repository, though I cannot check it right now. I am at work and here I have a different distro.

---

### Post by bored2k on 2005-03-29
[QUOTE=arrizaba]Good point., bored2k.
You should do then:  [COLOR=SandyBrown]sudo apt-get install flashplayer-mozilla[/COLOR]
I think it is in the multiverse repository, though I cannot check it right now. I am at work and here I have a different distro.[/QUOTE]
 [http://www.macromedia.com/shockwave/download/alternates/](http://www.macromedia.com/shockwave/download/alternates/) for the official download link .

---

### Post by xNight Wraithx on 2005-03-29
Last night when I went to the site, I didn't have flash installed. I then installed it and proceeded to remove Ubuntu from my computer while I tried to reinstall Windows XP which failed miserably. Now I am back to Ubuntu and have reinstalled Flash already so I should be able to check it out tonight. I really appreciate all of your help.

---

### Post by xNight Wraithx on 2005-03-29
Okie! Dokie! I can see the site now for America's Army and if gecko would leave me alone, I could download it.

---

### Post by xNight Wraithx on 2005-03-29
ummmkay! So do I go into terminal and apt-get the file because when i go to download it from tracker, i get this crazy long script.

---

### Post by bored2k on 2005-03-29
[QUOTE=xNight Wraithx]ummmkay! So do I go into terminal and apt-get the file because when i go to download it from tracker, i get this crazy long script.[/QUOTE]
 you downloaded a 800mb script ? what if you
sh filename.sh
the script ?

and by the way, you men wget the file, not apt-get it ;) .

---

### Post by xNight Wraithx on 2005-03-29
Well, I didn't download the script. I click on the download think and gecko pops up and then it doesn't go anywhere so I click on the *If your download doesn't start click here* and this is what I get...it's long:

#!/bin/sh
# This script was generated using Makeself 2.1.4

CRCsum="2379200993"
MD5="bcae59c8dcd4a48d11e6d06bfa070a09"
TMPROOT=${TMPDIR:=/tmp}

label="ArmyOps 2.3.0 for GNU/Linux"
script="./unpack_setup_stuff.sh"
scriptargs=""
targetdir="armyops-230-x86"
filesizes="781086720"
keep=n

print_cmd_arg=""
if type printf > /dev/null; then
    print_cmd="printf"
elif test -x /usr/ucb/echo; then
    print_cmd="/usr/ucb/echo"
else
    print_cmd="echo"
fi

MS_Printf()
{
    $print_cmd $print_cmd_arg "$1"
}

MS_Progress()
{
    while read a; do
	MS_Printf .
    done
}

MS_dd()
{
    blocks=`expr $3 / 1024`
    bytes=`expr $3 % 1024`
    dd if="$1" ibs=$2 skip=1 obs=1024 conv=sync 2> /dev/null | \
    { test $blocks -gt 0 && dd ibs=1024 obs=1024 count=$blocks ; \
      test $bytes  -gt 0 && dd ibs=1 obs=1024 count=$bytes ; } 2> /dev/null
}

MS_Help()
{
    cat << EOH >&2
Makeself version 2.1.4
 1) Getting help or info about $0 :
  $0 --help   Print this message
  $0 --info   Print embedded info : title, default target directory, embedded script ...
  $0 --lsm    Print embedded lsm entry (or no LSM)
  $0 --list   Print the list of files in the archive
  $0 --check  Checks integrity of the archive
 
 2) Running $0 :
  $0 [options] [--] [additional arguments to embedded script]
  with following options (in that order)
  --confirm             Ask before running embedded script
  --noexec              Do not run embedded script
  --keep                Do not erase target directory after running
			the embedded script
  --nox11               Do not spawn an xterm
  --nochown             Do not give the extracted files to the current user
  --target NewDirectory Extract in NewDirectory
  --tar arg1 [arg2 ...] Access the contents of the archive through the tar command
  --                    Following arguments will be passed to the embedded script
EOH
}

MS_Check()
{
    OLD_PATH=$PATH
    PATH=${GUESS_MD5_PATH:-"$OLD_PATH:/bin:/usr/bin:/sbin:/usr/local/ssl/bin:/usr/local/bin:/opt/openssl/bin"}
    MD5_PATH=`exec 2>&-; which md5sum || type md5sum`
    MD5_PATH=${MD5_PATH:-`exec 2>&-; which md5 || type md5`}
    PATH=$OLD_PATH
    MS_Printf "Verifying archive integrity..."
    offset=`head -n 374 "$1" | wc -c | tr -d " "`
    verb=$2
    i=1
    for s in $filesizes
    do
	crc=`echo $CRCsum | cut -d" " -f$i`
	if test -x "$MD5_PATH"; then
	    md5=`echo $MD5 | cut -d" " -f$i`
	    if test $md5 = "00000000000000000000000000000000"; then
		test x$verb = xy && echo " $1 does not contain an embedded MD5 checksum." >&2
	    else
		md5sum=`MS_dd "$1" $offset $s | "$MD5_PATH" | cut -b-32`;
		if test "$md5sum" != "$md5"; then
		    echo "Error in MD5 checksums: $md5sum is different from $md5" >&2
		    exit 2
		else
		    test x$verb = xy && MS_Printf " MD5 checksums are OK." >&2
		fi
		crc="0000000000"; verb=n
	    fi
	fi
	if test $crc = "0000000000"; then
	    test x$verb = xy && echo " $1 does not contain a CRC checksum." >&2
	else
	    sum1=`MS_dd "$1" $offset $s | CMD_ENV=xpg4 cksum | awk '{print $1}'`
	    if test "$sum1" = "$crc"; then
		test x$verb = xy && MS_Printf " CRC checksums are OK." >&2
	    else
		echo "Error in checksums: $sum1 is different from $crc"
		exit 2;
	    fi
	fi
	i=`expr $i + 1`
	offset=`expr $offset + $s`
    done
    echo " All good."
}

UnTAR()
{
    tar $1vf - 2>&1 || { echo Extraction failed. > /dev/tty; kill -15 $$; }
}

finish=true
xterm_loop=
nox11=n
copy=none
ownership=y
verbose=n

initargs="$@"

while true
do
    case "$1" in
    -h | --help)
	MS_Help
	exit 0
	;;
    --info)
	echo Identification: "$label"
	echo Target directory: "$targetdir"
	echo Uncompressed size: 763544 KB
	echo Compression: none
	echo Date of packaging: Fri Feb 18 06:28:20 EST 2005
	echo Built with Makeself version 2.1.4 on linux-gnu
	echo Build command was: "/home/icculus/projects/loki_setup/makeself/makeself.sh \\
    \"--nocomp\" \\
    \"armyops-230-x86\" \\
    \"/home/icculus/armyops230-linux.run\" \\
    \"ArmyOps 2.3.0 for GNU/Linux\" \\
    \"./unpack_setup_stuff.sh\""
	if test x$script != x; then
	    echo Script run after extraction:
	    echo "    " $script $scriptargs
	fi
	if test x"" = xcopy; then
		echo "Archive will copy itself to a temporary location"
	fi
	if test x"n" = xy; then
	    echo "directory $targetdir is permanent"
	else
	    echo "$targetdir will be removed after extraction"
	fi
	exit 0
	;;
    --dumpconf)
	echo LABEL=\"$label\"
	echo SCRIPT=\"$script\"
	echo SCRIPTARGS=\"$scriptargs\"
	echo archdirname=\"armyops-230-x86\"
	echo KEEP=n
	echo COMPRESS=none
	echo filesizes=\"$filesizes\"
	echo CRCsum=\"$CRCsum\"
	echo MD5sum=\"$MD5\"
	echo OLDUSIZE=763544
	echo OLDSKIP=375
	exit 0
	;;
    --lsm)
cat << EOLSM
No LSM.
EOLSM
	exit 0
	;;
    --list)
	echo Target directory: $targetdir
	offset=`head -n 374 "$0" | wc -c | tr -d " "`
	for s in $filesizes
	do
	    MS_dd "$0" $offset $s | eval "cat" | UnTAR t
	    offset=`expr $offset + $s`
	done
	exit 0
	;;
	--tar)
	offset=`head -n 374 "$0" | wc -c | tr -d " "`
	arg1="$2"
	shift 2
	for s in $filesizes
	do
	    MS_dd "$0" $offset $s | eval "cat" | tar "$arg1" - $*
	    offset=`expr $offset + $s`
	done
	exit 0
	;;
    --check)
	MS_Check "$0" y
	exit 0
	;;
    --confirm)
	verbose=y
	shift
	;;
	--noexec)
	script=""
	shift
	;;
    --keep)
	keep=y
	shift
	;;
    --target)
	keep=y
	targetdir=${2:-.}
	shift 2
	;;
    --nox11)
	nox11=y
	shift
	;;
    --nochown)
	ownership=n
	shift
	;;
    --xwin)
	finish="echo Press Return to close this window...; read junk"
	xterm_loop=1
	shift
	;;
    --phase2)
	copy=phase2
	shift
	;;
    --)
	shift
	break ;;
    -*)
	echo Unrecognized flag : "$1" >&2
	MS_Help
	exit 1
	;;
    *)
	break ;;
    esac
done

case "$copy" in
copy)
    tmpdir=$TMPROOT/makeself.$RANDOM.`date +"%y%m%d%H%M%S"`.$$
    mkdir "$tmpdir" || {
	echo "Could not create temporary directory $tmpdir" >&2
	exit 1
    }
    SCRIPT_COPY="$tmpdir/makeself"
    echo "Copying to a temporary location..." >&2
    cp "$0" "$SCRIPT_COPY"
    chmod +x "$SCRIPT_COPY"
    cd "$TMPROOT"
    exec "$SCRIPT_COPY" --phase2
    ;;
phase2)
    finish="$finish ; rm -rf `dirname $0`"
    ;;
esac

if test "$nox11" = "n"; then
    if tty -s; then                 # Do we have a terminal?
	:
    else
        if test x"$DISPLAY" != x -a x"$xterm_loop" = x; then  # No, but do we have X?
            if xset q > /dev/null 2>&1; then # Check for valid DISPLAY variable
                GUESS_XTERMS="xterm rxvt dtterm eterm Eterm kvt konsole aterm"
                for a in $GUESS_XTERMS; do
                    if type $a >/dev/null 2>&1; then
                        XTERM=$a
                        break
                    fi
                done
                chmod a+x $0 || echo Please add execution rights on $0
                if test `echo "$0" | cut -c1` = "/"; then # Spawn a terminal!
                    exec $XTERM -title "$label" -e "$0" --xwin "$initargs"
                else
                    exec $XTERM -title "$label" -e "./$0" --xwin "$initargs"
                fi
            fi
        fi
    fi
fi

if test "$targetdir" = "."; then
    tmpdir="."
else
    if test "$keep" = y; then
	echo "Creating directory $targetdir" >&2
	tmpdir="$targetdir"
	dashp="-p"
    else
	tmpdir="$TMPROOT/selfgz$$$RANDOM"
	dashp=""
    fi
    mkdir $dashp $tmpdir || {
	echo 'Cannot create target directory' $tmpdir >&2
	echo 'You should try option --target OtherDirectory' >&2
	eval $finish
	exit 1
    }
fi

location="`pwd`"
if test x$SETUP_NOCHECK != x1; then
    MS_Check "$0"
fi
offset=`head -n 374 "$0" | wc -c | tr -d " "`

if test x"$verbose" = xy; then
	MS_Printf "About to extract 763544 KB in $tmpdir ... Proceed ? [Y/n] "
	read yn
	if test x"$yn" = xn; then
		eval $finish; exit 1
	fi
fi

MS_Printf "Uncompressing $label"
res=3
if test "$keep" = n; then
    trap 'echo Signal caught, cleaning up >&2; cd $TMPROOT; /bin/rm -rf $tmpdir; eval $finish; exit 15' 1 2 3 15
fi

for s in $filesizes
do
    if MS_dd "$0" $offset $s | eval "cat" | ( cd "$tmpdir"; UnTAR x ) | MS_Progress; then
		if test x"$ownership" = xy; then
			(PATH=/usr/xpg4/bin:$PATH; cd "$tmpdir"; chown -R `id -u` .;  chgrp -R `id -g` .)
		fi
    else
		echo
		echo "Unable to decompress $0" >&2
		eval $finish; exit 1
    fi
    offset=`expr $offset + $s`
done
echo

cd "$tmpdir"
res=0
if test x"$script" != x; then
    if test x"$verbose" = xy; then
		MS_Printf "OK to execute: $script $scriptargs $* ? [Y/n] "
		read yn
		if test x"$yn" = x -o x"$yn" = xy -o x"$yn" = xY; then
			eval $script $scriptargs $*; res=$?;
		fi
    else
		eval $script $scriptargs $*; res=$?
    fi
    if test $res -ne 0; then
		test x"$verbose" = xy && echo "The program '$script' returned an error code ($res)" >&2
    fi
fi
if test "$keep" = n; then
    cd $TMPROOT
    /bin/rm -rf $tmpdir
fi
eval $finish; exit $res
./




And then a bunch of illegible(sp?) characters.

---

### Post by bored2k on 2005-03-29
[http://www.gamearena.com.au/files/details/html/15521](http://www.gamearena.com.au/files/details/html/15521)
[http://files.filefront.com/AA_SF_Linux_v23_Full_Install/;3813135;;/fileinfo.html](http://files.filefront.com/AA_SF_Linux_v23_Full_Install/;3813135;;/fileinfo.html)
[http://www.3dgamers.com/news/more/1096481028/](http://www.3dgamers.com/news/more/1096481028/)

---

### Post by Shaggy on 2005-03-29
You should download the script.

It will be called armyops230-linux.run.  I usually just wget it from file front, and then all you have to do is run the script.  And yes it is a 740M script :shock:

---

### Post by xNight Wraithx on 2005-03-29
3dgamer.com is the most promising site. i tried all three but when I click download nothing happens and I see this:

	
This is the GNU/Linux client and dedicated server for
"America's Army: Operations" version 2.3.0

If you have a previous version installed, you need to
uninstall it before installing this version. There is
a script in the game's directory called "uninstall"
for this purpose. Alternately, you can delete the
game's directory and (as the user who installed the
game) ~/.loki/installed/armyops.xml ...

Bug reports go to [https://bugzilla.icculus.org/](https://bugzilla.icculus.org/)

There is a mailing list for discussion. Send a blank email to
[email]armyops-subscribe@icculus.org[/email] to get on the list.

Also, a larger community of ArmyOps players (on Linux and
all other platforms) can be found in the web forums:

[http://forum.americasarmy.com/](http://forum.americasarmy.com/)



DO NOT REPORT LINUX BUGS TO THE MAILING LIST OR FORUMS.
Bug reports go to [https://bugzilla.icculus.org/](https://bugzilla.icculus.org/)


Enjoy the game!

---

### Post by bored2k on 2005-03-29
What the ... 

What about 
http://www.fileplanet.com/125830/120000/fileinfo/America's-Army:-Special-Forces-(Vanguard)-v2.2.1-%5BLinux%5D

---

### Post by xNight Wraithx on 2005-03-29
sorry, one more question.

When I am done downloading....do I just w-get it from the file location?

---

### Post by crane on 2005-03-29
[QUOTE=xNight Wraithx]sorry, one more question.

When I am done downloading....do I just w-get it from the file location?[/QUOTE]


not quite sure I understand this question. If you are done downloading it then you do not need wget.

just run the script.

Also if you ever run across the that problem again. (where it opens a script)
then just do this, Stop the download, on the download page it tells you to do a manual download it it doesn;t work right?
Just click the stop button to keep the script from opening in a window and right click on the manual link. Then select save as and save the file that way.
It should save it as a .run file, just select where you want to save it and click OK.

Good Luck, I'm downloading it myself. \\:D/

---

### Post by xNight Wraithx on 2005-03-30
yeah! I started downloading it about 6 hours ago and it still has an hour left....so I have to input that whole script line for line?

---

### Post by arrizaba on 2005-03-30
Hi again,

Do as crane suggested, i.e. download the script [COLOR=SandyBrown]armyops230_linux.run
[/COLOR]
and execute it using:

sh armyops230_linux.run

You are new to Unix, aren't you?  ;)

---

### Post by xNight Wraithx on 2005-03-30
Yeah! I am....I'm sorry for asking so many questions and I appreciate all of ya'll helping me out. I have no Unix/Linux/Programming background and was a spoiled Windows fanboy but I am liking Ubuntu and trying to work with it and learn and I appreciate everyone being so helpful.

---

### Post by xNight Wraithx on 2005-03-30
I get the no such directory message. I have the file in my Home directory do I need to cd to home first then try sh the script?

---

### Post by bored2k on 2005-03-30
Of course dude
here is the scenario:
--
File is in
/night/home/game.run

You are in
/night/home/muziek/

Only way to run it from there is to
/night/home/muziek/sh ~/game.run
--

Don't take the example literally ..

---

### Post by xNight Wraithx on 2005-03-30
Sorry, like I say I am basically illiterate and I appreciate the patience you all have shown with my incompetence.  I'll get there at some point though. When I go right in and click on the file, it won't open.

Then I tried:

$cd home 

I guess I need to do 


$cd richard home?


Maybe it went to desktop though anyway, I am new medicine that is making me really mellow and too messed up to really think right now 

 ](*,) 

Thanks again though. Maybe I can figure this out soon.

---

### Post by artinla on 2005-04-03
You were close.. you can type any of the following to change to your home directory

cd /home   

or

cd ~

to run the script, change to whatever folder you saved it in:

cd /home/yourusername/scriptdownloadfolder

and run it

sh whateverthescriptiscalled.sh

if it says you don't have permission to run it:

type the following:

chmod +x whateverthescriptnameis.sh

and run it again.  (the up arrow is your friend, just tap it a couple of times and you will see where you typed the command before)

also, for you dos types such as me..  I put an alias in my /etc/bash.bashrc to make cd.. (like in DOS) = cd .. (which is the linux equivalent)

add this line if you want:

alias cd..="cd .."

Have fun, Linux is a blast.

Art

---

### Post by gnutux on 2005-04-15
Well, you could just go to this link: [http://www.americasarmy.com/downloads](http://www.americasarmy.com/downloads) to get to the downloads without the flash player

gnutux

---

### Post by rimmer on 2005-04-17
Hi
I did an install of this game yesterday, and I was playing 4-5 hours later (It works).

This Is what I had to do.

1:- Make sure your graphics card is compatable with the game.
from the konsole run ```
glxgears
``` see what you get.
Then run ```
fgl_glxgears
``` also from the konsole, see what you get from the output, if there are any errors you will have to install the correct drivers for your card, all the information required to solve any problems can be found in this forum.
 
2:- Download the game I think it comes as a .bin or a .run file. Once you have it you will have to make it executable, you can do this 1 of 2 ways from the konsole type. ```
chmod 755 armyops230-linux.run
```  Or if your not used to using the konsole right click on the file --> Properties in the window *permissions*, next to *Owner* click in the execute box. Your file is now an excutable.

3:- I moved the file to my home dir /home/spider/file name.
open the konsole, type. ```
ls -l
``` The file should be in the list and it will be coloured green. 
Next in the konsole, type. ```
./armyops230-linux.run
``` A window should pop up giving you the option to change the install dirs *the defaults should be ok for you* the install will continue. This is the time to go and get a nice strong coffee.

4:- When it's finished it will give you the option to start. I recommend not to yet, why not ? well it's a personal thing I like to finish everything first. Then of to the konsole again and type, ```
whereis armyops
``` this will give you an idea of how and where it's installed. When I ran the install, it created a folder in my home dir /home/spider/armyops. 
To run the game open the konsole once more, type. ```
ls -l
``` You should see a folder called armyops so type ```
cd armyops
```; you're there. Then again type ```
ls -l
```  you should see a file called armyops and yes it should be coloured green. Type ```
./armyops
``` - there you go the game should start.

5:- I had a few issues connecting to a server because of the punkbuster software updates, however if you do a manual update to the pb program all works well at least for me.

Hope this helped and Happy fraggin. :grin:

---

