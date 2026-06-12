---
title: "OpenArena sound issues with .asoundrc"
date: 2009-03-22
forum: Gaming &amp; Leisure
---

### Post by racerraul on 2009-03-22
Here is my dilema...

I want my analog & digital outputs to work simultaneously.  So I got them to work with the .asoundrc file to look as follows.

> pcm.!default plug:both

pmc.both {
	pcm.analog {
        type hw
        card 0
        device 0
	}

	pcm.digital {
        type hw
        card 0
        device 1
	}
}


However, that kills the audio on OpenArena & Nexuiz.  In OpenArena, the error is that it was unable to init sound because PCM both is not defined.
Not sure what other does PCM need to be defined in other than .asoundrc. Banshee & Rhythmbox have no problems with my .asoundrc file with PCM both defined as you see above.



Now if I edit the .asoundrc file to look this way...

> pcm.!default {
	type hw
        card 0
        device 1
}

The sound in the games is OK, but I only get sound out of my digital output.

I could change the .asoundrc file accordingly, so that music plays in the game room & my office, and when I want to play games... but I want to have my cake & eat too.  

Any suggestions?

---

### Post by racerraul on 2009-03-22
I feel like I'm gettin no love here...

I swear I am here to stay, no more winders for me. someone help me or I will have to commit suicide and go back :lol:

---

### Post by racerraul on 2009-04-02
got it working...

I need to learn not to overlook the simple things.

---

