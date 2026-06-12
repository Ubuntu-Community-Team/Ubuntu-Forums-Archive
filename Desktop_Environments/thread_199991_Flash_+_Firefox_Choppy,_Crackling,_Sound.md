---
title: "Flash + Firefox Choppy, Crackling, Sound"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Jeff_From_VA on 2006-06-19
I am having an issue with flash playing sound properly. At first I could not get it to work at all, it would play 2 seconds of a video with no sound and would lock up firefox completly.  I installed and ran automatix and that got my flash playing with out crashing, but the sound is choppy and crakling.

Playing cd's, mp3's, dvd's, and the gnome system sounds all work perfectly.

I used to run gentoo on my pc, and flash worked fine after alot of messing with it to get it to work at all, so I know it is possible to use flash in linux w/o sound issues. 

Does anyone have any idea why this may be causing me trouble?

---

### Post by gerbman on 2006-06-20
[QUOTE=Jeff_From_VA]Does anyone have any idea why this may be causing me trouble?[/QUOTE]Not really, but you might try installing the alsa-oss package. I had no sound with Flash+Firefox before doing this.

---

### Post by Jeff_From_VA on 2006-06-21
I did.. :( - I hate flash, and it seems everything uses it now.

---

### Post by djmdave on 2006-06-22
I had problems getting sound working with flash too, although I had no sound whatsoever. Found the solution in the [dapper dev forums.]("http://www.ubuntuforums.org/showpost.php?p=1042626&postcount=14")

All I needed to do was 

```
sudo apt-get install alsa-oss
``` 
then run this command:

```
aoss firefox
``` 
Flash s with sound started running perfectly immediately after!

Hope it works for you too, because I know how frustrating it can be! ](*,)

---

### Post by degel3030 on 2006-06-22
is the only way to get firefox to start like that by default is to right click on the icon and go to properties and then change the command to 'aoss firefox' ?
just wondering cause thats what i did but i was thinking maybe there was another way

---

### Post by callit on 2007-06-27
I'm actually having a similar issue not resolved by the above fix.

Playing MP3s/videos have no issue with sound.  Flash audio in firefox is choppy.  I'm also having trouble with two things trying to play sound at once (with alsa explicitly specified where possible).

---

### Post by fizzmo on 2007-07-04
I have the same issue as above

---

### Post by fizzmo on 2007-07-08
anyone has a solution cause its very annoying :(

---

### Post by fbusy on 2007-07-10
I too have the same issue

---

### Post by TLD321 on 2007-07-12
I also have this problem, anyone know how to fix it?

---

### Post by kamagurka on 2007-09-11
Thanks, this worked for me, but please clarify something: Do I need to run Firefox with the aoss prefix all the time or does running the command once fix the sound gremlins flash - may its eyeballs fall into a wood chipper - has blessed me with?

---

### Post by Thrym on 2007-11-11
I also have a similar problem. I tried to get 5.1 sound for days now and when I finally found the solution (placing a asoundrc. file in my home folder) I noticed that flash sound in firefox does not work anymore. Before that everything was fine with the flash sound, but the sound was only stereo. This is how my asoundrc, looks like at the moment:

################################################## #######
#This is the standard setting (see: "!default")
#This profile, the default loaded, upmixes stereo sound to 5.1.

pcm.!default {
type plug
slave.pcm "surround51"
slave.channels 6
route_policy duplicate
}
################################################## ######
#This is the normal spdif output profile (optical, toslink).

pcm.!spdif {
type plug
slave.pcm "hw:0,1"
}

################################################## #####
#This is what one could call the "factory default setting", in other words, it only plays the actual channels. so if you fx want to watch a 5.1 movie, on the analog output, this is the option you want.


pcm.analog {
type plug
slave analog_slave;
}

pcm_slave.analog_slave {
pcm surround51;
format S32_LE;
}

if anyone has a solution for this problem, please help me out! 
Thanks in advance.

---

### Post by Thrym on 2007-11-12
okay I just found out that I had the same problem with the VLC player until I changed it's sound mode to alsa. Is there any way to change the flash sound in Firefox to alsa too? Thank you

---

### Post by dannystaple on 2008-02-03
I think using the aoss (an OSS alsa wrapper) may fix it by trying to do just that, but it still does not work for me. I wander if there is some horrible buffering change in the way ALSA is handling my card.

---

### Post by mt330404 on 2008-03-12
same issue here... audio/video plays fine but when it's a flash video i.e. youtube, cbsnews.com, it's choppy as HELL.. not even worth watching the videos when it's this choppy.. please help!! I ran the aoss firefox command after installing that package, but doesnt seem to be much difference before/after.

---

