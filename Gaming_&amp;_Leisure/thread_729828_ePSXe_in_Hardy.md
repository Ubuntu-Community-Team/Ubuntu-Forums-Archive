---
title: "ePSXe in Hardy?"
date: 2008-03-20
forum: Gaming &amp; Leisure
---

### Post by falkTX on 2008-03-20
Hi guys from the best OS in the world, I have a question:
Will be ePSXe available for the new release of Ubuntu, Hardy?

I try to install the Gutsy version but it needs "libglib1.2" that is at confilct with "libglib1.2ldbl" (or something like that).
Well, I can't install it, and I really think it's better than PCSX.

Or if you can tell me where I can find more plugins for PCSX, it will be great.. and I'll forget about ePSXe

---

### Post by disturbedite on 2008-03-20
i'd say forget about pcsx & epsxe!  use pSX.  dfreer on this forum has a repo with pSX in it.

---

### Post by acoustibop on 2008-03-20
What he said.  You can get pSX [here]("http://psxemulator.gazaxian.com/"), or (and this is advised if you're on 64bit) dfreer's repository, linked in [this thread]("http://ubuntuforums.org/showthread.php?t=394097").

The only library you need in Gutsy is libgtkglext1 (in the repositories) and I think this is likely to stay the same in Hardy.  You'll also need a working 3D videocard and a working soundcard.  It's also easy to configure (no plugins - end of headaches!) - in fact, you can probably get by configuring your controller and nothing else.

It's in active development and likely to keep up with any changes - ePSXe and PCSX haven't been updated in more than 4 1/2 years, and are unlikely ever to be updated again - runs games far better than the older emulators and has superior compatibility.

No-brainer for me... ;)

---

### Post by cisforcojo on 2008-03-20
Awesome! I've been killing myself trying to get a controller working with ePSXe and it's just just just terrible. I'll let you know if I have success!

EDIT: This emulator is incredible! Controller works. MUCH faster than ePSXe. They did an amazing job.

---

### Post by acoustibop on 2008-03-21
Actually, it's not "they," cisforcojo, it's him. pSX Author is the sole developer of pSX Emulator. ;)

---

### Post by disturbedite on 2008-03-21
oh, and pSX's PS2 support is progressing...  yay

---

### Post by cisforcojo on 2008-03-22
That's incredible that it's only 1 guy. I threw out a 'thank you' not specifically for that post but I've been scanning the forums looking for help today and saw a lot of useful stuff from you, acoustibop. Thought one was finally due!

---

### Post by acoustibop on 2008-03-22
Thanks for that, cisforcojo, but I'm not sure I'm too happy about the Thanks system.  Certainly, there are people around the forum who are much more helpful than I am, but who don't get as much thanks as I do.

BTW pSX Author has been posting on the [official pSX forum]("http://psxemulator.proboards54.com/") quite a bit recently - largely around the work he's been doing on Playstation 2 emulation in pSX.  There's some way (and time) to go yet, but it's looking promising.  Hopefully, considering pSX' performance as opposed to other Playstation emulators, when he does get it done, it should be less resource intensive than the main Playstation 2 emulator ATM - which is a plugin-based one - PCSX2.  It'll still need a fairly high end machine, though, and will use hardware calls to the videocard,

---

### Post by falkTX on 2008-04-01
I know pSX.
But the problem is that I want the best graphics and sound, on 1280x800 res.
And I need plugins for PSX hacking, thing that pSX should not be able to do (never tried)

PCSX that's an alternative but configuring plugins never worked for me (it always crashed)

---

### Post by acoustibop on 2008-04-01
I have had ePSXe and PCSX running in Linux, but not for some time - AIR it was a lot more hassle than in Windows - not only do you need to plugins that work, and most of them don't seem to, but there are workarounds you need to put in place - to change from digital to analog mode controller, you have to start ePSXe with a different switch as well as different settings, so you can't change mode ingame, for instance, as you can in Windows.  ePSXe for Linux, TBH, seems to me to be a very half-hearted port.

OTOH, I'm running the beta for Hardy now, and I have to say pSX runs even more sweetly then in Gutsy.  I also take issue with the "best graphics and sound" idea: ePSXe's graphics are worse than pSX': they're just more impressive.  pSX is more accurate: one of the things that first won me over to pSX was the way it showed the games without artifacts and distortion - in fact, until I started using pSX, I thought that was the way some of the games must be.  As someone living in a PAL area, inevitably a lot of my games are NTSC-US ones (ones that were never released as PAL versions) so I could never play them on a Playstation and see how they should appear.

I guess it's a bit like hi-fi.  You get the people who prefer accurate sound reproduction, so that you hear depths in a good recording of a good performance that you never would otherwise, and can get immersed in the musicality of the performance, but rubbish sounds like rubbish, and then there's the people who prefer their music to be loud and impressive - so you never hear the details and musicality, but rubbish sounds really impressive.

Horses for courses, I guess...

---

### Post by mivo on 2008-04-01
The repository for PSX is down, by the way, but the guy posted packages for 32- and 64-bit Gutsy in [this post]("http://ubuntuforums.org/showpost.php?p=4340576&postcount=182").

---

### Post by acoustibop on 2008-04-01
Useful, mivo - of course, you can always download pSX from its [homepage]("http://psxemulator.gazaxian.com/").

---

### Post by wingnux on 2008-04-28
Yeah but I REALLY wanted to use ePSXe for all the shaders, hi-res and other options it offers =/

---

### Post by disturbedite on 2008-04-28
> **wingnux said:**
> Yeah but I REALLY wanted to use ePSXe for all the shaders, hi-res and other options it offers =/
pSX really is the best emulator in every category imo, except for all those extra features not related/emulated to/by the original playstation.  if you *do* want those extraneous features, (that many of us don't care about ;)), then yes, something like ePSXe is a better solution.

---

### Post by wingnux on 2008-04-28
mv "most" "some"

The ePSXe fan/user base is really huge ;)

---

### Post by acoustibop on 2008-04-28
Obviously.  Until pSX Emulator came along, ePSXe was what I had been using, quite happily, for 6 years or more.  I think ePSXe is an excellent emulator.  And, of course, in the 10 years or so (must be) it's been going, for much of which it was the undisputed Playstation emulation leader, it built up an enormous following.

pSX is only about 2 1/4 years old.  It already has a very large following, but 2 1/4 years in a contended arena is not like 10 years in a largely uncontended (except for the last couple of years or so) arena.  I wouldn't doubt, though, that pSX has a vastly greater following now than ePSXe did 2 - or 3 or 4 or 5 years after its inception.

I think that also, sadly, there's simply not as much interest in Playstation emulation as there was - everyone one wants the 'latest and greatest' now, and that has to be the Playstation 2 at least - not to mention the idiots who can't understand why there isn't a Playstation 3 emulator NOW...

pSX will be a contender in the Playstation 2 area, as this is something pSX Author is largely occupied with now, with some success - although this won't mean a cessation to pSX' Playstation emulation, as both will be done in the same emulator.

It's also possible, although this is not a primary focus ATM, that when pSX Author is finally satisfied with pSX' Playstation emulation capabilities, he'll consider adding graphic enhancement - I have to say though, that having experienced pSX' accuracy against ePSXe's enhancement, that that doesn't enthuse me an awful lot, unless, somehow, he can incorporate it without losing the accuracy (pretty much impossible by definition).

Come back in another few years, and I have no doubt pSX will have totally eclipsed ePSXe.  But that's speculation, no matter how likely it is.

---

### Post by mivo on 2008-04-29
> **acoustibop said:**
> I think that also, sadly, there's simply not as much interest in Playstation emulation as there was - everyone one wants the 'latest and greatest' now [...]

I started to use the PSP to run PSone games. The system had some of the best RPGs in video gaming history (many of which were never released as PAL versions -- but this is the wrong place to ramble about that, I guess ;)).

---

### Post by disturbedite on 2008-04-29
> **wingnux said:**
> mv "most" "some"

The ePSXe fan/user base is really huge ;)
so what.  so does pSX... i don't care, and no one else should, how big any particular emulator's fan base is.  it is a matter which emulator does it's job best.  those can be two different things.

---

### Post by acoustibop on 2008-04-29
> **mivo said:**
> I started to use the PSP to run PSone games. **The system had some of the best RPGs in video gaming history** (many of which were never released as PAL versions -- but this is the wrong place to ramble about that, I guess ;)).

Definitely agreed - but people don't want the new consoles for great games - they want them for impressive graphics and stunning effects... :(

---

### Post by wingnux on 2008-07-29
Does anyone know how to make pSX work with OSS4?

---

### Post by Sugi on 2008-07-30
I am sorry for this stupid post, but do I have any chance of running PSx emulator with my machine?

p4 1.8 ghz
Gig of DDR PC3200
Geforce fx 5200 256mb

Is it even worth trying to install it and all the libs require for the emulator?

Sugi

---

