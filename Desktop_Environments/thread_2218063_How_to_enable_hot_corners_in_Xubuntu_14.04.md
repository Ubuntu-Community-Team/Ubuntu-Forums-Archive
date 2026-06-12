---
title: "How to enable hot corners in Xubuntu 14.04"
date: 2014-04-19
forum: Desktop Environments
---

### Post by geovino on 2014-04-19
I installed Xubuntu 14.04 and want to know how to enable hot corners in Xfce so I can use Windows Spread function. I have tried Compiz but it always breaks something. Is there a more stable program that can enable all windows spread by mousing to a corner of the screen?

---

### Post by Toz on 2014-04-19
[Brightside?]("http://packages.ubuntu.com/trusty/brightside") But it comes with some gnome dependencies.

---

### Post by tgalati4 on 2014-04-19
I think only gnome supports hot corners.  *Brightside* may work, but it may cause some interference with XFCE.

brightside - Add reactivity to the corners and edges of your GNOME desktop

---

### Post by grumblebum2 on 2014-04-20
I don't think any solution to enable hot corners will be of use if you don't have a
"Windows Spread function" in your window manager.
Don't know what else you would use besides compiz.

I find compiz fairly stable in ubuntu/unity but then again compiz
is now developed for unity by Canonical.

---

### Post by geovino on 2014-04-20
Isn't there any Windows Spread Function for Xfce?

---

### Post by grumblebum2 on 2014-04-20
You might find this thread helpful.
[https://forum.manjaro.org/index.php?topic=2664.0](https://forum.manjaro.org/index.php?topic=2664.0)
I do remember installing [**_[COLOR="#B22222"]skippy-xd[/COLOR]_**]("https://code.google.com/p/skippy-xd/") mentioned in the
thread but if i recall it was a bit buggy.
It seems to be still being developed so may be better.
There are instructions on installing from a ppa [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://www.webupd8.org/2013/07/skippy-xd-expose-like-window-picker-for.html")
There is no Trusty  deb  so i downloaded the Saucy deb from the ppa and it installed ok.
Going to test it in my flashback(Metacity) session.


What sort of problems do you have with compiz.
I think I have used compiz before in xfce.

---

### Post by geovino on 2014-04-20
Last time I installed Compiz on Xfce it crashed my video after reboot. I think compiz is too unstable for Xfce, or it doesn't like my old video card.

---

### Post by grumblebum2 on 2014-04-20
> **geovino said:**
> Last time I installed Compiz on Xfce it crashed my video after reboot. I think compiz is too unstable for Xfce, or it doesn't like my old video card.

What card and drivers do you use?
Have you ever ran Ubuntu/Unity with that card?

---

### Post by geovino on 2014-04-20
I have two 5 year old desktops that I test different distros on. One has ATI and the other Nvidia. I only use Nouveau driver these days because of the crashes from Nvidia drivers. I don't really know which desktop I was running it on. 

At this point its not that important. I have Ubuntu 14.04 on both and compiz works fine with Unity. Xfce is another situation. One day I'll find something that allows Xfce to do the handy windows spread function. I'll just use Ubuntu and elementary OS for that function until then.

Thanks for the help and advice. :)

---

### Post by grumblebum2 on 2014-04-20
*****Check post #6...you may have missed the edit.**
Well I tested with Metacity as the window manager and skippy-xd works ok.
I changed the setting in **~/.config/skippy-xd/skippy-xd.rc** to show alldesktops
and the windows on other desktops show as just an opaque blue.
You'll just have to test to see if it suits you.

For the screen edge you can use xdotool.
Set up a keyboard shortcut to run 
```
skippy-xd-fix
```

In my test I used **ctrl+alt+Super+w** so this xdotool command will activate
the shortcut keys when the mouse enters the top-right corner.
You will need to set this command at startup.
```
xdotool behave_screen_edge --delay 600 top-right key ctrl+alt+Super+w
```

An easier way would be to use easystroke to set a mouse gesture to run the **skippy-xd-fix** command
instead of using hot corners to trigger shortcut keys which then run the skippy-xd-fix command

---

