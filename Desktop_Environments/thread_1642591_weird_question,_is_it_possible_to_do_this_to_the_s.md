---
title: "weird question, is it possible to do this to the startup sound?"
date: 2010-12-10
forum: Desktop Environments
---

### Post by beasdd on 2010-12-10
ok, so i'm pretty new to linux/ubuntu.  i recently downloaded 10.10 and have been trying to customize my desktop a bit.  I changed the login sound file "/usr/share/sounds/ubuntu/stereo/desktop-login.ogg" (i think that was the path) to a custom sound, and it works just fine when i'm loading it.

idk if this would be possible, but is there a relatively "simple" (if any) way to have a few different log in sounds?  what i'm trying to do is have 3-4 custom sounds, and a random one of them plays when i log in.  

any ideas?  i'm kind of expecting for this to be impossible lol. but as a lifetime windows user, i'm curious to see what i can do on linux.

even if this isn't possible, if anyone wants to share some cool customization tricks, that would be awesome. :p

---

### Post by joshedmonds on 2010-12-10
You could write a script to run on login that waits x seconds (enough to play the existing file) then replaces the ogg file with another file randomly chosen from a pool.

This is just an idea, and others may have something better to offer.

I would start with basic shell scripts (see [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html") or any of the other million or so guides out there).

EDIT: In case that sounds too complicated, it isn't. Basically you write a text file of about 5-10 lines (depending on functionality) rename it to have a sh extension, and make an entry in System->Preferences->Startup Applications pointing to that file. The only things you might have trouble with are permissions to replace the file at /usr/... and randomising the file choice (you may want to look at using /dev/random or similar).

---

### Post by beasdd on 2010-12-14
thanks for the reply

i pretty much just copied the backup files program the website you gave used as an example.. i know that the last two lines are definitely wrong, but i don't really know what to do from here.

here is what i have ```
#!/bin/bash
sleep 15
SRCD="/usr/share/sounds/ubuntu/stereo/desktop-login.ogg/"
rndm = [$((RANDOM%3))]
if [ rndm = 3 ]; then
  TGTD="/home/kevin/Music/All/fn.ogg"
else if [ rndm = 2 ]; then
  TGTD="/home/kevin/Music/All/fg.ogg"
else
  TGTD="/var/backups/"
fi
OF=home-$(date +%Y%m%d).tgz
tar -cZf $TGTD$OF $SRCD

```

---

### Post by joshedmonds on 2010-12-18
I'm trusting your random implementation because I don't know specifically how I would do it. The couple of lines at the end are declaring a variable to use as the file name, in this case for archiving with tar. Of course you could do something similar, but if you have a small number of files it may be easier to specify each.

An idea (not a tested script) assuming files are named 1.ogg-3.ogg:
```
#!/bin/bash
sleep 15
RAND = [$((RANDOM%3))]
SRCDIR = /home/kevin/Music/All/
DESTDIR = /usr/share/sounds/ubuntu/stereo/desktop-login.ogg
SRCFILE = $RAND.ogg
mv $SRCDIR$SRCFILE $DESTDIR

```

Or you could specify each file name (again, not tested):
```
#!/bin/bash
sleep 15
rndm = [$((RANDOM%3))]
if [ rndm = 3 ]; then
  mv /home/kevin/Music/All/3.ogg /usr/share/sounds/ubuntu/stereo/desktop-login.ogg/
else if [ rndm = 2 ]; then
  mv /home/kevin/Music/All/2.ogg /usr/share/sounds/ubuntu/stereo/desktop-login.ogg/
else
  mv /home/kevin/Music/All/1.ogg /usr/share/sounds/ubuntu/stereo/desktop-login.ogg/
fi

```

---

### Post by __Sun__ on 2010-12-18
Dear [joshedmonds]("http://ubuntuforums.org/member.php?u=570458"), your script will not run in a Bourne shell due to a minor syntax error.

I just did some tweaking on my Ubuntu and got the random startup-sound player to work.
Moving music files at startup is a costly operation so avoid it.
Beforehand place all your custom .ogg files in /usr/share/sounds/ubuntu/stereo.

Now, copy and paste this shell script to a local file.

```

#!/bin/sh

# Specifiy files without the .ogg extension
# They MUST be in /usr/share/sounds/ubuntu[studio]/stereo
MUSIC_FILE1=some_file
MUSIC_FILE2=some_other_file
MUSIC_FILE3=yet_another_file

# Increment this if you add more files
RAND_MAX=3
RAND=$((1 + $(od -An -N2 -i /dev/urandom) % $RAND_MAX))
eval RANDOM_FILE=$MUSIC_PATH/\$MUSIC_FILE$RAND

# GTK+ default login sound player
# You can change this mpg321 /full/path/to/file for playing .mp3 files
/usr/bin/canberra-gtk-play --id=$RANDOM_FILE --description="GNOME Login"

```Now place this script, say, at $HOME/scripts/login-sound.sh. Make it executable with *chmod +x ./login-sound.sh*.
Go to System->Preferences->Startup Applications
Find `GNOME Login Sound' and click the `edit' button. Now, add the full path to your script, erasing whatever path was there before (back up that command just in case).

It worked on my laptop.
You can customise the last line to play mp3 files too (Make sure you update the path if you do this).

---

