---
title: "UT 2K4 DVD does not contain the linux installer .sh"
date: 2006-11-07
forum: Gaming &amp; Leisure
---

### Post by techrush on 2006-11-07
i have previously run UT 2k4 with no problems on this system but i lost my DVD so i picked another copy up today at the store on the cheap. the only problem is this disc does NOT contain the linux-installer.sh that was on my old disc. 

i tried using the megapack installer from [http://liflg.org/](http://liflg.org/) and it tells me i must have ut2004 installed before i can install it. 

any help on getting this thing installed would be appreciated :)

---

### Post by pay on 2006-11-07
I would upload my linux installer but it's 28.3mb and I've gone over my limit and it would take a few hours:(

---

### Post by techrush on 2006-11-07
apparently the "editors choice edition" of the game that i picked up does not come with the linux installer. not only that but it is in a format that makes it incompatible with the existing linux-installer.sh


basically im screwed

---

### Post by pay on 2006-11-08
That sucks. I never actually use the on cd installer because I'm on Gentoo. I just do ```
USE=cdrom emerge ut2004
```with the cd in the drive and it copies the files over. Pitty Ubuntu doesn't make it that easy (though just about everything else about Gentoo is harder).

---

### Post by rejser on 2006-11-08
Visited the atari site and found
[http://utforums.epicgames.com/showthread.php?t=554966](http://utforums.epicgames.com/showthread.php?t=554966)
Maybe could be something

A little strange, but could work

---

### Post by pay on 2006-11-08
Or maybe try installing it with wine and then start it with a script like```
sudo nano /usr/bin/ut2004
``````
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

``````
sudo chmod 755 /usr/bin/ut2004
```

---

### Post by thx_1138 on 2006-11-30
Argh!
I happened to pick this up just the other day because it caught my eye and it was inexpensive. I hate to say I found my disc to be the same!!!!! I wasnt aware that I actually had to look out for the tux symbol on the box, just so used of just buying the games I know should run without looking at the box anymore since they rarely mention the linux port. I found the exact post on the unreal forum and I read about the loki mega pack installer. But I would rather have an official installer from epic games.......... anyone else got some ideas or possible workarounds? Especially those that dont require a windows box to complete.......

---

### Post by holylucifer on 2006-11-30
here i upload the file that is needed to install ut2k4,

[http://www.filefactory.com/file/d079a2/](http://www.filefactory.com/file/d079a2/)  or

[http://www.sharebigfile.com/file/28749/linux-installer.sh.html](http://www.sharebigfile.com/file/28749/linux-installer.sh.html)

please note whoever surfs this thread months later, it is likely these download links won't work if very few people have downloaded from,since if no downloads are done they delete the file after a time of no downloads.

---

### Post by holylucifer on 2006-11-30
Anyways i think its times for me to reinstall windows xp , and play games on that, well this is the 2nd time ive come back to ubuntu, there might be a 3rd, but this command line stuff is Really not my thing,reallly.

well cya,gonna put xp cd in.

---

### Post by holylucifer on 2006-11-30
back now,  


[http://img124.imageshack.us/img124/3182/boorx5.jpg](http://img124.imageshack.us/img124/3182/boorx5.jpg)

heh well, basicly use pc for games and surf the net.

---

### Post by thx_1138 on 2006-12-02
I got the linux installer shell script and fired it up not expecting to get the installer to work, died after I entered the cd-key and then tried to get files from cd-roms........... Anyone else have any ideas.... keeping in mind the windows file raiding option is kinda out of the question since I dont run Windows on any of my computers anymore (It really liberating!) Im willing to try something else. Has anyone contacted Epic Games? Maybe I will email them and let them know as a linux gamer I usually dont get any mention of linux support on the box on any ported game and therefore dont bother looking anymore. I only read online about which games are given a port...... I will do that and update if I hear anything back from them.

---

