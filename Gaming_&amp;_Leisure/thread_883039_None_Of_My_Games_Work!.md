---
title: "None Of My Games Work!"
date: 2008-08-07
forum: Gaming &amp; Leisure
---

### Post by mikeMarek on 2008-08-07
I downloaded a couple games (Assault Cube, Cube 2, and Warsow) and none of them work. Assault Cube used to work, and then I tried to run Cube 2 but I got an error message saying that I'm missing some binary files. Now none of my games work. Here's what I am doing:

```

michael@Michael-Desktop:~$ cd ./Documents/Games/
michael@Michael-Desktop:~/Documents/Games$ tar -xf /home/michael/Documents/Program\ Installers/AssaultCube_v0.93.tar.bz2 
michael@Michael-Desktop:~/Documents/Games$ cd ./AssaultCube/
michael@Michael-Desktop:~/Documents/Games/AssaultCube$ ./assaultcube.sh
.//bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
michael@Michael-Desktop:~/Documents/Games/AssaultCube$

```

This happens for all of the games. Also, when I try to click on the shell script file and click "run in terminal", a terminal quickly pops up and dissapears.

Any help will be most appreciated! :KS
-Mike

---

### Post by ilrudie on 2008-08-07
First see if the games are in the repositories using synaptic.  If they are then just get them there and all dependencies will be handled.  Next check to see if there is a .deb version of the game.  This is the second easiest way to install.  It should assist you in solving dependencies.  If both of those options fail just try to download the libraries it says are missing from synaptic.

---

### Post by Sandlst on 2008-08-07
I'd like to add that 
[http://www.getdeb.net]("http://www.getdeb.net") 
is a great place to find up-to-date deb packages, although they are inherently less stable than the official repositories (I've never had an issue with them however). They have a specific game category, which can be reached at 
[http://www.getdeb.net/category.php?id=3]("http://www.getdeb.net/category.php?id=3").

---

### Post by FranMichaels on 2008-08-08
> **mikeMarek said:**
> I downloaded a couple games (Assault Cube, Cube 2, and Warsow) and none of them work. Assault Cube used to work, and then I tried to run Cube 2 but I got an error message saying that I'm missing some binary files. Now none of my games work. Here's what I am doing:

```

michael@Michael-Desktop:~$ cd ./Documents/Games/
michael@Michael-Desktop:~/Documents/Games$ tar -xf /home/michael/Documents/Program\ Installers/AssaultCube_v0.93.tar.bz2 
michael@Michael-Desktop:~/Documents/Games$ cd ./AssaultCube/
michael@Michael-Desktop:~/Documents/Games/AssaultCube$ ./assaultcube.sh
.//bin_unix/linux_client: **error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory**
michael@Michael-Desktop:~/Documents/Games/AssaultCube$

```

This happens for all of the games. Also, when I try to click on the shell script file and click "run in terminal", a terminal quickly pops up and dissapears.

Any help will be most appreciated! :KS
-Mike

Emphasis mine. Download libsdl-mixer1.2

sudo apt-get install libsdl-mixer1.2

or grab from synaptic

Installing games from the repositories, or a properly packaged deb (as noted by above posters) will do the trick and handle all this for ya! 

If you still have problems, keep looking for those error messages at terminal, and grab similarly named packages from synaptic (the missing file errors are genuinely helpful.)

---

