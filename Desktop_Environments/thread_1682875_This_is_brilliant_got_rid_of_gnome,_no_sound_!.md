---
title: "This is brilliant got rid of gnome, no sound !"
date: 2011-02-06
forum: Desktop Environments
---

### Post by ThaDoctor99 on 2011-02-06
Hmm I decided it was time I got rid of gnome.
I tried before back then the sound went awall as well this time I will not install gnome again rather try to find some solution to make the sound work.

I am shy to do some work if it gets to work

I have as to what reason there could be for the sound not to work.

If you need some information just ask

I use ubuntu Maverick Meerkat can't remember if that is .04 or .10
It is also 64 bit.

Awaiting some help :D

Thanks a lot for the time spend so far :D

---

### Post by Krytarik on 2011-02-06
What desktop environment are you using now?
How did you remove Gnome?

Try re-installing the meta-package of your current DE, like this:
```
sudo apt-get install --reinstall kubuntu-desktop
```

---

### Post by ThaDoctor99 on 2011-02-07
well I removed gnome from the synaptic menu 
I use fluxbox 

I removed gdm completely .... and also the meta package from gnome-desktop.
If I install that package wouldn't that mean that I am bound to have that installed ?

---

### Post by Jouke74 on 2011-02-07
Reinstall Alsa, that should get the sound back. Then also some packages which allow you to access the mixer, config etc. Those packages were taken out when deleting Gnome.

---

### Post by ThaDoctor99 on 2011-02-07
I reinstalled alsa-base still no sound... What else could I do ?

---

### Post by Krytarik on 2011-02-07
Then how did you install Fluxbox? Re-install exactly those metapackage. This should take care of all needed packages.

---

### Post by ThaDoctor99 on 2011-02-07
I installed fluxbox by 'sudo apt-get install fluxbox'

---

### Post by Krytarik on 2011-02-07
> **ThaDoctor99 said:**
> I installed fluxbox by 'sudo apt-get install fluxbox'
Then try this:
```
sudo apt-get install --reinstall fluxbox
```

---

### Post by ThaDoctor99 on 2011-02-07
Well about that. My computer can't really seem to understand what I mean when I say that it says
unknown option: fluxbox

^^ E: Invalid operation
________________________________________________________________________________________________
That is I understood it now
I thought you said 
'sudo apt-get --reinstall fluxbox'
not 'sudo apt-get install --reinstall fluxbox'
so I got it now. It does however still not work.

I also found that the meta package for gnome (that is the one just named 'gnome')
will not install it requires swfdec-mozilla and some other packages which can not be installed at the same time with my setup it seems.


What can I do then ?

---

### Post by Krytarik on 2011-02-07
Try re-installing the package "pulseaudio".

If that doesn't help either, install "alsa-utils", and check with the command "alsamixer" the alsa output levels.

---

### Post by ThaDoctor99 on 2011-02-07
Hmm now I have done all of that and everything seems to be in order...
I did install another desktop package though, the one from lubuntu 
to see if that helped - needles to say it didn't.

Hmm 
I begin to get really desperate here.
There is a lot of series I watch on my computer, and it seems to loose a lot when I don't have any sound.

---

### Post by Krytarik on 2011-02-07
How about the usual volume controls in Fluxbox?

How about system sounds? (background: It could be, that some codecs are missing.)

---

### Post by markthekdeguy on 2011-02-07
well done for leaving Gnome,
you dont need Pulseaudio in KDE, 
but i guess Pulseaudio *may* still be running,
may have residual config or the pulseaudio daemon
is running  .. i would personally

sudo apt-get purge pulseaudio

and reboot.
now hopefully you have a working ALSA audio sys. dont forget in Kmix
to enable all poss channels though, 
(open mixer/ settings / config channels - then drag over channels you want shown, from 'available' to 'visible' )

there will likely be residual Gnome stuff you dont need still actually running on KDE, like gamin gvfs etc, if you installed KDE on Ubuntu. 
i suggest a clean install,  

Likely much better idea if you're backed up may well be install a nice clean Kubuntu 10.04 LTS. much cleaner, then use Medibuntu, codecs etc and enjoy a mainly QT life. but with working audio :) :lolflag:

---

### Post by Krytarik on 2011-02-07
Despite the fact that *markthekdeguy* is missing the point that you aren't running KDE at all (you wouldn't install Fluxbox if you had a more or less decent machine), removing pulseaudio may be worth a try.

---

### Post by ThaDoctor99 on 2011-02-08
Well I have got a decent machine just really don't like gnome, eating the decentness out of my machine ;-)

Well I just like fluxbox :D
also I am gonna try to purge pulseaudio... :D

---

### Post by ThaDoctor99 on 2011-02-08
Well that purge of pulseaudio left me with a even bigger problem.
Now my alsa library (at least I think it is that) complains that it can't find pulse throws an error from pulse.c:229 (pulse_connect) PulseAudio: unableto connect: connection refused

That is from when I start mocp - my preferred music player.

---

### Post by ThaDoctor99 on 2011-02-08
I also got OSS which maybe I should just purge ????

---

### Post by Krytarik on 2011-02-08
Then install pulseaudio again, and don't remove OSS.

I did a short forums/web search, and the only thing I repeatedly come over is the alsamixer thing, which I mentioned earlier. Are you really sure, that nothing in it is muted or low!?

---

### Post by Krytarik on 2011-02-08
Another thing: I saw in the this guide that it is recommended to install the package "fluxconf" along with "fluxbox", try it:
[https://help.ubuntu.com/community/Installation/LowMemorySystems#Fluxbox](https://help.ubuntu.com/community/Installation/LowMemorySystems#Fluxbox)

---

### Post by ThaDoctor99 on 2011-02-08
well sound is on in alsamixer.
I don't know about everyother mixer though...
Well now I did a reinstall of pulseaudio and oss4-base
Perhaps there is some pulseaudio package ?

---

### Post by Krytarik on 2011-02-08
I even installed Fluxbox to check what options are available for you, after subtraction of the gnome tools.

In my Fluxbox "aumix" is available, you can also install "pavucontrol" (to control pulseaudio).

Besides that, have you any other options to connect to your soundcard/-chip?

---

### Post by ThaDoctor99 on 2011-02-09
Hmm pavucrontrol had everything turned down AND MUTED tried turned the sound up and unmute. And surprise STILL NO SOUND....
besides my aumix doesn't open.
complains that 
aumix: error opening mixer: No such file or directory.

---

### Post by Krytarik on 2011-02-09
I found this guide, try it:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

And please attach any history.log* files you find in "/var/log/apt", compress them therefore. When did you remove gnome, approximately?

---

### Post by ThaDoctor99 on 2011-02-09
approximately 3 days ago (or perhaps only 2)

---

### Post by ThaDoctor99 on 2011-02-09
there might be course for concern about the fact that aplay can't find my soundcard ? It were probably handled by gnome earlier...

---

### Post by ThaDoctor99 on 2011-02-09
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
        Subsystem: ASUSTeK Computer Inc. Device 16f3
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
        Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

And that is my hardware for sound.

I tried to modprobe snd-hda-intel.
Without making any changes to the fact that they dont speak

---

### Post by ThaDoctor99 on 2011-02-09
[http://www.alsa-project.org/db/?f=c32b3de97c9494b9bb1c29554ac9dfbfa7d0b82b](http://www.alsa-project.org/db/?f=c32b3de97c9494b9bb1c29554ac9dfbfa7d0b82b)

that is from alsa-info.sh

---

### Post by Krytarik on 2011-02-09
> **ThaDoctor99 said:**
> approximately 3 days ago (or perhaps only 2)
I asked that to easier check the log files I've requested.

---

### Post by Krytarik on 2011-02-09
> **ThaDoctor99 said:**
> 00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
        Subsystem: ASUSTeK Computer Inc. Device 16f3
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 9
        Memory at fae78000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

And that is my hardware for sound.

I tried to modprobe snd-hda-intel.
Without making any changes to the fact that they dont speak
Check with the output of the following command, if you are member of the "audio" group:
```
id
```Mine says:
> krytarik@krytarik-desktop:~$ id
uid=1000(krytarik) gid=1000(krytarik) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),**29(audio)**,30(dip),44(video),46(plugdev),104(fuse),105(lpadmin),112(netdev),119(admin),122(sambashare),1000(krytarik),1001(shared)
krytarik@krytarik-desktop:~$ 


EDIT: Your output looks similar to those in the guide, so I guess this is normal. But nevertheless check the above thing. I'll further read the guide, hold on.

---

### Post by ThaDoctor99 on 2011-02-09
uid=1000(tobias) gid=1000(tobias) groups=1000(tobias),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)

Should I be member of sound, in some of the documentation you gave it says I should NOT BE member of AUDIO.

Where were those logs you wanted to see...

---

### Post by ThaDoctor99 on 2011-02-09
[http://pastebin.com/KRfADtyL](http://pastebin.com/KRfADtyL)

That is the hisory.log there is only this one... and the .gz version.

---

### Post by Krytarik on 2011-02-09
> **ThaDoctor99 said:**
> uid=1000(tobias) gid=1000(tobias) groups=1000(tobias),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),122(sambashare)

Should I be member of sound, in some of the documentation you gave it says I should NOT BE member of AUDIO.

Where were those logs you wanted to see...
Yeah, I read this too. But as you can see, I am member of "audio" and sound works for me. Try adding yourself to the group. But I doubt that it helps, since there is no loaded sound module listed in the output of the alsa script.
```
sudo adduser tobias audio
```

---

### Post by ThaDoctor99 on 2011-02-09
Modprobing snd-hda-intel worked just now :D

Just one little thing could I add this to some file so it is loaded when I start the computer ?
some startup script which I can't remember what those are called.
nevermind I think I got it.

---

### Post by Krytarik on 2011-02-09
> **ThaDoctor99 said:**
> [http://pastebin.com/KRfADtyL](http://pastebin.com/KRfADtyL)

That is the hisory.log there is only this one... and the .gz version.
The package gnome isn't mentioned at all in this log, was that all?
> **ThaDoctor99 said:**
> Modprobing snd-hda-intel worked just now :grin:

Just one little thing could I add this to some file so it is loaded when I start the computer ?
some startup script which I can't remember what those are called.
Try adding its name to "/etc/modules".

---

### Post by ThaDoctor99 on 2011-02-09
well probably beat my home brew of a solution :D

---

### Post by ThaDoctor99 on 2011-02-09
Thanks for you help - Always liked this community a lot better than the equivalent for windows (well except for that there is none for windows anybody helping there are demanding money.... ) 
Awesome community :D

---

### Post by Krytarik on 2011-02-09
Now the final, ultimative question ;-):
Why do you like Fluxbox that much? It's so damn slimmed down. I'd rather choose Xfce, I tried it along with Fluxbox. It's somewhat in the middle of Gnome/KDE and Fluxbox.

EDIT: You're welcome! (We were posting at the same time.)

---

### Post by ThaDoctor99 on 2011-02-09
Yeah and guess what now my system froze (a bit of the reason I left gnome it froze to often.)
So I couldn't do anything so I had to do a hard reboot.
Well that resulted in me being back in the same mess.
Although alsa got lots of modules loaded now.

---

### Post by Krytarik on 2011-02-09
> **ThaDoctor99 said:**
> Yeah and guess what now my system froze (a bit of the reason I left gnome it froze to often.)
So I couldn't do anything so I had to do a hard reboot.
Well that resulted in me being back in the same mess.
Although alsa got lots of modules loaded now.
But you still have sound, or not?
Maybe we have to find some better drivers.

---

### Post by ThaDoctor99 on 2011-02-09
Yeah well sound went complete before there were no sound in my vlc and totem but it were in flash ! 
and in my command line music players...
That seems strange I would think video player were better at getting the sound than firefox (but firefox is a really large program so perhaps thats why...)


Well it went away again... Perhaps I should completely remove all the sound modules and load the same back that were used earlier ???

---

### Post by inobe on 2011-02-09
> **ThaDoctor99 said:**
> Yeah well sound went complete before there were no sound in my vlc and totem but it were in flash ! 
and in my command line music players...
That seems strange I would think video player were better at getting the sound than firefox (but firefox is a really large program so perhaps thats why...)


Well it went away again... Perhaps I should completely remove all the sound modules and load the same back that were used earlier ???

off topic your sig wreaks of spam, i would remove it or risk the inevitable!

---

### Post by Krytarik on 2011-02-09
> **ThaDoctor99 said:**
> 
Well it went away again... Perhaps I should completely remove all the sound modules and load the same back that were used earlier ???
Does it make a difference, if you load the mentioned module with /etc/modules or manually? Check with "lsmod" in both cases.

---

### Post by ThaDoctor99 on 2011-02-09
Well I did reload the library with the modprobe again.
I don't think it matters...
Well 
the problem is not that if I do an alsa force-reload it is just giving a lot of modules - and they were not they before the reboot.

---

### Post by ThaDoctor99 on 2011-02-09
my /etc/modules 
load
lp
rtc 
snd-hda-intel

---

### Post by Krytarik on 2011-02-09
So, I dug a bit into the driver section, try this backports package:
[http://packages.ubuntu.com/maverick-updates/linux-backports-modules-alsa-maverick-generic](http://packages.ubuntu.com/maverick-updates/linux-backports-modules-alsa-maverick-generic)

What is the behaviour right now?
- After a reboot, you have sound or not?
- When does it freeze, with the driver loaded after a reboot or with those after a manual modprobe?
- What is the Alsa script reporting in both cases?
- What kernels are currently installed? Is the behaviour with all the same?

EDIT: Seems, that there are no drivers at all in those package, check it.

EDIT 2: You could try those ppa:
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa)

---

### Post by ThaDoctor99 on 2011-02-10
Well when it froze before I modprobed the snd-hda-intel and started a video in vlc...
Started vlc and chose open file and then I searched and I think that were the freezing event. Did a hard reboot and got back in with no sound and a magnitude of different modules loaded which I did not have prior to the reboot.

So now I will try your driver.

---

### Post by ThaDoctor99 on 2011-02-10
Hmm this time I hope the sound stays on... Works in video player and herrie (since mocp won't start... I use this command line player) and probably also in firefox... :D So if it doesn't blow up again I am really thankful.

---

