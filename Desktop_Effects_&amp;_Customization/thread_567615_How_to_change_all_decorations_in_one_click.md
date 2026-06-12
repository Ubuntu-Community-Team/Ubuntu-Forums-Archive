---
title: "How to change all decorations in one click?"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by VictorR on 2007-10-04
Does anybody know or have a script to change all themes at once?
It should include:
(GTK + Metacity + Icons) + Emerald theme + Mouse Cursors + Desktop background + Panel backgrounds + (optional) themes for customizable apps, like Cairo-clock, Firefox and Thunderbird, GKRellm etc.

Would be nice if there were a set of scripts with all the above components included, so one could call one of those scripts and change everything instantly.

---

### Post by Chymera on 2007-10-06
there is no way to do this in one click, phisically speaking, you would need at least a click to open the theme selector, another one to select the theme, and another one to close the selector, in addition to another 3-4 clicks for the instalation.

However, the most click-economic way of getting your ful fledged look is this: [http://gnomelook.org/content/show.php/H-K+suite+gtk2?content=57433](http://gnomelook.org/content/show.php/H-K+suite+gtk2?content=57433)

There may be other theme suites available as well, but i've only noticed this one and its blue counterpart

---

### Post by VictorR on 2007-10-06
Assuming that every GUI tool is a wrapper for one or more terminal commands, I just thought maybe someone could suggest how to change themes for already running programs. For example, I tried the following combination for gkrellm
killall gkrellm && gkrellm -t AnotherTheme &

but lack of general knowledge of bash commands and syntax caused that I failed so far.

After discovering all the commands we need they could be collected in the script files, each for a certain combination of themes (say black theme or OSX-like theme) and calling the appropriate script one could change its desktop look at once.

---

### Post by Chymera on 2007-10-06
Nope, as far as I know that has yet to be implemented.... however i can see how it would make customization-enthusiast's lives a lot easier.
But in order to be able to implement something like that, you have to have full features theme suites (ie. window decorations, gtk+, icon set, wallpaper, etc.). And that's what i just showed you.-...

---

