---
title: "Skype 1.3b and alsa (dmix) issues"
date: 2006-06-29
forum: Desktop Environments
---

### Post by rem on 2006-06-29
Dear all,

Have installed the new Skype 1.3b which is so cool comparing with the old one but have some sound problems. I'm able to initiate a call but when the 2nd party answers I get this error message and of course, PROBLEMS WITH SOUND DEVICE error on Skype 

```
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
```

I switched to ALSA from ESD on System / Preferences / Multimedia Systems Selector as well on Skype / Tools / Options / Sound Devices, removed (purged) all Skype files and freshly install it, I configured my alsa files conformly to some how to's here but still doesn't work! Old 1.2 Skype always worked (with the problems we all already know about). 

Could you help on this one, please? Thanks a mil in advance!

Regards,
Rem.

---

### Post by matjaz_pirnovar on 2006-06-29
[QUOTE=rem]Dear all,

Have installed the new Skype 1.3b which is so cool comparing with the old one but have some sound problems. I'm able to initiate a call but when the 2nd party answers I get this error message and of course, PROBLEMS WITH SOUND DEVICE error on Skype 

```
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
```

I switched to ALSA from ESD on System / Preferences / Multimedia Systems Selector as well on Skype / Tools / Options / Sound Devices, removed (purged) all Skype files and freshly install it, I configured my alsa files conformly to some how to's here but still doesn't work! Old 1.2 Skype always worked (with the problems we all already know about). 

Could you help on this one, please? Thanks a mil in advance!

Regards,
Rem.[/QUOTE]

Hi,

I have the same/similar problem and some others seems as well. Refer to "New Skype Beta Out!" posting here, the thread is going there right now...

Let's work on it... ;)

M

---

### Post by rem on 2006-06-29
Hey,

I knew about that thread but i read it late this night (morning) here and didn't saw the part with your post just the new Skype out messages :) 
Maybe you posted it a little bit after I read it. Anyway, I'll subscribe to the thread of course... Thanks for pointing it out!

---

### Post by ajgreeny on 2006-06-29
I downloaded the beta skype a few minutes ago and tried it out.

Minor problem to start with as it seemed to reset all the levels of the microphone in kmix and i couldn't get my test call (echo 123) to record my voice.  A couple of clicks in kmix, however and all is now working great, and I can even play music with XMMS and make or receive calls too - Wonderful.

---

### Post by wieman01 on 2006-06-29
Have to repeat myself but the new version of Skype is called BETA for a reason... Altough I was impressed that it had recognized my bluetooth headset in the first place, I was shocked to find out that the headset would stop working after 15 - 60 seconds of service. Not sure what went wrong, but I won't put much effort into it... I simply switched back to the previous version of Skype which was fine.

Man... some developers never get it right. That's a bit embarassing to be honest. I cannot complain about the fact that some people prefer Windows to Linux because some things in Linux are just not as simple as they ought to be. I am saying this as a quality guy... hope you don't mind this comment.

He

---

### Post by ozorba on 2006-06-29
When I use echo123 it rings once and I get "Problem with the sound device".

---

### Post by rem on 2006-06-29
[QUOTE=wieman01]Have to repeat myself but the new version of Skype is called BETA for a reason... Altough I was impressed that it had recognized my bluetooth headset in the first place, I was shocked to find out that the headset would stop working after 15 - 60 seconds of service. Not sure what went wrong, but I won't put much effort into it... I simply switched back to the previous version of Skype which was fine.

Man... some developers never get it right. That's a bit embarassing to be honest. I cannot complain about the fact that some people prefer Windows to Linux because some things in Linux are just not as simple as they ought to be. I am saying this as a quality guy... hope you don't mind this comment.

He[/QUOTE]


Yes, you're right... but if I was to quit each time some beta thing or whatever didn't worked on Linux, I would still be using Windows at this time... I can't find a fix to this Skype issue, but maybe someone smarter will... it's worth trying. After all... if this will proove to be a lost cause, we'll wait for the 1.3 stable ;)

---

### Post by nocturn on 2006-06-30
[QUOTE=wieman01]I cannot complain about the fact that some people prefer Windows to Linux because some things in Linux are just not as simple as they ought to be. I am saying this as a quality guy... hope you don't mind this comment.
He[/QUOTE]

So, Windows is simpeler then Linux becaus the Skype devs (who have no relation with anyone in the Free Software community) are not capable of making their closed source software work on Linux?

You know that there are numerous free alternatives for Skype (using the SIP protocol) that are easy to install and work just great (ekiga for one).

If you rely on a specific closed-source package that is very low in quality, you should blame the vendor and not Linux/Ubuntu as even Microsoft cannot take responsability for every single piece of bad software written for their OS (as long as that badly written software does not take down the system).

---

### Post by wieman01 on 2006-06-30
Hi Nocturn, 

Yes, of course we are on the same page. I am complaining about the fact that some developers don't deserve the name, no more, no less. I am a frequent user of Ekiga and quite happy with it, but sometimes Skype just comes in handy. 

That being said, it is sad that Linux is not taken seriously as a commercial threat to obvious market leaders. Very often it is the little things (such as Skype) that keep average Joes (such as I am) from doing away with Windows (luckily I have managed to do just that, but admittedly it took me a while). One has to admit... if Linux & 3rd party programs developed for it were as simple as Windows is (sometimes at least), it would be way more popular. Ubuntu is certainly one step in the right direction.

And yes, you are right... it's nothing to do with Linux per se but with the lousy support from 3rd parties who just don't want to bother. But this does not change the fact I guess.

Anyway, as a quality & process guy I am the optistic type. I'll try again when the final version comes out (1.2 work fine for me).

Cheers / He

---

### Post by nocturn on 2006-06-30
[QUOTE=wieman01]
And yes, you are right... it's nothing to do with Linux per se but with the lousy support from 3rd parties who just don't want to bother. But this does not change the fact I guess.

Anyway, as a quality & process guy I am the optistic type. I'll try again when the final version comes out (1.2 work fine for me).

Cheers / He[/QUOTE]

You are right that the lack of those commercial products (in a decent form) is a major drawback for Linux adoption...   And unfortunately it is a chicken and the egg kind of problem.

Users do not want to migrate to Linux because of bad or no support for the programs they use (Skype being a big one) and companies like Skype do not put enough recources into Linux citing a small user base.

My best hope is to offer people Free alternatives that are designed specificly for Linux so they do not need proprietary software, this is much more in line with our philosophy too but only time will tell if this happens.

---

### Post by AiBo on 2006-06-30
[QUOTE=ajgreeny]I downloaded the beta skype a few minutes ago and tried it out.

Minor problem to start with as it seemed to reset all the levels of the microphone in kmix and i couldn't get my test call (echo 123) to record my voice.  A couple of clicks in kmix, however and all is now working great, and I can even play music with XMMS and make or receive calls too - Wonderful.[/QUOTE]

I am a gnome user with the same problem!  I even installed kmix.  what "couple clicks" did you do to get it to work?!?!

---

### Post by ajgreeny on 2006-06-30
Not sure I can help in gnome, but in kde with kmix all I had to do was make sure the mic was active, instead of aux, or line-in, or whatever it was set on and then bring the slider for mic level up to the top.

---

### Post by rem on 2006-06-30
[QUOTE=AiBo]I am a gnome user with the same problem!  I even installed kmix.  what "couple clicks" did you do to get it to work?!?![/QUOTE]

I don't think you actually need to install any kmix... there's a volume / mic control application on GNOME too! Applications / Sound & Video / Volume Control. I remeber that when I first installed Dapper, my mic wasn't working also but started it from Volume Control / Capture tab and activated the Mic Boost too from the Switches tab. Take a look around, hope it'll work for you too... :)

---

### Post by wawa on 2006-07-20
> Dear all,

Have installed the new Skype 1.3b which is so cool comparing with the old one but have some sound problems. I'm able to initiate a call but when the 2nd party answers I get this error message and of course, PROBLEMS WITH SOUND DEVICE error on Skype 

```
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
```


Hi

I think its because of customization in config file /etc/asound.conf to use dmix. Try

```
 sudo mv /etc/asound.conf /etc/asound.conf.bak
 sudo /etc/init.d/alsa-utils restart
```

and restart skype. Everything else should work too, but incase you will need dmix in the future, use the backup file.

Cheers

walyd

---

### Post by maruchan on 2006-07-26
> and restart skype. Everything else should work too, but incase you will need dmix in the future, use the backup file.

Thank you!!!! Skype works for me now, after this "problem with sound device" error kept popping up. I did remember setting up this dmix stuff a while ago, but I can't remember why. :)

---

### Post by amanda on 2006-08-07
I don't even have an "asound.conf" file, and just restarting skype isn't getting me anywhere. Grumble.

---

### Post by kblood on 2006-08-24
Hello there,

I think I have a very good solution for you all.
Dmix is used with soundcards that don't have hardware mixing (i.e. reproduce several sounds at the same time), and does software mixing (mixes the sounds in software, and sends just one sound to the soundcard).
The problem is that the dmix plugin in ALSA doesn't support redirecting the input from the microphone from the actual soundcard. The dmix plugin is, in a way, a "virtual soundcard", but it only does output.

The solution is to create in asound.conf a new definition for a mixed "virtual soundcard", that uses the hardware directly for input, and dmix for output, so you get everything working. I looked for a while for information, and came up with this (the trick is the new pcm.skype definition):

```
pcm.card0 {
  type hw
  card 0
}

pcm.dmixer {
  type dmix
  ipc_key 1025
  slave {
    pcm "hw:0,0"
    period_time 0
    period_size 2048
    buffer_size 32768
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

pcm.skype {
  type asym

  playback.pcm "dmixer"
  capture.pcm "card0"
}

pcm.!default {
  type plug
  slave.pcm "skype"
}

```

This works great for me, and I have system sounds activated, and can run xmms and still hear the Skype sounds, so... I hope it works for you all!

I am not an expert, just got tired of the same issue and went doing some research, mostly here:
[http://juljas.net/linux/skype/alsa-configuration.html#software_mixing](http://juljas.net/linux/skype/alsa-configuration.html#software_mixing)

---

### Post by hraposo on 2006-08-24
why i don't install "gizmo". It's so good as Skipe.

---

### Post by freskog on 2006-10-05
Thank you kblood, you are the man!

hraposo: I would love to use gizmo or ekiga, but all my friends use skype...

---

### Post by rflmnz on 2006-11-18
Hi, sorry my english....

I tried this solution to make Skype works...
[http://ubuntuforums.org/showpost.php?p=1416044&postcount=17](http://ubuntuforums.org/showpost.php?p=1416044&postcount=17)

But I'm using an USB audio device and when I change the asound.conf my sound goes only in the front headphone slot.... So everytime when I quit Skype and  I want to hear some music from the USB audio I have to clear the asound.conf content...

I need some help!!!! Thanks!!! 
(Se a resposta vier em português é melhor!!! [http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif))

---

### Post by rflmnz on 2006-11-18
Ok, I'm here again....

Is there a way to put Skype sound-out in my Nvidia CK804, and my others sound-outs in USB Audio??? Thanx again!

---

### Post by patrick295767 on 2006-11-19
> **rem said:**
> Dear all,

Have installed the new Skype 1.3b which is so cool comparing with the old one but have some sound problems. I'm able to initiate a call but when the 2nd party answers I get this error message and of course, PROBLEMS WITH SOUND DEVICE error on Skype 

```
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
```

I switched to ALSA from ESD on System / Preferences / Multimedia Systems Selector as well on Skype / Tools / Options / Sound Devices, removed (purged) all Skype files and freshly install it, I configured my alsa files conformly to some how to's here but still doesn't work! Old 1.2 Skype always worked (with the problems we all already know about). 

Could you help on this one, please? Thanks a mil in advance!

Regards,
Rem.

i am sure if you try as root it will work  like sudo skype
it s sthg crazy to do so, I know, but it worked.

Hence, permissiosn to fix manually !!

---

### Post by patrick295767 on 2006-11-19
> **wawa said:**
> Hi

I think its because of customization in config file /etc/asound.conf to use dmix. Try

```
 sudo mv /etc/asound.conf /etc/asound.conf.bak
 
```

and restart skype. Everything else should work too, but incase you will need dmix in the future, use the backup file.

Cheers

walyd

[COLOR="Red"][B]NOT CHANGES WIth sudo /etc/init.d/alsa-utils restart

as i AM REPEATING it is just a permissions problem !

Just run sudo skype 
and you will see it is working.
but ok, now, we know the problem
[/B][/COLOR]
what to do ??

Btw, We dont have any /etc/asound.conf

thank you

---

### Post by patrick295767 on 2006-11-19
> **amanda said:**
> I don't even have an "asound.conf" file, and just restarting skype isn't getting me anywhere. Grumble.

[COLOR="Red"]as I could say previously in red[/COLOR]

---

### Post by rflmnz on 2006-11-19
It didn't work for me... I&#7743; still seeing "problem with audio device..."

---

### Post by patrick295767 on 2006-11-19
> **rflmnz said:**
> It didn't work for me... I&#7743; still seeing "problem with audio device..."

with some help from patrick k, i have been adviced to use automatix.
it works

try this :

> #!/bin/bash 



if [ "$(cat '/etc/apt/sources.list' | grep 'www.getautomatix' )"  =   "" ] ;    then
echo "updating sources.list"
sudo echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" >>  "/etc/apt/sources.list" 
fi


wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
 gpg --import key.gpg.asc
 gpg --export --armor 521A9C7C | sudo apt-key add -

sudo apt-get update
sudo apt-get -f -y install automatix2

  automatix2


click on skype, let me know if it works this way ?

---

### Post by arnieboy on 2006-11-19
automatix2 needs to be run as normal user. Automatix automatically takes care of user environment variables.
Hence run it as
```
automatix2
``` (NOT with sudo)

---

### Post by Patrick K. on 2006-11-19
> **arnieboy said:**
> automatix2 needs to be run as normal user. Automatix automatically takes care of user environment variables.
Hence run it as
```
automatix2
``` (NOT with sudo)

or select it from the system tools menu. :P

---

### Post by rflmnz on 2006-11-19
I installed Skype from Automatix but its still not working... Even when I type sudo skype... Only changing asound.conf makes Skype works for me....

---

### Post by patrick295767 on 2006-11-19
> **arnieboy said:**
> automatix2 needs to be run as normal user. Automatix automatically takes care of user environment variables.
Hence run it as
```
automatix2
``` (NOT with sudo)

Thank you Arnieboy,
I discoverd it today. It s really great tool you made !!
(I corrected above)

I noticed that automatix2 did a 
apt-get install alsa-oss 
for the skype installation. That helped !

Thank you again !

Regards,

---

### Post by patrick295767 on 2006-11-19
> **rflmnz said:**
> I installed Skype from Automatix but its still not working... Even when I type sudo skype... Only changing asound.conf makes Skype works for me....

PLease Could you give us more deatails about the problems ?
I am curious to know what could be done to make it work at 100% and also would like to sure it is possible to have skype workign for all ubuntu.

---

### Post by rna on 2006-12-16
I had a similar problem with Skype 1.3b installed via automatix2:

ALSA lib pcm_dmix.c:801:(snd_pcm_dmix_open) The dmix plugin supports only playback stream

Turned out to be a simple fix in my case (just thought I'd share):

deleted ~/.asoundrc 

Found this information at [https://developer.skype.com/LinuxSkype](https://developer.skype.com/LinuxSkype)
If you are using ALSA 1.0.11 or later, and still have an /etc/asound.conf or ~/.asoundrc config file with settings related to dmix, you can now delete this file (or save it elsewhere if you think it has settings that you need). dmix is now handled internally by ALSA, and no configuration is required. Using these configuration files may cause "Problem with sound device" errors when attempting to make a call.

---

### Post by medya on 2007-03-18
>  sudo mv /etc/asound.conf /etc/asound.conf.bak
 sudo /etc/init.d/alsa-utils restart
this worked for me, but a question , should I do tihs everytime before runnig skype , is there any permanet solution ?

---

### Post by cesium62 on 2008-01-23
I hate those loose markets.  We should get a wrench and tighten it up.

<Did I lose you in that pun?>

---

