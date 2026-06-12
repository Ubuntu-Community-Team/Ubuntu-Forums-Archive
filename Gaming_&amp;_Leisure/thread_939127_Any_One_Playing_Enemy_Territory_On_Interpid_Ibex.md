---
title: "Any One Playing Enemy Territory On Interpid Ibex??"
date: 2008-10-05
forum: Gaming &amp; Leisure
---

### Post by attila_66 on 2008-10-05
Hello,

This weekend I installed Ibex beta to my computer.
I searched the repos but couldnt find Enemy Territory Wolfenstein.

Is there anyone installed and playing ET on IBEX??

---

### Post by Swarms on 2008-10-05
I guess you mean Enemy Territory: Wolfenstein?

---

### Post by syczu on 2008-10-05
Enemy territory isn't in repos. You can download it from here for example : [http://www.splashdamage.com/node/57]("http://www.splashdamage.com/node/57")

---

### Post by attila_66 on 2008-10-06
Hello,

I can not install using the .run file.

attila@ubuntuattilas:~$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install..............................................................................................................................................................................................................................................................................................................................
./setup.sh: 278: /home/attila/.setup7028: not found
./setup.sh: 289: /home/attila/.setup7028: not found
attila@ubuntuattilas:~$

I get this error.
Same happened in Hardy Heron also.

While using Hardy I installed it using repository.

Is there a .deb file to install ET wolfenstein to interpid ibex??

Thanks for any help.

---

### Post by Zimmer on 2008-10-06
I expect you have seen this, 
[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)
changed permissions and so on...
But it does mention the need for the libgtk1.2

I can see my Hardy install has libgtk2.0  installed and libgtk1.2 is listed seperately (not installed).

I have not yet tried to install ET since I upgraded to Hardy several weeks ago, and I cannot see it in the repos , yet you say you last installed by that method? Which repo was it in?

---

### Post by Zimmer on 2008-10-06
Yep , looks from this thread
[http://ubuntuforums.org/showthread.php?t=5246&highlight=territory&page=31](http://ubuntuforums.org/showthread.php?t=5246&highlight=territory&page=31)

that libgtk1.2 could be the answer...

---

### Post by attila_66 on 2008-10-06
Hello,

Zimmer sorry but i dont remember.
It was my first time with kubuntu.
I added all the repos in adept manager.
So made a search within the package manager.
Then found ET.
Installed it.

If you can not find it in repos.

This thread may help you to solve installation problem i mentioned above.

[http://ubuntuforums.org/showthread.php?t=5246&page=28](http://ubuntuforums.org/showthread.php?t=5246&page=28)

The problem i mentioned depends on 64 bit os.

Is there any 32 bit compatibility packages for ibex??


In one of previous Linux distro i copied all the enemy-territory folder content to usb stick.
After new install I copied all contents to /usr/local/games/enemy-territory folder.
And it worked for that linux distro.

I did the same for kubuntu.
But here when I type

attila@ubuntuattilas:/usr/local/games/enemy-territory$ ./et.x86
bash: ./et.x86: Permission denied
attila@ubuntuattilas:/usr/local/games/enemy-territory$

Premission denied message.

Any suggestion for this method??

---

### Post by attila_66 on 2008-10-06
Finally I got my Enemy Territory Back!!
First because of this install problem (I am using 64 bit)

[B]attila@ubuntuattilas:~$ sudo ./et-linux-2.60.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install........................................... .................................................. .................................................. .................................................. .................................................. .................................................. .........................
./setup.sh: 278: /home/attila/.setup7028: not found
./setup.sh: 289: /home/attila/.setup7028: not found
attila@ubuntuattilas:~$[/B]

I installed some lib32 compatibility packages
Dont ask which one dont remember.
But i installed one then tried no success
Installed other one tried
Finally succeeded.

I installed the program.

While running program

can't find libX11.so.6

problem appeard.
Little search on the web found that have to install
ia32-lib-sdl
ia32-libs
lib32asound2

libraries has to be installed.
Installed these libraries..

And the game started..

---

### Post by Gorgoth on 2008-10-07
Err... have you tried the deb package from PlayDeb.net? Thats the only place off the top of my head that has the deb packages.

---

