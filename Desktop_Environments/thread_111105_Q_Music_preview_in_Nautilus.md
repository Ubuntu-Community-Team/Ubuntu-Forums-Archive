---
title: "Q: Music preview in Nautilus"
date: 2006-01-01
forum: Desktop Environments
---

### Post by Aero-Z on 2006-01-01
Does anyone know which package installs the mp3 file preview (move mouse pointer over mp3 and it starts playing the song until the mouse pointer is moved elsewhere)?

---

### Post by mcduck on 2006-01-01
it's mpg123 :)

---

### Post by Aero-Z on 2006-01-01
[QUOTE=mcduck]it's mpg123 :)[/QUOTE]
Hmm, funny. I have it installed, but it's not working

---

### Post by kaamos on 2006-01-01
I have it working as root but not as normal user. As user, I don't even get the blue note over the audio files.

Strange.

---

### Post by mcduck on 2006-01-02
[QUOTE=Aero-Z]Hmm, funny. I have it installed, but it's not working[/QUOTE]
Do you have sound server running? I'm not at my ubuntu box right now, but I think the setting is in System/Preferences/Sound and 'Enable sound server startup'. You need that for sound previews..

Try if it works for wav files. That should work by default without installing anything.

---

### Post by Aero-Z on 2006-01-02
[QUOTE=mcduck]Do you have sound server running? I'm not at my ubuntu box right now, but I think the setting is in System/Preferences/Sound and 'Enable sound server startup'. You need that for sound previews..

Try if it works for wav files. That should work by default without installing anything.[/QUOTE]
Yea it worked. Thanks:)

---

### Post by giacomolg on 2006-02-10
And what to install for ogg preview playback?

Thank you

---

### Post by xcap on 2006-02-13
up

it must have a solution isn't it?

:)

---

### Post by Black.Solaris on 2006-03-05
I have a little bit of a different problem.  When I mouse over music files, it works fine, but then sometimes when I move the mouse away, the sound keeps playing.

I have tried Force Quitting Nautilus, but unfortunatly, that does not fix the problem.  The sound still keeps playing.

I have also tried waiting until the end of the song.  This too, does nothing, as it simply starts playing again.

I would like this feature to work, but if there is an easy way to disable it, that is fine as well.  It has gotten to the point that I get really nervous opening folders with music in them simply becuase the only way I have found to get rid of the problem is to restart, or wait approximatly 15 minutes for the sound to stop.  Only when this happens does Nautilus restart as well.

---

### Post by Morbett on 2006-03-20
I have the same problem.  Did you (or anybody else here) find a solution for it?

Thanks.



[QUOTE=Black.Solaris]I have a little bit of a different problem.  When I mouse over music files, it works fine, but then sometimes when I move the mouse away, the sound keeps playing.

I have tried Force Quitting Nautilus, but unfortunatly, that does not fix the problem.  The sound still keeps playing.

I have also tried waiting until the end of the song.  This too, does nothing, as it simply starts playing again.

I would like this feature to work, but if there is an easy way to disable it, that is fine as well.  It has gotten to the point that I get really nervous opening folders with music in them simply becuase the only way I have found to get rid of the problem is to restart, or wait approximatly 15 minutes for the sound to stop.  Only when this happens does Nautilus restart as well.[/QUOTE]

---

### Post by jmate24 on 2008-03-05
how do i install sound server on gutsy? do i use synaptic?
i'll try it if it works, but if it does not then i will return.

i am currently using gutsy 7.10

---

### Post by jmate24 on 2008-03-05
that did not work!:(

---

### Post by jmate24 on 2008-04-05
system===>Preferences===>sound then in the devices tab change all the defaults to your audio hardware and click test. (it's usualy the chipset name) then put your mouse over an ogg or mp3 file to test it. you may have to use package manager to download sound server i'm testing it out on hardy and will post the results.:)

---

### Post by jmate24 on 2008-06-12
thanks for your help but i use 7.10 and i guess i need to install a sound server with synaptic ever since either 7.04 or 6.10 sound previews have stopped it must have been a bug but i guess i will try to install a sound server by searching for 'sound server' in synaptic.

---

### Post by jmate24 on 2008-06-12
when i searched for a sound server i found the pulse audio sound server and installed it along with gmpeg and mpeg123 and 321 and in the system>preferences>sound in the devices menu i switched everything to pulse audio and it worked.

---

### Post by ankur.gupta on 2008-06-18
i can listen music by hovering over music file(mp3) in my ubuntu 8.04 but when i looked into synaptic package manager it shows that mpg123 or mpg321 are not installed. i am curious which package is responsible for music preview.

---

