---
title: "Tweaking Nautilus' file sorting order?"
date: 2010-12-31
forum: Desktop Environments
---

### Post by milkmiruku on 2010-12-31
I've recently switched from Windows to Ubuntu and have a question regarding tweaking the character order Nautilus uses for alphabetical sorting. In my music/graphics/etc folder hierarchies, I have used a hyphen at the start as a 'hack' to 'sticky' some folders above the rest for quicker access. This worked fine in Windows, but Nautilus ignores a hyphen in it's sorting calculations. Is there anyway, simple or complex to replicate this behaviour in Nautilus? Thanks for any help!

---

### Post by coffeecat on 2010-12-31
That's an interesting one. All the non-alphabetic symbols I've used don't make a difference, but if you preface the folder name with a numeric character, it does get "stickied" before the others. However, a single number such as 0 or 1 doesn't stand out enough and is easily confused as part of the folder name, but you could use a number followed by two hyphens. Try:

0--nameoffolder

or

1--nameoffolder

You can still clearly read the folder name and you could have a hierarchy of "stickied" folders that way.

---

### Post by milkmiruku on 2011-01-04
hmm, at least that would work, ta for the idea. er, i know there's probably a way to script something to change all existing folders begining with "- " - could anyone give me a pointer as to what i should be looking at? at least if a better solution comes up, it shouldn't be too hard to revert the names back! :)

---

### Post by Krytarik on 2011-01-04
I use pyRenamer for this sort of tasks, it has a GUI. There may be some command line tools, which can also do this.

Thanks for the tip with the numbers, coffeecat. I have the same setup as milkmiruku, initially set up in Windows a few years ago, overlooking this issue in Linux until now.

---

### Post by Serguey Basalaev on 2011-03-07
In Nautilus you can also add emblems to important folders and set Sort by Emblem

---

