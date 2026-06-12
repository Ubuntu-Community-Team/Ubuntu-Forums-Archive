---
title: "pSX fmv weirdness"
date: 2007-12-21
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2007-12-21
I recently installed pSX 1.13, and the playing the game itself seems to have no problems. However, from what I've played so far, the FMVs tend to stutter along. Is there any way I can fix this? Or should I try to invest in another emulator? I'm running Feisty on a Dell M1210. Any help at all would be appreciated. Thanks!

---

### Post by TheIdiotThatIsMe on 2007-12-21
That's odd, I'm actually a big fan of pSX and haven't ever really noticed any stuttering. Do you mind if I ask a few questions?

1. What are your system specifications including video, processor, RAM, and sound card?

2. How did you install it (.deb file, binary, compiled).

3. Does it happen specifically on one game, or on all FMV sequences across the board?

4. When you say stutter, is it sound and video, or only sound?

---

### Post by acoustibop on 2007-12-21
I would presume this is a specific game, MEGAMANULTIMATE.  As TheIdiotThatIsMe says, pSX normally doesn't show behaviour like this, but with the enormous range of ways Playstation games were written, and the lack of proper documentation on the workings of the Playstation, there will always be games with compatibility problems.

So, if you want to post about problems with a game, it's essential to identify it properly: not just the name, but the version as well.  The best way to identify a Playstation game is its name and game ID: there'll be a different game ID for each CD, if it's a multi CD game.

Something that often helps is using the -r switch, but that's about the best I can offer without more information on your problem.

---

### Post by MEGAMANULTIMATE on 2007-12-21
I have an Intel processor @ 2.16 GHz, GeForce Go 7400 video card, Sigmatel STAC 9221 AI sound card. I installed pSX via Synaptic Package Manager. I've tried out three games, including FFIX, FFVII, and FFVIII (nerd, I know). So far, all FMVs have been weird in this regard, unless it applies only to multidisc franchises. When the FMVs stutter, it is both audio and video. It pauses for only a millisecond, much like a hiccup. 

It's weird, though. If I run FFVIII as an image file with my Logitech speakers, the FMV plays without trouble (Same as in FFVII). But in FFIX, the video is what drags, and the opening music is fine. 

If I'm not making sense, I understand. This is weirding me out.

---

### Post by disturbedite on 2007-12-21
there are some games that have this type of problem.  i can't remember which ones specifically, off the top of my head tho...so you're not alone.

---

### Post by acoustibop on 2007-12-21
pSX isn't in any of the Ubuntu repositories, MEGAMANULTIMATE.  It may be that you've added dfreer's repository to your list, but that's not a Ubuntu repository (although it's for Ubuntu users).  Is that what you mean, or are you confusing pSX with PCSX, which is in the Ubuntu repositories?

If it is pSX that you're using, try increasing the latency values on the sound tab.  Don't increase them more than you have to to fix the sound problems, as too much latency and your sound will lag and go out of sync with the game.

As for video stuttering, quite simply, on your setup, it shouldn't.  However, bear in mind that some of the games you're playing may be copy protected - I can't tell you if they are, because you haven't said which versions they are, as I asked.before.  All the Final Fantasy games should play fine if played properly.

If they are copy protected games and you're playing them from images, you'll have to rip them to formats that include the CD's subcode, i.e .ccd/.img/.sub or .mdf/.mds - both of which have to be ripped in Windows, as the only applications that rip to them are Windows only - they don't even run in Wine.

If you're playing them from the CDs, your optical drives have to be capable of reading the subcode properly - many drives don't.  As a rule of thumb, -RW drives are usually better than -ROM drives at reading subcode.

Until you give us more specific answers to our questions, that's about the best I can offer.

---

### Post by MEGAMANULTIMATE on 2007-12-21
IX and VII are retail discs I bought at a store, while VIII is a series of image files I downloaded from a site on the internet. Are those the questions you wanted answered?

---

### Post by TheIdiotThatIsMe on 2007-12-22
> **MEGAMANULTIMATE said:**
> IX and VII are retail discs I bought at a store, while VIII is a series of image files I downloaded from a site on the internet. Are those the questions you wanted answered?

FFIX is a rather.... interesting one of the series. When I bought the game, I found I could not play it on a regular old Playstation, as on one of the FMV's (the one with the airship entering the city) would stutter very bad, then completely freeze the game. However, it worked fine on any Playstation 2 with the extra power. It is very possible that it is simply the game, especially with VII and VIII acting fine.

---

### Post by acoustibop on 2007-12-22
MEGAMANULTIMATE: What versions are your games?  Different versions vary as to video standards, copy or mod protection issues and even sometimes the way the game is coded.  The solutions to your problems may vary considerably depending on your answers to these questions.  Also, TheIdiotThatIsMe's question about how you installed pSX is very relevant: the only thing we know is that, although you said you installed it "via Synaptic Package Manager," it's not in any of the Ubuntu repositories - so you need to qualify your answer at least.

> **MEGAMANULTIMATE said:**
> It's weird, though. If I run FFVIII as an image file with my Logitech speakers, the FMV plays without trouble (Same as in FFVII).

Sounds like there may be a problem with your soundcard.  It may just have a high inherent latency.  If that's the problem, as I said, try increasing the values for the latency sliders if you're using pSX, but not too much.  Final Fantasy VII should play without issues on your machine; most or all versions are not copy protected.

> But in FFIX, the video is what drags, and the opening music is fine.

This game does tend to run a little slowly on lower end machines.  On your specs it should be fine.  Since most versions of IX have some kind of disc protection, it may be a problem with your drive reading the CDs.  Are you running fullscreen or in a window?

> **MEGAMANULTIMATE said:**
> IX and VII are retail discs I bought at a store, while VIII is a series of image files I downloaded from a site on the internet. Are those the questions you wanted answered?

Many versions of IX are copy or mod protected; this means that if you play from CD, your drive needs to be able to read the subcode to defeat the disc protection.

Downloading games from the internet is illegal and you should not say this in any reputable forum.  However, you may have discovered another reason why downloading games is dumb: they're often carelessly ripped and, since Playstation games have non-standard disc structures, and are often copy or mod protected, they have to be carefully ripped.  It's not as if new, sealed copies of Final Fantasy VIII are hard to get or expensive: just look on ebay or amazon.

Your best bet is probably to rip your own games (after buying a good copy of Final Fantasy VIII), using something like CloneCD or Alcohol that rip to formats that include the subcode from the CDs.  This is necessary for Final Fantasy IX, which is protected for most versions, and for European (PAL) versions of Final Fantasy VIII, which are copy protected. Unfortunately, you'll have to do this in Windows, since there are no Linux applications that can rip protected CDs to formats that include subcode.  Ripping CDs and DVDs is the only reason I still keep a copy of Windows installed.  See the [pSX Official Forum ripping howtos]("http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1195746305").

Hard drive access to a properly ripped image is faster and seems more reliable than reading from a CD: nevertheless, pSX, although it generally performs better than the other, older Playstation emulators, is notably better than they are at reading from CDs, as long as the optical drive is adequate.

---

### Post by acoustibop on 2007-12-22
> **TheIdiotThatIsMe said:**
> FFIX is a rather.... interesting one of the series. When I bought the game, I found I could not play it on a regular old Playstation, as on one of the FMV's (the one with the airship entering the city) would stutter very bad, then completely freeze the game. However, it worked fine on any Playstation 2 with the extra power. It is very possible that it is simply the game, especially with VII and VIII acting fine.

Yes, Final Fantasy IX is one of the more graphics-intensive Playstation games; nevertheless, my PAL copy seems to play fine on my ancient Playstation.  It's possible the laser on yours is starting to get out of alignment.

It's one of the interesting things about pSX, that it sometimes does seem to run games faster than a Playstation does, although, unlike the enhancing emulators, it's supposed always to run games at the correct speed.  However, it's been established that this is, in fact, a problem with the Playstation rather than pSX: sometimes it can't run the game at the developer's intended speed, while pSX can.

---

### Post by MEGAMANULTIMATE on 2007-12-22
All right, thanks for the help. Sorry about the downloading thing. The last thing I'd want to do is undermine anybody's credibility.

---

