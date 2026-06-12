---
title: "Internal mic not working after Ubuntu 8.10 upgrade"
date: 2008-10-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Elswood on 2008-10-23
My internal mic was working on my new Dell XPS M1530 Ubuntu notebook.  But it's not working after I upgrade to Intrepid Ibex, Ubuntu 8.10.  Anybody else with this problem?  Anybody with a solution?

Thanks!

---

### Post by shadowed87 on 2008-10-23
> **Elswood said:**
> My internal mic was working on my new Dell XPS M1530 Ubuntu notebook.  But it's not working after I upgrade to Intrepid Ibex, Ubuntu 8.10.  Anybody else with this problem?  Anybody with a solution?

Thanks!

same problem..but sometimes mic works..it's always muted...if you unmute it several times it starts working again (sometimes)..

i tryed with alsamixer and alsactrl store..same problem..it'll be muted again autimatically

sorry 4 my bad english

---

### Post by theozzlives on 2008-10-24
> **Elswood said:**
> My internal mic was working on my new Dell XPS M1530 Ubuntu notebook.  But it's not working after I upgrade to Intrepid Ibex, Ubuntu 8.10.  Anybody else with this problem?  Anybody with a solution?

Thanks!

Same prob. but remember 8.10 is a beta

---

### Post by Elswood on 2008-10-25
> **theozzlives said:**
> Same prob. but remember 8.10 is a beta

Okay.  Now there are three of us.  Anyone with a solution?  The release is less than a week away...

---

### Post by liviococcia on 2008-10-26
> **Elswood said:**
> Okay.  Now there are three of us.  Anyone with a solution?  The release is less than a week away...
Hello, i have the same issue with an Inspiron 1720, Mic's picking up, but very low level, and loads of background noise.

Also, i havn't got the '20+db Mic boost' setting in my HDA Intel edit/preferences, and i've looked through all the sound devices under the 'device' drop down.

If anyone has a solution, help would be great
regards

---

### Post by patrickballeux on 2008-10-27
Hi,

I have a Dell Inpiron 1521, and microphone is always muted.  I cannot record from it.  

What I was able to do is shutdown pulse, start Jack as my sound server and connect pulseaudio to jack.  Then with the monitors, I saw that microphone is working.

But since I am trying to record in Flash, which connects to Alsa which connect to pulse, nothing gets recorded.

I'm thinking about removing pulseaudio to see if it would help.

EDIT:  I removed Pulseaudio and the problem is still there.  It seems that it is related to the ALSA driver.  I am currently trying to find a workaround about this.  This is really annoying...

EDIT2:  Ok, reinstalled Pulseaudio, and using sound recorder, I was able to record from the external mic.  But the alsa miser (Volume control applet) is showing that all inputs are muted).  Flash is still unable to record since it is using the ALSA-Pulse source instead of using the native Pulseaudio source.

(I think I may have the same problem on my other laptop 32bits this one)

In 8.04, everything was perfect.

---

### Post by Elswood on 2008-10-27
Okay.  I got the internal mic to work by turning off Pulse in Skype.  Don't know if this will work in other programs.  Chose the first HDA device instead.  As reported by others, the sound volume for recording is very low.  Now, if I can get the wireless connection to be better, I will be set for skyping!

Thanks!

---

### Post by vbabiy on 2008-10-27
Not working for me either and I am on 8.10 full updated on Dell XPS m1530. It all worked perfect for me in 8.04.

Can't get the mic to work in skype or the sound record application.

---

### Post by shadowed87 on 2008-10-28
I tried other linux version (like archlinux or gentoo or slackware) and still the same problem when i upgrade to last kernel and alsa version...
all should work until kernel version 2.6.24-21-generic..i think..

---

### Post by psychoelf on 2008-10-29
Running on a Gateway 6850FX laptop.  8.04 worked great with Skype.  First issue I had after upgrading was that no sound was working.  Selected Alsa and had sound.  But Skype only has HDA selection or Pulse.  HDA does not work, but Pulse does.  Sound recorder also works with Pulse.  However, my microphone is always muted no matter how many times I unmute.  Skype will not pick up any mic sound, but sound recorder will albeit very quiet.

---

### Post by shadowed87 on 2008-10-31
up..

---

### Post by vbabiy on 2008-10-31
So I just updated my laptop and got some new kernel stuff now my skype works but the only problem the mic recording is no were near loud enough.

---

### Post by kursed on 2008-11-01
I've recently installed Ubuntu 8.10 (stable release) on my Sony SZ 483N/C notebook. And am unable to make the internal mic work. Skype doesn't pick up any voice. Any ideas as to what can be done about it?

P.S.
Sorry for posting it in the Dell section but the topic seemed relevant to me.

---

### Post by kursed on 2008-11-01
The following worked for me, see if it's the same for you guys as well.

[http://ubuntuforums.org/showthread.php?t=673628&page=2](http://ubuntuforums.org/showthread.php?t=673628&page=2)

---

### Post by hendrikwout on 2008-11-01
Hi, 

I've made a bug report about this problem in ibex (internal mic recording not loud enough). Plz confirm it there.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275998)


Kursed: I could compile alsa 1.0.15rc, I get compilation errors here.

---

### Post by alkamid on 2008-11-01
Hi,

Try this:
I went to Volume Control (right click on speaker icon on the Panel) and selected Device: Capture: ALSA PCM on front:0 (AD198x Analog) via DMA (PulseAudio Mixer). There's only one volume control for Master and I turned it up (it was muted). Now the microphone works well.

---

### Post by hendrikwout on 2008-11-01
> **alkamid said:**
> Hi,

Try this:
I went to Volume Control (right click on speaker icon on the Panel) and selected Device: Capture: ALSA PCM on front:0 (AD198x Analog) via DMA (PulseAudio Mixer). There's only one volume control for Master and I turned it up (it was muted). Now the microphone works well.

I only have a device: 'capture:ALSA PCM on front:0 (AD92xx Analog) via DMA (pulseAudio Mixer)' and the volume control was allready at max.

---

### Post by Zeedok on 2008-11-01
I got mine working.

I tried this:

> Try this:
I went to Volume Control (right click on speaker icon on the Panel) and selected Device: Capture: ALSA PCM on front:0 (AD198x Analog) via DMA (PulseAudio Mixer). There's only one volume control for Master and I turned it up (it was muted). Now the microphone works well. 

But it still didn't work.  Then I just went through all the settings in Volume control, un-muting everything I saw and eventually it worked.

I don't know what worked exactly, but trial and error worked for me.

---

### Post by yagee on 2008-11-01
Here too (XPS 1530). After upgrade the internal mic stays silent. After upgrading to alsa 1.0.18. The mic is way to silent to understand a bit but i can hear something. It seems I have to downgrade back to 8.04.

---

### Post by titimoi on 2008-11-02
same for me.. (xps m1530).. hope it will be fix soon

---

### Post by liviococcia on 2008-11-03
Same here, mic just about picking my voice, very low recording on a Dell inspiron 1720 using either skype or Sound recorder software

---

### Post by dragonx on 2008-11-03
I fix the microphone problem
[http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/](http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/)

---

### Post by dzenanr on 2008-11-04
I have installed Ubuntu 8.10 and I just cannot make microphone work. I have Dell Vostro 200 and Logitech microphone.

---

### Post by titimoi on 2008-11-04
> **dragonx said:**
> I fix the microphone problem
[http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/](http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/)

Doesn't work for me, the microphe (Capture) is still muted and as soon as as unmute it, close the windows and reopen it, it was muted automaticly...

---

### Post by talent03 on 2008-11-05
I have the exact same problem on my XPS m1330. I have noticed that this seems to be listed as a bug in several locations with launchpad. So far I have not been able to find a workaround. The line in works but the internal mic does record but a very low sound level, that can almost not be heard. I hope this issue can be resolved, and somebody more experienced can help fix this problem.

---

### Post by talent03 on 2008-11-05
> **dragonx said:**
> I fix the microphone problem
[http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/](http://weblogs.inf.udp.cl/nboettcher/31/10/2008/configurar-microfono-en-ubuntu-intrepid-ibex-en-equipo-dell-xps-m1330-m1530/)

This did not work for me.

---

### Post by marcellosales on 2008-11-06
Same problem here... I just installed 8.10 and I CANT SKYPE!!! I have a conference call today... Do I really have to login into my VISTA partition? C'mon... Save us from this...

I have an HP DV9500 and Ubuntu 7.* up to Ubuntu 8.04 mic worked... On Ubuntu 8.04 I had to install the pulsar, but this time NOTHING WORKS!!!

So, the sound recorder just freezes, doesn't even record anything, while SKYPE is only able to deliver the sound... The mic tests don't work with the procedures on the other page (the one in Spanish) since installing restricted drivers did not show the option for Digital Input...

Here's my lspci...

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Thanks,
Marcello

---

### Post by waggie on 2008-11-07
> **marcellosales said:**
> Same problem here... I just installed 8.10 and I CANT SKYPE!!! I have a conference call today... Do I really have to login into my VISTA partition? C'mon... Save us from this...

I have an HP DV9500 and Ubuntu 7.* up to Ubuntu 8.04 mic worked... On Ubuntu 8.04 I had to install the pulsar, but this time NOTHING WORKS!!!

So, the sound recorder just freezes, doesn't even record anything, while SKYPE is only able to deliver the sound... The mic tests don't work with the procedures on the other page (the one in Spanish) since installing restricted drivers did not show the option for Digital Input...

Here's my lspci...

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

Thanks,
Marcello

This is an official "me too" response.  I'm in the same boat as many other people here.

I have a Dell Inspiron XPS M1530, fairly stock, with the exception of the optional Bluetooth adapter.  I originally performed a clean install of 8.04, then performed an 8.10 upgrade.  I encountered some minor difficulties with video and with the trackpad, but those were resolved with relative ease.

My lspci:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

I can confirm that I show "Digital Mic" in my control panel, and that I select it correctly so that input should be working.  However, I experience the "re-muting" problem that others have described, and after fighting with it for awhile, including a BIOS upgrade to A09.  This is a real show stopper for me, I use Skype *frequently* for business and record readings for students learning English as a foreign language.

Most of the links people posted relate to setting the input properly, this seems not to be the case here.

Thoughts?

- Chris

---

### Post by muadnu on 2008-11-07
Same for me... I have a Dell Vostro 1400 (with a clean Intrepid install), and the internal mic records at a painfully low volume. I have looked through the forum and there doesn't seem to be anything that helps.

---

### Post by Daedalu on 2008-11-07
I have a Dell Inspiron 1526 and I can not get the mic working nor can I get the wireless to work. Any Ideas?

  I have loaded the release that just came out and it does not work either.

---

### Post by berman56 on 2008-11-07
Add another to the list.  I have a Dell Precision 390.  Everything worked great in 8.04.  After 8.10 upgrade, can't record.  I'm a intermediate level Ubuntu user, I've tried many things without success.  I'm stumped.  Huge debt of gratitude to anyone with some ideas?

---

### Post by shingalated on 2008-11-08
Same here...XPS M1330 upgraded from 8.04 to 8.10

---

### Post by linusr on 2008-11-08
+1

internal mic doesn't work on Vostro 1500 running Ubuntu 8.10

---

### Post by linusr on 2008-11-08
> **Elswood said:**
> Okay.  I got the internal mic to work by turning off Pulse in Skype.  Don't know if this will work in other programs.  Chose the first HDA device instead.  As reported by others, the sound volume for recording is very low.  Now, if I can get the wireless connection to be better, I will be set for skyping!

Thanks!

This works, though recording volume is very low.
Has anybody tried alsa from medibuntu or manually?

Thanks

---

### Post by titimoi on 2008-11-08
I had the same problem with Fedora 9 they resolved the problem I don'y know how, i don't have the time yet, but if one of you wants to have a look, it might be possible to resolve it the same way...

---

### Post by shadowed87 on 2008-11-09
OK finally my microphone is working ( DELL XPS M1530 ON UBUNTU 8.10 )...

the only way is use alsa instead of pulseaudio...follow this how to...

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

after reboot go to volume control, preferences and re-enable all channel again...then set max all volumes and Digital mic 1 as input source

after that try with sound recorder ...

STILL MUTE ??

ok randomly microphone will be muted but with this 2 commands:

amixer set Digital 100% 
amixer set Capture 100% rec

microphone should be on and loud

simply create a script
> #!/bin/bash
amixer set Digital 100% 
amixer set Capture 100% rec
exit

and launch it when needed..

I hope it'll work for you as worked for me

---

### Post by titimoi on 2008-11-09
I followed it all without any errors.. and it still doesn't work for me.. the microphone is still muted in alsa mixer, and skype still doesn't hear me..

---

### Post by titimoi on 2008-11-10
Wait, it does seems to work now when I modified some parameter in Application>sound & video>alsa mixer and when I > amixer set Digital 100%
amixer set Capture 100% rec The problem is now I don't have any sound anymore ! I mean that I see the Alsa-recorder that the level good is whenI speak, but I don't have any output anymore for anything (flash, mplayer ..) Do you have any Idea ?

---

### Post by mrbubblesort on 2008-11-10
> **shadowed87 said:**
> OK finally my microphone is working ( DELL XPS M1530 ON UBUNTU 8.10 )...

the only way is use alsa instead of pulseaudio...follow this how to...

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

after reboot go to volume control, preferences and re-enable all channel again...then set max all volumes and Digital mic 1 as input source

after that try with sound recorder ...

STILL MUTE ??

ok randomly microphone will be muted but with this 2 commands:

amixer set Digital 100% 
amixer set Capture 100% rec

microphone should be on and loud

simply create a script


and launch it when needed..

I hope it'll work for you as worked for me



I'm on a gateway 6860fx laptop and this worked for me as well, but is there a more permanent way to set this?  Perhaps a config file somewhere?  I'd like this to just work and not have to worry about it, you know?

---

### Post by Gausian on 2008-11-10
the latest updates seem to have helped the situation.  i can record sound with the sound recorder, however skype still refuses to work well with my sound device.

---

### Post by titimoi on 2008-11-10
which update do you mean ?

---

### Post by kswenson on 2008-11-10
> **Gausian said:**
> the latest updates seem to have helped the situation.  i can record sound with the sound recorder, however skype still refuses to work well with my sound device.

The update I did today fixed the problem for me as well!
Skype works too...
  it is set to use the "default device".
Are you sure you didn't change it while fiddling and forget to change it back?

---

### Post by titimoi on 2008-11-10
Oh my god I'm just so unlucky.. everytime somebody propose a trick, I test it and it is even woth.. and now that I don't have any sound anymore (even if I reverse every thing I did) And now.. just a normal update solved it for those who didn't do anything... help...

---

### Post by Gausian on 2008-11-11
I tried setting everything to "default device" and no-go.  I even tried re-installing skype without luck.

Im just going to have to use skype om my xp machine for now  until this gets fixed.  This is that last problem i have with Ubuntu.  Everything else works the way it should.

---

### Post by shadowed87 on 2008-11-11
it's impossible...i have all working without problem with my dell xps m1530 (skype ekiga rhythmbox wine...all!!) just using alsa instead pulseaudio ...just following my guide...how is possible you have the same pc but different reactions??

are you sure you have the same audio card ?

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

this is mine and my solution works 100%

---

### Post by jdeslip on 2008-11-12
Getting rid of pulseaudio is not really an acceptable solution...

---

### Post by titimoi on 2008-11-12
I do agree with that, I had to make a fresh install to be able to able to have a normal sound-system after that..

---

### Post by hendrikwout on 2008-11-13
> **shadowed87 said:**
> OK finally my microphone is working ( DELL XPS M1530 ON UBUNTU 8.10 )...

the only way is use alsa instead of pulseaudio...follow this how to...

[http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/](http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/)

after reboot go to volume control, preferences and re-enable all channel again...then set max all volumes and Digital mic 1 as input source

after that try with sound recorder ...

STILL MUTE ??

ok randomly microphone will be muted but with this 2 commands:

amixer set Digital 100% 
amixer set Capture 100% rec

microphone should be on and loud

simply create a script


and launch it when needed..

I hope it'll work for you as worked for me

Strange, this method didn't work for me, allthough I think pulseaudio is disabled: the volume of the mic is still very silent. Plz help.

---

### Post by jdeslip on 2008-11-13
I can get my mic to work just by killing the pulseaudio process.  But, I don't find doing this (or getting rid of pulseaudio completely) to be an acceptable solution!

---

### Post by titimoi on 2008-11-13
> **jdeslip said:**
> I can get my mic to work just by killing the pulseaudio process.  But, I don't find doing this (or getting rid of pulseaudio completely) to be an acceptable solution!

Did you have before the "auto-mute" poblem ?

---

### Post by jdeslip on 2008-11-13
> **titimoi said:**
> Did you have before the "auto-mute" poblem ?

Yes (and still seem to).

---

### Post by titimoi on 2008-11-13
> **jdeslip said:**
> Yes (and still seem to).

And can you use any sound-software after that ?
(what command do you use ? just "kill pulseaudio" ?)

Thanks ;)

---

### Post by jdeslip on 2008-11-13
Ya, the auto-mute doesn't seem to exist in alsa I guess.  I just use 'killall -9 pulseaudio' to kill it :)  Then my mic works good in skype.

---

### Post by titimoi on 2008-11-13
all right thanks a lot, it's still quicker as to reboot on XP...

---

### Post by talent03 on 2008-11-13
So we still do not have a solution other than killing or removing pulse-audio? This sucks. I was really hoping they would fix this problem in Intrepid as it was also standing in Hardy. At least they fixed the line out problem in hardy. Now we just need the mic to be fixed and all is good.

Too bad they pushed pulse-audio on all of us this time around. Hopefully they are much more well aware of the bugs and actually decide to fix them next time around. Hopefully.

---

### Post by bro on 2008-11-14
I didn't follow all of the discussion to be honest. For what it's worth, my solution for getting my mics to work with 8.10 intrepid 64-bit on a Dell 1330 xps. It does involve kicking pulseaudio. And the pick up from the built in front mic is a bit too soft.

System > Preferences > Sounds, I set everything to ALSA and the default mixer tracks to HDA Intel (alsa mixer)

Double click the sound applet on you panel to get to 'Volume control'
Clik preferences and enable Master, Headphone, PCM, Front, Capture, Digital Input Source. 
Strangely enough the Capture (,1,2) have muted mics when I enable them via preferences but this doens't influence the result at all. 

Close preferences. In playback Volume Control set everything under playback to reasonable values. On the options tab switch between 'Digital Mic 1' (built in mic) and 'Analog Inputs' (mic via jack input). 
To use 'Analog Inputs' I have to put the volume down a bit on the Recording tab (where is only 'Capture') to get better sound quality.

---

### Post by Michal77 on 2008-11-15
For Skype I've just installed static-oss version and them a mic works. It doesn't solve problem but let use Skype.

---

### Post by Naveen Soman on 2008-11-15
Absolutely no hope in bringin the mic bak to life.. been scourin the net for a fix since 8.10 upgrade... How is it tht it is such a common problem among laptop users?? First i thought it was a dv-6700 specific prob but was hugely mistaken.. Any temporary fixes for using mic wit Empathy client??

---

### Post by titimoi on 2008-11-15
> **Michal77 said:**
> For Skype I've just installed static-oss version and them a mic works. It doesn't solve problem but let use Skype.

Can you just tell me what did you install becose "sudo apt-get install static-oss" doesn't find anything.

---

### Post by brambles on 2008-11-16
> **titimoi said:**
> Can you just tell me what did you install becose "sudo apt-get install static-oss" doesn't find anything.

Try

sudo apt-get install skype-static-oss

Cheers

---

### Post by titimoi on 2008-11-16
thanks but it's the same it didn't find anything .. !

---

### Post by rockorequin on 2008-11-16
You need to add the medibuntu repository to get the skype-static-oss package. Based on [http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php), this will probably do it (ie I've replaced the distro with 'intrepid'):

echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free" | sudo tee -a /etc/apt/sources.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

Or you can just browse the packages via:

[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

eg

[http://packages.medibuntu.org/intrepid/skype-static-oss.html](http://packages.medibuntu.org/intrepid/skype-static-oss.html)

---

### Post by titimoi on 2008-11-17
Thanks again, but it hasn't change anything for me, the sound is still really low...

---

### Post by rockorequin on 2008-11-17
The problem is that ALSA doesn't detect the digital microphone sensitivity control in Intrepid, and the mike's default is the lowest level. In Hardy you just had to enable the Digital control (gnome-volume-control / Edit / Prefs) and then you could turn it up.

Only the Capture control is available in Intrepid, but this doesn't have any effect on digital mike sensitivity for me, just like it didn't have any effect in Hardy.

I logged bug #290505 about it ages ago but it doesn't look like any of the devs have read it :( From what I can tell, if you log bugs against ALSA or the kernel, they get ignored until a completely new kernel comes out and then you get an email asking if you'll test the new kernel to see if the bug has gone away.

In case it might help, I tried installing the 1.0.18 linux-sound-base / alsa-utils etc from the Debian repos to see if it would help, but I ran into a missing package (there was no 64-bit libasound2-plugins).

---

### Post by jdeslip on 2008-11-17
In my intrepid - I do have a digital volume bar in alsamixer (and gnome volume control).  I put it on max and it doesn't improve my recording volume...  It also seems to mute itself a lot.

---

### Post by kungfoofool on 2008-11-18
I am having the same problem (with a working mic at extremely low volume, along with other Skype-related audio problems) on multiple computers.

I wish I hadn't rolled up to the 8.10 upgrade in such a hurry. :(

---

### Post by 4Play on 2008-11-18
I also cant get the mic working in Intrepid :( and to boot half of the time the webcam isn't mounted (/dev/video0). Without skype its pretty complicated to continue using 8.10 on a regular basis

---

### Post by linusr on 2008-11-19
i too had the problem with internal mic with ubuntu 8.10 64-bit

but intially i installed ubuntu 8.10 64-bit RC & had all updates installed with no success

then did an re-install with Ubuntu 8.10 32-bit release version and some auto-updates, everythng works fine

internal mic works and recorded volume at audible level (using internal speakers)

---

### Post by khermans on 2008-11-21
Could this bug be related?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290505](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290505)

---

### Post by rockorequin on 2008-11-21
> **khermans said:**
> Could this bug be related?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290505](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/290505)

Yes, that's the bug I mentioned in an earlier post. :) My microphone works, but it's at very low volume. Some people can't get their microphone to work at all. My microphone *and* microphone sensitivity control worked great in Hardy. :( I've tried both the 64 bit and 32 bit versions of Intrepid and both are missing the mike sensitivity control.

Is there a way to tag bugs to get them some attention? I'd have thought that such a basic microphone problem is a major bug since it renders Intrepid useless for VoIP products like Ekiga and Skype, but none of the devs has posted anything to it. Maybe there's a duplicate which is more active?

---

### Post by monojit on 2008-11-22
I have a hp dv6205 laptop.I have done the following to get things done

1.go to system>preference>sound
2.under the "device" tab there is a field sound capturegarg
3.change the pull down list to **HDA intel CONEXANT  analog(ALSA)**

Hope it will work.

Regards

Mono

---

### Post by titimoi on 2008-11-22
nope, it was already on that choice :)

---

### Post by bigbrovar on 2008-11-23
I think this is not really the fault of the ubuntu devs poeple using other distros have reported the same problem. however i live far from my girlfriend and we usually skype. now she thinks i dont want to talk to her any more. i mean how do you explain that u cant its because i couldnt get pulse audio/alsa to work? .. she is not a techie. and would think > yeah right

---

### Post by jdeslip on 2008-11-23
Upgrading to intrepid from hardy has caused the demise of many relationships...

---

### Post by mavsman4457 on 2008-11-25
chalk me up for one more, good thing i'm somewhat smart uninstalling pulse audio and installing esound instead.  don't do that by itself though cause there's some file you need to remove to make sure ubuntu can start up without pulse audio.

---

### Post by Technoviking on 2008-11-26
This fix from Gutsy did work for me.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low)

---

### Post by linux_tech on 2008-11-27
Solutions that work on the 1520 may work on 1530 as well

Patch-
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=f323b03701097f485540e876d27be5cf29820229](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=f323b03701097f485540e876d27be5cf29820229)

ALSA settings-
[http://ankurjain.org/2007/11/03/ubun...r-options-tab/](http://ankurjain.org/2007/11/03/ubun...r-options-tab/)
[http://ankurjain.org/2007/11/03/ubun...inspiron-1520/](http://ankurjain.org/2007/11/03/ubun...inspiron-1520/)

---

### Post by figi22 on 2008-11-27
New Dell Studio, just installed Ubuntu 8.10.   Skype sound working but not mic.  Don't know whether to install Pulse or not?  What's that about?

Wish I'd just installed 8.04, after reading all this...

---

### Post by titimoi on 2008-11-27
> **linux_tech said:**
> Solutions that work on the 1520 may work on 1530 as well

Patch-
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=f323b03701097f485540e876d27be5cf29820229](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-hardy-lum.git;a=commit;h=f323b03701097f485540e876d27be5cf29820229)

ALSA settings-
[http://ankurjain.org/2007/11/03/ubun...r-options-tab/](http://ankurjain.org/2007/11/03/ubun...r-options-tab/)
[http://ankurjain.org/2007/11/03/ubun...inspiron-1520/](http://ankurjain.org/2007/11/03/ubun...inspiron-1520/)

just before I try anything, can you tell me what kind of problem did you have (low mic volume ? automatic muted mic as well ?

Thank's

---

### Post by supermikey on 2008-11-28
For 1420n users this is what I did:

[http://ubuntuforums.org/showthread.php?t=994731](http://ubuntuforums.org/showthread.php?t=994731)

---

### Post by jespdj on 2008-11-28
I tested this with a Fedora 10 Live CD, and get the same problem - the microphone only picks up the sound very faintly.

See the bug report: [bug #275998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275998)

It looks like this is a bug in newer versions of PulseAudio; it is not specific to Ubuntu.

---

### Post by jdeslip on 2008-11-28
supermikey - that did not work on my 1420n builtin mic.  Was it suppossed to make the builtin mic work or an external mic work?

---

### Post by supermikey on 2008-11-30
> **jdeslip said:**
> supermikey - that did not work on my 1420n builtin mic.  Was it suppossed to make the builtin mic work or an external mic work?

Yes it is. Did you make sure to have the proper selections when selecting the input sources? I know it seems trivial but they won't work without that. Having the latest Alsa drivers helps. In volume control make sure to select each device in turn and turn the volume all the way up, and toggle audio recording as on from that device.

If you have skype, give a call to the test call. If it worked you should be able to hear yourself talking when you get to the recording playback. Even on my system, there is no feedback from the speakers that the mic is recording, it just is.

---

### Post by jdeslip on 2008-12-01
Supermikey,

I followed your directions to the letter but audio recording in skype (and other applications) is still really quiet.  It records but at low volume.  Also, the devices still seem to auto-mute themselves whenever I close volume control and reload it, they are muted (not that muting seems to affect the recording volume...).

---

### Post by Nosig on 2008-12-07
I followed Supermikey's instructions exactly. I did have to mark the "options" possibilities via the preferences button (bottom ticks in that scroll menu) before I had the options tab available, that might be handy to add for other users. In Skype I set all audio settings to Pulse and unmarked the setting that allows Skype to adjust mike level, because skype seems to want to mute the microphone.

Doing all that I finally have my internal M1330 microphone working. It's a tad soft in a test call, but I think (hope) it's usable (still have to try a real call in the daytime).

---

### Post by janrikard on 2008-12-11
I tried the things in the tread, the mixer settings, , and it work, except the very low volume.
BUT, after ive rebooted and logged in, i cant get any sound, thers sound when i loggin, but after that i dont get any sound, the mixersettings looks ok.
Someone have any idea?

/rikard

---

### Post by nave.notnilc on 2008-12-29
bump

My brand-new Dell XPS M1330 has what seems to be the standard set of issues (I'm very disappointed, Ubuntu!), and my microphone works, but the sound level is extremely low.  I'm on a fresh, updated 64bit install.

Would like to keep this topic around :P

---

### Post by bro on 2008-12-29
My Dell XPS m1330 seems to have no issues at all besides the microphone problem. The bugtrackers found a workaround for that recently, read through this thread: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/275998)

---

### Post by Dr.Suave on 2008-12-31
I fixed it by installing kmix

---

### Post by bro on 2008-12-31
how exactly did installing kmix solve your problem? You 'just installed' it? Because in the bug-thread I mentioned people are looking into much more complicated workarounds.

---

### Post by Dr.Suave on 2008-12-31
> **bro said:**
> how exactly did installing kmix solve your problem? You 'just installed' it? Because in the bug-thread I mentioned people are looking into much more complicated workarounds.

I haven't read the whole thread, or your bug report - I just read the first page where people where talking about their microphone being always muted. I was also having a problem with microphone capture always being muted - I could record at an incredibly low level, but it was ridiculously low. I'd noticed that on another pc having the same problem capture was fine after installing kubuntu-desktop - on KDE *and* in Gnome.

My girlfriend was having problems with a muted microphone in Ibex as well, so I just opened a terminal, typed sudo apt-get install kmix and configured capture there. It was fine after that.

Might not work for everyone, but it did for me on two laptops, and I've heard someone else saying this method worked for them.

If an eternally muted microphone is your problem, I'd give kmix a try.

---

### Post by Mykyta on 2009-01-04
> **Dr.Suave said:**
>  I just opened a terminal, typed sudo apt-get install kmix and configured capture there. It was fine after that.


It did help me. It seems that "Mux"-option can not be adjusted with the Gnome-control, but kmix does work.

---

### Post by x C0MMAND0 x on 2009-01-23
**The following fix worked for me.  If somebody could try it who DOES have pulseaudio installed and confirm it works, please let me know because I did this with pulseaudio uninstalled.**

Fix workaround for Dell XPS M1330 Skype low mic volume.

```
sudo apt-get remove volumecontrol.app
```

```
sudo apt-get remove sound-recorder
```

```
sudo apt-get install kmix
```

```
kmix
```

1. Click on new volume icon in top right corner
2. Click on "Mixer"
3. Hit "Ctrl-M" if you DONT see the "Settings" option up top
4. Click Settings, choose "Configure Channels"
5. Be sure to select "Digital Input Source", "Digital", "Capture".
6. Choose "Digital Mic 1" and be sure to maximize "Capture" and "Digital".

*Note, you don't have a sound recorder but you can download many other free ones.

**I did this work around with pulseaudio UNINSTALLED and removed completely.  ALSA owns and it's all I need.  Now, Skype works PERFECT and the volume recording is loud.  Be sure in Skype to UNcheck the "Allow skype to adjust levels" option.

***I hope this works for you as it did for me.

****I have an image of what my Kmix setup looks like if anyone is interested, let me know as I haven't taken the time to figure out how to add images on here because they need scaling down.

---

### Post by pspotts on 2009-01-23
Folks,

I'm running 8.10 on a new Dell Studio, and just got the internal mic working using gnome volume control. Had to go into preferences and add the digital sources at the bottom of the list. Then under the new "options" tab that action sets up, I set the digital input source to Digital Mic 1.

All this comes via this thread:

[http://ubuntuforums.org/showthread.php?t=673628&page=2](http://ubuntuforums.org/showthread.php?t=673628&page=2)

Hope it works for some of you as well...

Pete

---

### Post by Poleh on 2009-01-26
> **x C0MMAND0 x said:**
> **The following fix worked for me.  If somebody could try it who DOES have pulseaudio installed and confirm it works, please let me know because I did this with pulseaudio uninstalled.**

Fix workaround for Dell XPS M1330 Skype low mic volume.

```
sudo apt-get remove volumecontrol.app
```

```
sudo apt-get remove sound-recorder
```

```
sudo apt-get install kmix
```

```
kmix
```

1. Click on new volume icon in top right corner
2. Click on "Mixer"
3. Hit "Ctrl-M" if you DONT see the "Settings" option up top
4. Click Settings, choose "Configure Channels"
5. Be sure to select "Digital Input Source", "Digital", "Capture".
6. Choose "Digital Mic 1" and be sure to maximize "Capture" and "Digital".

*Note, you don't have a sound recorder but you can download many other free ones.

**I did this work around with pulseaudio UNINSTALLED and removed completely.  ALSA owns and it's all I need.  Now, Skype works PERFECT and the volume recording is loud.  Be sure in Skype to UNcheck the "Allow skype to adjust levels" option.

***I hope this works for you as it did for me.

****I have an image of what my Kmix setup looks like if anyone is interested, let me know as I haven't taken the time to figure out how to add images on here because they need scaling down.

nope, afraid this had no effect for me.... still got VERY low recording on digital mic from Monitor - if I lean in really close it picks up and records fine, but I have to right up against it and talking very firmly...

---

### Post by DirtyCabbage on 2009-02-07
I have a Dell Inspiron 1545 and the microphone was working fine under 8.10 until I updated the ALSA drivers that came out last week. The sound was very quiet. To fix it I changed the both the Input Source options to "Mic". Previously they were on "Front mic" which worked fine (and I am using the front mic.

The Capture devices still appear muted, but sound records fine now.

---

### Post by oneriang on 2009-02-23
I has same problem.
I try to fix it.

I just do it on terminal show below...

sudo apt-get install libasound2 alsa-utils alsa-oss

ref this [_link_]("http://alsa.opensrc.org/Quick_Install")

then in value controller select [capture:Alsa pcm on front...]

I hope it will help you.

---

### Post by msumurph on 2009-03-02
My microphone had very low volume. Installing KMix worked for me.  Thanks!  I just unmuted the Mic that had the Boost feature.

---

### Post by subzero316 on 2009-04-16
:D Mine Solved :D

Mine didn't work initially. But I changed the settings on Pulse Preferences and it worked liked a charm. In fact it was so loud I had to reduce the capture volume and nil the boost.

I just Enabled -- Make Discoverable network sound devices available locally.

---

### Post by Nosig on 2009-04-16
And you can find these Pulse preferences where?

---

### Post by rockorequin on 2009-05-19
Alsa 1.0.20 is able to find the digital microphone volume control on my Dell XPS M1530 (1.0.20 has many bugfixes for hda_intel sound chips), and hence fixes the problem.

I first built and installed it manually (eg see the script at [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) - I downloaded it and modified it to get 1.0.20), but now I've installed the 2.6.30-rc6 kernel in Jaunty (the deb files are at [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc6)) to work around some ext4 and wireless bugs in the 2.6.28 kernel, and 2.6.30-rc6 already includes alsa 1.0.20.

---

