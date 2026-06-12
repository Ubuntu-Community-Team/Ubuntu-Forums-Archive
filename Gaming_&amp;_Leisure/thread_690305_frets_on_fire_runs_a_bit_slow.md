---
title: "frets on fire runs a bit slow"
date: 2008-02-07
forum: Gaming &amp; Leisure
---

### Post by jacob01 on 2008-02-07
frets on fire is a great game i have downloaded some songs for it and it is really cool the only problem is that some time when i quit is that it messes with my screen res settings and the refresh rate, its an easy fix but is kinda annoying. Also i was wondering if there is a new intel driver that would perform any better than the one that im currently using.

on certain songs it gets a little jittery, but still play able
also when a pop up notification comes up my xorg or somthing freezes but it can be fixt by restarting my xorg with ctrl alt backkspace

i know i could probably fix this witha cheap nvid card but i cant really fully justify getting one just for a couple games when i have an xbox

i can post my xorg.conf if you would like just ask





edit: i realize im not going to get much with the hardware i have just looking to get as much out of it as i can

---

### Post by disturbedite on 2008-02-07
did you install the version from the ubuntu repo or did you install the version from the fof website?
the ubuntu repo version has a bug that causes performance problems:
[https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/154418](https://bugs.launchpad.net/ubuntu/+source/fretsonfire/+bug/154418)

---

### Post by FrozenFox on 2008-02-07
As far as frets on fire screwing up your video settings, please try this. I have no clue if it will work correctly for frets, but it works for most of my other games, so i don't see why not. 

Note that I have no idea whether or not this can cause a security problem, but I've had no issues for some time. So try it at your own risk, blah blah.

Attached to this post is a script called Xlaunch, originally posted at one of the Gentoo forums. I think I've slightly modified it to correctly work with Ubuntu, I'm not sure (I have 3 versions of it, to work with 3 different distros (PClinuxos, sabayon, and ubuntu/mint) i've used. Essentially what it does is launch a game or app in another X session, so that you can ctrl+alt+F(key) to switch back and forth between x sessions and it would thus disallow your current X session's video stuff to be changed in favor of a new session, like windows alt+tab on crack. On ubuntu, I believe the default session is f7 (ctrl+alt+f7 to go to x session 1, and i think x session 2 will start on either 9 or 10, likely the former. ie ctrl alt f9).

(Note: overdoing the instructions here is for the benefit of those who may have less experience than I imagine you have, but have the same issue)

Extract the file from the tar.gz. These forums wouldn't let me upload it without a .sh suffix or whatnot, so i had to compress it. You should be able to right click it and extract, but if not, you can do tar -xvf  ~/Desktop/xlaunch.tar.gz. Anywho..

Open up the terminal / console / konsole and..

sudo gedit /etc/X11/Xwrapper.config  

(if youre on kubuntu, switch gedit with kwrite) and then change the line from allowed_users=console to allowed_users=anybody and save. Note that if anyone has a better way to do this or if it is 'unsafe' and you can make the script work better or something, by all means please speak up.

Download the script from this post to the desktop, then in the terminal move it to /usr/bin via:

sudo mv ~/Desktop/xlaunch /usr/bin/xlaunch

Almost done.. now just change it to executable form.

sudo chmod a+x /usr/bin/xlaunch  (or chmod 777 I think would work too. if you have problems, try that).

Now, run frets on fire with the script via the command xlaunch /path/to/the/game/game. Or make a link to the app on your desktop containing the same command.. say whereis fretsonfire in the terminal/console gives /usr/bin/fretsonfire, then you could make a link on your desktop with the command xlaunch /usr/bin/fretsonfire. This will launch the game under the next X session with settings seperate from your current session, so it should keep your video stuff from being messed up AND allow you to switch out of games that would normally disallow switching via ctrl+alt+f7 and f9 and such, similar to alt tab except.. well, much more useful and less problematic. Note: if you hear the sound but no video comes around, switch back to session1 and then back to session2 and it will go :)

As for your lag problems, turn off compiz / advanced desktop settings and then try the above stuff. But before messing with all that, try as disturbedite suggests and see if that helps.

---

### Post by jacob01 on 2008-02-07
ok cool im going to try the installing the game from the source package on the site then ill try running the game in a differant x session

---

### Post by jacob01 on 2008-02-12
i installed the one from the site and it runs even slower some songs are slower than 1 fps

---

### Post by googlah on 2008-04-02
Sorry for bringing up this thread again, but also me can confirm that Frets on Fire runs MUCH better from it's original package, than from Ubuntu's repos.

I thought it was something with my drivers, but it wasn't. Runned so smooth at 1280x1024 with AA on maximum, Ubuntu rocks. :guitar:

(I'm on a Nvidia 7800GTX)

---

### Post by jacob01 on 2008-04-02
yea i got a new video card the and i still notice a little differance but its not that noticeable

---

### Post by lexen on 2008-04-06
Can anyone compile FoF 1.2.512 to a .deb file and send it in to ubuntu?  Will this problem be fixed with 8.04?  I tried using alien to make my own .deb file, but I don't know how to run it.  After I install the .deb file, I can see it in synaptic, but I can't run it.  You can download it from me [here]("http://www.unseenirony.com/fretsonfire_1.2.512-linux-2_all.deb").

   If anyone can tell me how to compile it, I will.  I would love to help FoF by maintaining their ubuntu .deb files, but I don't know how.  Any help would be greatly appreciated.

---

### Post by k0rv3n on 2008-04-09
Hi. Dont know if this is the right place to ask this question but has someone else had problems with the sound?

I'm running FretsOnFire-1.2.451-RF-mod-4.15-linux32 on Ubuntu 7.10 x64 and I cant hear the sound from the guitar :(
I hear the background music and sound from playing wrong but not the actual guitar. If I use the non modded version the whole backgroundmusic get muted whan playing wrong but still no guitarsound.

I have tried to play the songs on my laptop with windows and everything works fine there.

Does anyone know what I can try?

---

