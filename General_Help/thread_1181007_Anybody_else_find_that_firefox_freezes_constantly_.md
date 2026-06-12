---
title: "Anybody else find that firefox freezes *constantly* in jaunty?"
date: 2009-06-07
forum: General Help
---

### Post by josephellengar on 2009-06-07
I just can't figure out what the problem is.  It even happens with no extensions or plugins installed.  I've had to go back to intrepid after several updates to jaunty because of this.  ](*,)  Does anybody know of a solution?

If needed: My machine is a 1gb RAM .8 ghz dual core  AMD Turion TL50 processor, gnome, Nvidia graphics.

---

### Post by jonobr on 2009-06-07
try using a different browser like seamonkey, opera and epiphany.

SHould be a snap to load via synaptic and it should indoicate if its a browser issue or other

Should have added [THIS thread]("http://ubuntuforums.org/showthread.php?t=1179472") which I recently saw and added to.
Others are noticing problems with FF

---

### Post by josephellengar on 2009-06-07
> **jonobr said:**
> try using a different browser like seamonkey, opera and epiphany.

SHould be a snap to load via synaptic and it should indoicate if its a browser issue or other

I feel like a total idiot.  LOL.  Thanks.

---

### Post by jonobr on 2009-06-07
no need yo feel like an idiot,
your being too hard on yourself.

---

### Post by oxf on 2009-06-07
> **idigchess said:**
> I feel like a total idiot. LOL. Thanks.
 
No you are not an idiot! OK if another browser works OK it might indicate its an issue with Firefox but...... FF is one of the most popular browsers and plenty of people use it just fine so it should be resolvable. Keep at it as I'm sure there are others who will benifit from the info as well!

---

### Post by Ceedub2 on 2009-06-07
You might try uninstalling it and reinstalling FF. Just an idea.

---

### Post by josephellengar on 2009-06-07
> **Ceedub2 said:**
> You might try uninstalling it and reinstalling FF. Just an idea.

I'll try, thanks.

---

### Post by josephellengar on 2009-06-07
> **oxf said:**
> No you are not an idiot! OK if another browser works OK it might indicate its an issue with Firefox but...... FF is one of the most popular browsers and plenty of people use it just fine so it should be resolvable. Keep at it as I'm sure there are others who will benifit from the info as well!

Yeah, I guess you're right.  Somebody else would have caught the problem if it were with firefox.  Could it be a problem with my hardware?  I think I listed it above.

---

### Post by nacho32 on 2009-06-07
I have this same problem 9.04 64 bit fire fox will freeze and cpu usages jumps to 100%, must force shutdown

---

### Post by benerivo on 2009-06-07
You could try a firefox build that is optimized for your system. Try swiftfox or swiftweasel, and this may solve your problem.

---

### Post by Mehashi on 2009-06-07
I have recently installed jaunty on three different machines, one single and two quad cores. Every single machine has had an issue with firefox. This is a shame as one of my friends can barely read his emails, and another cant go anywhere near youtube. I *love* firefox so this saddens me, and I have had to install different browsers for them. Whats even worse is that the bug affecting firefox also affects a couple of the other repository browsers so I havent managed to find a clean solution.

It seems that streaming is harder than it used to be! I am using firefox on my ubuntu machine at the moment and it is fine here, but trying to visit a youtube video earlier made the system lock up. The main problem now with firedox is that once I have used it for a while, when I close it it wont release the memory it was using.

I hope the guys find a stability solution as it was the functionality and stability that attracted me to FF in the first place! And I wouldnt want to give up the firebug web development plug-in!

---

### Post by rainwalker on 2009-06-07
Firefox doesn't freeze on me, but it pauses and becomes unresponsive a lot (usually when loading tabs). It's quite annoying and I've had this problem before, but it was back on Gutsy and I didn't really do anything to fix it (it eventually went away).

---

### Post by benerivo on 2009-06-07
> **Mehashi said:**
> ...The main problem now with firedox is that once I have used it for a while, when I close it it wont release the memory it was using...

Although this may not be a perfect answer, you can clear all memory usage with...```
sync

echo 1 > /proc/sys/vm/drop_caches

echo 2 > /proc/sys/vm/drop_caches

echo 3 > /proc/sys/vm/drop_caches
```

---

### Post by Mehashi on 2009-06-07
Thank you benerivo!

I will try this when I close firefox in a bit. Thank you for the solution!

I hope something is done about this as on a side note, at work IE7 is actually more consistent than Firefox which embarrasses the hell out of me as I have shown people how crap IE is and insist on using firefox for web-development!

I should have kept quiet! Thanks again for the fix [COLOR=Magenta](^_^)b[/COLOR]
__

---

### Post by Chronon on 2009-06-07
Microsoft's antagonistic stance toward web standards is still a good reason to avoid IE.

---

### Post by skipknyc on 2009-06-08
[FONT="Arial"]I hope this finds you well.

I, too, was experiencing "Firefox Interruptus" on a 32-bit machine of mine running 9.04 until I removed *firefox   3.0.10+nobinonly-Oubuntu0.9.04.1   meta package for the popular mozilla web browser* in Synaptic. This solution seems to be working pretty well, so far.

Best regards,
Skip[/FONT]

---

### Post by DeMus on 2009-06-08
Here Firefox does not freeze, does not crash, it is just slow. Some days ago I opened a thread in which the OP had a large screendump visible inside his post. Well, I do have a fast (20Mbit) internet line but the picture came in line by line by line by ....
I then installed Opera 10 beta and opened the same page with the same screendump. In a blink of an eye the picture was loaded and visible on screen. There has been a difference of 10 seconds at least.
How is this possible? I mean the people who create(d) Firefox are no dummies, they should be able to make a fast browser as well. Not only a fast one, a stable one to.
They simply have to otherwise it's over and done with Firefox. Then the big [COLOR="Blue"][SIZE="6"]e[/SIZE][/COLOR] will win again. This is unacceptable.

---

### Post by Michal77 on 2009-09-24
> **DeMus said:**
> Here Firefox does not freeze, does not crash, it is just slow. 

The same problem in Junty. No problem with Opera, Chrome or Seamonky just FF. Can't explain. :confused:
M.

---

