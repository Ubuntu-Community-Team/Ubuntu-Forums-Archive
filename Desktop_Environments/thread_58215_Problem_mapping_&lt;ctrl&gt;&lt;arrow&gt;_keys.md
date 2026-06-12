---
title: "Problem mapping &lt;ctrl&gt;&lt;arrow&gt; keys"
date: 2005-08-19
forum: Desktop Environments
---

### Post by nickles on 2005-08-19
1) **<ctrl><arrow> keys**
 
Using Kubuntu and a KDE konsole terminal, I would like to make the <ctrl><arrow> keys in bash work like the preconfigured <lalt><arrow> keys using readline's .inputrc.

However, although xev reports the <ctrl> key is being pressed, <ctrl><left> - as an example - would work exactly like <left> alone (<ctrl> suckers around?  :-|).

After a lot of attempts it seems to me, that XKB produces no distinctive keysym string (like "\C-\e[C") that I might use for such a mapping.

My xorg.conf shows (verified with setxkbmap):
   Driver = "kbd" ("keyboard" didn't work either)
   XkbModel = "pc105"
   XkbRules = "xorg"
   XkbLayout = "de"


2) **Annoying tilde behaviour**

I would like to get rid of being urged to press <space> after certain special characters (like tilde) in order to produce the latter (this is quite disturbing in vi where e.g. tilde bears a lot of functions).


3) **<esc> to clear line**

Is there an chance to map to <esc> the kill-line function (.inputrc, Emacs mode)?


thx

nickles

---

