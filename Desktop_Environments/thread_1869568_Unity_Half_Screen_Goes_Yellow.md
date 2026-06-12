---
title: "Unity Half Screen Goes Yellow"
date: 2011-10-25
forum: Desktop Environments
---

### Post by mamamia88 on 2011-10-25
What exactly can cause something like this?  Only real problem I have with unity after getting used to it

---

### Post by mcduck on 2011-10-26
Moving a window to the edge of the screen gives you that effect as an indicator for the feature that allows you to resize a window to use that half half your desktop (or maximize it if you drag it to the top of the desktop instead).

Were you actually moving a window (or still holding on to one after moving it) when you took the screenshot? In that case seeing the yellow box would be absolutely normal and working as designed.

In case you aren't actually moving any window that would of course be a sign of some problem...

---

### Post by mamamia88 on 2011-10-26
no that was long after any effect.

---

### Post by sebdevos on 2011-10-26
Same problem here after "installing" 11.10 version. Any ideas ??

---

### Post by mamamia88 on 2011-10-27
bump any options?  has anyone else reported same bug?

---

### Post by jakslev on 2011-10-28
I had the same thing happening to me. Here is the work-around:

1) Click the active window (for instance firefox) so that it returns to the standard size (non maximimized). 
2) Enjoy :)


Cheers, 

jakslev

---

### Post by mjuhasz on 2011-10-28
This is a regression that is scheduled to be fixed in unity 4.26. See the [bug report here]("https://bugs.launchpad.net/bugs/875557").

You can click on the workspace switcher to make the yellow artifact go away.

---

### Post by Monkey Boy on 2011-11-13
I have the same issue & often, I am running 11.01 64 bit, i5 760, 4gig ddr3, GTX 470.   Very cool OS, I am really enjoying ubuntu,  can't wait to see whats next :)   I also get an issue where it won't let me type something.  ahhh for FFing....   it keeps doing it all the time.

---

### Post by r_mano on 2011-11-15
Un-maximizing and maximizing the window also works to get rid of the artifact. Annoying, but I hope it will be fixed rapidly.

---

### Post by Monkey Boy on 2011-11-15
> **r_mano said:**
> Un-maximizing and maximizing the window also works to get rid of the artifact. Annoying, but I hope it will be fixed rapidly.

not for me :(  if I select the work space button it will go away for a little while then it comes back again.  After that it won't let me type on the screen. Its too bad cuz I could really use the work space feature.  It's too bad there was not more support for high end games,  it would be a great way for Ubuntu to make some money in the software center.  hmm maybe Texas Hold em,  :)

---

### Post by neopiper on 2011-12-08
Having the same problem here.  It happens when I switch between workspaces.

---

### Post by typhoon_tip on 2011-12-08
Bug was fixed in the grid plugin in Compiz, it is in the proposed rep now, should come to the final rep soon (I have installed and the bug goes away). To me, happened especially while switching workspace or resizing windows.

---

