---
title: "Empathy Sound Issues?"
date: 2009-06-22
forum: General Help
---

### Post by MrFairladyz on 2009-06-22
I have all sounds and notifications enabled to always go off (even when away/busy) in Empathy. There are no sounds coming from it at all. Any ideas on how to resolve this?

---

### Post by AreEK on 2009-06-22
Do you get any sound from your system at all?

---

### Post by MrFairladyz on 2009-06-23
yeah everything works just fine except for empathy

---

### Post by arindom on 2009-06-25
I am also not getting any sound notification from Empathy.

---

### Post by sergiom99 on 2009-08-07
Yes me too. Heres my config snapshot.
But i gues its all related to this: [http://live.gnome.org/Empathy/FAQ#head-abaca5d3b9aa0775c6c3f3588ddb064e5632228e](http://live.gnome.org/Empathy/FAQ#head-abaca5d3b9aa0775c6c3f3588ddb064e5632228e)

Any ideas?

---

### Post by jdackle on 2009-08-12
> **sergiom99 said:**
> Yes me too. Heres my config snapshot.
But i gues its all related to this: [http://live.gnome.org/Empathy/FAQ#head-abaca5d3b9aa0775c6c3f3588ddb064e5632228e](http://live.gnome.org/Empathy/FAQ#head-abaca5d3b9aa0775c6c3f3588ddb064e5632228e)

Any ideas?

The sound-theme they link to download from that FAQ-page is void of any sound-files actually! It also has an installer that does nothing...
Besides, I have no way to select a sound-theme from empathy's interface either.

Isn't there some package for say Debian that correctly installs just the sounds for events for empathy?
Or maybe a proper howto on where to get sound-themes from and HOW to correctly install them for empathy?

---

### Post by sergiom99 on 2009-08-12
There's a .deb package of it in [1].
It installed Ok, but there's no place to change the sounds of non-KDE apps in Kubuntu, so I couldnt try it.

[1] [https://launchpad.net/~cheleb/+archive/ppa](https://launchpad.net/~cheleb/+archive/ppa)

---

### Post by jdackle on 2009-08-16
> **sergiom99 said:**
> There's a .deb package of it in [1].
It installed Ok, but there's no place to change the sounds of non-KDE apps in Kubuntu, so I couldnt try it.

[1] [https://launchpad.net/~cheleb/+archive/ppa](https://launchpad.net/~cheleb/+archive/ppa)
Thanks a lot , sergiom99 ! :)

The sounds were correctly installed through the **sound-theme-freedesktop package**.
After that, I had to **go to the Panel-menu to System -> Preferences -> Sound and then to the Sounds tab and select the Default theme instead of Ubuntu**. So, the sound-theme change actually happens in the general desktop sounds, not just in empathy.

After that, empathy was issuing the sound events as expected.

Thanks ;)

---

### Post by frogotronic on 2010-02-08
This appears to be working for me as well.

---

### Post by haydemon on 2010-05-06
I tried it and I still cannot get sound notifications from Empathy. Running Lucid Lynx.

---

### Post by GilbertEvanG on 2010-05-06
I previously tried changing my sound theme to "default" and installing the sound-theme-freedesktop package on Lucid with no success.

I tried it again today, and miraculously it worked! I did a reboot this time, so maybe that made a difference.

---

### Post by ashwinipn on 2010-06-05
For me speaker works in empathy because when a call comes my speakers ring. However, when I try answering the call, I can't since although microphone shows the indicator activity, the caller can't hear me... I have not been able to figure this out yet. Empathy has very little setting options... So, I can't do much with it. All I can do is guess that it is probably using pulseaudio (my default) but microphone functionality may have some issues.... Any lead on this would be highly appreciated...

Ashwini

---

### Post by ckeller211 on 2010-06-09
I'm with ya ashwinipn.  I try to answer an incoming call and I get no sound and they cannot hear me either.  My microphone is status bar is moving too, but no sound.  Quite annoying as sound is recording and working in other programs.  Hopefully, someone has a fix.

---

### Post by zaidaus on 2010-10-11
I'm running 10.04. Using Empathy with SIP. I added my SIP providers details and was able to initiate a call. However, on the receiving end of my call, my voice was heard to be very choppy and distorted. I followed a hack given here [http://ubuntuforums.org/showthread.php?t=853276](http://ubuntuforums.org/showthread.php?t=853276) and did 'pkill pulse' after which the quality of my voice improved.

---

### Post by ashwinipn on 2010-10-12
Hi,
I agree with you on this.... Killing pulse has some desired effects... However some undesired too... such as sound server function to simultaneously playing sound in many different application. If an application directly accesses alsa or oss, it does not let other applications access them... Pulse was meant to serve that function... rather doing it OK... but some glitches as explanied coupled with lack of pulse support in various applications cause problems and a significant factor in lowering overall effect of ubuntu experience for many a adopters.

---

### Post by Iecur on 2010-12-12
> **ashwinipn said:**
> For me speaker works in empathy because when a call comes my speakers ring. However, when I try answering the call, I can't since although microphone shows the indicator activity, the caller can't hear me... I have not been able to figure this out yet. Empathy has very little setting options... So, I can't do much with it. All I can do is guess that it is probably using pulseaudio (my default) but microphone functionality may have some issues.... Any lead on this would be highly appreciated...

Ashwini

Hmm...I'm wondering if you tried that one tip I came about.  Not sure who or where I got it from might've realized it myself (last one is doubtful) but have you tried going to the _Sound Preferences_ window and going to the _Input_ tab and then checking on the _Connector_ and selecting something other than the default which for me was Microphone 1.  For some reason that didn't work but Microphone 2 did. There's only one on this computer as far as I know...

As for the Empathy problem all I can think of is make sure nothing is set to mute ?  The General Output volume and also Sound Preferences --> Sound Effects tab --> Alert volume and turning them both to max and having people IM you like crazy till it works.

---

### Post by buasaardk on 2011-01-26
I have the same problem as ashwinipn and ckeller211. When I make a call, there is no sound neither on my end nor on the other end. The sound bar moves but no sounds.

I thought it was a codec related problem, but I installed all codecs.

Actually only Ekiga works as SIP software, all the other (qutecom, twinke) have same problem. All other sound applications work perfectly.
Did anybody solve the problem in the meantime? Ekiga needs ages to startup, I would like to use Empathy.

Thank you in advance.

---

### Post by buasaardk on 2011-01-28
As I guessed it's a codec related problem for my voip provider which is Voipdiscount. In Qutecom I managed to get the program working setting the program to use GSM codec (I'm going to try the others), in Empathy it seems there is not a way to set a specific codec.

---

