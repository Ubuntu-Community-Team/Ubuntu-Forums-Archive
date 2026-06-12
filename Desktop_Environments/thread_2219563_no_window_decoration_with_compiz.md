---
title: "no window decoration with compiz"
date: 2014-04-24
forum: Desktop Environments
---

### Post by icu12345 on 2014-04-24
So I decided to try out the new Lubuntu 14.04 and so far it´s working out great. However, I do want to have a window manager that supports the ¨aero snap¨ feature... so I installed compiz just to use it as a window manager.

I have added compiz --replace to be executed every time upon startup but the window decoration option in ccsm just disappears. If I select it, window decoration works fine until next time I log in. How can I make the window decoration in ccsm permanently active?

Thanks!

---

### Post by deadflowr on 2014-04-24
I don't understand.
Do you have window decorations when compiz is enabled,(ie, windows have title bars and close,min,max buttons)
or it is when you click on window decorations, the option doesn't stick?

---

### Post by icu12345 on 2014-04-24
Well, when compiz is enabled I do not have window decorations (i.e. no title bars, no close, min, max buttons, etc.). Then I open up ccsm, put a tick next to window decoration and then it is all good... until next time I log in. Upon restart, logout/log in, etc. compiz starts and there are no window decorations. So again, I enable them in ccsm and it all works great until next time I restart.

So, is there a way to make window decorations permanently enabled?

---

### Post by icu12345 on 2014-04-25
anyone?

---

### Post by grumblebum2 on 2014-04-25
Instead of bloating Lubuntu with compiz just for aerosnap  you could achieve similar using wmctrl.
```
sudo apt-get install wmctrl
```

Check this command gives your screen width...
```
xdpyinfo | awk '/dimensions:/{print $2}' | cut -f 1 -d 'x'
```
eg for my res of 1680x1050
```
[COLOR="#008000"]glen@Trusty:~$[/COLOR] xdpyinfo | awk '/dimensions:/{print $2}' | cut -f 1 -d 'x'
1680
```

If that works, these two commands will tile a focused window left or right accordingly...
```
width=$(xdpyinfo | awk '/dimensions:/{print $2}' | cut -f 1 -d 'x') && half=$(($width/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$half,-1
```
```
width=$(xdpyinfo | awk '/dimensions:/{print $2}' | cut -f 1 -d 'x') && half=$(($width/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,$half,0,$half,-1
```

To bring out of the maximized_vert state...
```
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
```

I also use a command to resize and centre a window...
```
wmctrl -r :ACTIVE: -e **[COLOR="#FF0000"]0[/COLOR],[COLOR="#EE82EE"]450,260[/COLOR],[COLOR="#00FFFF"]860,560[/COLOR]**
```
A move and resize argument has the format '**[COLOR="#FF0000"]g[/COLOR],[COLOR="#EE82EE"]x,y[/COLOR],[COLOR="#00FFFF"]w,h[/COLOR]**'.The first value **[COLOR="#FF0000"]g[/COLOR]** is the gravity ...just leave as 0.
The four remaining values are a standard geometry specification: **[COLOR="#EE82EE"]x,y[/COLOR]** is the position of the top left corner of the window, and **[COLOR="#00FFFF"]w,h[/COLOR]** is the width and height of the window

If you want to bind the commands to keyboard shortcuts use **sh -c**
eg
```
sh -c "**width=$(xdpyinfo | awk '/dimensions:/{print $2}' | cut -f 1 -d 'x') && half=$(($width/2)) && wmctrl -r :ACTIVE: -b add,maximized_vert && wmctrl -r :ACTIVE: -e 0,0,0,$half,-1**"
```

I find the best way is to use mouse gestures with **easystroke**  because you focus the window as you do the gesture.

---

### Post by monkeybrain20122 on 2014-04-26
Since there is no gtk-window-decorator in lubuntu you need to either install it (not sure if possible) or get emerald.

---

### Post by icu12345 on 2014-04-26
> **grumblebum2 said:**
> ...

This is so cool!! Thanks for the tip ;)
I can use Easystroke also for a bunch of other useful stuff which is awesome

Is there a way to unsnap a window? So that the window returns to its original size and position. There is a workaround to maximize the window and then unmaximize it bur there must be a better way to do it...

---

### Post by grumblebum2 on 2014-04-26
When the window is tiled to half the screen I don't know how to return to original size and position because it's only toggling maximized_vert.
You could change the max/unmax command to only toggle  **maximized_vert** and then set the window to a certain [COLOR="#EE82EE"]**position**[/COLOR] and [COLOR="#00FFFF"]**size**[/COLOR].
Would only work for unmaximizing windows tiled left or right, not for a fully maximized window.
eg
```
wmctrl -r :ACTIVE: -b toggle,maximized_vert && wmctrl -r :ACTIVE: -e 0,[COLOR="#EE82EE"]**450,260**[/COLOR],[COLOR="#00FFFF"]**860,560**[/COLOR]
```
So you would use the original commands from the first post to tile left or right and then the above would return the window to a set size and position.

Tip for easystroke is to set the gesture button to 3....ie the right button.

---

