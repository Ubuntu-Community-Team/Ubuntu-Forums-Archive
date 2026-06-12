---
title: "Latest WINE update? (removed Esound?)"
date: 2007-04-18
forum: Gaming &amp; Leisure
---

### Post by willskills on 2007-04-18
Hi guys, 

It appears in the latest update of WINE, they have removed ESound support !!!

This is terrible - that was what was allowing me to get sound from WoW & vent at the same time. Doing everything through ALSA means my soundcard gets locked out after loading ventrilo. I used to just set the Input/Output to Esound in my Ventrilo settings, and everything worked great.......

So my question is; how do I downgrade WINE? I would need to check at home tonight, but I think I am using the WINE official repo, and I'm just not sure how to do that :)

Thanks for any help guys - and if anyone else is having sound troubles with games - get me in IRC - I have actually learnt a lot trying to sort out my game & voice comms problems! :D

---

### Post by willskills on 2007-04-18
Bump >_>

Sammy - where are you today? :D

---

### Post by Ferrat on 2007-04-18
WoW sound works flawless for me, just the same bug as allways with the grafic/audio connection but since my FPS is good I almoste never have that problem anymore. 

Vent for me has been a problem but that has been for a long time, worked in Dapper but never inte Edgy, altho I must admit I haven't really looked in to it =D

---

### Post by willskills on 2007-04-18
Well I can say that I did, a lot :)

I spent months reading all sorts of stuff and making changes, in the end, the thing that fixed it in Edgy for me, was enabling ESound in wincfg, as well as OSS, and then setting Ventrilo to use ESound for input/output.

I only got this working recently, and am now quite literally tearing my hair out - the latest WINE no longer has this support.

---

### Post by buttons on 2007-04-18
> **willskills said:**
> Well I can say that I did, a lot :)

I spent months reading all sorts of stuff and making changes, in the end, the thing that fixed it in Edgy for me, was enabling ESound in wincfg, as well as OSS, and then setting Ventrilo to use ESound for input/output.

I only got this working recently, and am now quite literally tearing my hair out - the latest WINE no longer has this support.

In synaptic, search for wine and select it.  Then go to Package->Force Version, and pick one.  Once you've applied (and thus downgraded), search for wine and select it again, this time going to Package->Lock Version.   If you want to upgrade it in the future you will have to unlock it, but in the meantime it won't nag you about having updated software.

---

### Post by willskills on 2007-04-18
> **buttons said:**
> In synaptic, search for wine and select it.  Then go to Package->Force Version, and pick one.  Once you've applied (and thus downgraded), search for wine and select it again, this time going to Package->Lock Version.   If you want to upgrade it in the future you will have to unlock it, but in the meantime it won't nag you about having updated software.

Utterly awesome mate - but I just read that elsewhere.

So much love for this community \o/

---

### Post by MurnShaw on 2007-04-18
Instead of doing that, you can just get an alsa-oss wrap at [http://packages.debian.org/unstable/sound/alsa-oss](http://packages.debian.org/unstable/sound/alsa-oss).

---

### Post by AndrewRiedi on 2007-04-18
Esound is not removed from wine, although it may not have been built properly.  There was a bunch of problems with the ubuntu 0.9.35 packages.  However, Arts was removed because it caused a bunch of bugs, and it is no longer developed.

---

### Post by Ferrat on 2007-04-18
I got Esound in wine 0.9.35? but then again I allways build my own from source

I've gotten vent 2.1.4 working (everything but me talking) and WoW sound and any other sound app I want running at the same time without problems, the mic could be a settings issue in linux haven't checked that yet but Im only using ALSA and OSS

---

### Post by willskills on 2007-04-19
Ok - well my mic works fine - guess I should try building the latest WINE from source, 'cause mine doesn't have ESound anymore ;)

---

### Post by chiefwhosm on 2007-04-19
If you read the latest Wine Issue off the winehq site you'll see that ESD isn't out yet, but someone was suggesting removing it because no one uses it, according to the info, someone then replied they used it :)

---

### Post by willskills on 2007-04-19
Yeah I saw that :)

Is there any way that we can make comments? I haven't had a chance to go back to an older version of WINE yet - but I wonder how many of the guys dev'ing WINE, actually play games & use voice comms with it.

I tried tinkering last night with the version I had installed, just before going to bed, and still only sound in Ventrilo, not WoW, using Alsa-oss for input/output/mixer in Ventrilo settings.

ARGH :D

---

### Post by chiefwhosm on 2007-04-19
I think the only way is to sign up to the mailing list and post your comments on it. 'Course then you get many wine emails :) A while back I was on it, because I'd been tinkering with gta3/vice city and had worked out a way (if someone coulda done it for me that is) to get the games videos/sound running properly. But since I mainly use windows, after several mailing list emails I decided to quit the mailing list so dunno if my questions ever got a reply :)

---

### Post by willskills on 2007-04-23
Just a quick note to say, I downgraded, and my WoW sound & vent work great.

People were saying ESD was not removed, yet when I update to 9.3.5 (I tried it from source too) and I still don't have EsounD in my winecfg audio tab! Very strange :)

Currently using 9.3.3 (I think, will need to check when I get home ^^)

---

