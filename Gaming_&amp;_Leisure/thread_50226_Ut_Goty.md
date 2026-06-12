---
title: "Ut Goty"
date: 2005-07-19
forum: Gaming &amp; Leisure
---

### Post by C1ph3R on 2005-07-19
this is my first game that im putting on linux and im having some problems.
i went to princess leas site read through that, but my question is where am i supposed to put the run file for it to be detected?

---

### Post by Goldenmouse on 2005-07-19
[QUOTE=C1ph3R]this is my first game that im putting on linux and im having some problems.
i went to princess leas site read through that, but my question is where am i supposed to put the run file for it to be detected?[/QUOTE]
 The run file goes anywhere.  You just have to do from the root terminal:
chmod 755 asdf.run
where asdf.run is the name of the run file, then do:
./asdf.run
And you should be looking at a graphical installer.

On a similar note, I have UT GOTYE installed, but an not getting any sound whatsoever.  I AM, however, getting sound from a linux install of Neverwinter Nights.  I suspect that under engine.engine, my audio device is not set properly.  What I had by default was: AudioDevice=ALAudio.ALAudioSubsystem

---

### Post by bored2k on 2005-07-19
[QUOTE=Goldenmouse]The run file goes anywhere.  You just have to do from the root terminal:
chmod 755 asdf.run
where asdf.run is the name of the run file, then do:
./asdf.run
And you should be looking at a graphical installer.

On a similar note, I have UT GOTYE installed, but an not getting any sound whatsoever.  I AM, however, getting sound from a linux install of Neverwinter Nights.  I suspect that under engine.engine, my audio device is not set properly.  What I had by default was: AudioDevice=ALAudio.ALAudioSubsystem[/QUOTE]
 No sound ? Did you do the ESD+Alsa trick? that's how sound worked on my Steam (Counter-Strike). [http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd+gandalf](http://ubuntuforums.org/showthread.php?t=32063&highlight=alsa+esd+gandalf)

Anyways, this is how I got UT:GOTY working. Not that I still play on Linux (I have Win for that), but this is how.
> 

1)  xhost +
2)  su - 
3)  export DISPLAY=:0.0
4)  chmod 755 ut-install-436.run
5)  bash ut-install-436.run
     a) Select /usr/games/ut for install path
     b) Select /usr/bin for link path
     c) Insert CD 1 into your CD-Rom Drive

     d) Hit the 'Begin Install' button
     e) Follow the on screen instructions
     f) Exit when complete

#! /bin/sh

export UT_DATA_PATH=/usr/games/ut/System
ut



---

### Post by C1ph3R on 2005-07-19
this is what i get in root terminal

root@ubuntu:/home/ # xhost +
access control disabled, clients can connect from any host
root@ubuntu:/home/ # su -
root@ubuntu:~ # export DISPLAY=0.0
root@ubuntu:~ # chmod 755 ut-install-436.run
chmod: cannot access `ut-install-436.run': No such file or directory
root@ubuntu:~ #

---

### Post by C1ph3R on 2005-07-19
[QUOTE=C1ph3R]this is what i get in root terminal

root@ubuntu:/home/ # xhost +
access control disabled, clients can connect from any host
root@ubuntu:/home/ # su -
root@ubuntu:~ # export DISPLAY=0.0
root@ubuntu:~ # chmod 755 ut-install-436.run
chmod: cannot access `ut-install-436.run': No such file or directory
root@ubuntu:~ #[/QUOTE]
 anyone got ideas on how to get this working?

---

### Post by bored2k on 2005-07-19
[QUOTE=C1ph3R]anyone got ideas on how to get this working?[/QUOTE]
 root@ubuntu:~ # chmod 755 ut-install-436.run

Do you have that file ? Are trying UT or UT:GOTY because filename would be different.

---

### Post by C1ph3R on 2005-07-19
[QUOTE=bored2k]root@ubuntu:~ # chmod 755 ut-install-436.run

Do you have that file ? Are trying UT or UT:GOTY because filename would be different.[/QUOTE]
 ut goty, i got the file from princessleas site, the file is ut-install-436-GOTY.run.. so what do i do now?

---

### Post by bored2k on 2005-07-19
[QUOTE=C1ph3R]ut goty, i got the file from princessleas site, the file is ut-install-436-GOTY.run.. so what do i do now?[/QUOTE]
 Continue the steps with the ut-install-436-GOTY.run instead of the one pointed.

---

### Post by C1ph3R on 2005-07-19
chmod: cannot access `ut-install-436-GOTY.run': No such file or directory
 
i got the file from princessleas site and put it on my desktop, but its not finding it still

---

### Post by bored2k on 2005-07-19
[QUOTE=C1ph3R]chmod: cannot access `ut-install-436-GOTY.run': No such file or directory
 
i got the file from princessleas site and put it on my desktop, but its not finding it still[/QUOTE]
 Put in your HOME. In order to access it, you need to be in the same folder you got it from. So 
cd Desktop then do the command, or simply put it in your home.

---

### Post by C1ph3R on 2005-07-19
chmod: cannot access `ut-install-436-GOTY.run': No such file or directory


still gettin that when its in the home folder

---

### Post by C1ph3R on 2005-07-20
any ideas?

---

### Post by jdodson on 2005-07-20
type "ls" into the terminal and paste the output to the post.

---

### Post by someuser77 on 2005-12-02
when i try to run UT i get:
```
$ ut
./ut-bin: error while loading shared libraries: ./Core.so: cannot restore segment prot after reloc: Permission denied

```
what can i do?

---

