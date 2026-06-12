---
title: "Vostro 1500 + ubuntu 7.10 = Microphone problems"
date: 2007-11-11
forum: Dell  Ubuntu Support
---

### Post by Dreamskiller on 2007-11-11
Hi everybody; I'm french, so sorry for my poor english ^^.

I've a little problem with my Vostro, everything work fine (Bluetooth, Wifi, Sound and headphones, Compiz with my 8600M Gt, etc) but i've still a little problem.
I often use Teamspeak to play (I play W3 with playonlinux) and I must plug a mic to speak.
But I don't find the way to make it work, evenif I can use the integrated microphone by choosing "Digital input source : digital mic 1", but the sound is low. 
It's strange because i don't have any option about microphone, and i don't have mic boost.
Some screens of my sound menu ;
[[img]http://nsa01.casimages.com/img/2007/11/11/0711110424081584768.png[/img]](http://www.casimages.com)
[[img]http://nsa01.casimages.com/img/2007/11/11/0711110425031584771.png[/img]](http://www.casimages.com)
[[img]http://nsa01.casimages.com/img/2007/11/11/0711110425271584773.png[/img]](http://www.casimages.com)
[[img]http://nsa01.casimages.com/img/2007/11/11/0711110425521584775.png[/img]](http://www.casimages.com)

Thanx a lot for your answer

---

### Post by Dreamskiller on 2007-11-14
I'm sure its something simple, but i don't find the problem :s

---

### Post by Dellfan on 2007-11-14
You should be able to enable the microphone by:

1) Double click on the volume icon on the panel.
2) Select Edit>Preferences.
3) Select Microphone,Mic boost,Capture.

Once you do this you should find a  new capture tab in volume control panel.Here make sure nothing is muted(no red x on microphone icon). In options tab make sure you selected Microphone as input source.

---

### Post by Dreamskiller on 2007-11-14
Hehe, I know that, the problem is that i Don"t Have Capture, Microphone and mic boost.
You can see here all the things that i can enabled in preferences :s.
I dunnno why i don't have mic :/
In Analog line input i can choose mic 1, but i thing it's the integrated mic (it works, but not as loud as i want...)

---

### Post by Dellfan on 2007-11-14
Take at look at:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

Especially Method G... (readers digest version)

sudo aptitude install linux-backports-modules-generic

and then you may have to do the following

sudo gedit /etc/modprobe.d/alsa-base

in the editor, add the following line at the end of the file:

 options snd-hda-intel model=dell-m42

or perhaps

options snd-hda-intel probe_mask=1 model=3stack

A suggestion... this was all easily found using Google with the search "+ubuntu +vostro +sound"... always remember google is your friend and it is earier to use it to search ubuntu forums that the built in search tools... :)

---

### Post by Dreamskiller on 2007-11-15
In fact I have already done that, but maybe with other lines (Dunno why there are so much different lines to add to alsa-base :s).
But for the moment it just don't works.
I'm going to add that to my alsa-base, should i have the microphone, mic boost and capture in the preferences' menu then?

Ps:Thx for your help, but i don't like your way to answer ^^, maybe, if you have red my first message can you see that i've the sound working on my computer, so you may have understood that i've already installed the generic modules package^^. (and google is my love ;))

---

### Post by Dellfan on 2007-11-15
If sound was installed and working correctly then you should be able to enable it via Edit-Preferences in the Sound Volume applet. The fact that you can't points to it either being not correctly installed or not correctly configured.

Was not trying to be snide. One of the big problems with offering help over a web forum is that you have not idea of the questioner's knowledge level, what they may have done, or how correct their problem description is. Also, many, many people post questions without trying anything or doing any looking around.

When I spent some time looking last night for Vostro info it seemed that everyone that was having issues was having issues with alsa. I don't have a Vostro to play with and it just works on a stock install of 7.04 and 7.10 on my 1505, which has a similar Intel audio setup to your Vostro.

---

### Post by Dreamskiller on 2007-11-16
Microphone Fixes
Method A
does work: Dell Vostro 1500 (card: SigmaTel STAC9205)
This workaround comes from this ALSA bug: [WWW] [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3495](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3495)
      Open Volume Control
      Go to Edit -> Preferences
      Make sure "Digital" and "Digital Input Source" is selected
      On the "Recording" tab, make sure the "Digital" slider is non-muted and turned up
      On the "Options" tab, make sure the "Digital Input Source" is set to "Digital Mic 1"
In fact, i'had done all of this things before asking help, but i don't works, only my internal microphone works >.<.
Apparently there are no changes, but i'll test more this w-e, i don't have any external mic here (my internal microphone still works correctly, but with a low sound).

PS: It's ok ^^, I understand. But I search a lot, it's the first time I'm really asking for help on a forum.

---

### Post by Dreamskiller on 2007-11-17
So, no one can help?
I tried a lot of things, but nothing new... my external mic still doesn't work.

---

### Post by mushroomcloudwarrior on 2007-12-12
I'm using Kubuntu on a Dell vostro 1500, haven't been able to find myself a fix for this problem..

External Mics dead as a duck :( i'll just keep looking.

---

### Post by 5of0 on 2008-01-20
I fixed this on my own vostro 1500 by going to the volume control panel and choosing Change Device->Sigmatel XXXXXX (OSS Mixer)
Where XXXXXX is the model of your sound card.

---

