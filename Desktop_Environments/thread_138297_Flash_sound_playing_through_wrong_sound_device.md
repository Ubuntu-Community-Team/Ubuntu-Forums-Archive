---
title: "Flash sound playing through wrong sound device"
date: 2006-03-01
forum: Desktop Environments
---

### Post by frobroj on 2006-03-01
Hi all. I have searched high and low on the forums for something like this but to no avail. The problem I am having is that when I connect my Logitech USB headset I get all sound except flash through the headset(After I change the default sound card in the sound preferences). However flash is working and is producing sound it just seems to be going the way of the OSS and not the ESD. I would think that there must be an easy fix for this. After all sound is playing correctly its just not getting to the correct device. I have tried modifying the /etc/mozilla-firefox/mozilla-firefoxrc file to reflect "ESD" and about every other variable "AOSS" etc.. Please help us... 

Thanks!!! :) Rossella (My coworker) said she will cook you lasagna if you can help!
AND SHE IS ITALIAN!!!!

---

### Post by frobroj on 2006-03-06
Buehler..... Buehler...... Buehler......

---

### Post by temcat on 2006-03-10
I have the same problem in Dapper. And the sound seems distorted...

---

### Post by Stealth on 2006-03-10
[http://www.ubuntuforums.org/showthread.php?t=89827&](http://www.ubuntuforums.org/showthread.php?t=89827&)

Same thing I gave temcat, see if this works...

---

### Post by frobroj on 2006-03-10
Thanks for the link but we have already tried that to no avail. The sound works great for flash, it simply is directed to the wrong audio device. Is there some conf file for flash that we can modify to specify the device? 

Note:ALL OTHER SOUNDS WORK GREAT IN FIREFOX. THEY ARE DIRECTED TO THE PROPER AUDIO DEVICE. ONLY THE FLASH MEDIA OUTPUTS TO THE WRONG DEVICE.

Thanks All! We appreciate the help!

---

### Post by manatlan on 2006-04-03
Same trouble ... on dapper (flight6)
i've got 2 sound cards ...an onboard and an audigy ...
in preferences > sound : it's setuped on the audigy ...
all others apps seems to be good ....
except flash player in firefox, which redirect the flash sound to my onboard one ;-( (and flash in opera or epiphany don't play any sound on my cards ?!?)

---

### Post by Kordesh on 2006-05-22
I too am running Dapper with an audigy 2 card and I am having the same issue. I get sound fine via the correct means on everything else, but all flash is outputting sound to my headphones on my onboard card -_-.

---

### Post by ZipoTe on 2006-05-23
I had this problem on Breezy... so I tried with Dapper and... YES I HAD SOUND WITH FLASH!! but.. suddenly one day... it just didn't work: FLASH SOUND DISAPPEARED!! ](*,)  i've done everything and it doesn't work :( 

Can anyone help?

And... can anyone explain why it worked at the beginning and now it doesn't??

THANK YOU!!


--sorry for my english :P--

---

### Post by Jungleboss on 2006-06-08
I too have the same problem. All sound except flash's is directed to my primary sound card. Anyone have a possible solution to this? I use KDE and Flash works, except for the sound coming from the wrong card. Thanks!

---

### Post by iblastoff on 2006-06-11
has there been a solution for this problem? my flash in firefox works fine too, except its also playing to the 'wrong' sound card on my system (it goes to my onboard instead of my actual card). everything else plays fine

---

### Post by keithjr on 2006-06-15
I've just recently started having the exact same problem in dapper.  There seems to be no way to change the device to which flash directs sound output.  This problem is unsolvable, I guess.  Shucks.  The end.

---

### Post by kjkrum on 2006-06-15
My USB headset is my only sound device.  I got no sound from the Flash plugin in Breezy or Dapper.

When I set FIREFOX_DSP="esd", I get this:

kevin@aphrodite:~$ firefox
unrecognized option: /usr/lib/firefox/firefox-bin
unrecognized option: -a
unrecognized option: firefox
esd: Esound sound daemon already running or stale UNIX socket
/tmp/.esd-1000/socket
This socket already exists indicating esd is already running.
Exiting...

With anything else, Firefox starts OK but I get no sound.

Flaky sound APIs are the #1 thing holding back Linux on the desktop, IMO... :|

---

### Post by frobroj on 2006-06-16
I think the problem here is that this may be a Flash issue. Perhaps thats why the post has been ignored. It does appear to be a valid problem that is affecting quite a few folks. I will try to see if I can get anywhere with Macromedia.. er Adobe to get the problem resolved. If I have any luck I will post it. 
Thanks all for chiming in. Hopefully we will be able to find a solution. 

JM

I did some digging on the Adobe site to no avail. Some other posts mentioned that the flash accesses the sound card directly and not through the sound server which sounds like the issue. I put in a post on the Adobe forum and asked if there was a fix or a way to change the device. Hopefully I will hear something soon.

Oh and another thing or two. This issues has happened for me on Breezy & Dapper. Recently I tested it on a base install of Dapper and after I installed AUTOMATIX. I love that package.

THX
JM

---

### Post by nashife on 2006-06-16
[QUOTE=frobroj]I think the problem here is that this may be a Flash issue. Perhaps thats why the post has been ignored. It does appear to be a valid problem that is affecting quite a few folks. I will try to see if I can get anywhere with Macromedia.. er Adobe to get the problem resolved. If I have any luck I will post it. 
Thanks all for chiming in. Hopefully we will be able to find a solution. 

JM[/QUOTE]

I'm glad to hear that someone's going to try to solve this. :)  Looking forward to a possible solution!  

I'm also running into the same problem in dapper, and I came to look for help. Chiming in.

---

### Post by Dali on 2006-06-23
Just adding my two bits:  

Same problem here.

Looking forward to a fix!

Cheers,

dali

---

### Post by Bosambo on 2006-08-23
Hi all...had this problem too.
Not sure about your setup or sound needs but I found it was all solved when I truned off the onboard soundcard via the BIOS.

---

### Post by jaylittle on 2006-09-10
Thread Bump.

I'm having the same problem as well.  If anybody finds anything... just post it here :)

---

### Post by jaylittle on 2006-09-10
Well that was quick.  I managed to solve this problem by specifically telling alsa which card should be my primary card.  By doing this I have made my USB sound card the default and flash seems to use it now.   The information I used was found in this thread:

[http://www.ubuntuforums.org/showthread.php?t=188148&highlight=default+sound+flash](http://www.ubuntuforums.org/showthread.php?t=188148&highlight=default+sound+flash)

Be sure to place the overrides at the end of the alsa-base file rather than the beginning.  Do not change the standard autoloader entries as suggested earlier in the thread.  They will just change back at some point.

---

### Post by speedothebrief on 2006-09-21
I went through about 4 of the fixes I've seen floating around here on this topic and eventually just turned off my internal sound card via BIOS, which is working fairly well. I do have a few problems still... like when I turn the master sound control up/down/mute, it doesn't affect my flash sound at all. ARRRGHH

---

