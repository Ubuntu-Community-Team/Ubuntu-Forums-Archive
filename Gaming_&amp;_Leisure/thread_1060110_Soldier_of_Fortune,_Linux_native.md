---
title: "Soldier of Fortune, Linux native?"
date: 2009-02-04
forum: Gaming &amp; Leisure
---

### Post by crazyfuturamanoob on 2009-02-04
I watched a couple youtube videos about SoF, read some reviews and articles, and it looks quite cool.

Are them all Linux-native, or just first one? How many sequels there are, 3?

---

### Post by Sand &amp; Mercury on 2009-02-06
> **crazyfuturamanoob said:**
> I watched a couple youtube videos about SoF, read some reviews and articles, and it looks quite cool.

Are them all Linux-native, or just first one? How many sequels there are, 3?
There are two sequels, though the last one is made by a different company and apparently isn't very good.

SoF and SoF2 run off the Quake 2 and 3 engines respectively, both of which usually have no trouble running off Linux. Even if there's no port they'll probably have no problem running under Wine.

---

### Post by crazyfuturamanoob on 2009-02-07
I googled, and found SoF1 the only Linux native. How can I get it? I bet that old game isn't being sold today.

---

### Post by Sand &amp; Mercury on 2009-02-07
The official website points to Amazon:

[http://www.amazon.com/Soldier-of-Fortune-Platinum-Edition/dp/B00005OBQC/sr=8-7/qid=1163024612/ref=sr_1_7/002-5266344-3314447?ie=UTF8&s=videogames](http://www.amazon.com/Soldier-of-Fortune-Platinum-Edition/dp/B00005OBQC/sr=8-7/qid=1163024612/ref=sr_1_7/002-5266344-3314447?ie=UTF8&s=videogames)

---

### Post by crazyfuturamanoob on 2009-02-07
> **Sand & Mercury said:**
> The official website points to Amazon:

[http://www.amazon.com/Soldier-of-Fortune-Platinum-Edition/dp/B00005OBQC/sr=8-7/qid=1163024612/ref=sr_1_7/002-5266344-3314447?ie=UTF8&s=videogames](http://www.amazon.com/Soldier-of-Fortune-Platinum-Edition/dp/B00005OBQC/sr=8-7/qid=1163024612/ref=sr_1_7/002-5266344-3314447?ie=UTF8&s=videogames)

So do I need a windows CD to be able to play/install SoF1?

Do I also need to download Linux binaries?

---

### Post by minisori on 2009-02-07
I remember to play the first one on linux. The linux version was standalone and had nothing to do with the windows version.

It was sold by a company that used to do linux ports many years ago, they had some games. Unfortunately the company shut :S.

---

### Post by crazyfuturamanoob on 2009-02-08
Where can I get the Linux version?

---

### Post by minisori on 2009-02-08
As i said the company closed time ago, so i guess nowhere. Maybe you can find copies on ebay or somewhere else.

---

### Post by crazyfuturamanoob on 2009-02-08
Now I got SoF1 Linux client, on a CD.

So I inserted CD, it got automounted, and:
> 
$ cd /media/cdrom0
$ sh setup.sh
setup.sh: 9: function: not found
x86_64

Maybe that's because I use 64bit Ubuntu?

If someone can modify it working, here is setup.sh:
```

#!/bin/sh
#
# Product setup script - Loki Entertainment Software

# Go to the proper setup directory (if not already there)
cd `dirname $0`

# Return the appropriate architecture string
function DetectARCH {
	status=1
	case `uname -m` in
		i?86)  echo "x86"
			status=0;;
		*)     echo "`uname -m`"
			status=0;;
	esac
	return $status
}

# Return the appropriate version string
function DetectLIBC {
      status=1
      if [ -f `echo /lib/libc.so.6* | tail -1` ]; then
	      if fgrep GLIBC_2.1 /lib/libc.so.6* 2>&1 >/dev/null; then
	              echo "glibc-2.1"
	              status=0
	      else    
	              echo "glibc-2.0"
	              status=0
	      fi        
      elif [ -f /lib/libc.so.5 ]; then
	      echo "libc5"
	      status=0
      else
	      echo "unknown"
      fi
      return $status
}

# Detect the Linux environment
arch=`DetectARCH`
libc=`DetectLIBC`

# Find the installation program
function try_run
{
    setup=$1
    shift
    fatal=$1
    if [ "$1" != "" ]; then
        shift
    fi

    # First find the binary we want to run
    failed=0
    setup_bin="setup.data/bin/$arch/$libc/$setup"
    if [ ! -f "$setup_bin" ]; then
        setup_bin="setup.data/bin/$arch/$setup"
        if [ ! -f "$setup_bin" ]; then
            failed=1
        fi
    fi
    if [ "$failed" -eq 1 ]; then
        if [ "$fatal" != "" ]; then
            cat <<__EOF__
This installation doesn't support $libc on $arch

Please contact Loki Technical Support at support@lokigames.com
__EOF__
            exit 1
        fi
        return $failed
    fi

    # Try to run the binary
    # The executable is here but we can't execute it from CD
    setup="$HOME/.setup$$"
    cp "$setup_bin" "$setup"
    chmod 700 "$setup"
    if [ "$fatal" != "" ]; then
        "$setup" $*
        failed=$?
    else
        "$setup" $* 2>/dev/null
        failed=$?
    fi
    rm -f "$setup"
    return $failed
}


# Try to run the setup program
status=0
rm -f "$setup"
if ! try_run setup.gtk && ! try_run setup -fatal; then
    echo "The setup program seems to have failed on $arch/$libc"
    echo
    echo "Please contact Loki Technical Support at support@lokigames.com"
    status=1
fi
exit $status

```

I'd really like to experience the violence of SoF but I'm not installing 32bit OS just for that.

---

### Post by argie on 2009-02-08
Use bash instead. Say ```
bash setup.sh
``` instead of just sh.

---

### Post by crazyfuturamanoob on 2009-02-08
> **argie said:**
> Use bash instead. Say ```
bash setup.sh
``` instead of just sh.

```

$ bash setup.sh
This installation doesn't support glibc-2.0 on x86_64

Please contact Loki Technical Support at support@lokigames.com

```

I always thought bash is same than sh.

Sorry, I posted this in another thread as well.

---

### Post by argie on 2009-02-08
Starting 6.10, the default sh in Ubuntu is dash.

It seems that you will be able to play the game if you do install the 32-bit libraries (which will run on your current kernel, so you can use other 64-bit programs), and then run the appropriate binary installation program. What is the directory tree like on the CD? Can you find an bin/i386/libc or bin/i386/ directory somewhere? Essentially, what you have to do is find the right setup file and then copy that and the data to your hard-drive, install and then remove the setup files.

If you want help finding the right architecture, run the following command and copy the output to a file which you can upload as an attachment (it simply displays the directory tree starting from the current folder):
```
ls -aR | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'

```

---

### Post by crazyfuturamanoob on 2009-02-09
> **argie said:**
> Starting 6.10, the default sh in Ubuntu is dash.

It seems that you will be able to play the game if you do install the 32-bit libraries (which will run on your current kernel, so you can use other 64-bit programs), and then run the appropriate binary installation program. What is the directory tree like on the CD? Can you find an bin/i386/libc or bin/i386/ directory somewhere? Essentially, what you have to do is find the right setup file and then copy that and the data to your hard-drive, install and then remove the setup files.

If you want help finding the right architecture, run the following command and copy the output to a file which you can upload as an attachment (it simply displays the directory tree starting from the current folder):
```
ls -aR | grep ":$" | sed -e 's/:$//' -e 's/[^-][^\/]*\//--/g' -e 's/^/   /' -e 's/-/|/'

```

Added attachment.

---

### Post by argie on 2009-02-09
Alright, this is worth trying, but you will need the 32-bit libraries installed:
```
sudo aptitude install ia32-libs
```

Then, run the attached script in the same manner as you would run the one on your CD. It might be easier to do this if you were to copy the contents of your CD to a folder and then replace the setup.sh you have with this one (remember to make the setup.sh executable). I've simply replaced the sections where it detects the architecture and library with what I think will work.

I don't know how to uninstall the game though, so it's worth finding out how to do that before you start.

---

### Post by HavocXphere on 2009-02-09
SoF1 was very good, expecially the multiplayer.
SoF2 was OK...the throwing knife was fun in MP.
Never played 3.

---

### Post by johnjohn2 on 2009-02-09
> **HavocXphere said:**
> SoF1 was very good, expecially the multiplayer.
SoF2 was OK...the throwing knife was fun in MP.
Never played 3.

3 is my fave but can't get it to work

---

### Post by crazyfuturamanoob on 2009-02-09
> **argie said:**
> Alright, this is worth trying, but you will need the 32-bit libraries installed:
```
sudo aptitude install ia32-libs
```

Then, run the attached script in the same manner as you would run the one on your CD. It might be easier to do this if you were to copy the contents of your CD to a folder and then replace the setup.sh you have with this one (remember to make the setup.sh executable). I've simply replaced the sections where it detects the architecture and library with what I think will work.

I don't know how to uninstall the game though, so it's worth finding out how to do that before you start.
I can't play it, your script didn't find bin/x86/sof (which doesn't even exist), and /usr/local/bin doesn't have any new files (nothing sof related). What did I do wrong?
> 
arho@arho-laptop:~$ sudo aptitude install ia32-libs
[sudo] password for arho: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

arho@arho-laptop:~$ cd Downloads/Soldier\ of\ fortune\ linux/soldier_of_fortune/
arho@arho-laptop:~/Downloads/Soldier of fortune linux/soldier_of_fortune$ chmod +x setup.sh
arho@arho-laptop:~/Downloads/Soldier of fortune linux/soldier_of_fortune$ bash setup.sh
----====== Soldier of Fortune installation program ======----

You are running a x86 machine with glibc-2.0
Hit Control-C anytime to cancel this installation program.

Would you like to read the README file ? [Y/n] n
Please enter the installation path [/usr/local/games/sof] /usr/local/games/sof 
No write permission to /usr/local/games
Please enter the installation path [/usr/local/games/sof] ^Z
[1]+  Stopped                 bash setup.sh
arho@arho-laptop:~/Downloads/Soldier of fortune linux/soldier_of_fortune$ sudo bash setup.sh
----====== Soldier of Fortune installation program ======----

You are running a x86 machine with glibc-2.0
Hit Control-C anytime to cancel this installation program.

Would you like to read the README file ? [Y/n] n
Please enter the installation path [/usr/local/games/sof] /usr/local/games/sof
Please enter the path for binary installation [/usr/local/bin] /usr/local/bin
Do you want to install desktop items? [Y/n] y
Installing to /usr/local/games/sof
238967 MB available, 1 MB will be installed.

Continue install? [Y/n] y
Unable to find file 'bin/x86/sof'
Installing Base Install ...
 100% - /usr/local/games/sof/sof.xpm
 100% - /usr/local/games/sof/sof-bin
 100% - /usr/local/games/sof/base/gamex86.so
 100% - /usr/local/games/sof/base/player.so
 100% - /usr/local/games/sof/ref_gl.so
 100% - /usr/local/games/sof/liboasnd.so
 100% - /usr/local/games/sof/libTitan.so
 100% - /usr/local/games/sof/libopenal.so
 100% - /usr/local/games/sof/libSDL-1.1.so.0
 100% - /usr/local/games/sof/base/pak0.pak
 100% - /usr/local/games/sof/base/pak1.pak
 100% - /usr/local/games/sof/kver.pub
 100% - /usr/local/games/sof/README

Installation complete.
arho@arho-laptop:~/Downloads/Soldier of fortune linux/soldier_of_fortune$ cd ~
arho@arho-laptop:~$ /usr/local/games/sof/sof-bin 
/usr/local/games/sof/sof-bin: error while loading shared libraries: libTitan.so: cannot open shared object file: No such file or directory
arho@arho-laptop:~$ ls /usr/local/games/sof/
base      liboasnd.so   libSDL-1.1.so.0  README     sof-bin  uninstall.sh
kver.pub  libopenal.so  libTitan.so      ref_gl.so  sof.xpm
arho@arho-laptop:~$ 


Edit:
I got it working!!!! YAYYYYYY!!!!!

```

cd /usr/local/games/sof
LD_LIBRARY_PATH=. ./sof-bin

```

---

### Post by crazyfuturamanoob on 2009-02-11
So I got it working. 

But sometimes it crashes, giving this message:
```

Fatal signal: Segmentation Fault (SDL Parachute Deployed)

```

---

### Post by argie on 2009-02-12
Sorry for the delay, my internet has been out for a while.

If the crashes are so frequent as to disrupt the game, it may be worth it to try installing the binaries that are compiled against glibc-2.1 

To do this, just change the libc variable to "glibc-2.1". That is, replace this line:
```
libc="glibc-2.0"
```
with this line:
```
libc="glibc-2.1"
```

If this doesn't work, then you may need to obtain an older version of glibc and use the LD_LIBRARY_PATH variable you used earlier to point to that. However, [this guide]("http://www.swanson.ukfsn.org/loki/00README.loki_compat")(which really needs to be backed up somewhere visible, it was hard to find) says that you shouldn't need to. Perhaps this refers to using the GLIBC-2.1 version?

---

### Post by crazyfuturamanoob on 2009-02-12
> **argie said:**
> Sorry for the delay, my internet has been out for a while.

If the crashes are so frequent as to disrupt the game, it may be worth it to try installing the binaries that are compiled against glibc-2.1 

To do this, just change the libc variable to "glibc-2.1". That is, replace this line:
```
libc="glibc-2.0"
```
with this line:
```
libc="glibc-2.1"
```

If this doesn't work, then you may need to obtain an older version of glibc and use the LD_LIBRARY_PATH variable you used earlier to point to that. However, [this guide]("http://www.swanson.ukfsn.org/loki/00README.loki_compat")(which really needs to be backed up somewhere visible, it was hard to find) says that you shouldn't need to. Perhaps this refers to using the GLIBC-2.1 version?
You didn't mention the file I have to edit. Sorry, everything is not so obvious to me. Installation script?


The crashes seem to happen at certain locations of game levels.

For example, on the first level, there is a door, which will often crash the game, but not always, if I am not moving while opening it or just look at certain direction.


Those spots are totally unpredictable, and I gotta save often. In addition, that game doesn't let save more than 5 times, so sometimes its very, very annoying to play.


Edit: Finished campaign. Whoa, the end was so lame. Laser & plasma guns? WTF???

---

### Post by jcer93705 on 2010-10-17
Hi i cant get sound out of the game and i'm running off wine in ubuntu 10.10

---

