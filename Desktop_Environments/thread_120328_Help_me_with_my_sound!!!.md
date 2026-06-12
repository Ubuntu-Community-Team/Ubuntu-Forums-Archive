---
title: "Help me with my sound!!!"
date: 2006-01-21
forum: Desktop Environments
---

### Post by Cool_dude_Prav on 2006-01-21
I was working with XMMS and the sound was crystal clear (as is the speciality of Linux)

But once, I shut down without exiting XMMS (play was stopped) and since then, whenever I try to play any sound file in XMMS or any other MediaPlayer on KUbuntu, I cannot listen to any sound...
In fact I cant even listen to the Welcome tune on Kubuntu or the shutdown tune...

Plz help me ASAP...

Prav.

---

### Post by Cool_dude_Prav on 2006-02-02
someone plz help... i feel like i have become deaf without any sounds on my KUbuntu... :-s

---

### Post by apswartz on 2006-02-03
Is artsd running? Show us the results of this command...

ps ax |grep artsd

---

### Post by Cool_dude_Prav on 2006-02-04
[QUOTE=apswartz]Is artsd running? Show us the results of this command...

ps ax |grep artsd[/QUOTE]
```
root@PravNET:~# ps ax|grep artsd
 8447 ?        S      0:00 /usr/bin/artsd -F 10 -S 4096 -s 60 -m artsmessage -c drkonqi -l 3 -f
 9010 pts/1    S+     0:00 grep artsd

```

Hope this helps... :cry: 

Plz help me ASAP... ](*,) 

Thanks in advance...

---

### Post by YourSurrogateGod on 2006-02-04
Did you try?

Settings -> Sound -> Sound System

Then in the tab "General", see if "Enable Sound System" is checked.

---

### Post by Rory on 2006-02-04
Have you done a hard reboot, just to see if it kills any processes that may be running that shouldn't be?

---

### Post by Cool_dude_Prav on 2006-02-04
[QUOTE=YourSurrogateGod]Did you try?

Settings -> Sound -> Sound System

Then in the tab "General", see if "Enable Sound System" is checked.[/QUOTE]
Yup... Its enabled...

[QUOTE=Rory]Have you done a hard reboot, just to see if it kills any processes that may be running that shouldn't be?[/QUOTE]
I have rebooted many times since I reported this problem... (Scroll above to see that the first post was 1 week ago)

So plz suggest some thing else...

---

### Post by analyticalman on 2006-02-04
Have you gone into kmix and checked that the PCM switch is set to a high level as well as the master volume?  Have you tried kaffeine to play your tunes?

---

### Post by Cool_dude_Prav on 2006-02-04
[QUOTE=analyticalman]Have you gone into kmix and checked that the PCM switch is set to a high level as well as the master volume?  Have you tried kaffeine to play your tunes?[/QUOTE]

Yup tried all...

Sometimes the audio plays on XMMS/Kaffeine/AmaroK without any errors but no sound is heard...

Other times it says - Your audio device is being used by another program... even though no other audio-related program is running...
I even rebooted many times...

---

### Post by Peter41az on 2006-02-04
Are you using arts or Kmix trying to get the sound? try this.. 

go under multimedia and click volume control there. even when i futz with Arts all day and Kmix, it wont come back until i set settings in volume control.  Try this after you have already tried restarting the sound server. Sometimes the sound server gets taken over by running processes. 

Hope this helps.

---

### Post by coolclassic on 2006-02-05
I now have the same problem, sound was working untill last night when I put a cd in. I have done all the above and can not get it working.This affects games, movies and music.

---

### Post by Cool_dude_Prav on 2006-02-08
I tried whatever all of you mentioned above to no use at all...

I use KMix for audio... Volume is set to full... Speakers work with in-built radio as well as MiCr0$0fT Windows... So plz help me to make it work with KUbuntu... as I really miss some quality in the audio which is not available in Windows...

Update...
Now I seem to get an error message while I try to play audio in XMMS...
```
Please Check that:

Your soundcard is configured properly.
You have the correct output plugin selected.
No other program is blocking the program.
```

error message while I try to play audio in Kaffeine...
```
There were no decoders found to handle the stream, you might need to install the corresponding plugins
```
But the fact is that all possible decoders are installed for both XMMS and Kaffeine and amaroK, and yet i can play sound in any format nor do I listen to the startup and shutdown sounds...

In fact I cant hear any sounds at ALL!!!

Someone plz help... S.O.S

---

### Post by cwaldbieser on 2006-02-08
[QUOTE=Cool_dude_Prav]I tried whatever all of you mentioned above to no use at all...

I use KMix for audio... Volume is set to full... Speakers work with in-built radio as well as MiCr0$0fT Windows... So plz help me to make it work with KUbuntu... as I really miss some quality in the audio which is not available in Windows...

Update...
Now I seem to get an error message while I try to play audio in XMMS...
```
Please Check that:

Your soundcard is configured properly.
You have the correct output plugin selected.
No other program is blocking the program.
```

error message while I try to play audio in Kaffeine...
```
There were no decoders found to handle the stream, you might need to install the corresponding plugins
```
But the fact is that all possible decoders are installed for both XMMS and Kaffeine and amaroK, and yet i can play sound in any format nor do I listen to the startup and shutdown sounds...

In fact I cant hear any sounds at ALL!!!

Someone plz help... S.O.S[/QUOTE]

What are your aRTs settings?  On the HardWare tab, what sound system are you using?

---

### Post by Rory on 2006-02-08
When I first started using Linux, sound was a nightmare for me.  It was all eventually resolved by me simply playing with my KMix settings (section 'B' below).

I have two main suggestions:
A) first, given your error message, check that all codecs are installed again:
step 1: make sure you've added all repos, especially the PLF repo:
[http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories)

step 2: add these codecs again, just to make sure you've captured everything.  I suggest you do all of these commands, including the last gst-register one.  I don't think it hurts to cover your bases by doing everything.
[http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs](http://easylinux.info/wiki/Ubuntu#How_to_install_Multimedia_Codecs)

B) Open KMix
Now that everything is installed, above, you can try my settings.  This is what works for me, but it may be worth a shot for you:

Kmix 
Output 	> Master Surround (on,max)
	    > Master (on, max)
	    > PCM (on, main volume control)

Input	> CD (on)


I know you're frustrated, but recognize that people are trying to help you.  

Rory

---

### Post by Cool_dude_Prav on 2006-02-10
hey guys...

i found out that after medling with KMix settings I can hear the error sounds like when K3B burn got over, was stopped etc.. It is I cant play sounds from any Multimedia player but can hear other sounds...

And XMMS still says that the sound is being utilized by some other software... (Refer above for details)
So plz help me!!!

---

### Post by Rory on 2006-02-10
Well, this is good news.  You're half way there.  You have sound.  This issue seems to be codec support and/or the player you're using.

As a test, I would download a file and play the same file through multiple players.  It likely won't work but don't depend on testing with one player at this stage.

Did you follow my instructions, above, re: adding the PLF and backports repo and then re-installing all codecs?  I'd suggest this as a next step.  

I'd also install RealPlayer 10 and test it on a couple of sites.  You're really playing a game of deduction, at this stage.  But, you're moving in the right direction.

Rory

---

### Post by Cool_dude_Prav on 2006-02-12
hmm.. i tried to install those codecs...

i found only 2-3 of them... like vorbis and w32codecs

and btw, if u dint notice, i mentioned that those songs/music was being played on my system,
and once i booted accidentally leaving XMMS on and it was SINCE then that the songs are not being played on ANY PLAYER...

I dont think it might be a codec issue... :s

Prav.

---

### Post by Rory on 2006-02-12
If you only found a couple of those codecs, then I suspect you didn't update your repository with PLF and backports.

I'd also like to say that your tone is rude and demanding.  People are trying to help you, yet you don't seem thankful.  Instead, you're being pushy and if you don't get the proper advice, you response borders on impolite.  As a result, I'm going to move on to another thread.

Best of luck!

R.

---

### Post by Cool_dude_Prav on 2006-02-13
hey, i am really sorry that you felt me to be a bit rude...
and as u said, i was really getting frustrated... i have been jumping from irc to irc... and have been asking at 2 forums (ubuntu and Kubuntu) without much results...
that may have led me to desperation... and I really feel bad about this...

And regarding that codec thing, i tried many times to fetch updates AFTER adding that plf repo., but only some of the plugins were available...

I then went to ubuntu package search (avlble on Ff and Konqueror) and searched for those and installed them manually using dpkg -i and now it is all over...
(I dint install the gstreamer plugins, as I am not using it)
And I must say, i am really indebted to u :KS , as amaroK is currently playing my fav. music... (crazy frog)

but the thing is that Kaffeine and XMMS are not playing..
But i dont care about XMMS now as amaroK rocks equally hard... ;)
But Kaffeine not playing video files is a matter of concern...
Plz help out this last problem of mine [-o<

And I wud be really indebted to all of the Ubuntu community...[-o<

And once again, I apologise if i have offended anyone by being a bit impatient and/or rude...

Prav.

---

### Post by cwaldbieser on 2006-02-13
[QUOTE=Cool_dude_Prav]hey, i am really sorry that you felt me to be a bit rude...
and as u said, i was really getting frustrated... i have been jumping from irc to irc... and have been asking at 2 forums (ubuntu and Kubuntu) without much results...
that may have led me to desperation... and I really feel bad about this...

And regarding that codec thing, i tried many times to fetch updates AFTER adding that plf repo., but only some of the plugins were available...

I then went to ubuntu package search (avlble on Ff and Konqueror) and searched for those and installed them manually using dpkg -i and now it is all over...
(I dint install the gstreamer plugins, as I am not using it)
And I must say, i am really indebted to u :KS , as amaroK is currently playing my fav. music... (crazy frog)

but the thing is that Kaffeine and XMMS are not playing..
But i dont care about XMMS now as amaroK rocks equally hard... ;)
But Kaffeine not playing video files is a matter of concern...
Plz help out this last problem of mine [-o<

And I wud be really indebted to all of the Ubuntu community...[-o<

And once again, I apologise if i have offended anyone by being a bit impatient and/or rude...

Prav.[/QUOTE]

I have had more success with gxine than kaffeine.  What happens when you try to play something in kaffeine?

---

### Post by Cool_dude_Prav on 2006-02-13
it shows that proper decoder not installed,

although I have installed
-> all xine codecs
-> lame
-> sox
-> ffmpeg
-> mjpegtools
-> vorbis-tools
-> w32codecs

What should i do?
BTW, here is the EXACT error shown by kaffeine.. (cope+paste)
```
There were no decoders found to handle the stream, you might need to install the corresponding plugins
```

What must I do? I tried to search in adept/synaptic for kaffeine and found all its related files are installed!!!

Prav.

---

### Post by Cool_dude_Prav on 2006-02-13
woops i never realised kaffeine used gstreamer, was looking only at xmms player :D
I just installed all possible gstreamer plugins available in case...

the gstream ones i installed include..
-> gstreamer0.8-plugins
-> gstreamer0.8-lame
-> gstreamer0.8-ffmpeg
-> gstreamer0.8-a52dec
-> gstreamer0.8-cdio
-> gstreamer0.8-gtk
-> gstreamer0.8-lame
-> gstreamer0.8-mad
-> gstreamer0.8-mms
-> gstreamer0.8-mpeg2dec
-> gstreamer0.8-swfdec

But now it says...
```
OSS device "/dev/dsp" is already in use by another program.
```
What might be the problem...

And I am getting happier by the moment as all my problems are getting solved slowly :mrgreen:

Prav.

---

### Post by short4lif2 on 2006-02-13
The multiple sounds issue is a big one.  I have had it for a long time.  Only one program can use my sound card at a time.  There have been many solutions posted about this but none have helped me.

---

### Post by Cool_dude_Prav on 2006-02-17
anyone plz help me with (perhaps) the last problem... :D

Please...

---

### Post by cwaldbieser on 2006-02-17
[QUOTE=Cool_dude_Prav]anyone plz help me with (perhaps) the last problem... :D

Please...[/QUOTE]
```

$ lsof /dev/dsp

```
Should tell you the process using the sound device.  If it is esd, try
```

$ killall esd

```

---

### Post by Rory on 2006-02-17
If you have Amarok playing and are happy with it, then XMMS not working shouldn't be a big deal.  Good to see you making some progress.  I love Amarok.

As for Kaffeine... hmm... Have you tried loading Xine?  Or MPlayer?  I use Xine and have always been pleased with it.  

In terms of multiple sounds, I've had that, too.  I've just ended session and gone back in or killed my Mplayer process.

Try Xine, as a start.  Right now, looking for alternatives that will work will at least give you new options.

R.

---

### Post by mishell on 2006-02-17
I would like thank u all 4 help :) Now in warsaw is 4 in the morning and I wonder do I need to sleep couse my sound is working perfectly at the moment :) 

I had different situation couse I had sound after starting Kubuntu (geez I wanted to write windows :/) and after logging out but in all sorts of multimedia progs it was silence. 

Once again I'm very gratefull thank you one more time :)

I really love death metal >:D

---

### Post by mishell on 2006-02-17
Shit I doesn't work :/ The best thing is I dunno what I had done. And again the system sound works properly yeah I'll be listenig to the bebs all my life, but then it comes to the mp3 nothing happens

---

### Post by Rory on 2006-02-18
step 1: make sure you've added all repos, especially the PLF repo:
[http://easylinux.info/wiki/Ubuntu#Ho...a_repositories](http://easylinux.info/wiki/Ubuntu#Ho...a_repositories)

step 2: add these codecs, just to make sure you've captured everything. I suggest you do all of these commands, including the last gst-register one. I don't think it hurts to cover your bases by doing everything.
[http://easylinux.info/wiki/Ubuntu#Ho...timedia_Codecs](http://easylinux.info/wiki/Ubuntu#Ho...timedia_Codecs)

---

### Post by mishell on 2006-02-18
heh I got it :). Its not about the codecs. Problem is that some program is using alsa therever I am using it or not, I have to kill some proces which is using it and then all problems R gone. 

really helpful code is
ps ax| grep artsd 

killing it makes everything ok :)

Once again thank U all for help

---

### Post by Cool_dude_Prav on 2006-02-21
[QUOTE=cwaldbieser]```

$ lsof /dev/dsp

```
Should tell you the process using the sound device.  If it is esd, try
```

$ killall esd

```[/QUOTE]
nothing works... :(

[QUOTE=mishell]heh I got it :). Its not about the codecs. Problem is that some program is using alsa therever I am using it or not, I have to kill some proces which is using it and then all problems R gone. 

really helpful code is
ps ax| grep artsd 

killing it makes everything ok :)

Once again thank U all for help[/QUOTE]
I tried but no use...

Someone else? Is there any other way to make kaffeine work??

I am also trying Xine and MPlayer... lemme see...

---

