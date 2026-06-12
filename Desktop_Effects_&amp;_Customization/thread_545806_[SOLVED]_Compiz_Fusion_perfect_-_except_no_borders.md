---
title: "[SOLVED] Compiz Fusion perfect - except no borders / titlebars"
date: 2007-09-08
forum: Desktop Effects &amp; Customization
---

### Post by bmdavis on 2007-09-08
Hi all,

      Thanks to all those who contribute. Really helpful and appreciate the feedback.

      AFter going through multiple tutorials, I've been able to install Ubuntu Feisty on my Dell Inspiron 6400 with an ATI x1400 card. Even my wireless, sound, and CompizFusion (compiz) are working well!  I have taken off Beryl and Emerald completely via the Synaptic Package Manager, and all is still ok... 

Except for the TitleBars. The title bars / window borders are missing.  I've searched for this in multiple threads, but can't find the solution.  Again, compiz works great, and I have tried enabling and disabling every time of window placement (i.e. smart).  Only can move windows through the Alt + Tab. 

Another important note. If I enter  "compiz --replace" I get a bunch of text and lose everything in compiz (i.e. the cube, ability to alt tab, and more).  Wish I could paste the errors I receive, but I just tried it and now I'm stuck in this window. Ha!

Thanks for the help.

---

### Post by bmdavis on 2007-09-08
Did compiz --replace again, allowed me to switch out and copy from my terminal the error:

There is already the  win manager running, you should use the --replace option to override it
~$ compiz --replace
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
GConf backend: There is an unsupported value at path /apps/compiz/plugins/water/allscreens/options/toggle_rain_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/water/allscreens/options/toggle_wiper_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/unfold_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path 
/apps/compiz/plugins/cube/allscreens/options/next_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/prev_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/rotate/allscreens/options/initiate_button. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


I think I edited the xorg.conf too much over the last few weeks, so I attached that for any of you as well. Perhaps it need some cleaning?  I would try the 24 / 16 switch, but I see too many repeats.

---

### Post by Mongo5000 on 2007-09-08
try putting this in compiz manager in the window decorations plugin.

in the code field put gtk-window-manager

---

### Post by bmdavis on 2007-09-08
PERFECT!!

Thank you thank you thank you!!

this has to be one of the fastest fixes anyone has posted that worked! ha!! :)

Many blessings to you....

Grateful,
     Brian

---

### Post by mikeize on 2007-09-18
This also solved a problem I had, but my cube still doesn't work!  I can ctrl+alt+left click and drag, and it rotates in 3d, but instead of a cube, it's like 2 sides (2 desktops).  I have 4 desktops enabled, and I can click between them in the desktop toolbar, but no cube.  What can I do?  

 compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: fusioncap.png
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: compizcap.png

I've read that the missing Xgl is no problem, since I've got nvidia, but I don't know how to fix this other stuff.

-mike

edit:  okay, I found the fix in another thread --it was to compiz settings>general options>desktop size  make horizontal size, and # of desktops both = 4.

But now my problem is that everytime I reboot or restart X, the 'window decoration' plugin/option is unchecked, which leaves me with no titlebar/resize/close etc.  I have to check it, then do emerald --replace.  How can I fix that?

---

### Post by TedGarvin on 2007-09-20
> **mikeize said:**
> 
But now my problem is that everytime I reboot or restart X, the 'window decoration' plugin/option is unchecked, which leaves me with no titlebar/resize/close etc.  I have to check it, then do emerald --replace.  How can I fix that?

I have the same problem.  I can't figure it out at all.  I'll be watching this thread with great interest.

---

### Post by Havek on 2007-09-20
I have  a similar problem, when compiz is running i have winow borders and everything else works but i can not move any windows and some pop up with half off the screen.  I tried putting in the window decorations plugin  gtk-window-manager.  Then when i try to run compiz it starts up but says 

```
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/compiz/default-cubecap.png 
```

and still will not let me move windows.

---

### Post by mikeize on 2007-09-21
I solved it...  with a reformat/reinstall!  I think I'm gonna go with beryl this time.

-mike

---

### Post by crb on 2007-09-22
Or, just enable the decorator plugin.

You can do this, and enable a good bunch more also, like so:

```
gconftool --set /apps/compiz/general/allscreens/options/active_plugins \
      --type list --list-type string \   
'[gconf,png,svg,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,place,switcher,screenshot,resize]'

```
Found [here]("http://bgoglin.livejournal.com/11253.html").

---

### Post by exchequer598 on 2007-10-21
> **crb said:**
> Or, just enable the decorator plugin.

You can do this, and enable a good bunch more also, like so:

```
gconftool --set /apps/compiz/general/allscreens/options/active_plugins \
      --type list --list-type string \   
'[gconf,png,svg,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,place,switcher,screenshot,resize]'

```
Found [here]("http://bgoglin.livejournal.com/11253.html").

I did the above, but got this error

```
Error: Parse error: Didn't understand ` ' (list must start with a '[')
prasannah@home:~$ '[gconf,png,svg,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,place,switcher,screenshot,resize]'
bash: [gconf,png,svg,decoration,wobbly,fade,minimize,cube,rotate,zoom,scale,move,place,switcher,screenshot,resize]: command not found

```

---

