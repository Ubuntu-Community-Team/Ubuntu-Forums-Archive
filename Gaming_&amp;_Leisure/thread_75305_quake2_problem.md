---
title: "quake2 problem"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by tregetour on 2005-10-13
When I start up quake2 I get:

QuakeIIForge 0.3
using /home/jdevries/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Device or resource busy
SNDDMA_Init: Could not open /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx


What's going on and how do I fix it? Thank you.

---

### Post by seethru on 2005-10-13
do you see that file in your quake2 directory?

---

### Post by tregetour on 2005-10-13
Which file and where would i look?

---

### Post by asipi on 2005-10-13
That: default.cfg and pics/colormap.pcx

for sound issue check which process using /dev/dsp
maybe esd or artsd depending on using gnome or kde.
Stop that process with its normal way if possible or with kill -9 <pid> as root.

---

### Post by ericsp on 2005-10-13
I get the following response after typing quake2 at the command prompt:

> ------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
Trying joystick dev /dev/js0
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Read init event
Using joystick dev /dev/js0
SNDDMA_Shutdown
recursive shutdown
Error: Couldn't load pics/colormap.pcx
ericsp@Tantalos:~$

any suggestion?

---

### Post by doood81 on 2005-10-15
sounds like your pk0.pk3 is corrupt. It is not able to find a default colormap.

[http://www.icculus.org/lgfaq/loki/q3faq.html](http://www.icculus.org/lgfaq/loki/q3faq.html)

This man's site is well known for linux quake issues, browse his place for a while :-)

---

### Post by gpw797 on 2005-10-19
I got same error msg as ericsp

the colormap.pcx file isn't in directory - I installed quake2 and quake2 data through synaptic

---

### Post by hammett111 on 2005-10-21
Copy your "gamex86_64.so" or "gamex86.so" file from your installation /usr/local/games/quake2 for mine, to /.quake2/baseq2 folder. This should solve your problems.

---

### Post by FerGeCo on 2006-05-08
I solved the issue by renaming de PAK0.PAK to pak0.pak .. casesensative (:

Grtz

---

### Post by Khaotik on 2006-06-18
> 
When I start up quake2 I get:

QuakeIIForge 0.3
using /home/jdevries/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Device or resource busy
SNDDMA_Init: Could not open /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx


What's going on and how do I fix it? Thank you.


I got the exact same problem. How was it fixed? Excuse my noobiness.

---

### Post by Winball on 2006-08-30
You probably need pak0 pak1 pak2 (and pak3?) from your quake2 cd. Their located in baseq2 folder. The colormaps.pcx are in pak0 if im not wronge.

---

### Post by HAARP on 2006-08-31
Yeah, you need the paks from the CD.
Also, I recommened using the Loki's Quake2 installer. The one in the repos is some strange version.

---

### Post by pharcyde on 2006-09-01
You could try following the steps outlined on this page.

[https://help.ubuntu.com/community/Games/Native/Quake2](https://help.ubuntu.com/community/Games/Native/Quake2)

---

### Post by veg on 2006-09-07
I had this problem last night, and solved it the Debian way:

I installed quake2 and quake2-data, like the previous posters.

I then did:

dpkg-reconfigure quake2-data

which brought up a text based menu asking me where to install the maps from - I chose to install from an original Quake2 CD (my brother's) and then update using a point release from the net. It then installed everything automatically and hey presto, running 'quake2' works.

BUT... I still got the problem with /dev/dsp , so no sound!

Any ideas? (I'll post the exact error message when I get home tonight).

I'm running PowerPC Ubuntu on a G4 Mac Mini. Originally installed from a Breezy install CD and updated via the net to Dapper. This may complicate things...

---

### Post by veg on 2006-09-07
Incidentally, I installed prboom at the same time and that works fine, with sound. Just in case that helps.

---

### Post by veg on 2006-09-08
OK, so the actual error message looks a little different from the ones mentioned above:

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.

anyone know what this means?

---

### Post by veg on 2006-09-13
I found the answer to the "no sound" issue elsewhere in the forums, namely:

[http://ubuntuforums.org/showthread.php?t=79014&page=3&highlight=quake2](http://ubuntuforums.org/showthread.php?t=79014&page=3&highlight=quake2)

ie, start quake2 using the following command:

quake2 +set snddriver ao +set snddevice oss

Worked for me first time. One odd thing: the sound seems to be on "maximum" and the usual GNOME volume control didn't change anything. I had to physically turn down the speakers. Any ideas? Same issue occurs for me with Frozen Bubble and Vegastrike too.

---

### Post by scientist47 on 2007-04-10
I had some problems with the quake2-data configuration, so I had to unzip and copy the pak0.pak manually. After that I got

```
Error: Couldn't load pics/colormap.pcx
```

I solved this by doing 

```
sudo chmod 644 /usr/share/games/quake2/baseq2/pak0.pak
```

So the problem was that the files unpacked from the data archive did not give read permission to any user. 


I still have a problem with the sound. There is sound, but it is delayed a second. Haven't looked in to it yet.

---

### Post by mbradlcu on 2007-04-23
here's what fixed the sound problem for me,, incidentally this worked for the kingpin game too
as root
echo 'kingpin 0 0 direct' > /proc/asound/card0/pcm0p/oss

just replace kingpin with what ever the game executable is.

---

### Post by VoodooSmurf on 2007-04-26
```
------- sound initialization -------
ALSA snd error couldn't set params (Invalid argument).
------- Loading ref_softx.so -------
LoadLibrary("./ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx
```

that's what i'm getting...  and I was browsing my baseq2 directory, and it looks like i'm missing 
paks 0-9, is there a place I can get these from?  will the demo have them? I've lost my q2 CD somehwere...

---

