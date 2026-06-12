---
title: "How To Install Savage on AMD64/X86"
date: 2006-09-10
forum: Gaming &amp; Leisure
---

### Post by Casey on 2006-09-10
FOR BOTH THESE GUIDES, PERFORM ALL STEPS BEFORE RUNNING SAVAGE... now to the guides...

First the HowTo for the x86

download savage_linux.sh.gz ([http://downloads.s2games.com/online_orders/savage_linux.sh.gz]("http://downloads.s2games.com/online_orders/savage_linux.sh.gz")), extract the contents.
In the directory where savage_linux.sh resides:
```

$ chmod a+x savage_linux.sh
$ ./savage_linux.sh

```
To install the patch:
download the patch([http://liflg.org/?what=dl&catid=6&gameid=15&filename=savage_2.00c-english.update.run]("http://liflg.org/?what=dl&catid=6&gameid=15&filename=savage_2.00c-english.update.run")), open a terminal and navigate to the directory where the patch resides.
```

$ chmod a+x savage_2.00c-english.update.run
$ ./savage_2.00c-english.update.run

```

To install SEP3T
Download SEP-3T ([http://www.notforidiots.com/autoupdater/SEP-3T.tar.gz]("http://www.notforidiots.com/autoupdater/SEP-3T.tar.gz"))
Extract the contents of the SEP3T archive to a folder.  Enter that folder in the file manager.  Select All.  Copy the contents of that folder over to your savage directory overwriting when prompted.

Final Steps:
```

$ cd [your savage folder] (/home/casey/savage for me)
$ nano -w savage

```
Find this line:
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./savage.bin /home/casey/savage

Change it to look like this:
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin /home/casey/savage

ctrl-o		(Saves Changes)
ctrl-x		(Exits nano)
Note the single change (savage.bin to silverback.bin)

Congratulations, your x86 savage install is done and up to date.

*************
Now the howto for the AMD64

download savage_linux.sh.gz ([http://downloads.s2games.com/online_orders/savage_linux.sh.gz]("http://downloads.s2games.com/online_orders/savage_linux.sh.gz")), extract the contents.
In the directory where savage_linux.sh resides:
```

$ chmod a+x savage_linux.sh
$ ./savage_linux.sh --keep -target /home/casey/Desktop/
$ cd release/bin
$ cp -r x86 x86_64
$ cd ..
$ cd setup.data/bin/Linux
$ cp -r x86 x86_64
$ cd /home/casey/Desktop/release
$ ./INSTALL.linux

```
Installation has begun, continue with the patch.  You may delete the "release" folder created on your desktop.  I am also unaware of why using -target /home/casey/Desktop creates a subfolder release, but that appears to be how it works. You should, of course, replace /home/casey with the location where you would like to temporarily unpack it to.

To install the patch:
download the patch([http://liflg.org/?what=dl&catid=6&gameid=15&filename=savage_2.00c-english.update.run]("http://liflg.org/?what=dl&catid=6&gameid=15&filename=savage_2.00c-english.update.run")), open a terminal and navigate to the directory where the patch resides.
```

$ chmod a+x savage_2.00c-english.update.run
$ ./savage_2.00c-english.update.run --keep --target /home/casey/Desktop/patch
$ cd patch/bin/Linux/
$ cp -r x86 x86_64
$ cd /home/casey/Desktop/patch/
$ ./update.sh

```
You may now remove the patch folder on your desktop (or whever you extracted the patch to)

To install SEP3T
Download SEP-3T ([http://www.notforidiots.com/autoupdater/SEP-3T.tar.gz]("http://www.notforidiots.com/autoupdater/SEP-3T.tar.gz"))
Extract the contents of the SEP3T archive to a folder.  Enter that folder in the file manager.  Select All.  Copy the contents of that folder over to your savage directory overwriting when prompted.

Final Steps:
```

$ cd [your savage folder] (/home/casey/savage for me)
$ nano -w savage

```
Find this line:
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./savage.bin /home/casey/savage

Change it to look like this:
LD_LIBRARY_PATH=libs:$LD_LIBRARY_PATH ./silverback.bin /home/casey/savage

ctrl-o		(Saves Changes)
ctrl-x		(Exits nano)
Note the single change (savage.bin to silverback.bin)

Congratulations, your AMD64 savage install is done and up to date.

---

### Post by Existance0 on 2008-07-12
What if I downloaded the SFE version? Thus the update is already in with the game.

I found the answer to my question anyone else that needs this info its...

[here](http://www.newerth.com/smf/index.php/topic,259.0.html)

Fail :( 
```
arie@arie-desktop:~/Desktop/Savage$ ./savage.sh

```
returns
```

./savage.sh: 6: ./silverback.bin: Permission denied

```

Can someone tell me how to fix this.

---

