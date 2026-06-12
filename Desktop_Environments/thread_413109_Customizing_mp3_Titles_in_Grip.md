---
title: "Customizing mp3 Titles in Grip"
date: 2007-04-18
forum: Desktop Environments
---

### Post by MichiganMan on 2007-04-18
Grip is a great program.  Thanks to the guide [here]("http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151") I've completely moved on from EAC in Wine.  But I still have two problems:

1.  Getting grip to properly title the mp3.  What I want is: "Track# - Song Title.mp3", or sometimes: "Band - Song Title.mp3"

Towards that end I've altered the standard Rip File Format command line to ~/mp3/%t/%n.wav, or: ~/mp3/%t/ - %n.wav or: ~/mp3/%t/ - /%n.wav  However, nothing seems to change the resulting outcome of: "Band  Title.mp3" for the resulting mp3.  Which leads me to my second problem.  

2. The resulting m3's ID3 tag all read: "Band / Title" in the Title section of the ID3 tag.  

I've been working on this for days.  What am I missing?

---

### Post by MetalMusicAddict on 2007-04-18
You shoulda just asked in my thread. :)

> **MichiganMan said:**
> Grip is a great program.  Thanks to the guide [here]("http://ubuntuforums.org/showthread.php?t=183125hp%3Ft=25151") I've completely moved on from EAC in Wine.  But I still have two problems:

1.  Getting grip to properly title the mp3.  What I want is: "Track# - Song Title.mp3", or sometimes: "Band - Song Title.mp3"

Towards that end I've altered the standard Rip File Format command line to ~/mp3/%t/%n.wav, or: ~/mp3/%t/ - %n.wav or: ~/mp3/%t/ - /%n.wav  However, nothing seems to change the resulting outcome of: "Band  Title.mp3" for the resulting mp3.  Which leads me to my second problem.  

2. The resulting m3's ID3 tag all read: "Band / Title" in the Title section of the ID3 tag.  

I've been working on this for days.  What am I missing?

But from your post above it looks like you need to edit the string in the "Encoder Command-line" field and not the "Encode file format" one.

Really the "Rip File Format" doesnt matter. Its the end result that does.

So to get: "Track - Song Title.mp3" for the filename "Encode file format" will look like **~/mp3/%A/%d/%t - %n.%x**

As for whats happening in your tags show me your string in your "Encoder Command-line" field.

---

### Post by MichiganMan on 2007-04-18
Huh, that worked, and I see why I didn't try it.  

I had given up on changing the Encode config because the %n did, and continues to produce both the Band and the Title together.  ie. Linkin Park  Forward instead of just the name of the track, as one would expect.  That threw me off the trail.  My subsequent attempt to separate the Band from the Title: ~mp3/%A/%d/%t/%n.%x produced a Directory for each track number which obviously wasn't what I was looking for.  This led me to believe that the Encode file format for some reason only specified the resulting file's directory.  Your command line put the track number and hyphen right where I wanted it, so I see now that the Encode line is the place I want to be.  I'm still confused on how to get the %n to only return the track title.  

As for the Ecoder command line, it probably looks familiar: -V 3 --vbr-new %w %m

Thank you for the assistance, and another thank you for the excellent guide I cited above.

---

### Post by MetalMusicAddict on 2007-04-18
Do you have "Add ID3 tags to encoded files" and "Add ID3v2 tags to encoded files" marked in Config->ID3?

The **~/mp3/%A/%d/%t - %n.%x** should get you **~/mp3/Linkin Park/Meteora/1 - Forward.mp3**.

**%n** gets you the TrackName. See [HERE]("http://nostatic.org/grip/doc/ar01s04.html#gripswitches").

---

### Post by MichiganMan on 2007-04-18
Ah Jimminy Crickets.  I got it. And its a dumb oversight on my part.  The crux of my confusion seemed to be that %n all by itself kicked out both the Band and Title in the mp3's title.  After you showed me that the Encode config was indeed the place to format the title (as I initially thought) it occured to me that the CD I was using might be the issue.  Sure enough, it seems that the freedb entry for the CD I was using, Linkin Park - Meteora, has the band's name in all the track titles.  So not surprisingly, that's what I got for %n, which, like I said, led me to look for SOME way I must have been coding the command lines wrong.  Another CD with a more accurate freedb entry produced exactly the expected outcome with ~mp3/%A/%d/%t - %n

sigh. So, thank you for getting me back on the right track.  :)

---

### Post by MetalMusicAddict on 2007-04-19
Good to hear it.

---

