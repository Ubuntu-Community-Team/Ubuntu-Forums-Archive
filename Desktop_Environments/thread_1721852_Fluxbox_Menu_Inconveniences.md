---
title: "Fluxbox Menu Inconveniences"
date: 2011-04-05
forum: Desktop Environments
---

### Post by EMABrad on 2011-04-05
I've got Fluxbox running on my Maverick machine, and, while I love it, there are just a few pet peeves of mine, as it stands right now, one of the most annoying of which are the fact that, as far as I know, I have to choose between two things that I love, but can't have both.

My problem is as follows: I semi-regularly add software (like LyX, as of today) to my machine, and obviously want this software to show up in its destined place in my (mostly default-formatted) Fluxbox menu.  This is all fine and dandy, but my problem lies in the fact that I also want to be able to add entries manually for things that are not automatically detected as software, like Folding@Home and Minecraft, but my current configuration prohibits me from being able to do both, because if I were to use the default file, then my customizations are overwritten, but if I copy the file and use the copy instead, the copy obviously isn't updated.

Any solutions?

---

### Post by kerry_s on 2011-04-05
read the manual, it can be done. the fastest way would probably be to google a sample menu.

---

### Post by EMABrad on 2011-04-06
The manual is not useful for this issue.  How can I make Fluxbox automatically generate new entries within a new menu framework that I create?  Is that even possible?

---

### Post by kerry_s on 2011-04-06
look here:
[http://old.fluxbox.org/docbook/en/html/x756.html](http://old.fluxbox.org/docbook/en/html/x756.html)

the " [include] (path/to/menu) " is the 1, you'll need a entry for the stock menu & 1 for your personal menu.

example:

[begin] (fluxbox)
[include] (/usr/share/fluxbox/menu) **"i'm not sure where it is now, check path"**
[include] (/path/to/my/menu)
[end]

---

### Post by EMABrad on 2011-04-06
Hmmm... I see.  So while I cannot have Fluxbox automatically update its menu within the framework that I give it, I can provide a second menu within which its default, automatically updated menu is nested.  Unfortunately, this seems to limit the amount of customization I have over the menu, should I choose to take this route.  Based on the research I have done, and based on your aid, it seems as though, given the current framework Fluxbox implements, I am not able to perfectly implement what I want.  I can get quite close, though.  Is this correct?

---

