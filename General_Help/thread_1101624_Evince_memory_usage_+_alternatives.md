---
title: "Evince memory usage + alternatives"
date: 2009-03-20
forum: General Help
---

### Post by achilleas.k on 2009-03-20
I've noticed in other posts around the forum that other people have had high memory usage when using Evince. Most of these posts are mentioned as an off-topic point in their respective threads, which is why I'm making a new one.

I too have noticed how Evince seems to be a major memory hog and it is especially noticeable as soon I close the document I'm viewing and I see the memory usage chart (which I have permanently open on the top panel) drastically drop down.

Side info: I'm using Ubuntu 8.10, 64bit on a ZD8000 HP laptop (P4 3.4 GHz, 1 GB RAM, ATI Mob. Radeon X600 256 MB - FGLRX driver.)

I have several questions on the matter I would like to put out, not so much to be answered directly but mostly as a discussion so I can finally figure out if this behavior is some localized bad configurations or a general problem.

Do other people have similar problems with Evince?
Why does Evince require so much loading when scrolling?
Why does alternative software require so much less memory? (more on this down the line)

The first question I can't address directly.
On the second question however I'd like to say that I could understand for the loading of pages slowly and indeed I tolerate this behavior because I believe that loading a 1000 page document completely may be inefficient, if you're only reading say 2 pages. However other software does not behave this way (they scroll much smoother/faster) and indeed consume less memory from start to finish.

Now for the alternative software, I don't claim to have exhaustively tested the alternatives. My "benchmarking" (and I use the term very loosely) merely consisted of opening a few large documents for a few minutes and scrolling through them quickly, possibly jumping a few hundred pages ahead using the "goto" box.
Focusing on two of the alternatives (xpdf and FoxIt reader) I noticed that a) they scroll splendidly, no loading, no stuttering and b) they use much, much less memory from the start. I couldn't try Adobe Acrobat because (correct me if I'm wrong, please) they don't have a 64bit version yet.

More specifically:
- FoxIt reader is still a version 1.0 beta and was downloaded off their website. It starts off with around 15 MiB mem usage and slowly climbs to around 25 after scrolling for a few minutes, jumping to random pages. Document used was a 31 MiB, 1309-page book.
- XPDF: installed from the repositories, same document: starts with around 6.5 MiB usage, climbs to 25 after a few minutes of scrolling and "goto"-ing.
- Evince, same document, same procedure. Starts off at a WHOPPING 80 MiB. Scrolling through pages requires loading and after a few minutes climbs to 122 MiB!!!

Does Evince use some sort of cache that gets loaded with it and has been building up for the past few months I've been using it?
If it's not that or something similar, why is this happening? Is it a problem with the software or is there something wrong with my own installation?

The reason I'm posting all this here is because Evince is the default Ubuntu document viewer, so I'm guessing if there's a problem a lot of people would be affected.

---

