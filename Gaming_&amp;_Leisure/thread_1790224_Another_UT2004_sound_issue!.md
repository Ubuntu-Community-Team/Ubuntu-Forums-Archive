---
title: "Another UT2004 sound issue!"
date: 2011-06-24
forum: Gaming &amp; Leisure
---

### Post by MrMichaelHill on 2011-06-24
I've spent a few days looking around the forums and have tried so many different things and nothing seems to make the sound work on my native install of Unreal Tournament 2004, I've also asked in the IRC channel... Being ubuntu though I know it will fix... somehow... 

when running "ut2004" from console no errors or messages are displayed... there literally is just no sound 


Any help is greatly appreciated


Thanks.

Mike.

---

### Post by MrMichaelHill on 2011-06-25
Tried PADSP and making links to my openAL files...

---

### Post by Virus666 on 2011-06-25
If **padsp** does not work for you, you may try "**ALSA wrapper for OSS applications**." Install **alsa-oss** package via **Synaptic** and start the game with **aoss** command.

```
aoss ut2004
```

---

### Post by MrMichaelHill on 2011-06-26
Synaptic shown I already had alsa-oss installed so I removed it and re-installed it, typed the aoss ut2004 command and it loaded fine with no sound but displayed this message in terminal...

```
michael@ubuntu-quadcore:~$ aoss ut2004
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

```

---

### Post by Virus666 on 2011-06-26
> **MrMichaelHill said:**
> Synaptic shown I already had alsa-oss installed so I removed it and re-installed it, typed the aoss ut2004 command and it loaded fine with no sound but displayed this message in terminal...

```
michael@ubuntu-quadcore:~$ aoss ut2004
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

```


Well, it seems that some of the required sound files are missing.


[LIST=1]
[*]Install following packages via Synaptic: **libopenal1**, **libsdl1.2debian**
[*]Download the [linux-x86.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=30925&d=1177599405") file which was refered [NESFreak]("http://ubuntuforums.org/member.php?u=77308")'s entry related to UT2004: [http://ubuntuforums.org/showpost.php?p=2531783&postcount=4]("http://ubuntuforums.org/showthread.php?t=394706&highlight=unreal+anthology")
[*]Extract the file and copy the **content** of its System file to the UT2004's System file.
[*]Try to launch the game with **PulseAudio OSS Wrapper (padsp)**: ```
padsp ut2004
```
[*]If padsp fails to give the sound; try to launch the game with **ALSA wrapper for OSS applications (alsa-oss)**: ```
aoss ut2004
```
[/LIST]
Good luck... :-)

---

### Post by MrMichaelHill on 2011-06-26
I already seem to have **libopenal1** installed, and **libsdl1.2debian**, should I download any of the other files displayed below though?[B]


[IMG]http://img856.imageshack.us/img856/2333/screenshotsynapticpacka.png[/IMG]
[/B]

---

### Post by MrMichaelHill on 2011-06-26
I skipped that stage and downloaded the tar.bz2 and extracted it etc... PADSP worked!


Sweeet!

It doesn't sound 100% but I'll give it a quick blast now and report back!

---

### Post by MrMichaelHill on 2011-06-26
Right all seems well... ran from console using aoss, played for 20mins and all is great, thank you very much for the help! I'll make myself a nice tutorial for future reference from all this! the only thing that may be of interest now that isn't causing any problems I can see is some errors from the console read-out

```

***michael@ubuntu-quadcore:~$ padsp /usr/local/games/ut2004/ut2004 ***
open /dev/[sound/]mixer: Input/output error
WARNING: ALC_EXT_capture is subject to change!
Defaulting to false
Defaulting to false
Resolved ut2004master1.epicgames.com -> 199.255.40.173
Connection established.

```the Connection established is the final point where I began playing online for 20 or so mins...

---

### Post by Virus666 on 2011-06-26
Well, I am appreciate that you made it... :-)

As [NESFreak]("http://ubuntuforums.org/member.php?u=77308") refered his entry, UT2004 requires some native sound files and for some reason some of the copies of the game do not have such thing. He fixed the problem by using the sound files from the demo version of UT2004. :mrgreen:

I do not know why PADSP does not work well but I had the same issue too... Anyway, if ALSA-OSS (aoss) does the job, then there is no problem.

I have just wrote an instruction to install Unreal Tournement forum Unreal Anthology and I have touched the sound issue. As you have the retail version of UT2004, you do not need the rest but sound stuff may usefull for you.
[http://ubuntuforums.org/showpost.php?p=10981407&postcount=80](http://ubuntuforums.org/showpost.php?p=10981407&postcount=80)

Last of all, it is better to mark this threat as [SOLVED] for the future visitors... ;-)

---

### Post by MrMichaelHill on 2011-06-27
> **Virus666 said:**
> 

I do not know why PADSP does not work well but I had the same issue too... Anyway, if ALSA-OSS (aoss) does the job, then there is no problem.

  

PADSP works fine, it sounded a bit crackly at the start but that is just my speakers, in game the sound was great, aoss on the other hand didn't produce any sound.

Anyway, I greatly appreciate the time you have taken to help, I have been searching for days and had read about copying the demo files, I did try it a while back with no luck so I'll hang onto these ones I've downloaded!

Thank you once again! =D>

---

