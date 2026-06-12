---
title: "Now Sound when starting applications about &quot;Applications&quot; -&gt; &quot;Run Application&quot;"
date: 2005-03-05
forum: Desktop Environments
---

### Post by pirast on 2005-03-05
Hey,
When I start applications like tuxracer or frozen-bubble with "Applications" -> "Run Application" in gnome, there isn't any sound. When I start them in a console there is sound.

What is wrong?

On unbuntuusers.de there has someone the same problem...

 :-( 

Thanks for reading  :mrgreen: 

Greetings,
Martin

---

### Post by kassetra on 2005-03-05
[QUOTE=pirast]Hey,
When I start applications like tuxracer or frozen-bubble with "Applications" -> "Run Application" in gnome, there isn't any sound. When I start them in a console there is sound.

What is wrong?
[/QUOTE]

Try this for me, Applications->Games->Frozen Bubble
is there sound when you do it that way?

---

### Post by pirast on 2005-03-05
Hi again,
no sound when trying Applications->Games->Frozen Bubble, too...

In the frozen-bubble menu I can't activate "sound". When I start it in a console, I can activate/deactivate the sound.

Greetings,
Martin

---

### Post by bored2k on 2005-03-05
[QUOTE=kassetra]Try this for me, Applications->Games->Frozen Bubble
is there sound when you do it that way?[/QUOTE]
 try disabling sound server

computer > desk preferences > sounds

---

### Post by pirast on 2005-03-05
Hey,
now there is sound. But I haven't got any sound in gnome. Is it possible that I have sound in programs with sound when I start them with "Start Application" and I have sound in gnome?

If yes, let me please know.

Greetings,
Martin

---

### Post by kassetra on 2005-03-05
[QUOTE=pirast]Hey,
now there is sound. But I haven't got any sound in gnome. Is it possible that I have sound in programs with sound when I start them with "Start Application" and I have sound in gnome?

If yes, let me please know.

Greetings,
Martin[/QUOTE]

Sounds like you're missing some sound libraries... OSS (which is the basic library) doesn't allow more than one sound stream at a time... what kind of sound card do you have, do you know?

---

### Post by pirast on 2005-03-05
Hey,
I can tell you the following about my soundcard: It's an intergrated soundchip. My motherboard is the Asus A7N8X-X with the nforce2 chip.

It an AC97 soundchip. More I don't know. But if it's very important, I could search if I find more pieces of information about my soundchip.

Greetings,
Martin

---

### Post by kassetra on 2005-03-05
[QUOTE=pirast]Hey,
I can tell you the following about my soundcard: It's an intergrated soundchip. My motherboard is the Asus A7N8X-X with the nforce2 chip.

It an AC97 soundchip. More I don't know. But if it's very important, I could search if I find more pieces of information about my soundchip.

Greetings,
Martin[/QUOTE]

That's all I needed to know.  First let's check to make sure the correct sound modules are loaded.
Open a terminal and type the following:
 ```
lsmod |grep snd
``` 
and tell me if you see "snd_ac97_codec" in the left hand side.

---

### Post by pirast on 2005-03-05
yes, I can see it:

```
snd_intel8x0           33068  3
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
gameport                4736  2 snd_intel8x0,analog

```

---

### Post by kassetra on 2005-03-05
Ok good.  That means that you have the correct "drivers" for your sound card.  Now let's check for sound systems...

1. Open Synaptic (Computer->System Configuration->Synaptic Package Manager)
2. Click the Search button.
3. Type alsa and press enter.

Now, tell me what is installed (the green squares).

---

### Post by bored2k on 2005-03-06
[QUOTE=kassetra]Ok good.  That means that you have the correct "drivers" for your sound card.  Now let's check for sound systems...

1. Open Synaptic (Computer->System Configuration->Synaptic Package Manager)
2. Click the Search button.
3. Type alsa and press enter.

Now, tell me what is installed (the green squares).[/QUOTE]

Ok i have his same sound "card" so here's the default ubuntu installed alsa files :

alsa-base
alsa-utils
gstreamer0.8-alsa
libpt-plugins-alsa

How _can_ I get multiple sounds here ?

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]How _can_ I get multiple sounds here ?[/QUOTE]

We all have the same one and I've got multiple sounds plus sounds in frozen bubble.  

So let's add the files I added:
1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed.  (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)

Try sound now.

---

### Post by bored2k on 2005-03-06
[QUOTE=kassetra]We all have the same one and I've got multiple sounds plus sounds in frozen bubble.  

So let's add the files I added:
1. Install alsa-oss
2. Install alsa-headers
3. Make sure you have libesd0 and gstreamer0.8-esd installed.  (if not, install)
4. Make sure esound and esound-common are installed. (if not, install)

Try sound now.[/QUOTE]
 OK I just installed those and checked for the others.

Personally , i was asking multiple sounds in ubuntu in general , not particularly the game.

On my 1st ubuntu install i remember i made it possible, but i did so many things i dont know nor remember wich one worked .

??

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]Personally , i was asking multiple sounds in ubuntu in general , not particularly the game.[/QUOTE]

Right.  Same procedure to make it work for a game as it is to make it work in general.

Ok, next.
1. Right click on the little volume control in your top panel and the choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other for Alsa.  Make sure nothing is muted.
2b. If it does not open and instead gives you an error, let me know.

---

### Post by bored2k on 2005-03-06
[QUOTE=kassetra]Right.  Same procedure to make it work for a game as it is to make it work in general.

Ok, next.
1. Right click on the little volume control in your top panel and the choose Open volume control.
2a. *IF* it opens, you should see two tabs, one for OSS and the other for Alsa.  Make sure nothing is muted.
2b. If it does not open and instead gives you an error, let me know.[/QUOTE]

Ok now this aint good , i did as u -ordered- but now i run into a funky problem ...


in gstreamer-properties, they were both OSS setup and i could test the Output -Sink , now i get Failed 2 construct pipelinefor OSS- Open S....System

Now xmms wille freeze if i try opening an mp3 :'( , and if i put it 2 work on alsa it will say i need 2 configure my sound card.

In rhythmbox i get oss device /dev/dsp is being used .

:s

btw my sound server startup is disables

edit >> the thought of me having no sound removed any type of sleepyness i mightva had [1.20am]

---

### Post by bored2k on 2005-03-06
Ok i reset gnome and now i have sound [breathes heavily]

but still no multisound ... 

wow... im in the caribbean [temperature = HOT] and the thought of no mp3s just made things chilly over here

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]in gstreamer-properties, they were both OSS setup and i could test the Output -Sink , now i get Failed 2 construct pipelinefor OSS- Open S....System

Now xmms wille freeze if i try opening an mp3 :'( , and if i put it 2 work on alsa it will say i need 2 configure my sound card.

In rhythmbox i get oss device /dev/dsp is being used .

btw my sound server startup is disables
[/QUOTE]

It's ok.  We're going to switch you to a sound daemon that allows multiple sounds.
1. In gstreamer-properties, change the Default Sink to output: ESD - Enlightenment Sound Daemon (Why not alsa you ask?  Because alsa makes crackling noises with the ac97)
2. Change your Output plugin in XMMS to eSound output plugin.  (You also might want to think about using beep-media-player ; it's essentially identical to xmms, uses same plugins and skins, only it's made for gtk2 and it's much nicer.)
3. Enable your sound server startup.

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]but still no multisound ... 
[/QUOTE]

Multisound is not available in OSS... which is why we're changing it.  :)  You either run ALSA *instead* of OSS or you run ESD on *top* of OSS in order to get multisound.  In our case, alsa is an option, but one that sounds bad (literally).

---

### Post by bored2k on 2005-03-06
Ça marche !!! Domo arigato !!! Merci beaucoup !!!

thnx a lot imma gmail these instructions 2 myself in case i ever 4get !


btw my 1st post here on the forums was related to xmms and u said same thing about bmp :P , but at that time it crashed every now and then, havent tested the new 0.9.x tho

edit > thnx  a lot !!, again .. like ...20times now lol

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]btw my 1st post here on the forums was related to xmms and u said same thing about bmp :P , but at that time it crashed every now and then, havent tested the new 0.9.x tho[/QUOTE]

You are super welcome!  (and yes, I did look at that post when you said I was the first person to talk to you... so I knew I had suggested it before... and I'm suggesting it again because I'm using 0.9.7 from the backports and it's just "da bomb" ...)

:)

You should now have multisounds all happy.  :)

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]thnx  a lot !!, again .. like ...20times now lol[/QUOTE]

You're welcome you're welcome you're welcome to the infinite power.  :)
(p.s. I have to say this, your avatar CRACKS ME UP!  I LOVE IT!)

and holy cow.  this is my 500th post.

---

### Post by bored2k on 2005-03-06
yes i do thanks, i ALMOST hated listening to an mp3 with gaim on, between mp3s id get lik 200s2pid gaim sounds :@:@:@

funny...i hav backports, my bmp is .9.6.1
probably cuz im on warty ... but thazz ok i got multisound ]*emulates the yahoo farmer sound: yahoooooooooo*

---

### Post by bored2k on 2005-03-06
[QUOTE=kassetra]You're welcome you're welcome you're welcome to the infinite power.  :)
(p.s. I have to say this, your avatar CRACKS ME UP!  I LOVE IT!)

and holy cow.  this is my 500th post.[/QUOTE]
 lol ... i think i found my avatar looking for bizarre or something :P

500 ... thats a whole lotta posts for a month and some days :o

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]funny...i hav backports, my bmp is .9.6.1
probably cuz im on warty ... but thazz ok i got multisound ]*emulates the yahoo farmer sound: yahoooooooooo*[/QUOTE]

hehehehe bpm 0.9.7 is in staging... :)  I'm on warty too.
Here is a list of [plugins made for bmp]("http://www.sosdg.org/%7Elarne/w/Plugin_list") (some are very nice, like bmp-docklet, which I use constantly!)

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]500 ... thats a whole lotta posts for a month and some days :o[/QUOTE]

I know I know!  I just know how to do a bunch of user-type-stuff in Linux and I love Ubuntu and I want to share!  :)

And, I talk a lot.  heh.

---

### Post by bored2k on 2005-03-06
[QUOTE=kassetra]hehehehe bpm 0.9.7 is in staging... :)  I'm on warty too.
Here is a list of [plugins made for bmp]("http://www.sosdg.org/%7Elarne/w/Plugin_list") (some are very nice, like bmp-docklet, which I use constantly!)[/QUOTE]


This is a lil fizz of topic , but is hoary "less" unstable enough for me to try and get a hold of it ?  every time I see a screenshot of the "Places" panel i wanna write it down in my monitor with a purple marker !!

---

### Post by bored2k on 2005-03-06
[QUOTE=kassetra]I know I know!  I just know how to do a bunch of user-type-stuff in Linux and I love Ubuntu and I want to share!  :)

And, I talk a lot.  heh.[/QUOTE]
 lol yes u do know  a lot , iv read several posts from u, and most of them u resolve the problem lol

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]This is a lil fizz of topic , but is hoary "less" unstable enough for me to try and get a hold of it ? every time I see a screenshot of the "Places" panel i wanna write it down in my monitor with a purple marker !![/QUOTE]

Considering that it's going to be released next month, it's getting pretty close.  You might want to wait for the "Release Candidates" that should be coming out later this month.

---

### Post by kassetra on 2005-03-06
[QUOTE=bored2k]lol yes u do know  a lot , iv read several posts from u, and most of them u resolve the problem lol[/QUOTE]

I really try hard to fix the stuff I know about.  I won't try to help someone with something I know nothing about, because that gets people in trouble.  heh.

I guess I'm a "power" Linux user nowadays.  heh.  :)  (I've certainly killed, mangled, murdered, and destroyed enough installations to know what NOT to do!)

---

### Post by bored2k on 2005-03-06
[QUOTE=kassetra]I really try hard to fix the stuff I know about.  I won't try to help someone with something I know nothing about, because that gets people in trouble.  heh.

I guess I'm a "power" Linux user nowadays.  heh.  :)  (I've certainly killed, mangled, murdered, and destroyed enough installations to know what NOT to do!)[/QUOTE]
 lol

Well thanks anyway ill do that :D


Imma 10-3 now and go 10-7.
[ [http://faculty.ncwc.edu/toconnor/polcodes.htm](http://faculty.ncwc.edu/toconnor/polcodes.htm) ]

---

### Post by pirast on 2005-03-06
[QUOTE=kassetra]Ok good.  That means that you have the correct "drivers" for your sound card.  Now let's check for sound systems...

1. Open Synaptic (Computer->System Configuration->Synaptic Package Manager)
2. Click the Search button.
3. Type alsa and press enter.

Now, tell me what is installed (the green squares).[/QUOTE]
 Hey,
The following packages are installed (marked green):

alsa-base
alsa-utils
gstreamer0.8-alsa
libpt-plugins-alsa

Greetings,
Martin

---

### Post by pirast on 2005-03-06
Hi there again,
I installed the packages, nothing is muted in the volume control, in gstreamer-properties there is the default sink ESD.

Yes, that's it. I restarted my system already, but no sound in frozen-bubble etc..  :-& 

Any ideas?

Greetings,
Martin

---

