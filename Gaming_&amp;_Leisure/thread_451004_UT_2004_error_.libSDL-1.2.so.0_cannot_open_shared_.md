---
title: "UT 2004 error ./libSDL-1.2.so.0: cannot open shared object file"
date: 2007-05-21
forum: Gaming &amp; Leisure
---

### Post by psyopper on 2007-05-21
RESOLVED - SEE PAGE 2!

Problem was caused by not having the correct launcher, nothing to do with libSDL as the title states - it is a symptom, not the problem. Below is the body of the original message

Hi all,

I purchased the Midway Unreal Anthology on a whim yesterday not even realizing that it didn't include the Linux installers. I know this now after cruising around here (and some other places) trying to figure out how to install.

I started with installing Unreal Tournament 2004 following this guide:

[http://ubuntuforums.org/showthread.php?t=394706]("http://ubuntuforums.org/showthread.php?t=394706")

My setup - Ubuntu 7.04 w/ Nvidia drivers

Specifically I used the script that NESFreak wrote and it worked really well. With one problem... UT 2004 won't start. Actually that's not correct either. It will start if I manually double-click the /path/to/game/ut2004-bin in Nautilus. 

If I make a launcher it doesn't launch and when I try the launcher command in the terminal I get:

```
 error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```

I've tried the following launchers:

/usr/local/games/ut2k4/System/ut2004-bin
/usr/local/games/ut2k4/System//ut2004-bin
/usr/local/games/ut2k4/System/ut2004
/usr/local/games/ut2k4/System//ut2004

I can still play it if I click the ut2004-bin manually, but it's boring having to dig all the way through Nautilus, especially when I am doing the same command in the terminal and it doesn't work!

I tried replacing libsdl and libopenal as recommended elsewhere and that had no joy either. 

Any ideas?

---

### Post by Cappy on 2007-05-21
[http://ubuntuforums.org/showthread.php?t=444533&highlight=libSDL-1.2.so.0](http://ubuntuforums.org/showthread.php?t=444533&highlight=libSDL-1.2.so.0)

---

### Post by psyopper on 2007-05-22
Unfortunately I'm not using a 64 bit processor or a 64 bit version of Linux.

I did notice that in /usr/lib my libSDL-1.2.so.0 is actually a link to libSDL-1.2.so.0.11.0

I tried replacing the link with the actual libSDL from the guide I noted above. When I try to run it in the terminal it looks like it wants to run but winds up looking like this:

```
brad@Ubuntu:~$ /usr/local/games/ut2k4/System/ut2004-bin



: 

Exiting due to error
brad@Ubuntu:~$
```

I know I've seen this before, but it was also a reference to 64bit linux.

---

### Post by Cappy on 2007-05-22
you need to update the libSDL?
```

sudo aptitude install libsdl1.2debian-alsa
sudo cp /usr/lib/libSDL-1.2.so.0 /usr/local/games/ut2k4/System/
```

---

### Post by psyopper on 2007-05-22
> **Cappy said:**
> you need to update the libSDL?
```

sudo aptitude install libsdl1.2debian-alsa
sudo cp /usr/lib/libSDL-1.2.so.0 /usr/local/games/ut2k4/System/
```

No joy, I already have the latest version of libSDL installed. I made sure that the files were the same in /usr/local/lib and /usr/local/games/ut2k4/System. 

Even more interesting... I created a link to ut2004-bin and tried executing it (double click). It launches properly inside /usr/local/games/ut2k4/System but when I move it to the desktop it fails. And further my user/group has full read write access to the entire path to ut2004-bin.

Does anyone have a working launcher they could post? Or at least look at the properties of their launcher and post the command here?

Thanks for everything so far!

---

### Post by Cappy on 2007-05-22
The correct wrapper is actually /usr/local/games/ut2k4/ut2004
It si the wrapper than is run when you use the command "ut2004" to start the game

---

### Post by psyopper on 2007-05-23
> **Cappy said:**
> The correct wrapper is actually /usr/local/games/ut2k4/ut2004
It si the wrapper than is run when you use the command "ut2004" to start the game

Right. That was the one I was originally using. It didn't help either. I don't see how this particular file could be the problem though and the link I created points directly to the file in /usr/blah/blah/System. Unless the link is trying to execute the file from within home/blah/desktop.

Is there a way to "command" the launcher to look for the file(s) in /usr/blah/System?

---

### Post by psyopper on 2007-05-24
bump

---

### Post by psyopper on 2007-05-26
bumpity bump...

Anyone? 

Does everyone on this board manually navigate to their /<UT2004>/System directory to run UT2004-bin? Does no-one have a working launcher?

---

### Post by Cappy on 2007-05-26
> **psyopper said:**
> bumpity bump...

Anyone? 

Does everyone on this board manually navigate to their /<UT2004>/System directory to run UT2004-bin? Does no-one have a working launcher?

I definitely don't. "ut2004" does it for me.

from /usr/local/games/ut2k4/ut2004:
```

# Set the home if not already set.
if [ "${UT2004_DATA_PATH}" = "" ]; then
    UT2004_DATA_PATH="`FindPath $0`/System"
fi

LD_LIBRARY_PATH=.:${UT2004_DATA_PATH}:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH

```

Maybe that line is what you are looking? If it is looking in the wrong location, it looks like it might be resolved by giving it the correct path yourself?
Unfortunately, I'm not quite sure how to solve your problem just due to my lack of knowledge on the subject. I've never run into a problem like this nor seen a problem like this solved.

---

### Post by psyopper on 2007-05-26
That's the thing, I don't HAVE a UT2004. I have UT2004.exe, ut-2004.bin but I just don't have the UT2004 because the version I have is non-linux so it was not included. 

I have the bin, but I do not have the launcher script which is what I am hoping someone will post...



> **Cappy said:**
> I definitely don't. "ut2004" does it for me.

from /usr/local/games/ut2k4/ut2004:
```

# Set the home if not already set.
if [ "${UT2004_DATA_PATH}" = "" ]; then
    UT2004_DATA_PATH="`FindPath $0`/System"
fi

LD_LIBRARY_PATH=.:${UT2004_DATA_PATH}:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH

```



---

### Post by Cappy on 2007-05-27
Ah, I thought you said you had it and it wouldn't work.

Anyway, here it is:
```

#!/bin/sh
#
# ut2004 startup script
#

# Function to find the real directory a program resides in.
# Feb. 17, 2000 - Sam Lantinga, Loki Entertainment Software
FindPath()
{
    fullpath="`echo $1 | grep /`"
    if [ "$fullpath" = "" ]; then
        oIFS="$IFS"
        IFS=:
        for path in $PATH
        do if [ -x "$path/$1" ]; then
               if [ "$path" = "" ]; then
                   path="."
               fi
               fullpath="$path/$1"
               break
           fi
        done
        IFS="$oIFS"
    fi
    if [ "$fullpath" = "" ]; then
        fullpath="$1"
    fi

    # Is the sed/ls magic portable?
    if [ -L "$fullpath" ]; then
        #fullpath="`ls -l "$fullpath" | awk '{print $11}'`"
        fullpath=`ls -l "$fullpath" |sed -e 's/.* -> //' |sed -e 's/\*//'`
    fi
    dirname $fullpath
}

# Set the home if not already set.
if [ "${UT2004_DATA_PATH}" = "" ]; then
    UT2004_DATA_PATH="`FindPath $0`/System"
fi

LD_LIBRARY_PATH=.:${UT2004_DATA_PATH}:${LD_LIBRARY_PATH}
export LD_LIBRARY_PATH

# Let's boogie!
if [ -x "${UT2004_DATA_PATH}/ut2004-bin" ]
then
	cd "${UT2004_DATA_PATH}/"
	exec "./ut2004-bin" $*
fi
echo "Couldn't run UT2004 (ut2004-bin). Is UT2004_DATA_PATH set?"
exit 1

# end of ut2004 ...

```

---

### Post by psyopper on 2007-05-27
> **Cappy said:**
> Ah, I thought you said you had it and it wouldn't work.

Anyway, here it is:

Awesome! Thank you VERY much, this worked almost perfect. I had to edit the file and declare the path manually but it worked after that!!

For those following in my footsteps, open a terminal and... 

```
sudo gedit /usr/bin/ut2004
```

This will open a blank file named ut2004 in gEdit with sudo permission. Add the following lines:

```

# setting the data path myself...
UT2004_DATA_PATH="/path/to/ut2004/System"

```

Remember: change "/path/to/ut2004/System" to the actual path to your Unreal Tournament 2004 "System" directory.

Add them just above this line:```

# Set the home if not already set
```

Save and exit gEdit. This saved the file ut2004 in /usr/bin. Don't leave the terminal yet...

```

sudo chmod 755 /usr/bin/ut2004

``` 

This last step will make it executable by everyone on your system. This whole process made a launcher script in your /usr/bin directory which is conveniently in the system path variable on boot. Now you can make a shortcut to launch UT2004 by entering "ut2004" (without the quotes) in the command line of the shortcut you create. Alternately you can just enter "ut2004" (again, without the quotes) in a terminal to launch the game.

---

### Post by scrime on 2008-09-09
I know it´s old but this helped me after reading this post I figured out > ln -s /usr/lib/libSDL-1.2.so.0 /home/scrime/Games/ut2004/System/libSDL-1.2.so.0 in the terminal (obviously replacing my exact location) fixes the > ./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory problem.


For the 64 bit guys have a look here [http://www.unrealadmin.org/forums/showthread.php?t=7507]("http://www.unrealadmin.org/forums/showthread.php?t=7507")

---

