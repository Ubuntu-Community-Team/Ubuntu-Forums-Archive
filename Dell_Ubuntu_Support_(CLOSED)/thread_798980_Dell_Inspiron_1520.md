---
title: "Dell Inspiron 1520"
date: 2008-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by marks_linux on 2008-05-18
Hi have now installed 8.04 on a Dell 1520. The experience has been good so far. Wireless worked out of hte box, Webcam, sound and even my vodafone 3G card work (after getting umtsmon).

all good except (see it coming?) video playback is pretty horrid in VLC and Media player once the vdeo is larger then the size of a playing card, stuttering playback and lipsync problems.

The graphics card is I believe Intel GM965. Any clues on how to get a little bit more out of my install? Running glxgears gives a framerate of 165.

Seem the whole desktop engine got a whole lot more complicated than it was in Dapper!

---

### Post by marks_linux on 2008-05-19
correction the graphics card is Intel GMA x3100

---

### Post by rikhell on 2008-05-19
> **marks_linux said:**
> correction the graphics card is Intel GMA x3100



video card has been blacklisted due to driver issues. This applies to some Radeon Mobility cards, Radeon rv350 and rv450 cards, and the Intel 965 (X3000, X3100).copy from a preveus reply

---

### Post by marks_linux on 2008-05-19
Does this apply to 8.04?

also removed Compiz and now glxgears is 275fps. no noticable improvement in movie playback though :(

I had better than 275 in glxgears about 4yrs ago :(

---

### Post by notwen on 2008-05-19
Please disregard the X3100 blacklisted comment as it is not blacklisted in Hardy Heron, only in Gutsy or earlier versions including Compiz-Fusion.  Which driver are you using?

This shouldn't resolve you problem, but have you by chance tried adding the Medibuntu repos?  Perhaps a missing media plugin may be hindering video playback?  Check [here]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f") fore more info about Medibuntu.

---

### Post by marks_linux on 2008-05-19
Good news re 8.04 I did check before installing and didn't find anything relating to x3100 for Hardy ;)

I installed the Medibuntu repos last night, but not made a difference which is a shame.

I manually added "intel" as a driver in xorg.conf

Does anyone has an xorg.conf they could post that is working with x3100?

cheers

---

