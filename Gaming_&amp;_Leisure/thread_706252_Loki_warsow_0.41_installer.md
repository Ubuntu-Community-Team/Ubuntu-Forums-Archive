---
title: "Loki warsow 0.41 installer"
date: 2008-02-24
forum: Gaming &amp; Leisure
---

### Post by MarkUK on 2008-02-24
Ok used ubuntu in the past and have decided to come back , warsow has been updated to 0.41 , seen as loki has compiled an installer i thought i would give it a go , but no matter what i do i always get this error

clipper@clipper-desktop:~$ sudo sh warsow_0.41-english.run
Verifying archive integrity... All good.
Uncompressing Warsow 0.41-english Installer..............................
eval: 1: ./setup.sh: Permission denied


Now i have tried ,sudo chmod a+x warsow_0.41-english.run, sudo chmod 755 warsow_0.41-english.run 

And i still get the error !

Can anyone help with this 

Cheers
Mark

---

### Post by Perfect Storm on 2008-02-24
[http://gaming.gwos.org/doku.php/games:alphabetical:w:warsow](http://gaming.gwos.org/doku.php/games:alphabetical:w:warsow)

contains a link to getdeb + how to install it for both 32-bit and 64-bit if you want to do t manually.

---

### Post by MTiN on 2008-02-24
but both the debs and the steps to install apply for warsow 0.32, not 0.41!!
I am also having problems trying to run it, didn't even find those install scripts! could you tell me where you got them from,MarkUK?

---

### Post by Perfect Storm on 2008-02-24
Doesn't matter, just change change the number/name in the steps.

---

### Post by $4real$ on 2008-02-28
i am very new to linux/ubuntu, i love it, but have had a few problems (wich are on my end of the understanding things,lol) and i have hit a roadblock,
I have followed the instructions from [http://gaming.gwos.org/doku.php/guides:64bit:warsow]("http://gaming.gwos.org/doku.php/guides:64bit:warsow")
and was able to install by changing the version numbers, but have encountered a problem wean setting up the icon so i can play, i entered the codes but it wasnt reconising my icon, I changed the name and still no go,this is what it says forreal@forreal-laptop:~$ cd ~/Desktop
forreal@forreal-laptop:~/Desktop$ mv warsow.png ~/.Games/Warsow
mv: cannot stat `warsow.png': No such file or directory
forreal@forreal-laptop:~/Desktop$ nano ~/.Games/Warsow-launch.sh

now i made a mistake and hit enter and then in the window it brought me to is wear i entered the rest of it 
 #!/bin/bash

cd ~/.Games/Warsow
./warsow.x86_64

 #!/bin/bash

cd ~/.Games/Warsow
./warsow.x86_64















                                [ Read 4 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell



and tried to save with "ctrl" o and "cntrl" x to exit somthing came up and i hit enter and it said it wrote 4 lines i exited thinking i was done and then entered in a normal terminal 
chmod +x ~/.Games/Warsow-launch.sh
alacarte

which brought me to the screen and I tried to make what i thought was a launch for the game, just with out the icon, but was very wrong,lol, now i have no clue how to get in to the game, if any one has a clue please help:confused:

---

### Post by Perfect Storm on 2008-02-28
> forreal@forreal-laptop:~/Desktop$ mv warsow.png ~/.Games/Warsow

make sure to rename the icon when you save to Desktop.

> 
now i made a mistake and hit enter and then in the window it brought me to is wear i entered the rest of it
#!/bin/bash

cd ~/.Games/Warsow
./warsow.x86_64

#!/bin/bash

cd ~/.Games/Warsow
./warsow.x86_64

Erease line 6 and below - it seems you have put it twice.


if you made the launcher right in alacarte, it should be in applications tab ---games

---

### Post by $4real$ on 2008-02-28
Thank you, I tried that and I cant get the icon to show up wean im making the launcher and the generic launcher that is used is put in games but wean i click it nothing happens:confused: how can i uninstall the game? I will try and re-install and see if that works, i must have done something wrong

---

### Post by Perfect Storm on 2008-02-29
```
cd ~/.Games
rm -rf Warsow
rm -rf Warsow-launch.sh
```

Will delete Warsaw, you need to remove the entry as well in applications tab ---> games


Note, in the part where it says 
> Name: Warsow
Command: sh /home/USERNAME/.Games/Warsow-launch.sh
Comment: War§ow is a First-person shooter (FPS) game designed for online play.

Icon: ~/.Games/Warsow/warsow.png

to change USERNAME with your user name

---

