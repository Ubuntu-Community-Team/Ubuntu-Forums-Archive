---
title: "Terminus on Ubuntu"
date: 2005-08-14
forum: Gaming &amp; Leisure
---

### Post by edemark on 2005-08-14
Hi all 

I have installed my Terminus but when I try to start it i get the following error message: 
mark@supernova:~$ terminus
terminus: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory

I was looking up on synaptic but i could only find the version 2.10 of this libstdc++

Is there any way to get hold of this shared library to be able to run this game? Or what would you suggest? Is there any way to resolve this problem?

thaks for your answers
mark

---

### Post by fragmental on 2005-09-22
[QUOTE=edemark]Hi all 

I have installed my Terminus but when I try to start it i get the following error message: 
mark@supernova:~$ terminus
terminus: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory

I was looking up on synaptic but i could only find the version 2.10 of this libstdc++

Is there any way to get hold of this shared library to be able to run this game? Or what would you suggest? Is there any way to resolve this problem?

thaks for your answers
mark[/QUOTE]
 Same problem here.  I hope someone can find a solution.

---

### Post by fragmental on 2005-09-22
[QUOTE=edemark]Hi all 

I have installed my Terminus but when I try to start it i get the following error message: 
mark@supernova:~$ terminus
terminus: error while loading shared libraries: libstdc++.so.2.8: cannot open shared object file: No such file or directory

I was looking up on synaptic but i could only find the version 2.10 of this libstdc++

Is there any way to get hold of this shared library to be able to run this game? Or what would you suggest? Is there any way to resolve this problem?

thaks for your answers
mark[/QUOTE]
 I'm having the same problem.  Did you ever get it fixed?

Try using synaptic or apt-get to get the runtime library of libstdc++ 2.10 and then link to it.

Make sure you don't have more than 2 gigs of swap.

---

### Post by edemark on 2005-09-22
Thanks for the idea 

So far i could not get it to work. I have find some libstdc++ 2.8 tar.gz files but i was not able to compile the library. 
Now I am downloading libstdc 2.10 packages from repository and will try out if symlinking or linking works and then i will get back

I hope it will work out

---

### Post by fragmental on 2005-09-22
by 2 gigs of swap I meant "2 gigs of swap+memory"

---

### Post by edemark on 2005-09-23
Yeah it did the trick
Now terminus works will add to the list of really good linux games if i have observed well so far it was not on that list.

Still have one question why this 2 gigi memory staff bother? 
I do not have more than 2 gigs but i might get one day is it a bad idea?

thank you a lot for the idea

---

### Post by fragmental on 2005-09-23
[QUOTE=edemark]Yeah it did the trick
Now terminus works will add to the list of really good linux games if i have observed well so far it was not on that list.

Still have one question why this 2 gigi memory staff bother? 
I do not have more than 2 gigs but i might get one day is it a bad idea?

thank you a lot for the idea[/QUOTE]
 The l[linux gaming faq](http://www.icculus.org/lgfaq/)  is a great source for linux gaming info.

It says:
"Q: Terminus won't start, no matter what I try to do.

A: Do you have more than 2G of virtual memory [core plus swap together]? If so, you need to reduce the level of either one, or the other, until you're under 2G total. An easy way to do this is to give your kernel the parameter "mem=XXXM" at boot time, so that XXX plus your swap comes to less than 2G. "

You could probably add a boot option to grub with the "mem=XXXM" paramater so that you could boot in like that when you want to run terminus and and then boot into normal mode when you don't. It's kind of a pain though. I'm not sure what this problem is all about.  I had over 2G of swap space alone and the game wouldn't run so I turned off one of my swap partitions.  It's not an optimal fix, but it works.

---

### Post by edemark on 2005-09-23
So i will try to live on few memory

Thanks again I am now going to patch the game to see if something happens and than go on playing

thanks again

---

### Post by edemark on 2005-09-23
So patching was not that good idea as since i have applied 1.81 patch game does not start any more with the following messages:

terminus: Symbol `cerr' has different size in shared object, consider re-linkingterminus: Symbol `__vt_8bad_cast' has different size in shared object, consider re-linking
terminus: Symbol `__vt_10bad_typeid' has different size in shared object, consider re-linking
CD-ROM found at /dev/hdc

However i will keep on trying to patch the game with earlier patches. 
The issue of over 2 gig of memory is resolved in the 1.5 patch (according to terminus home page). Though you cannot find this patch on that page you might visit [http://www.terminuspoint.com/](http://www.terminuspoint.com/)

i will get back after i tried 1.5 and 1.4 patches

---

### Post by fragmental on 2005-09-24
[QUOTE=edemark]So patching was not that good idea as since i have applied 1.81 patch game does not start any more with the following messages:

terminus: Symbol `cerr' has different size in shared object, consider re-linkingterminus: Symbol `__vt_8bad_cast' has different size in shared object, consider re-linking
terminus: Symbol `__vt_10bad_typeid' has different size in shared object, consider re-linking
CD-ROM found at /dev/hdc

However i will keep on trying to patch the game with earlier patches. 
The issue of over 2 gig of memory is resolved in the 1.5 patch (according to terminus home page). Though you cannot find this patch on that page you might visit [http://www.terminuspoint.com/](http://www.terminuspoint.com/)

i will get back after i tried 1.5 and 1.4 patches[/QUOTE]
 I used this [http://www.vvisions.com/terminus/patches/TerminusLinuxPatch11to181.tar.gz](http://www.vvisions.com/terminus/patches/TerminusLinuxPatch11to181.tar.gz) patch and I get the same errors but the program starts up fine.  The only problem I've had is that I have to turn off "nebula" or everything is white.  However, even with the patch applied I still had to limit my memory+swap to less than 2G.  It's possible that I didn't apply the patch correctly.  I never found a way to tell what version I was running.

Ok, it doesn't run...but it did run before I rebooted.  Odd.

---

### Post by edemark on 2005-09-24
I do not know but i just could not get the patched version to work i guess that i will just get happy that the original version works

Thanks again the help it helped a lot
NOW I CAN PLAY

thanks

---

### Post by macgyver2 on 2005-09-24
[QUOTE=edemark]Now terminus works will add to the list of really good linux games if i have observed well so far it was not on that list.[/QUOTE]
Yes, excellent game!  I haven't played that in such a long time...  I should find where my CDs went to.  I *love* the realistic physics.

---

### Post by fragmental on 2005-09-25
[QUOTE=edemark]I do not know but i just could not get the patched version to work i guess that i will just get happy that the original version works

Thanks again the help it helped a lot
NOW I CAN PLAY

thanks[/QUOTE]
 Just realised I'm having the exact same problem. I don't knwo why the patched version doesn't run.  It's very annoying. I wonder what the latest patch is that will run.

---

### Post by edemark on 2005-09-25
Partly I guess that the problem is that we do not really have a libstdc++.so.2.8 but we use an other file. I am wondering if we had the same error using the real 2.8 library. I we would not have this error than i guess is just registering on the development forum and ask for this. I might do that but if you have the same problem is better that they have two petitions

i hope it can be resolved

---

### Post by mleopold on 2005-10-09
[QUOTE=edemark]So patching was not that good idea as since i have applied 1.81 patch game does not start any more with the following messages:

terminus: Symbol `cerr' has different size in shared object, consider re-linkingterminus: Symbol `__vt_8bad_cast' has different size in shared object, consider re-linking
terminus: Symbol `__vt_10bad_typeid' has different size in shared object, consider re-linking
CD-ROM found at /dev/hdc

...

i will get back after i tried 1.5 and 1.4 patches[/QUOTE]

Did you get anywhere with this? I followed the instructions as best I could
 apt-get install libg++2.8.1.3-glibc2.2
 cd /usr/lib/
 ln -s libstdc++-3-libc6.2-2-2.10.0.so libstdc++.so.2.8

I installed a pristine copy of Terminus (patch level 1.1) and that work like a charm.. Then I tried to patch to 1.81 and then.. Nothing.. What I really wanted was to play the TPE version, as I understand this requires Terminus 1.81, so this is kind of disappointing.

I noticed that the output of the 1.1 and 1.81 versions is exactly the same up to a point, and then the 1.81 halts. I've included the output below - for me the 1.81 version halts just after "mixing 4/1024"

sabina@quark:/usr/lib$
/usr/local/games/Terminus/terminus /usr/local/games/Terminus/terminus: Symbol cerr' has different size in shared object, consider re-linking
/usr/local/games/Terminus/terminus: Symbol __vt_8bad_cast' has different size in shared object, consider re-linking
/usr/local/games/Terminus/terminus: Symbol __vt_10bad_typeid' has different size in shared object, consider re-linking
CD-ROM found at /dev/hdd
CD-ROM found at /dev/hdc (mounted)
Opened /dev/dsp for writing.

Opened /dev/dsp for reading.

Set 16 bits

Info 123: Set stereo sound

Set 44100Hz audio

mixing 4/12
Using Glide renderer...
Glide failed to initialize.  Falling back to OpenGL...

---

### Post by mleopold on 2005-10-09
[QUOTE=mleopold]
Opened /dev/dsp for reading.
Set 16 bits
Info 123: Set stereo sound
Set 44100Hz audio
mixing 4/12
[/QUOTE]

After googling some more I found this post - the problem is related to sound.. Not a big suprise given the output.. Anway the commandline below worked for me.. You could put it in the config to store it permanently...

[http://forums.myterminus.net/viewtopic.php?t=761&sid=bd2c1ae865db9619dac0a35a9e6fc328](http://forums.myterminus.net/viewtopic.php?t=761&sid=bd2c1ae865db9619dac0a35a9e6fc328)

/usr/local/games/Terminus/terminus +linux_sound_output /dev/audio

---

### Post by fragmental on 2005-10-10
Is /dev/audio the device for audio output?  I was thinking that /dev/dsp was an oss thing but I couldn't remember.  I might have even done a little searching to see what audio device I was using, but I think I didn't know where to look so I gave up and forgot about it.

---

### Post by edemark on 2005-10-10
That is cool this determination of audio device did make the trick for me and the game is fully on now

I am going to edit terminus entry in the best linux games list on this forum to let everybody know that it works perfectly
It is really nice to be able to play v 1.81 

thanks to all and enjoy having fun

---

### Post by fragmental on 2005-10-10
worked for me too. thanks

---

### Post by _march_ on 2008-08-01
I know - this thread is very old ;) 
Does anyone know how to install this game on Hardy? I tried this [Wiki]("http://translate.google.com/translate?u=http%3A%2F%2Fwiki.ubuntuusers.de%2FSpiele%2FTerminus&hl=de&ie=UTF8&sl=de&tl=en") but [libg++2.8.1.3-glibc2.2]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libg%2B%2B2.8.1.3-glibc2.2") is only available for gutsy, feisty and dapper. I also tried to install a package from an older distribution (gutsy) but it isn't working. Any solutions?

---

### Post by _march_ on 2008-08-03
Any ideas?

---

### Post by _march_ on 2008-11-03
Is no one playing this game under Hardy or Intrepid? Seems that I'll have to setup a VM.

---

### Post by bob2098 on 2008-11-22
I got it working on intrepid 64bit by installing libstdc++2.10-glibc2.2_2.95.4-24_i386.deb from the gutsy package list and linking it to the /usr/lib32 directory as libstdc++.so.2.8. This makes the game start but it will crash if you try and type to change a name or to name a save game file.

```
terminus: ../../src/xcb_io.c:182: process_responses: Assertion `((int) (((dpy->last_request_read)) - ((dpy->request))) <= 0)' failed.
Aborted
```


So if you create the save game on Windows and use windows to change ship names etc you will be able to play.

---

