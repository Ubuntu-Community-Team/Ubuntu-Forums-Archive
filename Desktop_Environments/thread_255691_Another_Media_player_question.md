---
title: "Another Media player question"
date: 2006-09-11
forum: Desktop Environments
---

### Post by Badchoices on 2006-09-11
Ok, I've scoured the site and don't appear to be able to find an answer.  How do I get the  Windows media player codecs to work (and where to get them from?).
Obviously I'm new to Linux, so a little advice would be great.  I'd have to say though, the installation was a breeze and everything works.  Just have to convince the wife that this is the better way to go, then I can retire XP.
Cheers](*,)

---

### Post by newlinux on 2006-09-11
take a look at:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by Badchoices on 2006-09-11
Brilliant - thanks for that.

---

### Post by newlinux on 2006-09-11
And welcome to Linux and Ubuntu. Happy ubuntuing...

---

### Post by Badchoices on 2006-09-26
Ok, tried everything - and had partial success.  In Totem, I managed to get the video working for WMV files, just no sound.  I went back to check the codecs I had installed and all seemed fine until I updated them again - and I seem to be back to square one (again).  I haven't given up, just taking a step back.

Also, the Mozilla-Mplayer extension for firefox isn't happy - the error I'm getting back involves a dependancy failure:
mozilla-mplayer:
 Depends: mplayer (>=1.0-pre5) but it is not installable or
 	mplayer-nogui (>=1.0-pre5) but it is not installable or
 	mplayer-powerpc (>=1.0-pre5) but it is not installable or
 	mplayer-g4 (>=1.0-pre5) but it is not installable
Doesn't appear to say much more than that - and unfortunately - I've had 11yrs of windows exposure (although have now thrown it out the window and now completely Ubuntu, so still feeling my way around.

Any information would be useful. - Thanks:-k

---

### Post by LORD_PoLvO on 2006-09-26
looks like u need to update ur sources list, hmm kk 

[http://http://www.ubuntulinux.nl/source-o-matic]("http://http://www.ubuntulinux.nl/source-o-matic")

that site is the source o matic there you can get a newer sources list which will include the dependencies you need. :D

to edit your sources list just do this 

```
alt-f2
gnome-terminal

```

```
sudo gedit /etc/apt/sources.list
```

then replace what is in there with teh updated sources list from the source o matic that should help u  ;D

Happy ubuntuing my friend

---

### Post by LORD_PoLvO on 2006-09-26
also remember after taht is done use the command 

```
sudo apt-get update
```

this updates your new sources

thenm installing should be as simple as sudo apt-get install program_name

---

### Post by Badchoices on 2006-09-26
Hey - cheers for the advise. To be honest with you, I'm not sure what I've done now - nothing broken through, must be a good thing.

Depends: mplayer (>=1.0-pre5) but it is not installable or
 	mplayer-nogui (>=1.0-pre5) but it is not installable or
 	mplayer-powerpc (>=1.0-pre5) but it is not installable or
 	mplayer-g4 (>=1.0-pre5) but it is not installable
{managed to grab all of the above}
Also requires:
libfaac0
libmp4v2-0_2.0.0
libxvidcore4

Interestingly enough, when I installed -powerpc then -g4 it complained that -g4 wouldn't install because of -powerpc.

Now - the good news is that it appears that I can play streaming WMV format - but it doesn't look as if Totem will play WMV files - still complains about missing codecs.

To the best of knowledge - would the OS require a restart to commit the codecs?  Which wouldn't make a lot of sense since it has picked up the streaming files ok?  I guess I'm learning..

---

### Post by Avenue on 2006-09-27
Instead of starting another thread, I thought i'd paste my questions here.

I am very new to Linux and trying to install the codecs for Windows Media files and came across this post.  After going to the RestrictedFormats page, I copied and pasted the install commands and ran them.  After this is run or installed, I get this error:

chad@Avenue:~$ sudo dpkg -i w32codecs_20060611-1plf1_i386.de
Password:
dpkg: error processing w32codecs_20060611-1plf1_i386.de (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-1plf1_i386.de

Unfortunately I have no idea what this means.  What do I do next?

Thanks for the help!!

---

### Post by Badchoices on 2006-09-27
Hi Avenue,
To be honest not sure I can help much, however, I jotted down everything I did after I got it working, and I'm sure there are easier ways of doing this, but I'm still learning, however, see if this helps:

Before installing the Mozilla-Mplayer componant under the Symatic software installer, connect to [http://packages.ubuntulinux.org/](http://packages.ubuntulinux.org/)
Enter the name of these:
mplayer-nogui
mplayer-powerpc 
mplayer-g4
libfaac0
libmp4v2-0_2.0.0
libxvidcore4

Installation process appears to be in the following order;

1. libfaac0
2. libmp4v2-0_2.0.0
3. libxvidcore4
4. Mplayer-nogui
5. mplayer-powerpc
6. mplayer-g4
7. Mozilla-mplayer

Note*: either -nogui & -powerpc seems to have a conflict with the other, as such there will be errors, doesn't appear to make a difference, so not sure what's going on.

Also, all of this managed to get streaming WMV files to work off the net and via Firefox - didn't appear to make a difference to the codec's for Totem Movie Player.  The way I've got around that is to open the WMV files in a firefox browser and it works.
Ultimately it would be great to get Movie Player to work as well, but in the meantime, all good.

---

### Post by Badchoices on 2006-09-27
and, yes, I've just noticed, I've mis-spelt several things :-)

---

