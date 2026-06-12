---
title: "New terminal user needs help"
date: 2013-10-31
forum: Gaming &amp; Leisure
---

### Post by blightedagent on 2013-10-31
As a TCG player who just switched to Linux I was surprised to find this thread: [http://ubuntuforums.org/showthread.php?t=1503674](http://ubuntuforums.org/showthread.php?t=1503674)  

Astoundingly, my copying and pasting seemed to work. I have a new folder called "gccg"  with all applicable files.  The "ccg-client"  icon appears to be a zip file?  How can I open it to run the client?  I'm sure the directions from the previous post told me but I can't seem to make it work. I'm a super newb and the command line frightens and confuses me, but this seemed to work(way better than the other dozens of terminal command failures i've tried).  It seems I'm close to actually using this program so any help is greatly appreciated.

---

### Post by dannyboy79 on 2013-10-31
did you do all this? go to the folder within the terminal by using the cd command to "change directory" and type this in the terminal
```
./Mtg
```
what happens?

---

### Post by blightedagent on 2013-11-01
No such file or directory.  I thought I did everything correctly.  After copying and pasting each of the commands I never got any error messages and I noticed it downloading a lot of stuff.  Maybe I missed something.

---

### Post by dannyboy79 on 2013-11-02
ok, let's step back and see which steps you've accomplished. Im looking at the install steps here: [http://gccg.sourceforge.net/](http://gccg.sourceforge.net/)
```
mkdir gccg
```

```
cd gccg
```

```
wget http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz
```	

```
tar xzvf gccg-core-1.0.10.tgz
```	

```
./gccg_package install client fonts linux-i386
```

If everything went right you can finally use gccg_package to install the game modules

View the list available modules
```
./gccg_package status
```
Install game modules you wish to play
./gccg_package install <game>[/CODE]

did you do all that?

---

### Post by blightedagent on 2013-11-02
I can do everything up to the font install, but when I type this:  
./gccg_package status

It says no such directory found.  

And to install game modules I'm assuming that in the space of <game> I want to put Mtg.  I've tried both and they both says no such directory found.

---

### Post by dannyboy79 on 2013-11-03
i am not sure what you're doing wrong as I just performed the steps above and when I run
```
./gccg_package status
```
it shows me all available modules just fine
```
---
---
Fetching module list [1] [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)
** GET [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml) ==> 200 OK
---
Fetching module list [2] [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
** GET [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml) ==> 200 OK
---
Fetching module list [3] [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)
** GET [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml) ==> 200 OK (1s)
---
Fetching module list [4] [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)
** GET [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml) ==> 200 OK
---
Fetching module list [5] [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)
** GET [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml) ==> 200 OK
============================================================
                     STATUS OF MODULES
============================================================
Module              | Installed | Available | Status  | Src
------------------------------------------------------------
client              | v0.9.7.9  | v0.9.7.9  | OK      | [1]
coc                 |           | v0.2      | -       | [4]
coc-decks           |           | v0.1      | -       | [4]
coc-official-sets   |           | v0.1      | -       | [4]
coc-server          |           | v0.1      | -       | [4]
core                | v1.0.10   | v1.0.10   | OK      | [1]
darwin-i386         |           | v0.9.6.0  | -       | [1]
dev-tools           |           | v2.0      | -       | [4]
docs                |           | v0.4.148  | -       | [2]
fonts               | v2.0      | v2.0      | OK      | [1]
fonts-windows       |           | v2.0      | -       | [4]
linux-i386          | v0.9.7.0.1| v0.9.7.0.1| OK      | [1]
linux-x86_64        |           | v0.9.7.0  | -       | [1]
lotr                |           | v1.2.0    | -       | [3]
lotr-server         |           | v0.9.0    | -       | [2]
metw                |           | v1.0.164  | -       | [2]
metw-de             |           | v0.7      | -       | [2]
metw-server         |           | v0.8.97   | -       | [2]
mtg                 |           | v1.3.9    | -       | [2]
mtg-cards           |           | v1.87.0   | -       | [2]
mtg-cards-000       |           | v24       | -       | [2]
mtg-cards-001       |           | v15       | -       | [2]
mtg-cards-002       |           | v16       | -       | [2]
mtg-cards-003       |           | v15       | -       | [2]
mtg-cards-004       |           | v15       | -       | [2]
mtg-cards-005       |           | v15       | -       | [2]
mtg-cards-006       |           | v15       | -       | [2]
mtg-cards-007       |           | v15       | -       | [2]
mtg-cards-008       |           | v15       | -       | [2]
mtg-cards-009       |           | v15       | -       | [2]
mtg-cards-010       |           | v15       | -       | [2]
mtg-cards-011       |           | v15       | -       | [2]
mtg-cards-012       |           | v15       | -       | [2]
mtg-cards-013       |           | v15       | -       | [2]
mtg-cards-014       |           | v15       | -       | [2]
mtg-cards-015       |           | v15       | -       | [2]
mtg-cards-016       |           | v15       | -       | [2]
mtg-cards-017       |           | v15       | -       | [2]
mtg-cards-018       |           | v15       | -       | [2]
mtg-cards-019       |           | v15       | -       | [2]
mtg-cards-020       |           | v15       | -       | [2]
mtg-cards-021       |           | v15       | -       | [2]
mtg-cards-022       |           | v15       | -       | [2]
mtg-cards-023       |           | v15       | -       | [2]
mtg-cards-024       |           | v15       | -       | [2]
mtg-cards-025       |           | v15       | -       | [2]
mtg-cards-026       |           | v15       | -       | [2]
mtg-cards-027       |           | v15       | -       | [2]
mtg-cards-028       |           | v15       | -       | [2]
mtg-cards-029       |           | v15       | -       | [2]
mtg-cards-030       |           | v15       | -       | [2]
mtg-cards-031       |           | v15       | -       | [2]
mtg-cards-032       |           | v15       | -       | [2]
mtg-cards-033       |           | v15       | -       | [2]
mtg-cards-034       |           | v15       | -       | [2]
mtg-cards-035       |           | v15       | -       | [2]
mtg-cards-036       |           | v15       | -       | [2]
mtg-cards-037       |           | v15       | -       | [2]
mtg-cards-038       |           | v15       | -       | [2]
mtg-cards-039       |           | v15       | -       | [2]
mtg-cards-040       |           | v15       | -       | [2]
mtg-cards-041       |           | v15       | -       | [2]
mtg-cards-042       |           | v15       | -       | [2]
mtg-cards-043       |           | v15       | -       | [2]
mtg-cards-044       |           | v15       | -       | [2]
mtg-cards-045       |           | v15       | -       | [2]
mtg-cards-046       |           | v15       | -       | [2]
mtg-cards-047       |           | v15       | -       | [2]
mtg-cards-048       |           | v15       | -       | [2]
mtg-cards-049       |           | v15       | -       | [2]
mtg-cards-050       |           | v15       | -       | [2]
mtg-cards-051       |           | v15       | -       | [2]
mtg-cards-052       |           | v15       | -       | [2]
mtg-cards-053       |           | v15       | -       | [2]
mtg-cards-054       |           | v15       | -       | [2]
mtg-cards-055       |           | v15       | -       | [2]
mtg-cards-056       |           | v15       | -       | [2]
mtg-cards-057       |           | v15       | -       | [2]
mtg-cards-058       |           | v15       | -       | [2]
mtg-cards-059       |           | v15       | -       | [2]
mtg-cards-060       |           | v15       | -       | [2]
mtg-cards-061       |           | v15       | -       | [2]
mtg-cards-062       |           | v15       | -       | [2]
mtg-cards-063       |           | v15       | -       | [2]
mtg-cards-064       |           | v15       | -       | [2]
mtg-cards-065       |           | v15       | -       | [2]
mtg-cards-066       |           | v15       | -       | [2]
mtg-cards-067       |           | v15       | -       | [2]
mtg-cards-068       |           | v15       | -       | [2]
mtg-cards-069       |           | v15       | -       | [2]
mtg-cards-070       |           | v15       | -       | [2]
mtg-cards-071       |           | v15       | -       | [2]
mtg-cards-072       |           | v15       | -       | [2]
mtg-cards-073       |           | v15       | -       | [2]
mtg-cards-074       |           | v15       | -       | [2]
mtg-cards-075       |           | v15       | -       | [2]
mtg-cards-076       |           | v2        | -       | [2]
mtg-cards-077       |           | v2        | -       | [2]
mtg-cards-078       |           | v1        | -       | [2]
mtg-cards-079       |           | v1        | -       | [2]
mtg-cards-080       |           | v3        | -       | [2]
mtg-cards-081       |           | v2        | -       | [2]
mtg-cards-082       |           | v1        | -       | [2]
mtg-cards-083       |           | v1        | -       | [2]
mtg-cards-084       |           | v1        | -       | [2]
mtg-cards-085       |           | v2        | -       | [2]
mtg-cards-086       |           | v2        | -       | [2]
mtg-cards-087       |           | v1        | -       | [2]
mtg-server          |           | v1.3.9    | -       | [2]
nr                  |           | v1.2      | -       | [4]
nr-decks            |           | v1.0      | -       | [4]
nr-official-sets    |           | v1.0      | -       | [4]
nr-server           |           | v1.1      | -       | [4]
nr-virtual-sets     |           | v1.0      | -       | [4]
poker               |           | v0.4.7    | -       | [2]
server              |           | v0.9.7.9  | -       | [1]
source              |           | v0.9.7.9  | -       | [1]
windows32           |           | v0.9.7.0  | -       | [1]
wt                  |           | v0.0.1    | -       | [5]
============================================================

```
are you mistyping something? type in "./gc" (without quotes obviously) and then hit the tab key to have it auto-complete the command. copy and paste what the few lines from the terminal so I can see what you're typing.

---

### Post by blightedagent on 2013-11-03
I must have missed something.  
 
zoomzilla@zoomzilla-Inspiron-N5040:~$ ./gc
bash: ./gc: No such file or directory
zoomzilla@zoomzilla-Inspiron-N5040:~$ 


If I follow the instructions again that shouldn't do any harm correct?

---

### Post by blightedagent on 2013-11-03
so I deleted my GCCG folder and started the whole process over again.  here were my results.

```
zoomzilla@zoomzilla-Inspiron-N5040:~$ mkdir gccg
zoomzilla@zoomzilla-Inspiron-N5040:~$ cd gccg
zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ wget [http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz](http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz)
--2013-11-03 16:51:48--  [http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz](http://gccg.sourceforge.net/modules/gccg-core-1.0.10.tgz)
Resolving gccg.sourceforge.net (gccg.sourceforge.net)... 216.34.181.96
Connecting to gccg.sourceforge.net (gccg.sourceforge.net)|216.34.181.96|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 22409 (22K) [application/x-gzip]
Saving to: `gccg-core-1.0.10.tgz'

100%[========================>] 22,409       140K/s   in 0.2s    

2013-11-03 16:51:49 (140 KB/s) - `gccg-core-1.0.10.tgz' saved [22409/22409]

zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ tar xzvf gccg-core-1.0.10.tgz
./
./xml/
./xml/gccg-game.dtd
./xml/modules.dtd
./xml/gccg-set.dtd
./xml/installed.xml
./decks/
./gccg_package
./doc/
./tools/
./tools/launch_client
./sounds/
./COPYING
./scripts/
./scripts/common.include
./lib/
./games.dat
./graphics/
zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ ./gccg_package install client fonts linux-i386                                           
---                                                               
Fetching module list [1] [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)                                                          
** GET [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml) ==> 200 OK (2s)
---
Fetching module list [2] [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
** GET [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml) ==> 200 OK (1s)
---
Fetching module list [3] [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)
** GET [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml) ==> 200 OK (1s)
---
Fetching module list [4] [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)
** GET [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml) ==> 200 OK (2s)
---
Fetching module list [5] [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)
** GET [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml) ==> 10200 OK (1s)
Fetching [http://gccg.sourceforge.net/modules/gccg-client-0.9.7.9.tgz](http://gccg.sourceforge.net/modules/gccg-client-0.9.7.9.tgz)
** GET [http://gccg.sourceforge.net/modules/gccg-client-0.9.7.9.tgz](http://gccg.sourceforge.net/modules/gccg-client-0.9.7.9.tgz) ==> 200 OK (49s)
Fetching [http://gccg.sourceforge.net/modules/gccg-linux-i386-0.9.7.0.1.tgz](http://gccg.sourceforge.net/modules/gccg-linux-i386-0.9.7.0.1.tgz)
** GET [http://gccg.sourceforge.net/modules/gccg-linux-i386-0.9.7.0.1.tgz](http://gccg.sourceforge.net/modules/gccg-linux-i386-0.9.7.0.1.tgz) ==> 200 OK (17s)
Fetching [http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz](http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz)
** GET [http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz](http://gccg.sourceforge.net/modules/gccg-fonts-2.0.tgz) ==> 200 OK (10s)
Installing module client
Installing module linux-i386
Installing module fonts
zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ ./gccg_package status
---
Fetching module list [1] [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)
** GET [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml) ==> 200 OK
---
Fetching module list [2] [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
** GET [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml) ==> 200 OK (2s)
---
Fetching module list [3] [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)
** GET [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml) ==> 200 OK
---
Fetching module list [4] [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)
** GET [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml) ==> 200 OK (1s)
---
Fetching module list [5] [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)
** GET [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml) ==> 10200 OK (1s)
============================================================
                     STATUS OF MODULES
============================================================
Module              | Installed | Available | Status  | Src
------------------------------------------------------------
client              | v0.9.7.9  | v0.9.7.9  | OK      | [1]
coc                 |           | v0.2      | -       | [4]
coc-decks           |           | v0.1      | -       | [4]
coc-official-sets   |           | v0.1      | -       | [4]
coc-server          |           | v0.1      | -       | [4]
core                | v1.0.10   | v1.0.10   | OK      | [1]
darwin-i386         |           | v0.9.6.0  | -       | [1]
dev-tools           |           | v2.0      | -       | [4]
docs                |           | v0.4.148  | -       | [2]
fonts               | v2.0      | v2.0      | OK      | [1]
fonts-windows       |           | v2.0      | -       | [4]
linux-i386          | v0.9.7.0.1| v0.9.7.0.1| OK      | [1]
linux-x86_64        |           | v0.9.7.0  | -       | [1]
lotr                |           | v1.2.0    | -       | [3]
lotr-server         |           | v0.9.0    | -       | [2]
metw                |           | v1.0.164  | -       | [2]
metw-de             |           | v0.7      | -       | [2]
metw-server         |           | v0.8.97   | -       | [2]
mtg                 |           | v1.3.9    | -       | [2]
mtg-cards           |           | v1.87.0   | -       | [2]
mtg-cards-000       |           | v24       | -       | [2]
mtg-cards-001       |           | v15       | -       | [2]
mtg-cards-002       |           | v16       | -       | [2]
mtg-cards-003       |           | v15       | -       | [2]
mtg-cards-004       |           | v15       | -       | [2]
mtg-cards-005       |           | v15       | -       | [2]
mtg-cards-006       |           | v15       | -       | [2]
mtg-cards-007       |           | v15       | -       | [2]
mtg-cards-008       |           | v15       | -       | [2]
mtg-cards-009       |           | v15       | -       | [2]
mtg-cards-010       |           | v15       | -       | [2]
mtg-cards-011       |           | v15       | -       | [2]
mtg-cards-012       |           | v15       | -       | [2]
mtg-cards-013       |           | v15       | -       | [2]
mtg-cards-014       |           | v15       | -       | [2]
mtg-cards-015       |           | v15       | -       | [2]
mtg-cards-016       |           | v15       | -       | [2]
mtg-cards-017       |           | v15       | -       | [2]
mtg-cards-018       |           | v15       | -       | [2]
mtg-cards-019       |           | v15       | -       | [2]
mtg-cards-020       |           | v15       | -       | [2]
mtg-cards-021       |           | v15       | -       | [2]
mtg-cards-022       |           | v15       | -       | [2]
mtg-cards-023       |           | v15       | -       | [2]
mtg-cards-024       |           | v15       | -       | [2]
mtg-cards-025       |           | v15       | -       | [2]
mtg-cards-026       |           | v15       | -       | [2]
mtg-cards-027       |           | v15       | -       | [2]
mtg-cards-028       |           | v15       | -       | [2]
mtg-cards-029       |           | v15       | -       | [2]
mtg-cards-030       |           | v15       | -       | [2]
mtg-cards-031       |           | v15       | -       | [2]
mtg-cards-032       |           | v15       | -       | [2]
mtg-cards-033       |           | v15       | -       | [2]
mtg-cards-034       |           | v15       | -       | [2]
mtg-cards-035       |           | v15       | -       | [2]
mtg-cards-036       |           | v15       | -       | [2]
mtg-cards-037       |           | v15       | -       | [2]
mtg-cards-038       |           | v15       | -       | [2]
mtg-cards-039       |           | v15       | -       | [2]
mtg-cards-040       |           | v15       | -       | [2]
mtg-cards-041       |           | v15       | -       | [2]
mtg-cards-042       |           | v15       | -       | [2]
mtg-cards-043       |           | v15       | -       | [2]
mtg-cards-044       |           | v15       | -       | [2]
mtg-cards-045       |           | v15       | -       | [2]
mtg-cards-046       |           | v15       | -       | [2]
mtg-cards-047       |           | v15       | -       | [2]
mtg-cards-048       |           | v15       | -       | [2]
mtg-cards-049       |           | v15       | -       | [2]
mtg-cards-050       |           | v15       | -       | [2]
mtg-cards-051       |           | v15       | -       | [2]
mtg-cards-052       |           | v15       | -       | [2]
mtg-cards-053       |           | v15       | -       | [2]
mtg-cards-054       |           | v15       | -       | [2]
mtg-cards-055       |           | v15       | -       | [2]
mtg-cards-056       |           | v15       | -       | [2]
mtg-cards-057       |           | v15       | -       | [2]
mtg-cards-058       |           | v15       | -       | [2]
mtg-cards-059       |           | v15       | -       | [2]
mtg-cards-060       |           | v15       | -       | [2]
mtg-cards-061       |           | v15       | -       | [2]
mtg-cards-062       |           | v15       | -       | [2]
mtg-cards-063       |           | v15       | -       | [2]
mtg-cards-064       |           | v15       | -       | [2]
mtg-cards-065       |           | v15       | -       | [2]
mtg-cards-066       |           | v15       | -       | [2]
mtg-cards-067       |           | v15       | -       | [2]
mtg-cards-068       |           | v15       | -       | [2]
mtg-cards-069       |           | v15       | -       | [2]
mtg-cards-070       |           | v15       | -       | [2]
mtg-cards-071       |           | v15       | -       | [2]
mtg-cards-072       |           | v15       | -       | [2]
mtg-cards-073       |           | v15       | -       | [2]
mtg-cards-074       |           | v15       | -       | [2]
mtg-cards-075       |           | v15       | -       | [2]
mtg-cards-076       |           | v2        | -       | [2]
mtg-cards-077       |           | v2        | -       | [2]
mtg-cards-078       |           | v1        | -       | [2]
mtg-cards-079       |           | v1        | -       | [2]
mtg-cards-080       |           | v3        | -       | [2]
mtg-cards-081       |           | v2        | -       | [2]
mtg-cards-082       |           | v1        | -       | [2]
mtg-cards-083       |           | v1        | -       | [2]
mtg-cards-084       |           | v1        | -       | [2]
mtg-cards-085       |           | v2        | -       | [2]
mtg-cards-086       |           | v2        | -       | [2]
mtg-cards-087       |           | v1        | -       | [2]
mtg-server          |           | v1.3.9    | -       | [2]
nr                  |           | v1.2      | -       | [4]
nr-decks            |           | v1.0      | -       | [4]
nr-official-sets    |           | v1.0      | -       | [4]
nr-server           |           | v1.1      | -       | [4]
nr-virtual-sets     |           | v1.0      | -       | [4]
poker               |           | v0.4.7    | -       | [2]
server              |           | v0.9.7.9  | -       | [1]
source              |           | v0.9.7.9  | -       | [1]
windows32           |           | v0.9.7.0  | -       | [1]
wt                  |           | v0.0.1    | -       | [5]
============================================================
zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ ./gccg_package install <Mtg>
bash: Mtg: No such file or directory
zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ ./gccg_package install <game>
bash: game: No such file or directory
zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ ./gccg_package install Mtg
---
Fetching module list [1] [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml)
** GET [http://gccg.sourceforge.net/modules/available.xml](http://gccg.sourceforge.net/modules/available.xml) ==> 200 OK (1s)
---
Fetching module list [2] [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml)
** GET [http://www.reneploetz.de/gccg/available.xml](http://www.reneploetz.de/gccg/available.xml) ==> 200 OK (2s)
---
Fetching module list [3] [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml)
** GET [http://lotrtcgwiki.com/files/gccg/available.xml](http://lotrtcgwiki.com/files/gccg/available.xml) ==> 200 OK (1s)
---
Fetching module list [4] [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml)
** GET [http://games.phtn.de/gccg/available.xml](http://games.phtn.de/gccg/available.xml) ==> 200 OK (1s)
---
Fetching module list [5] [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml)
** GET [http://wtactics.org/files/gccg/modules/available.xml](http://wtactics.org/files/gccg/modules/available.xml) ==> 10200 OK
zoomzilla@zoomzilla-Inspiron-N5040:~/gccg$ 
```




It appears I've done it correctly,but now Im unsure how to actually run the client.  Thanks for all your help so far, I really appreciate you walking a newb like me through all this.

---

### Post by dannyboy79 on 2013-11-05
have you tried just ```
./mtg
```

---

### Post by blightedagent on 2013-11-06
yeah, no such directory.

---

### Post by drmrgd on 2013-11-06
> **blightedagent said:**
> yeah, no such directory.

According to the instructions at their sourceforge page, you need to run the game with a capital letter:

> 
Each game module has a startup script with the same name as the module, with capitalized first letter. You can launch the game using it. 


i.e. for metw module
```
./Metw
```


From the gccg directory, try it with:

```

./Mtg

```

---

### Post by blightedagent on 2013-11-07
yeah, that was what I first tried.

---

