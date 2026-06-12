---
title: "Can't install Unreal Gold"
date: 2007-03-19
forum: Gaming &amp; Leisure
---

### Post by bluehue on 2007-03-19
Hey everyone,

I'm having trouble installing Unreal Gold (single player, not Tournament) on Edgy. I'm using the "unreali-install.run" installer from [http://icculus.org/~chunky/ut/unreal/](http://icculus.org/~chunky/ut/unreal/)

This is the error output I'm getting:
```

sudo sh unreali-install.run
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." unreali-install.run -check
 All good.
Uncompressing UnrealI for Linuxtail: Warning: "+number" syntax is deprecated, please use "-n +number"
........................................................
/home/spiral/.setup3644: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The program returned an error code (127) 
```
Any ideas where the problem might be? :confused:

---

### Post by conjur3r on 2007-03-19
Try installing libgtk:

 # sudo apt-get install libgtk1.2

---

### Post by bluehue on 2007-03-19
> **conjur3r said:**
> Try installing libgtk:

 # sudo apt-get install libgtk1.2
Wow, thanks! The installer fired right up as soon as I got that installed. However, my problem is now different as I can't start the game:
```

/usr/local/games/unreal$ unreal
dirname: missing operand
Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?

```
I tried setting the environment variables as per the installer instructions at [http://icculus.org/~chunky/ut/unreal/README.Chunky](http://icculus.org/~chunky/ut/unreal/README.Chunky)
```

export UT_INSTALL=/usr/local/games/ut/
and
export UT_INSTALL=/usr/local/games/unreal 

```
To no avail. I'm thinking it's not working because the above paths are for UT, and not for Unreal Gold.

---

### Post by bluehue on 2007-03-19
Also tried the following:
```

export UT_DATA_PATH=/usr/local/games/unreal
spiral@spiral-desktop:/usr/local/games/unreal$ unreal
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?

``` and...
```

export UT_DATA_PATH=/usr/local/games/unreal/System
spiral@spiral-desktop:/usr/local/games/unreal$ unreal
./UnrealTournament: error while loading shared libraries: Engine.so: cannot open shared object file: No such file or directory

``` :confused: :(

---

### Post by conjur3r on 2007-03-19
> **bluehue said:**
> 
```

/usr/local/games/unreal$ unreal
dirname: missing operand
Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?

```


Try
 /usr/local/games/unreal$ ./unreal

Note the **./** which means to execute the binary in the current folder.

---

### Post by bluehue on 2007-03-19
> **conjur3r said:**
> Try
 /usr/local/games/unreal$ ./unreal

Note the **./** which means to execute the binary in the current folder.
It gives me the same error as if I had typed "unreal"
```

./unreal
./UnrealTournament: error while loading shared libraries: Engine.so: cannot open shared object file: No such file or directory

```
Mind you, the UT_DATA_PATH is set to:
```

UT_DATA_PATH=/usr/local/games/unreal/System

```
When I enter:
```

export UT_DATA_PATH=/usr/local/games/unreal

```
I get the following error:
```

spiral@spiral-desktop:/usr/local/games/unreal$ ./unreal
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?

```

---

### Post by conjur3r on 2007-03-19
Where did you install to?  The instructions you linked to didn't have anything special after installation.

Try unsetting all of those environment variables you've added just so that we can start from a clean slate.  Then try executing unreal again.

 # unset UT_DATA_PATH
 # unset UT_INSTALL

What error messages do you get?  If you get the same one, try running ldd and copy the output here.
 # ldd unreal

---

### Post by conjur3r on 2007-03-19
I just did a quick search and it turns out that the instructions you're using is installing Unreal Gold as a mod for Unreal Tournament.  This means that you need Unreal Tournament installed!

Here's the page [http://icculus.org/~ravage/unreal/unrealgold/](http://icculus.org/~ravage/unreal/unrealgold/) for more information.

---

### Post by bluehue on 2007-03-19
Here's the output I get:
```

spiral@spiral-desktop:/usr/local/games/unreal$ unset UT_DATA_PATH
spiral@spiral-desktop:/usr/local/games/unreal$ unset UT_INSTALL
spiral@spiral-desktop:/usr/local/games/unreal$ ./unreal
./UnrealTournament: error while loading shared libraries: Engine.so: cannot open shared object file: No such file or directory
spiral@spiral-desktop:/usr/local/games/unreal$ ldd unreal
        not a dynamic executable

```

---

### Post by bluehue on 2007-03-19
You're absolutely correct. From [http://www.linuxhardware.org/article.pl?sid=03/04/18/169209:](http://www.linuxhardware.org/article.pl?sid=03/04/18/169209:)
> 
The original Unreal can also be run natively in Linux, provided you have Unreal Tournament already. It runs as an addon expansion pack, which is good, as you can usually find Totally Unreal in stores still, which includes both games. Then just head over to icculus.org and grab ravage's Unreal Gold installer, and you're good to go. If you have the original version of Unreal, you should use Chunky's UnrealI installer instead. Note that the interface it uses is that of Unreal Tournament, but the game content is the same as Unreal. This is not supported by Epic Games at all, but if you want some single-player Unreal action, this is a great hack. Also, ravage has provided an installer for the Return to Na Pali expansion pack. Note that Unreal Gold includes this expansion on the Unreal Gold disc. 
Unreal original and/or Gold may only be played as add-ons to UT and cannot be ran as standalone games. Off to get a hold of UT!

Thanks for the help conjur3r! :)

---

### Post by conjur3r on 2007-03-19
Good luck with it.  At least we learnt that we did nothing wrong :)

---

### Post by Dritzen on 2007-03-19
You're probably going to get Unreal Tournament installed and then find that it plays super fast.

I had the same issue but there's a script on this forum that allows you to slow UT down before it starts.  A quick search should find it though.

Good luck.

---

