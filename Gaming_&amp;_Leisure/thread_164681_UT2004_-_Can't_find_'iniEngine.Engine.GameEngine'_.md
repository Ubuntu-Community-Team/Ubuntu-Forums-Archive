---
title: "UT2004 - Can't find 'ini:Engine.Engine.GameEngine' in configuration file"
date: 2006-04-23
forum: Gaming &amp; Leisure
---

### Post by ironfistchamp on 2006-04-23
Thats the basic error after installing on Dapper flight 6. After the installation I ran it once when it asked me. That was fine. Then when I tried to run it from the menu the splash screen flashed up and that was it. So I did it from the console and this is what I get. 

X@ubuntu:~$ ut2004
Can't find 'ini:Engine.Engine.GameEngine' in configuration file

History:

Exiting due to error

How can I fix this. I had the same prob on Breezy but I left Breezy as it was so unstable. Maybe it was a dodgy disk or something.

So can anyone help?

Oh and while I'm at it when I tried to install G/W (Guild Wars for those of you who don't know) I had problems. Cedega installed it and then when I came to the "Your graphics card is not supported" bit I clicked yes and was greeted by a huge black screen. After restarting I clicked on the GW profile on the left in P2P and I couldn't click play. Again this happened in Breezy. Any ideas?

Thanks

Ironfistchamp

---

### Post by pay on 2006-09-17
This is abit late but did you install the UT2k4 as root? I got the same error and to play the game i then had to run it as root. ie:```
sudo ut2004
```

---

### Post by ironfistchamp on 2006-09-17
Hehe tis a bit late :p  

I think that is what I did. I think I just chowned the entire dir so its mine. No one else uses this machine so its not a prob.

Thanks anyway

Ironfistchamp

---

### Post by Perfect Storm on 2006-09-17
Don't run ut2004 as root (security reasons).
The error you have happens when you hit the startbutton right after you installed ut2004 which will give you permission problem.
You can install it with root (global user) 
sudo sh /blah/blah/installer.sh then exit the installer. Grab the megapack which contains the latest patch + EC extract the file and cd /into/the/extracted/folder
Now copy it to the ut2004 folder:
sudo cp -r * /usr/local/games/ut2004

Done.

---

### Post by Hemmer on 2006-11-12
argh too late for me too. shame they didnt insist that the installer was ran as sudo. other than that, it works fantastically on edgy - majorly impressed!

---

### Post by HearWa on 2007-02-24
Hello, I just registered so I could post how I fixed this problem. The error happens not because of an invalid configuration but because you don't have the correct permissions for the ut2004 configuration directory ('.ut2004' in your home folder). This happened to me because I first ran the game as root after I installed the game.

So in shory just remove the .ut2004 folder from your home directory. Afterwards, run ut2004 as a user and you're good to go.

And yes, running ut2004 as a super user is a horrible idea. :)

---

### Post by zenakuten on 2007-03-30
More to the point, you need to do:

sudo chown your_user_name .ut2004
sudo chgrp your_user_name .ut2004
cd .ut2004
find . -exec chown your_user_name {} \;
find . -exec chgrp your_user_name {} \;


I also had an error about XColormap something or another.  This means you need to change the bit depth on the XServer.  24 bit is definitely no good.

---

### Post by General_Ts0 on 2007-03-31
Thx much, works like a charm.  I see the link in 'OTHER' under Applications and after running this sequence of commands, works great.


Now, how in the hell do I install the MegaPack ?  Followed above instructions to get it copied into the folder w/ UT and even [these]("http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml") but all I end up w/ his a 'UT2004MegaPack as a sub folder in the /usr/local/games/ut2004 folder.  Launch the game, don't see that any changes have 'took'.  Looked for some sort of executable in the 'System' subfolder of UT2004MegaPack but notta.

---

### Post by Perfect Storm on 2007-04-01
[http://gaming.gwos.org/e107_plugins/content/content.php?content.56](http://gaming.gwos.org/e107_plugins/content/content.php?content.56)

---

### Post by DrFreeze on 2007-09-08
sorry to revive this old thread, but i have this same problem, but i think i dug myself into a deeper hole

what i did is, first installed UT as root, into /usr/local/games/ut2004. after installing i clicked yes to the "play now" prompt, launching the game. Soon though i found i had to be root to launch, and i wasnt very happy

i did the chown thing in this thread, but not on .ut2004 in /home (i never get this folder?) but on the /usr/local/games/ut2004 folder, which then prevented me from uninstalling. Then i simply rm -rf ed the entire game folder, and tried installing as my own user

however, everytime the game seems to remember my preferences from the first root install, and i can still not launch as a normal user :(
g
did my rm -rf **** things up beyond repair?

i could completely re-install ubuntu (running a fresh install) but i would rather not do that

also, should i decide to reformat, i trust i should just install ut as a normal user?

---

### Post by Perfect Storm on 2007-09-08
```
sudo rm -rf .ut2004
cd /usr/local/games
sudo rm -rf ut2004
cd /usr/local/bin
sudo rm -rf ut2004

```


Should do it.

---

### Post by DrFreeze on 2007-09-08
thanks, that worked, i now installed it as a normal user, and it all works now

ive got two more question, if you dont mind off course

1. were can i put in extra resolutions? my screen is 1440*900, yet ut only shows options up to 1280*854
2. is there any way i can make a clickable shortcut on my desktop to launch UT?

thanks for the fast answer :)

NINJA edit: never mind question 2, found that out already myself :)

---

### Post by Perfect Storm on 2007-09-08
If your xorg.conf is set up with that res.

next step would be taking a look

in the .ini file

```
nano /home/orion/.ut2004/System/UT2004.ini
```

Also get the Mega pack right away, perhaps it will solved your problem.

---

### Post by DrFreeze on 2007-09-08
thanks a bunch, i didnt know where to find that ini file

as for the map pack, i have the editors choice edition, so i think i already have it (its the free expansion with the three extra vehicles right? cicada and such?)

man, this is quite nice, once i get bored with UT, ill probably start messing around with Quake 4 :)

---

### Post by Kenchu on 2007-09-22
***edit***

nm what i said. didnt see page 2. :)

---

### Post by Psy-Krow on 2007-10-13
not to troll, but this thread helped me to figure out how to fix this problem.

**_What Helped_**
[quote=zenakuten]More to the point, you need to do:

sudo chown your_user_name .ut2004
sudo chgrp your_user_name .ut2004
cd .ut2004
find . -exec chown your_user_name {} \;
find . -exec chgrp your_user_name {} \;[/quote]

**_What I realized_**
during the installation, the .ut2004 directory in your home directory gets set to root if you run the game immediately while still under sudo.

**_To correct_**
so that you don't have to run the game via sudo, change the ownership of your .ut2004 directory recursively.

```

sudo chown -R username:username ~/.ut2004
```

this basically simplifies what zenakuten was explaining.

now you should be able to run ut2004 without needing super user.

hope this helps any1 else that stumbles across this.
comon ut3!

---

### Post by magikx21 on 2007-11-23
I'm still have this problem. After I installed the first time I hit start but then it didn't work after that. I removed it reinstalled it and I have set ownership and group on all the files yet still when I try to run this without sudo I get an error.

---

