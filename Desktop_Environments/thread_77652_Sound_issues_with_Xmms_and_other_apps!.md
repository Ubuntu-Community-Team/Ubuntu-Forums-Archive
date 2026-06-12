---
title: "Sound issues with Xmms and other apps!"
date: 2005-10-17
forum: Desktop Environments
---

### Post by Pumpino on 2005-10-17
I had this trouble with Hoary and was hoping that it would be fixed, but alas, I'm having the same problem with Breezy.

When I'm playing MP3s in Xmms, sound for other programs like Thunderbird and aMSN doesn't work.  This is annoying, cause I want to be able to play music and have Thunderbird play a sound when new mail arrives.

Also, Xmms halts regularly, saying that sound is not available (or something or rather).  I have to go into it and change it from Alsa to OSS driver and back again to get it to play music again.  Xmms regularly locks up too, so I have to do a ps -aux and kill several instances of it manually.

Other people must be having this trouble too.  What's the solution?

---

### Post by Ulrik on 2005-10-17
Most likely your sound card does not support hardware mixing, so you have to use a software mixing daemon. The default for Ubuntu is ESD. So you basically just have to set output in XMMS to ESD rather than Alsa or OSS. That should do the trick.

---

### Post by Takis on 2005-10-17
[QUOTE=Ulrik]The default for Ubuntu is ESD. So you basically just have to set output in XMMS to ESD rather than Alsa or OSS.[/QUOTE]
While the default for Ubuntu is ESD, that's not the default for Kubuntu, which is artS. You can install xmms-arts, which tells XMMS to talk to artS, but this seems to be crashing at the moment.

---

### Post by Pumpino on 2005-10-17
Thanks.  I've installed xmms-arts, so I'll see how I go.

I did a search for ESD in Synaptic and couldn't find it.  Why is this?  Why is the default daemon different for Ubuntu and Kubuntu?

EDIT:  Arggg, it's crashed already!  "Please check your sound card is configured properly, you have the correct output plugin selected, no other program is blocking the sound card".  Why is this an issue?  Never had this trouble with SUSE or Kanotix. :(

---

### Post by Takis on 2005-10-17
[QUOTE=Pumpino]Arggg, it's crashed already![/QUOTE]
[QUOTE=Takis]You can install xmms-arts, which tells XMMS to talk to artS, but this seems to be crashing at the moment.[/QUOTE]
Till it's fixed, I recommend you use Amarok.

---

### Post by Pumpino on 2005-10-17
If it's an issue with sound output, why would using Aromak resolve the issue?  I'm happy to try Amorak if it fixes it, but I'm curious as to why. :)

---

### Post by Takis on 2005-10-17
I think the issue is with XMMS itself, most likely with the xmms-arts plugin. Since Amarok doesn't use this plugin, it appears to be working. Unfortunately I'm not too much of a fan of Amarok, and quite a fan of XMMS, but till it's fixed, what can we do...? :confused:

---

### Post by Pumpino on 2005-10-17
I could always use Totem. ;)

PS. When is downloading w32codecs going to be fixed?  I can't use Kaffeine because w32codecs can't be retrieved.

---

### Post by Pumpino on 2005-10-17
Tried Amarak.  "gst-engine claims it cannot play MP3 files".  Sheesh, you'd think the Kubuntu developers would get it right so that we could play MP3s in either Xmms or Amarak. *grumbles*

EDIT:  Downloaded the arts engine for Amarok.  Didn't work.  The Xine engine is finally working...

---

### Post by bluck on 2005-10-17
[QUOTE=Takis]While the default for Ubuntu is ESD, that's not the default for Kubuntu, which is artS. You can install xmms-arts, which tells XMMS to talk to artS, but this seems to be crashing at the moment.[/QUOTE]


in xmms prefs, ensure you are using eSound for audio output.  seems to work for  me.

---

### Post by Pumpino on 2005-10-18
eSound produces an error message on my machine.  You must be lucky. :)  Guess I'm stuck with Amarok or Totem for now. :(

---

### Post by Pumpino on 2005-10-18
I've just spent 30 mins test driving Amarok, and after tweaking its appearance, it's really not too bad.

Tick the box to make it look like Xmms in appearance, change the colour scheme to the Funky Monkey theme, select the reinhardt style, and get rid of the splash screen and tray icon, and it's a lot like Xmms with added features.  You can select lyrics in the context menu, and it displays the lyrics for each song that's being played.  Xmms won't do that.  With a bit of customising, Amarok is worth a decent try!

---

### Post by kingbanditjing on 2005-11-11
amarok has always given me problems, and i tried using it instead of xmms, but still experieneced various issues.  xmms is definitely still the best.

the problem has to do with programs locking alsa in order to use it.  i may be using the wrong terminology here, but a solution in previous releases was a modification to some conf file for alsa, lowering the release time on alsa so other programs could use it.

note this is not just with xmms, any alsa app will run into this issue.  one thing i question is, why is ESD the default?  as cool as ESD was back in the day (network transparency) it is not being actively developed.  surely there is a nice solution using alsa?  also, i recall a rumor that arts was being dropped even by KDE in the next major release, so that is also not the solution.

alright linux community, this problem should have been solved years ago when it first reared it's ugly head.  what is a REAL solution??

---

### Post by f1dave on 2005-11-11
Hello everyone.

All of the problems you describe can be attributed to the arts sound server. At the moment, there are critical bugs which people are working away very hard on in the breezy version of arts (or it could be the KDE Beta 3.5 version 2 that I mean too). I run breezy with that very version of kde, and I navigate my problems successfully like so:

*I let arts crash at startup. Thats ok, i realise that at some point it will be fixed and I can upgrade it.
*I run amarok with amarok-xine plugin for my listening pleasure.
*I like to play games- preferably good ones with sound. Enemy Territory works fine with sound as soon as i kill amarok.

Now, you can keep up with the issues concerning kubuntu and kde 3.5 at the following site:

[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems)

You'll notice people have loyally posted their bugs and bugfixes for problems with everything from arts to akregator. In the meantime, I would encourage those people in the Open Source community to 'pay' for their software. Instead of sitting here and saying "why havent the ubuntu people fixed it already?", remember that YOU, as a user, are an ubuntu person. You can submit bug reports. You can link to helpful sites like this. You can code, or test, or document. Everyone can pitch in and help out, and things will be improving before you know it.

---

### Post by beerorkid on 2005-11-15
from user ampersand:

Right click somewhere in the xmms main window, and go to properties, change the output to something else (usually ALSA) and try again.

from here [http://www.ubuntuforums.org/showthread.php?t=86588&highlight=correct+output+plugin+selected](http://www.ubuntuforums.org/showthread.php?t=86588&highlight=correct+output+plugin+selected)

worked for me.

---

