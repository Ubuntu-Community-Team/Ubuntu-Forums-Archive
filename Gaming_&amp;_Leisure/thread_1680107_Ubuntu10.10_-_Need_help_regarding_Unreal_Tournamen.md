---
title: "Ubuntu10.10 - Need help regarding Unreal Tournament."
date: 2011-02-02
forum: Gaming &amp; Leisure
---

### Post by Panties on 2011-02-02
Hi guys,
I seriously need help on installing this original "Unreal Tournament" classic. (not GOTY version) I have inserted the CD already.
I did try those from:-
[http://ubuntuforums.org/showthread.php?t=153181](http://ubuntuforums.org/showthread.php?t=153181)
&
[http://www.lokigames.com/products/ut/downloads/README.436](http://www.lokigames.com/products/ut/downloads/README.436)

but somehow, it failed.


I downloaded the files from [http://www.lokigames.com/products/ut/updates.php3](http://www.lokigames.com/products/ut/updates.php3)

and it did not work. Here's what i type in the terminal. 
digitallife@DigitalLife:~$ cd Downloads/
digitallife@DigitalLife:~/Downloads$ sudo chmod +x *.run
[sudo] password for digitallife: 
digitallife@DigitalLife:~/Downloads$ ls
CurseClient.application  PlayOnLinux_3.8.8 (1).deb  ut-436              ut.run
CurseSetup-3.0.0.10.exe  PlayOnLinux_3.8.8.deb      ut-install-428.run
mfc42.dll                setup.exe                  ut-install-436.run
msvcp60.dll              unreali-install.run        UTPatch436.run
digitallife@DigitalLife:~/Downloads$ sh ut-install-436.run
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 889744922 2341625838
digitallife@DigitalLife:~/Downloads$ sh ut-install-428.run
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 572276461 4007534314
digitallife@DigitalLife:~/Downloads$ sh ut-install-436.run --keep
Creating directory ut-436
mkdir: cannot create directory `ut-436': File exists
ut-install-436.run: 125: Cannot create target directory: not found
ut-install-436.run: 125: you should perhaps try option -target OtherDirectory: not found
digitallife@DigitalLife:~/Downloads$ sh ut-install-428.run --keep
Verifying archive integrity...tail: cannot open `+6' for reading: No such file or directory
Error in check sums 572276461 4007534314
digitallife@DigitalLife:~/Downloads$ 


It doesn't matter to me if it is 428 or 436, I just can't install the game. I do not know whats wrong. 
What have I done wrong?
I also re-download it from another mirror site and try it out, it just wont install. It shows the exact same error!

Please Help.

Regards,
Panties

---

### Post by R33D3M33R on 2011-02-02
Run this before installing:

```
export _POSIX2_VERSION=199209 
```

---

### Post by Panties on 2011-02-02
> **R33D3M33R said:**
> Run this before installing:

```
export _POSIX2_VERSION=199209 
```



OMG! Is that all? COOL! It worked!! Thanks man!! XD

Another issue, which I would like to share!
If you get error like
> Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?
I got this fix from 
> 
[http://ubuntuforums.org/archive/index.php/t-8053.html](http://ubuntuforums.org/archive/index.php/t-8053.html)

You need to set the UT_DATA_PATH variable to point to ut's system files. Try the following command before running ut:
export UT_DATA_PATH=/usr/games/ut/System
If that doesn't work try this:
export UT_DATA_PATH=/usr/local/games/ut/System
or replace the path value with the one that is correct for your system.



Which makes my UT work like a charm.
The only thing that I would like to know, where/how can I put this export UT_DATA_PATH=/usr/local/games/ut/System into the start-up system? 

Because everytime I want to play my UT in my terminal.. I have to..

```

export UT_DATA_PATH=/usr/local/games/ut/System
ut

```


which I would like to just type ut, and the game runs. Any idea?

---

### Post by kDDs on 2011-02-02
> **R33D3M33R said:**
> Run this before installing:

```
export _POSIX2_VERSION=199209 
```

Sorry to go off topic slightly, but what exactly does that do?

You have to use that command to install other loki games, like heroes 3.

---

### Post by R33D3M33R on 2011-02-03
> **Panties said:**
> OMG! Is that all? COOL! It worked!! Thanks man!! XD

Another issue, which I would like to share!
If you get error like

I got this fix from 



Which makes my UT work like a charm.
The only thing that I would like to know, where/how can I put this  export UT_DATA_PATH=/usr/local/games/ut/System into the start-up system?  

Because everytime I want to play my UT in my terminal.. I have to..

```

export UT_DATA_PATH=/usr/local/games/ut/System
ut

```
which I would like to just type ut, and the game runs. Any idea?

There should exist a file named ut (without extension) in the game root folder. 

/usr/local/games/ut/

It's a text script file that runs the UT binary. Open it with a text editor and set the variable there.


> **kDDs said:**
> Sorry to go off topic slightly, but what exactly does that do?

You have to use that command to install other loki games, like heroes 3.

I think it just tells the system that the installer uses older syntax.

---

### Post by Geezusjedi on 2011-02-06
all u need are these four files: 
libgtk1.2-common_1.2.10-18.1build2_all.deb
libglib1.2ldbl_1.2.10-19build1_i386.deb
libgtk1.2_1.2.10-18.1build2_i386.deb
unreal.tournament_436-multilanguage.run

run them in that order and when u get to the last file put the cd in before u run it. thats all.
i tried to atatch the files but got some security error. if u know how to get around that let me know.

---

