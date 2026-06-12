---
title: "How can i run these games?"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by eighthate on 2006-06-06
how Can i Run those games on linux 6.06?
Steam (for counter strike)
Diablo2+lord of destruction
starcraft+broodwar

Thanks

---

### Post by ZylGadis on 2006-06-06
There is a box in the upper right corner of your screen. It is called "search."

---

### Post by eighthate on 2006-06-06
[QUOTE=ZylGadis]There is a box in the upper right corner of your screen. It is called "search."[/QUOTE]
-.-
THANKS FOR UR HELP!
^^

---

### Post by patrick295767 on 2006-06-06
[QUOTE=eighthate]how Can i Run those games on linux 6.06?
Steam (for counter strike)
Diablo2+lord of destruction
starcraft+broodwar

Thanks[/QUOTE]

You should try : 
cedega (paying or some trial period)
  
or 

the free cvscedega
  
I use the free cvscedega and it's working more than great for Broodwar
On the other hand, I didnt manage to play with my friend in IPX connection ...
not much time to do it ... [http://www.ubuntuforums.org/showthread.php?t=187882&highlight=broodwar](http://www.ubuntuforums.org/showthread.php?t=187882&highlight=broodwar)
If you'd like to install cvscedega without any efforts (3 command lines) I can make for you an automatic installation... I was thinking to make one (via using cvswine.sh)... 

Gretz

---

### Post by ZylGadis on 2006-06-06
Having in mind that the answers to all three of your questions are on the first four pages of this forum at the moment (without any search), your wasting everyone else's time because you are not willing to spend 1 minute of yours is disgusting.
Respect others' time so that they respect your questions.

---

### Post by eighthate on 2006-06-06
[QUOTE=ZylGadis]Having in mind that the answers to all three of your questions are on the first four pages of this forum at the moment (without any search), your wasting everyone else's time because you are not willing to spend 1 minute of yours is disgusting.
Respect others' time so that they respect your questions.[/QUOTE]

I was just saying Thanks! I wounder y u take it so personnal..

---

### Post by patrick295767 on 2006-06-06
> Originally Posted by ZylGadis
Having in mind that the answers to all three of your questions are on the first four pages of this forum at the moment (without any search), your wasting everyone else's time because you are not willing to spend 1 minute of yours **is disgusting.**
Respect others' time so that they respect your questions.

[QUOTE=eighthate]I was just saying Thanks! I wounder y u take it so personnal..[/QUOTE]
  
Some warfare there ... :-\"

---

### Post by eighthate on 2006-06-06
[QUOTE=patrick295767]You should try : 
cedega (paying or some trial period)
  
or 

the free cvscedega
  
I use the free cvscedega and it's working more than great for Broodwar
On the other hand, I didnt manage to play with my friend in IPX connection ...
not much time to do it ... [http://www.ubuntuforums.org/showthread.php?t=187882&highlight=broodwar](http://www.ubuntuforums.org/showthread.php?t=187882&highlight=broodwar)
If you'd like to install cvscedega without any efforts (3 command lines) I can make for you an automatic installation... I was thinking to make one (via using cvswine.sh)... 

Gretz[/QUOTE]

i Guess u could try one :p

---

### Post by patrick295767 on 2006-06-06
[QUOTE=eighthate]i Guess u could try one :p[/QUOTE]
  
I dont think really script is necessary or maybe ...? 
 
Let's make experiment: 
just type : 

```
sudo bash
cd /root
wget http://cvscedega.linux-gamers.net/WineCVS.sh
sh WineCVS.sh
```
  
Then, select to download the profile 1.
Then, bla bla, you enter r  
to run the profile script 
 
then type as user into an xterm or konsole : 
```
whereis cvscedega 
cvscedega 
and you should see the help 
```

Let me know if it works !!
=======
ref: 
 cvs -d:pserver:cvs@cvs.transgaming.org:/cvsroot login
[http://doc.ubuntu-fr.org/applications/jeux/cedega](http://doc.ubuntu-fr.org/applications/jeux/cedega)

---

### Post by DAaaMan64 on 2006-06-06
I am trying to compile the damn thing, it works and everything, there is even a cvscedega directory in my /home/daaaman64/.WineCVS/ directory.  But for whatever reason when I type cvscedega I get told command not found!  Can someone please help?  I would just buy it but last time I tried it on my old graphics card nothing ran well, so I want to test it first.

---

### Post by patrick295767 on 2006-06-07
[QUOTE=DAaaMan64]I am trying to compile the damn thing, it works and everything, there is even a cvscedega directory in my /home/daaaman64/.WineCVS/ directory.  But for whatever reason when I type cvscedega I get told command not found!  Can someone please help?  I would just buy it but last time I tried it on my old graphics card nothing ran well, so I want to test it first.[/QUOTE]
  
type : ```
whereis cvscedega 
ls -la /usr/bin/cvscedega
```
  
Did you do the profile 1 and runned it ?
  
With profile 0, taht can give cvscedega not found.

 greetz

---

### Post by DAaaMan64 on 2006-06-09
Ok, I would love to try to use profile 1, however it attempts to use "su" instead of "sudo" prompting for the root password, which is different than the "sudo" password?  What should I type?

---

### Post by patrick295767 on 2006-06-09
[QUOTE=DAaaMan64]Ok, I would love to try to use profile 1, however it attempts to use "su" instead of "sudo" prompting for the root password, which is different than the "sudo" password?  What should I type?[/QUOTE]

type:
```
su 
```

or if not working : 

type : 
```
sudo bash 

```
then , u are root ! :-) :KS
  
Greetz

---

### Post by echo $USER on 2006-06-09
I got steam working with wine.  CS and DOD run great; all the source games not so good if even at all.

---

### Post by chadk on 2006-06-13
When I try running WineCVS.sh I get:
```
--------- Error log - file /home/chad/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/chad/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found

```

---

### Post by Sandlst on 2006-06-13
[QUOTE=chadk]When I try running WineCVS.sh I get:
```
--------- Error log - file /home/chad/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/chad/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found

```[/QUOTE]
Type ```
sudo apt-get install cvs
``` When something spits out a command not found error, I usually do a synaptic search for relavent terms (cvs for above), usually works good, just FYI.

---

### Post by chrism66 on 2006-06-19
** Edited got working//Ok, I got cvscedega installed. No to really show my 'Newbie' status how do I get Steam to run under cvscedega? Thanks!!//**
 

All right I would like to thank patrick295767 for all his expertise in helping me get CS-S up and running. Many, many thanks patrick!!! 

I got it to run using the following:
 WINEDEBUG=-all sudo wine C:/Program\ Files/Steam/Steam.exe

Is this the right way with cvscedega?

I am currently running under DX 7 and visually it is no better than regular CS. I was wonder if I could select profile #4 under  WineCVS.sh setup which is DX 9 reular wine profile? Well I am getting close to leaving Windblows real soon!!

Chris

---

### Post by lzap on 2006-07-06
[QUOTE=patrick295767]
```
sudo bash
cd /root
wget http://cvscedega.linux-gamers.net/WineCVS.sh
sh WineCVS.sh
```
[/QUOTE]

The URL you provided is not working...

---

