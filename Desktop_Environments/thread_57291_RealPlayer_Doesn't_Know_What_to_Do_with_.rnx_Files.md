---
title: "RealPlayer Doesn't Know What to Do with .rnx Files"
date: 2005-08-15
forum: Desktop Environments
---

### Post by palsyboy on 2005-08-15
I'm working on a friend's newly installed Kubuntu machine, and his sister wants to see, of all things, *Big Brother* live streams.  Anyway, I'm trying to get RealPlayer to use her subscriber login (or whatever she needs), and it has no idea what to do with an .rnx.  Kynaptic has nothing relating to an rnx extension.  I've also tried HelixPlayer, but it gives me the same error:
_________________________
Component Missing
The player does not have the capabilities to play back this content.
["Check for Updates..."] ["Details..."]
The following components are required:
rnx

URL:
file:///tmp/signin.rnx
_________________________

Any help would be appreciated.

---

### Post by matthew1 on 2005-09-18
NFL field pass is one item that has a signin.rnx form, that won't work with linux. I found a work-around, as follows:

1. Go to [https://account.real.com/login/](https://account.real.com/login/) and login there, via html form.

2. Two possible procedures:

2a-i: Click on "Guide" near the top
2a-ii: Click on "Sports at menu to left, it expands, then click on "NFL"
2a-iii: Choose your game to listen to, dialog box opens, choose to open with realplayer

2b: After step 1, just go directly to: [http://sports.guide.real.com/nfl](http://sports.guide.real.com/nfl) (I haven't tested this version, but it should work)

This doesn't actually help with the rnx form, but bypasses it.

---

