---
title: "UT2004 and UT (permission problem?)"
date: 2006-07-02
forum: Gaming &amp; Leisure
---

### Post by Grimmeehh on 2006-07-02
Hi, I have trawled these forums looking for a solution to this problem, but have been unsuccessful. I have installed both UT and UT2004 in unbuntu, but i remain unable to run them.

trying to run either from the console yields:

```
colzybub@colzybub-desktop:~$ ut
bash: /usr/local/bin/ut: /bin/sh: bad interpreter: Permission denied
```

or attempting to use nonXgl:
```

colzybub@colzybub-desktop:~$ nonXgl ut
non-network local connections being added to access control list
/usr/bin/nonXgl: /usr/local/bin/ut: /bin/sh: bad interpreter: Permission denied
/usr/bin/nonXgl: line 15: /usr/local/bin/ut: Success
```

same with ut2004. How can i set it so i can run both games? I dont understand what ive done wrong here, judging by various posts noone seems to have given a solution to this problem. Did i muck it up when i installed it by not using the correctt operands?



any help is much appreciated, if I can play these then I dont need to boot windows  :)

nb. if its of any use this works fine:

```
colzybub@colzybub-desktop:~$ glxgears -printfps
52653 frames in 5.0 seconds = 10530.440 FPS
52392 frames in 5.0 seconds = 10478.276 FPS
52394 frames in 5.0 seconds = 10478.638 FPS
52613 frames in 5.0 seconds = 10522.457 FPS
52457 frames in 5.0 seconds = 10491.379 FPS
```

---

### Post by scxtt on 2006-07-02
```
bash: /usr/local/bin/ut: /bin/sh: bad interpreter: Permission denied
```this means that you either don't have the sh shell (which now-a-days is just a link to /bin/bash) or you can't execute it (which would be strange) ... see what you get for this command:```
ll /bin | grep sh
```
i get:
[indent]:> ll /bin | grep sh
-rwxr-xr-x 1 root root 649K 2006-04-21 18:51 bash
lrwxrwxrwx 1 root root    4 2006-06-09 03:08 rbash -> bash
[color=red]lrwxrwxrwx 1 root root    4 2006-06-09 03:08 sh -> bash[/color][/indent]

---

### Post by Grimmeehh on 2006-07-02
```
colzybub@colzybub-desktop:~$ ll /bin | grep sh
bash: ll: command not found

```

i take it thats not good? hrm..

---

### Post by FallenWizard on 2006-07-02
it should be
```
ls /bin | grep sh
```

---

### Post by Grimmeehh on 2006-07-02
I get:

```
colzybub@colzybub-desktop:~$ ls /bin | grep sh
bash
rbash
sh

```

for that one. doesnt look like it means a lot though.

---

### Post by Grimmeehh on 2006-07-02
.. assume you both meant:

```
colzybub@colzybub-desktop:~$ ls -l /bin | grep sh
-rwxr-xr-x 1 root root  664084 2006-04-21 23:51 bash
lrwxrwxrwx 1 root root       4 2006-06-15 20:24 rbash -> bash
lrwxrwxrwx 1 root root       4 2006-06-15 20:24 sh -> bash

```

so yes i get the same as you on that one. thanks, any suggestions?

---

### Post by scxtt on 2006-07-02
"ll" is a universally known alias for "ls -l", it's even in .bashrc - but i think it's commented out initially ... i'm so used to using it, i forgot not everyone might know that :p ... 

so what do you get for:
[indent]head -25 /usr/local/bin/ut[/indent]i don't know if there's a bunch of comments in the beginning of the startup script, so that might not help at first ...

---

### Post by Grimmeehh on 2006-07-03
Ah right, good to know :)
Sorry for the slow reply, been at work and was busy last night:

```
#!/bin/sh
#
# Unreal Tournament startup script
#

# The user preferences directory
UT_PREFS="${HOME}/.loki/ut"

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

```

But i doubt thats the problem i get the same problems if i just try to run it from the directory.. could i just enter the path of UT into that so it doesnt go "finding" it ?its just sitting on a 50gb vfat partition (incidentally i thought vfat was viewable from windows, its not, i guess i was wrong there, but thats something else)

---

### Post by scxtt on 2006-07-03
try putting sudo in front of "ut":
[indent]$:> sudo ut[/indent]

---

### Post by Grimmeehh on 2006-07-03
[QUOTE=scxtt]try putting sudo in front of "ut":
[indent]$:> sudo ut[/indent][/QUOTE]
 Have done, that was the first thing i tried infact.

```
colzybub@colzybub-desktop:~$ sudo ut
sudo: unable to execute /usr/local/bin/ut: Permission denied
```

I dont understand whats gone wrong. Typical example of people being put off linux ! im definately still wanting to get this working for UT and UT2004 though. if i did that it would reduce my windows need a fair bit since im playign 2k4 quite a bit right now.

---

### Post by crane on 2006-07-03
Did you install as sudo?
Try running it like this.
just type this in a terminal window.
/usr/local/games/ut2004/ut2004

---

### Post by Grimmeehh on 2006-07-03
Yes installed as sudo

```
sudo sh /media/cdrecorder/linux-installer.sh
```

although i have installed it on another partition not to the games directory.... is that a problem? trying to run it from there does not work and gives the same error (using correct path instead of /usr/local/games/ut2004/ut2004)

does that matter? the "automatic" partition program on unbuntu doesnt give enough hdd space so i made a new 50gb partition and put ut and 2k4 on that. does it only work on the main drive, is that the problem ?

---

### Post by scxtt on 2006-07-03
i can't see that being the problem ... and even if it could be, sudo would have made it a moot point (who has more permissions than root?) ... my brother has both those games - if he didn't live ~40mi away from me i'd try installing them myself, just to see if i had similar problems - tho i was able to install Quake4 w/ no issue ...

make sure "ut" is trying to run the right script (if it's not /usr/local/games/ut2004/ut2004) and **make sure the script is *executable*** ... if i try to run a "text file" - i get a similar error:
[indent]:> ll | grep test.txt
-rw-r--r-- 1 scxtt scxtt   15 2006-07-03 15:16 test.txt
:> ./test.txt
bash: ./test.txt: Permission denied[/indent]

---

### Post by Grimmeehh on 2006-07-03
typing "ut" or "ut2004" doesnt mean much really since running from the directory yields the same result.

the script in the base directory of ut2004 reads:

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

that script loots executable to me:

```
colzybub@colzybub-desktop:~$ ls -l /vFATPartition/ut2004
-rwxr-xr-x 1 colzybub users 1251 2006-07-03 19:42 /vFATPartition/ut2004
```

as is the bin file:

```
colzybub@colzybub-desktop:~$ ls -l /vFATPartition/System/ut2004-bin
-rwxrwxrwx 1 colzybub users 12488812 2006-07-03 19:42 /vFATPartition/System/ut2004-bin
```

and this points the right way too:

lrwxrwxrwx 1 root root 20 2006-06-29 21:32 /usr/local/bin/ut -> /vFATPartition/ut/ut

i even just reinstalled the game and no difference (though i forgot to put it in a directory so the files are  abit messy atm)

---

### Post by Grimmeehh on 2006-07-03
ok i figured i would install quake4 to see if it was a global thing but i cant access the dvd drive to copy files required. :neutral: and i cant get in there via the console either (probably cos of my lack of knowledge, and lack of ability to find pages that tell me what to do) .. so thats out the window.

tempted to say bugger it, but i do want to be able to use linux effectively, and i know it takes time to learn this stuff.

---

### Post by crane on 2006-07-03
I'll think on this  a bit, one question, are you using xgl or compiz? Last I recalled 3D games did not funtion well when running xgl.
Also, have you tried running it with sudo just to see if it works. Depending on where you installed it you may not have permissions.

---

### Post by Grimmeehh on 2006-07-04
sudo makes no difference, as far as i can tell permissions are fine where its installed.

(no idea about compiz or xgl, .. so i dont know, perhaps ive missed something vitally important- yes i have installed nvidia drivers and get the nvidia splash screen) im using a basic clean install of ubuntu, so whatever it uses by default.

I did follow a guide to make a script for nonXgl, but that doesnt work either.

```
colzybub@colzybub-desktop:~$ nonXgl ut
non-network local connections being added to access control list
/usr/bin/nonXgl: line 15: /usr/local/bin/ut: Permission denied
/usr/bin/nonXgl: line 15: /usr/local/bin/ut: Success

```

which is an odd message.

thanks for the help

---

### Post by Grimmeehh on 2006-07-05
absolutely bizzare. I gave up, formatted the other drive and ran liveCD and changed the partition size to 60gb on /

ran the installer, works first time. crazy, dont understand why it wouldnt work on a different drive. Oh well. Thanks for the help anyway chaps! maybe one to remember if anyone else gets that problem.

---

### Post by lordmule on 2006-07-05
I had the same problem after upgrading to dapper. I continued to use my old /home but /etc/fstab mounted it without exec permissions thus I could execute any applications from that disk

I modified my /etc/fstab for the /home  like this

/dev/hdc4       /home           ext3    rw,user,exec         0       2

my ut is stored on my /home btw 
i was once again able to play ut again ;)

---

