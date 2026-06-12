---
title: "Compiz bug when matching Window title"
date: 2010-03-20
forum: Desktop Environments
---

### Post by evan2645 on 2010-03-20
Hello all. I thought about filing a bug report but figured I'd see if anyone here has experienced similar issues first.

I have noticed that if you want to create window rules (or placement rules) in compiz for several different windows based on the window title, that compiz exhibits behavior more similar to grepping for the title value rather than looking for an exact match.

What I wanted to do was create several gnome-terminal sessions without decoration on the desktop. I created three different terminal profiles, each displaying a different window title, in order to get the placement right. The profiles were configured to have titles such as 'term_desktop1', 'term_desktop2', etc... Then, I would make window placement rules in compiz, placing each session at a different coordinate on the screen.

The issue I saw was that the first placement (and window size) rule was matched before any of the rest, even though the number at the end of the title was incrementing. So I ended up with several windows being placed at the same coordinate despite having specified those exact titles in other rules. This leads me to believe that the method which Compiz is using to match window titles is patternistic rather than absolute. Is this by design? Has anyone else had similar issues? Maybe I should be putting the window title in quotes? I've noticed that Compiz will also apply the window rules to any window with a title that includes the one given in the rule (i.e. when I open the window to edit the profile properties in gnome-terminal, Compiz will apply the window rules to that window even though the title is more like 'Edit term_desktop1 Profile' or something). TIA

PS>> I was able to work around this by naming the windows with the variable as a prefix, like 'first_term', 'second_term', and so on.

---

### Post by furball4 on 2012-12-21
I was going the exact same thing, for the same reason. Turns out Compiz uses regexes, so if you want exact matches you'd use title=^term_desktop1$ and so forth.

Details: [http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

---

