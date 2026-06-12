---
title: "Dell Optiplex GX Sound"
date: 2010-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wolfgangmcq on 2010-08-19
I have a Dell Optiplex GX which I got used. After scratching my head wondering why there wasn't any sound, I poked my head into the computer & found that there wasn't any speaker. There was, however, a port that looked like this on the motherboard:
 
[FONT=Courier New].[/FONT]
[FONT=Courier New]. EXT[/FONT]
[FONT=Courier New]. SPKR[/FONT]
[FONT=Courier New].[/FONT]
 
Four little wires sticking up, labelled EXT SPKR. So I went and got a speaker, then made the unpleasant discovery that the connector looked like this:
 
___
[FONT=Courier New]|_o_[COLOR=red]_o_[/COLOR][COLOR=black]|[/COLOR][/FONT]
 
[COLOR=black]*Two* connectors, not four! However, they were spaced the same as the ones on the circuit board. I fiddled around, but couldn't get the sound to work no matter how hard I tried.[/COLOR]
 
I have since surmised that the connector on the motherboard is an "analog audio" connector similar to that on the back of a CD player. If this is the case, then the connectors should be arranged like this:
 
[FONT=Courier New][COLOR=red].[/COLOR] [COLOR=lime]. .[/COLOR] [COLOR=blue].[/COLOR][/FONT]
[FONT=Courier New][COLOR=red]R[/COLOR] [COLOR=lime]GND[/COLOR] [COLOR=blue]L[/COLOR][/FONT]
 
[FONT=Courier New][COLOR=black]Anyone have any ideas on how to connect the speaker?[/COLOR][/FONT]

---

### Post by mörgæs on 2010-08-20
Just attach the left speaker to L and GND (=ground) and the right one to R and GND. 

Sometimes Alsamixer mutes the sound and /or sets the controls at minimum. Did you check this?

---

### Post by wolfgangmcq on 2010-09-02
I only have one speaker, which I want to put into the computer.
 
Yes, I did check for muting; my sound automatically mutes sometimes, I don't know why. However, this is *not* the problem.

---

### Post by wolfgangmcq on 2012-03-19
Problem solved--it was a different kind of speaker that I needed.

---

