---
title: "transset-df in fluxbox"
date: 2008-06-29
forum: Desktop Environments
---

### Post by mishathegoat on 2008-06-29
Hey everyone,
Would anyone happen to know how to get the fluxbox menu to be semi-transparent? And all the windows automatically? So far I've only seen examples that say I need to run transset-df from the terminal and select the window itself one-by-one.

---

### Post by johnalexrob on 2011-07-18
there are a couple of ways to change window alpha:

1: using transset-df -c ALPHA and replacing ALPHA with the alpha in decimal form and clicking the window. this will not remember the transparency.

2: right-click the window's decoration and under transparency change the focused window alpha. left-click to decrease and right-click to increase. then under the remember menu, select transparency. 

3: under the ~/.fluxbox/apps file, add an entry for each window you want transparent. I'm no expert on this file, just do it with method 2 a few times and study the apps file afterward. mine has an entry for xterm, it is-

```
[app] (name=xterm) (class=XTerm)
   [Alpha]              {171 101}
[end]
```171 is my focused alpha and 101 is my unfocused alpha. 

note that if configuration->transparency->force-pseudo-transparency in your fluxbox menu is checked, the window will lose transparency when it loses focus. the same goes for using transset-df.

the menu's alpha is changed with fluxbox->configuration->transparency->menu alpha. again, left-click to decrement the value and right-click to increment it. this has to have the force-pseudo-transparency option selected to work.

also, for the transparency to work, a compositor must be running. i use xcompmgr. add "xcompmgr &" into your ~/.fluxbox/startup file and transparency will work from startup. also, if you add the -c -f options to xcompmgr, the menu will be truly transparent (as opposed to pseudo transparent). I also found that it affected my conky and made it transparent too. also remember that it will slow down moving windows, so make sure your computer is fast enough to handle it, or it will annoy you.

I hope I could be of some help.

---

