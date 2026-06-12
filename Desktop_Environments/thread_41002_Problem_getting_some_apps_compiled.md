---
title: "Problem getting some apps compiled"
date: 2005-06-11
forum: Desktop Environments
---

### Post by osorensen on 2005-06-11
Ive just installed Ubuntu and i have some problems getting some apps too work, like Xmms, Valknut etc

the problem is that when im building the apps ( configure) there is always something missing, heres an example : 

```

The glib-config script installed by GLIB could not be found
*** If GLIB was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GLIB_CONFIG environment variable to the
*** full path to glib-config.
configure: error: *** GLIB >= 1.2.2 not installed - please install first ***

```

when looking at the SPM its already installed  :roll: 

i guess i need to add some lines to the configure file but i have no idea were, anybody have an example ?

btw im loving this distro, one of the best ive seen :)

---

### Post by GrumpySmurf on 2005-06-11
Is there a particular reason why you're compiling applications instead of installing the packages via apt?

I know xmms can be installed via apt, though I've never heard of Valknut.  If you mean the DC program, there's a number of other apps for Direct Connect, such as dcgui (gtk based).

Generally speaking on a package-based distribution such as Ubuntu/Debian, Red Hat/Fedora Core, SuSE, Mandrake and the others, it is preferable to install the packages instead of compiling source.  This is a good habit to be in as it makes your system more managable, and keeps in the "spirit" of the distribution you're using.  Plus, on a distribution like Ubuntu that uses apt, all the dependencies are downloaded for you.

---

### Post by osorensen on 2005-06-11
ive been using a lot of Redhat before, never had any experience APT

any good guides i can read on using it ?  :)

---

### Post by Xian on 2005-06-11
[QUOTE=osorensen]ive been using a lot of Redhat before, never had any experience APT

any good guides i can read on using it ?  :)[/QUOTE]

Sure. Check out the [AptGet How-To](http://www.ubuntulinux.org/wiki/AptGetHowTo).

---

### Post by FLeiXiuS on 2005-06-11
[QUOTE=osorensen]ive been using a lot of Redhat before, never had any experience APT

any good guides i can read on using it ?  :)[/QUOTE]


man apt-get

teehee.

---

### Post by Xian on 2005-06-11
Oh, and it's easy to miss but don't overlook this line in that How-To:

"All these commands require sudo!"

 ;-)

---

### Post by angkor on 2005-06-11
Well, to be able to listen to some nice tunes while you discover the wonderful workings of apt do:

```
sudo apt-get install xmms
```

---

### Post by osorensen on 2005-06-11
Your awesome guys  :-P 

i actually figured out how to enable universe repository teehee :D so easy now rofl

---

### Post by osorensen on 2005-06-12
hmm i managed to get Xmms installed using universe repository the app load up fine but after i try play an mp3 it locks up and i have to kill the process  :roll: 

any idea whats wrong ? i would post a log if i could find it :D

EDIT : I changed some plugins and it doesnt lock up anymore, it plays CDs and MP3s but im missing the sound  :roll: guess thats kinda essential for listening to moosic hihi

any suggestions ? :)

---

### Post by angkor on 2005-06-12
Sometimes alsa is muted by default, open up a mixer and crank it up. Otherwise go to the Ubuntu guide and follow the guidelines about configuring sound to work properly on Hoary...

[http://www.ubuntuguide.org/#configuresoundproperly](http://www.ubuntuguide.org/#configuresoundproperly)

Good luck :)

---

### Post by osorensen on 2005-06-12
I did everything in that guide but didnt help, sound is working great on the rest of the system just not xmms  :roll:

---

### Post by Xian on 2005-06-12
You mean it won't play anything?
What output plugin are you using?

---

### Post by osorensen on 2005-06-12
I can add mp3s and audio cds to xmms and play them all fine but sound is missing

OUTPUT : ALSA 1.2.10

---

### Post by Xian on 2005-06-12
Try disabling the sound server and see if that helps on the next login.
From the main panel:

System > Preferences > Sound
Untick 'Enable Sound Server Startup'

---

### Post by FLeiXiuS on 2005-06-12
What soud card do you have, it's possible there isn't any modules for it.  
```
sudo lsmod |grep snd
```
Whats the output of that?

---

### Post by Xian on 2005-06-12
[QUOTE=FLeiXiuS]What soud card do you have, it's possible there isn't any modules for it.  
```
sudo lsmod |grep snd
```
Whats the output of that?[/QUOTE]
He noted that sound is working fine on the rest of the system.
Problem is only with XMMS.

---

### Post by osorensen on 2005-06-12
[QUOTE=FLeiXiuS]What soud card do you have, it's possible there isn't any modules for it.  
```
sudo lsmod |grep snd
```
Whats the output of that?[/QUOTE]

```

snd_intel8x0           29984  3
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  0
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  2 snd_pcm
snd                    50276  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9824  2 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

```


Well heres the output but like Xian said sound is working fine in all other apps, i can even listen to music by using the CD Player that included after install

sound is working in VLC both in videos and MP3s, so looks like some plugins are working on my system, just not with xmms  :roll:

---

### Post by Xian on 2005-06-12
If disabling the sound server made no difference, then open the XMMS preferences window again and make sure that you have MPEG Layer 1/2/3 Player plugin available and enabled.

---

### Post by osorensen on 2005-06-12
[QUOTE=Xian]If disabling the sound server made no difference, then open the XMMS preferences window again and make sure that you have MPEG Layer 1/2/3 Player plugin available and enabled.[/QUOTE]
 Its working :D

hmm i clicked off sound server and switched to eSound Output Plugin and it started workin :D

Thanks for all the help ;)

---

