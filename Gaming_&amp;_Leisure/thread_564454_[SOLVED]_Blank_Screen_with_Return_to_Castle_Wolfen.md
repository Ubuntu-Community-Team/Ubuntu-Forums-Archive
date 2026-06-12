---
title: "[SOLVED] Blank Screen with Return to Castle Wolfenstein"
date: 2007-10-01
forum: Gaming &amp; Leisure
---

### Post by Circus-Killer on 2007-10-01
okay, i managed to get doom3 running natively using the binaries from idsoftware's ftp site. i tried to do the same with return to castle wolfenstein, but i am running into a problem.

i've installed the linux binaries, along with the necessary data files from the original cd. when i try start wolfenstein, it just shows me a blank screen, and thats it. end up having to do a reboot.

i find this strange because i can run both doom3 and enemy territory, so i dont see any reason for return to castle wolfenstein not to work. anyways, was hoping someone has had the same problem and figured out how to fix it. any suggestions? :confused:

---

### Post by Circus-Killer on 2007-10-01
*bump*

---

### Post by cwmoser on 2007-10-01
I run Wolfenstein 3D like this:

sudo  apt-get install  dosbox

$  dosbox
Z> mount  c  /media/sda1
Z>  C:
C>  cd  \games\wolfall
C>  WOLF3D.EXE

Note that I installed the dosbox app.
The path to your instance of WOLF3D.EXE is probably different.

Carl





> **Circus-Killer said:**
> okay, i managed to get doom3 running natively using the binaries from idsoftware's ftp site. i tried to do the same with return to castle wolfenstein, but i am running into a problem.

i've installed the linux binaries, along with the necessary data files from the original cd. when i try start wolfenstein, it just shows me a blank screen, and thats it. end up having to do a reboot.

i find this strange because i can run both doom3 and enemy territory, so i dont see any reason for return to castle wolfenstein not to work. anyways, was hoping someone has had the same problem and figured out how to fix it. any suggestions? :confused:

---

### Post by Circus-Killer on 2007-10-02
thanks for the tip. unfortunetly, im not looking to run it through an emulator, otherwise i would have used wine. in fact, i might resort to using wine if i cant figure out my problem.

the thing is, i downloaded the binaries for the game (as i did for doom3 and quake4), but unlike those 2 games, wolf doesnt seem to work like the others do. i would really like to run all the games that can run natively to run natively.

thanks again though for your help. always appreciated.

---

### Post by Sockerdrickan on 2007-10-02
Well I need the terminal output

---

### Post by Circus-Killer on 2007-10-02
ummm how do i see the terminal output? when i start the game, it goes to fullscreen, but just plain black. complete blank screen. from their i can do nothing but reset the computer. :confused:

---

### Post by Sockerdrickan on 2007-10-02
You start the game from a terminal and read the output when it exits, if it froze you can kill it from another TTY :) kill -9 id
get id with this
ps -e|grep processnamehere

---

### Post by Circus-Killer on 2007-10-02
no, you not hearing me, i get a complete freeze, cant do anything except hit the reset button.

---

### Post by Sockerdrickan on 2007-10-03
wowomg...
Start it in windowed mode with the terminal at the side of it

---

### Post by Circus-Killer on 2007-10-04
okay, i managed to get it working. i did 2 things, not sure which one made it worked. i'm gonna mention both things that i did, but i should suspect that the latter one will be the one that 'fixed' the problem.

first off, when i copied the data files to wolf's main directory, i did so using sudo. so i think maybe it could of been a problem with permissions when the game was trying to access those data files, which were written in root and owned by root. i changed the permissions on those data files, but i doubt thats what fixed the problem.

i think ultimately what was going wrong, was that i was selecting return to castle wolfenstein from the applications menu. under there the launcher has a full path to the games executable. i replaced that full path with simply 'wolfsp' for single player  and 'wolfmp' for multiplayer, without specifying the full path. i think this is the one that got the game working.

i only mention this in hopes that maybe someone just as silly as me might find this info useful. but yah, as said, problem solved, game works.

i did have a problem with the sound, there being no sound at all, but i simply followed the troubleshooting steps in [this howto]("https://help.ubuntu.com/community/Games/Native/ReturnToCastleWolfenstein"). hope this helps.

---

