---
title: "No sound in steam game"
date: 2013-05-05
forum: Gaming &amp; Leisure
---

### Post by chodge987 on 2013-05-05
Hi all,

Ive migrated over to Ubuntu 13.04 fully from many years of using windows as far back as windows 98.

I am enjoying the experience of UBUNTU, everything is blazing fast and simple interface.

However I am using the steam 64bit client for linux and I downloaded a game "S.P.A.Z" (Space Pirates And Zombies), this game worked no problem on Windows 7 but when I run it on UBUNTU the sound does not work?

My sound card work ok on the UBUNTU desktop and also on the websites like YOUTUBE, It even works ok on the videos for games thruogh the Steam client. 

Can somebody help me to get it to work ingame?

I'm new to all the sudo apt malarky, like learning a new language so please if you may... in lehmans terms :confused:

Kind Regards

---

### Post by chodge987 on 2013-05-05
Is there any way I can generate hardware info in order to help with this query?

---

### Post by Perfect Storm on 2013-05-05
First try kill the sound deamon.

Open the terminal (search in DASH for it).

and write;
```
 killall pulseaudio
```
Try start SPAZ again.

You can also try run SPAZ via the terminal and see what's up;
```
steam steam://rungameid/107200
```

---

### Post by Perfect Storm on 2013-05-05
Found this on steam with a quick google search: [http://steamcommunity.com/app/107200/discussions/0/846940249024195945/](http://steamcommunity.com/app/107200/discussions/0/846940249024195945/)

You need to install 32-bit libs to your 64-bit system. Steam and its games are only 32-bit.
It's an easy fix;
```
sudo apt-get install ia32-libs
```

---

### Post by chodge987 on 2013-05-05
[**[COLOR=#C61919][B]Artificial Intelligence**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=19") You are the best,

I already had the 32 bit libs installed and tried everything via the spaz forum site and steam forum site.

I then tried your killall pulseaudio... hey presto it worked first time.

Thank you so much and kudos to you :biggrin:

---

