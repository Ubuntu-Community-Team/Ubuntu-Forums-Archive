---
title: "no window buttons on 12.04, etc."
date: 2012-04-27
forum: Desktop Environments
---

### Post by cthom on 2012-04-27
i've checked ccsm and window decoration is checked and set to 'any'. still no buttons :(

(oddly, compiz is working fine (didn't expect that..) apart from photowheel not visible :/ )

and to push the boat out a bit more, how do i get emerald back???

---

### Post by zombifier25 on 2012-04-27
1. Try running
```
gtk-window-decorator --replace
```
in the terminal.
2. For getting Emerald to Precise, follow this tutorial:
[http://ubuntuforums.org/showthread.php?t=1870792](http://ubuntuforums.org/showthread.php?t=1870792)

---

### Post by cthom on 2012-04-27
bingo! sorted in a second :D

---

### Post by GeoffreyTransom on 2012-04-29
> **zombifier25 said:**
> 1. Try running
```
gtk-window-decorator --replace
```
in the terminal.


Didn't work here. Just had a cursor blinking at me without evr doing anything whatsoever. Tried sudo-ing it... same result.

I have one machine that upgraded faultlessly, and one where for the life of me I can't get the minimise/maximise/close buttons to appear. 

Config editor -> apps -> metacity -> general -> button_layout is set up properly (set to **:minimize,maximize,close** ), I've installed gnome-tweaks and it's set up properly... and I still have to right-click on the bottom bar to close ANYTING.

Back in the olden days, upgrading Ubuntu was much less of a pain in the *** than upgrading Windows. The last 4 ubuntu versions: not so much.

---

### Post by zombifier25 on 2012-04-30
> **GeoffreyTransom said:**
> Didn't work here. Just had a cursor blinking at me without evr doing anything whatsoever. Tried sudo-ing it... same result.

I have one machine that upgraded faultlessly, and one where for the life of me I can't get the minimise/maximise/close buttons to appear. 

Config editor -> apps -> metacity -> general -> button_layout is set up properly (set to **:minimize,maximize,close** ), I've installed gnome-tweaks and it's set up properly... and I still have to right-click on the bottom bar to close ANYTING.

Back in the olden days, upgrading Ubuntu was much less of a pain in the *** than upgrading Windows. The last 4 ubuntu versions: not so much.
Are you using Compiz?

---

### Post by dandaman96 on 2012-05-02
"compiz --replace" didn't do anything. 

"metacity --replace" brought back the window boarders as well as the max/min/close buttons.

Why does Ubuntu need to destroy my desktop of preference with every upgrade?  I've been a LONG time supporter, but I'm getting sick of this.

---

### Post by zombifier25 on 2012-05-02
If you do metacily --replace, you'll lose Compiz.

I think when you upgrade, your Compiz profile is messed up. Reset it (if you're using Unity):
```
unity --reset
```
If not:
```
gconftool --recursive-unset /apps/compiz-1
```

---

### Post by Michael Longval on 2013-02-01
Thanks zombifier25

```
unity --reset
```

fixed it for me ;)

Mike

---

