---
title: "Enemy Territory + TS2 again"
date: 2005-01-11
forum: Gaming &amp; Leisure
---

### Post by Braese on 2005-01-11
Hi, i read this Forum since 3 Month, it is great.
I use Ubuntu Warty, with all upgrades (apt-get upgrade), standard kernel.

I installed Teamspeak2 with tar x-jf ts2_client_rc2_2032.tar.bz2, then i go to cd ts2_client_rc2_2032 folder, and install it per sudo sh setup.sh . Teamspeak2 works, ok thats good. After that i installed ET, with chmod a+x et-linux-2.55.x86.run , xhost + and then sudo ./et-linux-2.55.x86.run , install went fine. after that i installed the patch, all works. i start et in console, et works.

after that i start TS2 , and after this i start et. et hangs on sound initialization. i read this forum, and teamspeak forum.

in root console i did this:
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
no error here.
i start et again, it hangs on sound initialization :-(

my soundcard is soundstorm from nforce2, sound works in all other things. module is intel8x0.

what can i do now? i dont want go back to windows to play et :-(

ps: i tried to use alsa dev branch, 1.08rc2, perhaps this is the problem, but i tried ./configure --with-cards=intel8x0 --with-sequencer=yes;make;make install .
it says: unsupported soundcard

---

### Post by X-fact0r on 2005-01-12
Hi, try this lines inside a terminal... and then run ET.
```
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss
```If this solution works for you, then is just a matter of adding them to a startup script so that these 3 lines are initialized during boot.

---

### Post by Braese on 2005-01-12
didn´t work.
i installed for testing alsa 1.08rc2 (driver, libs and utils) installation worked now. but my et + ts2 problem wasnt fixed.

---

### Post by Braese on 2005-01-17
bump

updated to Hoary. but my problem isnt solved :-(
is here noone with nforce2 soundstorm/intel8x0 ?

---

### Post by ming0 on 2005-01-23
Someone figured it out in this post:

[http://ubuntuforums.org/showthread.php?t=6162&highlight=teamspeak](http://ubuntuforums.org/showthread.php?t=6162&highlight=teamspeak)

You need to enable sudo su (root) access to give the commands--or put them into a startup script...

good luck

---

### Post by jensyt on 2005-01-23
Here's another resource that may help (if the above linked one doesn't):

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34)

---

### Post by ming0 on 2005-01-23
[QUOTE=jensyt]Here's another resource that may help (if the above linked one doesn't):

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=34)[/QUOTE]
 The above article messed my sound up a little bit (all of my sound was disabled). I had to reset and then used the 'sudo su' method.

---

### Post by jensyt on 2005-01-23
[QUOTE=ming0]The above article messed my sound up a little bit (all of my sound was disabled). I had to reset and then used the 'sudo su' method.[/QUOTE]
Sorry, I didn't write the article, nor have I used it. It may be outdated, so you may want to contact the author with your problems to see if he can fix his howto.

---

### Post by Braese on 2005-01-24
i don´t have a permission problem, i did the commands in root console. But didn´t work for me. I read the posted Article too, didn´t help me, so i back to Windows for now. I have read so many Tutorials, nothing worked for me.

With nforce Sound Drivers Teamspeak freezes and with Alsa it didn´t work. Intel8x0 aka Soundstorm is a horrible Card for Linux when you will play multiple Sounds.

Perhaps the next Nvidia Nforce Drivers are based on Alsa and then hardware mixing worked, or anyone here have another Suggestion.

---

### Post by ming0 on 2005-01-24
This may or may not be an option, but you might be able to get a pci soundcard and disable n-force sound at the BIOS?? I have a soundblaster audigy gamer (1), and it really works pretty well--I don't usually have to do much to get it working.

Could you borrow a soundcard from a friend to check this idea out?

Sorry I can't give you any better advice :neutral:

---

### Post by Braese on 2005-03-12
[QUOTE=ming0]This may or may not be an option, but you might be able to get a pci soundcard and disable n-force sound at the BIOS?? I have a soundblaster audigy gamer (1), and it really works pretty well--I don't usually have to do much to get it working.

Could you borrow a soundcard from a friend to check this idea out?

Sorry I can't give you any better advice :neutral:[/QUOTE]
 i will let you know, that ET + TS2 is working now with the brand new Nvidia 1.0-0301 Drivers on Soundstorm. perhaps its OSS only, but it works like a charme now without any Modification. I only installed the Audio Driver and it works.

Now i can play my Favourite Game with Teamspeak2 at the same time on Ubuntu, thx for all Tips and Tricks

---

### Post by CrustyDOD on 2005-04-18
[QUOTE=X-fact0r]Hi, try this lines inside a terminal... and then run ET.
```
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss
```If this solution works for you, then is just a matter of adding them to a startup script so that these 3 lines are initialized during boot.[/QUOTE]
Sorry for topic digging!

running this commands in root terminal works for me and TS and ET are working normally..

1. Since all startup scripts have stop/start... things how can i make this loaded during boot? Can i put it into /etc/init.d under some filename and do that update-rc.d thingy?

2. what in the earth does this 3 lines do? any info site so that i can read it?

---

### Post by ming0 on 2005-04-18
1.) You should be able to make a bash script that runs @ startup. Just put this in /etc/init.d as ETSound:
 ```
 #!/bin/bash          
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss
```

And then:
 ```
sudo chmod 755 /etc/init.d/ETSound
``` 

and then:
 ```
sudo cd /etc/rc2
``` 

and then:
 ```
sudo ln -s /etc/init.d/ETSound ./S99ETSound
``` 

That *should* do it--but I'm no expert in getting bash and init scripts working ;)

If anyone spots a problem, or if there are inconsistencies, please post here or PM me and I'll fix it :)

---

### Post by CrustyDOD on 2005-04-19
great it works just fine!

thx!

---

