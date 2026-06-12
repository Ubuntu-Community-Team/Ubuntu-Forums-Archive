---
title: "UT2004-No Sound"
date: 2006-06-22
forum: Gaming &amp; Leisure
---

### Post by Rosenrot on 2006-06-22
I Have UT2004 and ive recently been able to get the game running very well with the help of AI

but now i have no sound
ive searched on the forum and ive tried the fixes posted before except the one in this article about adding "sleep 5" in UT2004's shell executable

<a>http://ubuntuforums.org/showthread.php?t=140486</a>

but I have no idea what a shell executable is or how to add to it

thanks in advance!

---

### Post by Rosenrot on 2006-06-22
anyone?

---

### Post by Perfect Storm on 2006-06-22
You should properly post the output of UT2004 when running it in the terminal. So people can see the error the shows up :)

---

### Post by Rosenrot on 2006-06-22
im not getting an error

i start UT2004 it works fine
but there's no sound : |

---

### Post by MetalMusicAddict on 2006-06-22
Start it from a terminal, not a launcher.

---

### Post by Rosenrot on 2006-06-22
i started it through terminal and i get this


b@b-desktop:~$ /usr/local/games/ut2004/ut2004
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".


i have no idea what its telling me im 'missing'

---

### Post by MetalMusicAddict on 2006-06-22
It looks like a driver issue. Look at [THIS]("http://www.rage3d.com/board/showthread.php?p=1333227291") thread. Its a little old but should help. Google is your friend. ;)

---

### Post by Rosenrot on 2006-06-22
that thread had solutions for a video card driver fix
ive already fixed my video card driver earlier

the person with the problem also said UT2004 was 'crashing'
my ut2004 doesn't crash
ive can play it fine with very smooth gameplay

just no sound
and ive searched on google constantly (about 6+hours) looking for a fix

but all i find is forum's that are discontinued and a solution was never met : /
so this is all a bit frustrating for me

---

### Post by MetalMusicAddict on 2006-06-22
Seen [THIS]("http://www.linuxquestions.org/questions/showthread.php?t=237788") one? If so, Im at a loss. :-k

---

### Post by Rosenrot on 2006-06-22
thank you that thread is much better : ] and i went to

alsamixer

and it says

master-80
tone-MM  (im guessing mute?)
Bass 50<>50
treble 50<>50
3d Contr MM
3d Contr- 0
PCM 80<>80
PCM Cent 100

also if i try to kill art sd i get the following error

b@b-desktop:~$ killall artsd
artsd: no process killed
b@b-desktop:~$ killall-9 artsd
bash: killall-9: command not found

and in the last post i have no idea what he was saying to do in terminal : /

please excuse my Newbness : |

---

### Post by Oblong_Cheese on 2006-06-22
I have no sound in UT2004 although it complains like this:

```

open /dev/[sound/]dsp: No such device

```

I have Googled, forum-searched and banged my head endlessly. I can't figure it out. Everyone else has a similar, but different error.

Any ideas anyone?

I get the same thing with Wolf:ET too. I suppose they're related.

---

### Post by Rosenrot on 2006-06-22
[QUOTE=Oblong_Cheese]I have no sound in UT2004 although it complains like this:

```

open /dev/[sound/]dsp: No such device

```

I have Googled, forum-searched and banged my head endlessly. I can't figure it out. Everyone else has a similar, but different error.

Any ideas anyone?

I get the same thing with Wolf:ET too. I suppose they're related.[/QUOTE]

i had that before i installed my nvidia driver then it went away oddly

now im just getting

Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".



im also trying to install the update 3339 for ut2004 but idk how to install it in linux : /

---

### Post by Perfect Storm on 2006-06-23
Download the megapack and you have it all - [http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11](http://gaming.gwos.org/index.php?option=com_joomlaboard&Itemid=30&func=view&id=256&catid=11)

Extract the file (you can right click it and choose extract)

**Warning: This is a dangerous way to use linux, and are not something to do normally and should be avoided:**

Open the terminal:
```
gksudo nautilus
```
Now you have a file browser with adminstration priveledge, move the extracted files to **/usr/local/games/ut2004**

Close the adminstration priveledge file-browser. Done.

---

### Post by Rosenrot on 2006-06-27
thanks: ] I installed the patch

i got sound once when i was showing my friend that it had no sound(cus he wanted to have a lan match) and it worked only that time i had started it and ive tried starting it numerous times..no sound

and im still getting the error 
b@b-desktop:~$ /usr/local/games/ut2004/ut2004
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".

which i find odd cus its not the
open /dev/[sound/]dsp: No such device

which ive had in the past

and im told the errors im getting now mean nothing and are harmless : |

---

### Post by jonboy99 on 2006-06-28
Hi, not sure if you've fixed this problem yet, but i'm having the same.

However, i've downloaded the demo 2 days ago and it plays fine with sound, and it's an older version (3334).  I smugly read your thread thinking i would have no problems when I bought the full game, but no sound.

However, after loading the demo then quitting, then the 2nd or third time I run the game the sound is fine, so it must be something in the config, not your computer.
FWIW I also get the same error in the terminal as you describe with the demo, so I think that's unrelated.

Let me know if this workaround does it for you too.  Demo file is here:  (the zipped version doesn't unzip for me for some reason so I downloaded the 280meg unzipped version from the 1st australian public server)

[http://www.3dgamers.com/dlselect/games/unrealtourn2k4/ut2004-lnx-demo3334.run.html](http://www.3dgamers.com/dlselect/games/unrealtourn2k4/ut2004-lnx-demo3334.run.html)

[EDIT]  Ok, it doesn't seem to be the demo that sorts it, every 3rd or 4th time i run the program, the sound works.  Arse.

---

### Post by jonboy99 on 2006-06-28
Ok, this thread on the linspire forum sorted it for me:

[http://forum.linspire.com/viewtopic.php?p=283179](http://forum.linspire.com/viewtopic.php?p=283179)


Before running ut try typing:

```
killall artsd
```

I have entered this in the UT startup script and problem sorted.  No idea why the demo runs without needing to do this but seems a common problem.

[EDIT]  Ah, you've tried this.  Oh well.

---

### Post by Rosenrot on 2006-06-29
i have no way of downloading the demo at the moment for that system because my internet is down(onbaord modem problem) and i don't have a usb stick or anything

and when i try killall artsd
i get this

b@b-desktop:~$ killall artsd
artsd: no process killed

i find this odd
also when i try to kill alsa i get the same error

---

### Post by Vectrox on 2006-06-29
Im also having this problem with UT2004 and various other games, this works for me:

1. Open terminal ;) 
2. Then enter: "killall esd".

After youve done this, start UT2004 and most likely the sound will work.

---

### Post by haani on 2006-07-04
[QUOTE=Vectrox]Im also having this problem with UT2004 and various other games, this works for me:

1. Open terminal ;) 
2. Then enter: "killall esd".

After youve done this, start UT2004 and most likely the sound will work.[/QUOTE]

thanks this fixed my issue with sound!!!!

---

### Post by Rosenrot on 2006-07-04
i stated earlier that i tried killall esd and it didn't work

and i also get errors with killall alsa

---

### Post by lordmule on 2006-07-06
ok I sort of came across this experience and the solution that has always worked for me.

System->Preferences->Sound
uncheck the box for 'enable software sound mixing (ESD)'

when you launch the game from the terminal you should **not** see anything like  

'unable to open /dev/dsp'

if you do make sure you have no other audio apps running like amarok/xmms

strangely when the sound worked for me i reenabled ESD from the process above and the sound continues to work? it might be one of those first time configuration things.

hope this helps

---

### Post by Rosenrot on 2006-07-06
i tried your suggestion lordmule

didn't help : /

and ive never had 'unable to open /dev/dsp/' since i fixed my video card issue oddly

i made sure i didn't have any audio apps open

ive been searching franticly on google trying to find an answer but everyone just says to disable esd, alsa, and artsd  when those processes are already killed

so mabey its my sound card?

i get sound from pretty much every other application that uses sound 
example: rythmbox, gaim, movie player, linux games etc.

ill try reinstalling my sound card driver and post back here

o and i also have a Sound Blaster Audigy 2 if that helps at all

---

### Post by lordmule on 2006-07-07
it may be silly but have you tried browsing through the file 

System/Default.ini

You might find some options to change the sound engine detected when you installed, I however only have one.

```

[Engine.Engine]
AudioDevice=ALAudio.ALAudioSubsystem

```

It might help to check against the options I got, however I am using onboard audio.

```

[ALAudio.ALAudioSubsystem]
UseEAX=False
Use3DSound=False
UseDefaultDriver=True
CompatibilityMode=False
MaxEAXVersion=255
UsePrecache=True
ReverseStereo=False
Channels=32
MusicVolume=0.10000
AmbientVolume=0.500000
SoundVolume=0.30000
VoiceVolume=4.000000
VolumeScaleRec=0.100000
DopplerFactor=1.0
Rolloff=0.5
TimeBetweenHWUpdates=15
DisablePitch=False
LowQualitySound=False
UseVoIP=True
UseVAD=False
UseSpatializedVoice=False
SpatializedVoiceRadius=100000
EnhancedDenoiser=False
LocalZOffset=0.0

```

I believe that audigy cards can do hardware mixing so according to my knowledge that means you can have multiple audio apps running concurrently without problems. So changing esd, artsd, etc wont do a great deal, its more about support under UT. Id be looking for other people with audigy cards + UT + their setup.:-k

---

### Post by livingtarget on 2006-07-07
First I would check whether /dev/dsp exists. If it doesn't well you're in bigger trouble.

You can use this command to check it (or just browse with the filebrowser)
> ls -a /dev/dsp 

Secondly make sure the sound isn't muted (alsamixer), if it isn't go in ut2004 and make sure you didn't put the sound all the way down in here. So far for the obvious things.

UT2004 runs with oss, alsa support can only be emulated.
From /usr/local/games/ut2004/System/ do: 
> aoss ./ut2004-bin

AOSS usually delays the sound a bit, which I always find feels very weird. If you manage to get sound now it's probably that you are already playing music/sound when running ut2004. Try killing the arts daemon (provides kde sound) or the esd daemon (provides gnome sound). Sound daemons like 'arts' and 'esd' always restart when you reboot, you can disable them somewhere I think.

If you want to edit the shell script try:
> sudo gedit /usr/local/games/ut2004/ut2004

Basically try to put commands like "sleep 5" before/after: 
> exec "./ut2004-bin" $*

As lord mule suggested you can try the configuration files, HOWEVER do NOT change default.ini! Change UT2004.ini in /home/your_user_name/.ut2004/System/ this is a hidden folder, but you can browse to it none the less.

If all that fails it's most likely a driver issue or another problem.

---

### Post by Waste on 2006-07-10
> **livingtarget said:**
> 
UT2004 runs with oss, alsa support can only be emulated.
From /usr/local/games/ut2004/System/ do: 


If you read the README.linux in the /ut2004 directory, it says this;

> Q: I am using the ALSA drivers; are they supported?
  A: Yes, this game works with ALSA directly (and doesn't require the
     OSS emulation layer).

I am also having this same problem and have tried all suggestions in this thread to no avail.

---

### Post by Rosenrot on 2006-07-12
when i was trying to fix this problem ast night
when i was looking through my .ini file everything was the same as LordMule's

so i decided to start ut2004(sorry i didn't use command line to open it : /wasn't thinking) and sound worked perfectly and i could close and open the program and it would still work anytime during my session

but then i had to restart my computer for updates thinking i had already fixed the ut2004 issue

but when i rebooted ut2004 would no longer boot with sound again

and when i did sleep 5 i would get an error when i tried to start ut2004 in the terminal

i will try sleep 5 again andd post back with more information

and thanks for the help everyone!

---

### Post by Rosenrot on 2006-07-12
here is my ut2004 shell

# Let's boogie!
if [ -x "${UT2004_DATA_PATH}/ut2004-bin" ]
then
	cd "${UT2004_DATA_PATH}/"
	exec "./ut2004-bin" $* 
fi
echo "Couldn't run UT2004 (ut2004-bin). Is UT2004_DATA_PATH set?"
exit 1

# end of ut2004 ...

i have tried countless ways of adding sleep 5 but I don't know the correct way to add it
ill keep getting time interval errors for "slepp" "exec" and "./ut2004-bin

---

### Post by Lord C on 2007-10-31
> **Vectrox said:**
> Im also having this problem with UT2004 and various other games, this works for me:

1. Open terminal ;) 
2. Then enter: "killall esd".

After youve done this, start UT2004 and most likely the sound will work.

Fixed it for me too, thanks =]

---

### Post by eternalwolfman on 2009-04-18
I am running ubuntu 9, and had no sound with the most recently patched ut2004. I fixed it by making a copy of libopenal.so1 (a link within the directory ./usr/lib) and renaming it openal.so and putting it in the same ./usr/lib directory as well. 

My previous efforts with the open al wrapper and other attempts did not yield any results, so I hope that this may solve some still unresolved issues for people.

---

