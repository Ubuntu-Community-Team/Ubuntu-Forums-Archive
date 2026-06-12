---
title: "ET sound issues"
date: 2007-04-26
forum: Gaming &amp; Leisure
---

### Post by yodaky on 2007-04-26
I know this has been an issue in the past as I remembering reading the posts.  I have tried searching for them but whenever I enter "Enemy Territory", "et sound", "enemy territory sound" or anything similar I get a page saying that there were no results.  If I back up to the previous page (page 1) in the Gaming forum I see a thread that has Enemy Territory in it so I fail to see why I can't find any results.

Anyway, I have installed the game fine but sound will not work unless I do :
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
killall esd
et

Doing the above works, so when I try to do:
sudo -s
echo "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" >> /etc/environment
echo "echo "et.x86 0 0 disiable" > /proc/asound/card0/pcm0c/oss" >> /etc/environment
exit

I still get sound until I reboot.  Is there anyway to add any of the above to a script or something so I don't have to do this every time I want to play the game?

Thanx

---

### Post by yodaky on 2007-04-26
No need to reply I guess.  I was really trying to get TC:E installed and the sound in it works just fine for some reason :/

---

### Post by Focus Fate on 2007-04-26
I too get no sound :(

---

### Post by F43RY on 2007-04-27
> **yodaky said:**
> No need to reply I guess.  I was really trying to get TC:E installed and the sound in it works just fine for some reason :/
I've your same problem and I would like to avoid to type the same command every reboot.
Could you explain to me what did U exactly do? What is TC:E? 

Thx

---

### Post by abowman on 2007-04-27
> **F43RY said:**
> I've your same problem and I would like to avoid to type the same command every reboot.
Could you explain to me what did U exactly do? What is TC:E? 

Thx

I sounded to me like he just wanted to play the mod True Combat:Elite.  He didn't get the sound to work in ET, and didn't need to because he found out that it worked in TC:E.

---

### Post by yodaky on 2007-04-28
Yea I was only trying to give True Combat: Elite a try and noticed the sound worked in there.  Oddly enough it still doesn't work in ET but it does in TC:E.

---

### Post by mr_niceguy on 2007-05-09
You should be able to automate these commands by prepending them to the enemy territory launcher script, which is '/usr/local/bin/et'.

Just edit the file (it is text) and right below the first line add the following:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

---

### Post by F43RY on 2007-05-10
> **mr_niceguy said:**
> You should be able to automate these commands by prepending them to the enemy territory launcher script, which is '/usr/local/bin/et'.

Just edit the file (it is text) and right below the first line add the following:

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

This solution works only launching et with sudo the first time. Launching et as normal user it doesn't works until I type 

```
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

```

or until I type at least once
```

sudo et

```

It looks like the script in /usr/local/bin/et couldn't execute the lines I added because he hasn't root privilege.

What can I do?


Thx

---

### Post by ultramancool on 2007-05-11
How about wedging sudo in front of both of 'em so you get: 
```

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```

Oh, and thanks for the fix by the way :)

---

### Post by lolwtf on 2007-06-02
this is bull i have typed it exactly as u guys have typed it and it doesnt work argh!!!! i supose i will have to look 4 about 3 days for some 1 who does know wot they r talking about (like i did 4 gfx) sigh..................................

---

### Post by Rafty on 2007-06-03
[size=12]**No sound in ET / TC:E**[/size]

the following should help you, if you have no sound at all in ET/TC:E or no sound in ET/TC:E when Teamspeak is running at the same time.

in a terminal type:
```
sudo -s
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
exit
```

to get this commands started after booting automaticly:
open an editor with root rights and type
```
#!/bin/sh
#Bug in Wolfenstein ET
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
```
save the file as "et-sound" in "/etc/init.d/". after this file is created you need to tell your system about it:
```
sudo chmod 755 /etc/init.d/et-sound
sudo update-rc.d et-sound defaults
```

-------------

Edit:
in case of
[color=orange]bash: /proc/asound/card0/pcm0p/oss: Permission denied[/color]
type in a terminal
[color=orange]sudo chmod 777 /proc/asound/card0/pcm0p/oss[/color]

---

### Post by F43RY on 2007-06-03
Hi,
I'll try it as soon as I'll get home. I hope it will be the final solution for this annoying issue.

I'll give you a feedback asap.


thx again.

---

### Post by F43RY on 2007-06-04
YEAH \\:D/
It works!!!!!!


Thank you very much

---

