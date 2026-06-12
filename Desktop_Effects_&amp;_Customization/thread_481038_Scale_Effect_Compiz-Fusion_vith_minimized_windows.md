---
title: "Scale Effect Compiz-Fusion vith minimized windows"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by Mr Greencastle on 2007-06-22
I can't, for the life of me, find out how to use the scale plugin to scale and unminimize all the windows.
It was possible in Beryl, is there a way to do this in Fusion yet?

---

### Post by avik on 2007-06-22
Unless I'm mistaken, the scale plugin is only used for the application switchers and the Exposé style application pickers.  I don't believe it's actually used to change the size of the actual windows.

---

### Post by Mr Greencastle on 2007-06-22
Oh, I guess I didn't state it very clear, sorry.

What I meant was: 

When I initiate the scale plugin, only the windows that aren't minimized to the task-bar are scaled. Whereas, In Beryl, there was an option to scale all windows, even if they were minimized to the task-bar. It would just temporarily unminimize them from the taskbar.

Is there anyway to do this in Fusion, if not is it scheduled to be included in the future?

The reason I ask is that I used to use the scale plugin instead of a taskbar, now I am forced otherwise.

Regards,
Mr Green

---

### Post by RAOF on 2007-06-22
No, you can't do this at the moment - windows are unmapped (ie: their pixmaps/textures are deleted, and they no longer redraw) on minimize, and the Beryl changes which allowed this to work were somewhat of a hack.

Like all good things compiz-related, this is waiting on input transformation/redirection support in Xorg.  Once that's available, windows will no-longer be unmapped, just (essentially) moved somewhere you can't see :).

Once that happens, this will work, and the switcher will be able to show thumbnails of minimized windows, etc.

---

### Post by Mr Greencastle on 2007-06-22
Thanks for letting me know!
Its not that big of a deal though, I'll stick with gnome's panels for now, as I can't figure out awn, or kiba (just want them to be launchers, not taskbars)

---

### Post by hyperair on 2007-06-27
Couldn't the scale plugin just put a huge icon of the window? Like how the switcher (Alt+Tab) handles minimized windows?

The same thing could be done for the ring switcher. I'm sure this would be a rather useful feature for the time being.

---

### Post by barrosz on 2007-06-30
> **hyperair said:**
> Couldn't the scale plugin just put a huge icon of the window? Like how the switcher (Alt+Tab) handles minimized windows?

The same thing could be done for the ring switcher. I'm sure this would be a rather useful feature for the time being.

+1

---

### Post by Girindor on 2008-02-25
I guess that would be a "me too". The scale function is such a cool utility, especially when made to activate by, for instance, moving the mouse to the top right corner of the screen etc.

Unfortunately since it does not detect minimized windows that really reduces its functionality...

I hope this gets fixed!

---

### Post by Ardrias on 2008-03-06
Toying around with this a for a bit, I can just say: I want it to work for minimized windows too! :popcorn:

---

### Post by flomar on 2008-03-09
hi,

i'm missing this plugin as well. Has anybody found a workaround to scale/expose all windows (even minimized)?

Flo

---

### Post by willywilly on 2008-03-10
[http://forum.compiz-fusion.org/showthread.php?t=119](http://forum.compiz-fusion.org/showthread.php?t=119)

They said that it will be available shortly. In Dec 2006.

---

### Post by flomar on 2008-03-10
> **willywilly said:**
> [http://forum.compiz-fusion.org/showthread.php?t=119](http://forum.compiz-fusion.org/showthread.php?t=119)

They said that it will be available shortly. In Dec 2006.

willywilly, thank you for the link! i posted there to get some updates on this topic.

Flo

---

### Post by ryanhaigh on 2008-03-12
I would love to see some progress on this, even if it is just using the windows icon as a workaround, probably with the window border to increase the 'clickable' area.

---

### Post by ryanhaigh on 2008-03-13
I have just been reading about how the new compositor in [gnome 2.22]("http://library.gnome.org/misc/release-notes/2.22/#sect:metacity") will have "live previews when switching windows with Alt+Tab" . Can someone tell me whether this works for minimized windows in this release? If they are not shown with live previews then how are they shown?

---

### Post by flomar on 2008-03-19
hi,

i think what you mean is something like this: [http://mylinux.suzansworld.com/wp-content/uploads/2008/03/metacity-composite.jpg](http://mylinux.suzansworld.com/wp-content/uploads/2008/03/metacity-composite.jpg)
that already works with compiz (icons when minimized).

flo

---

### Post by ryanhaigh on 2008-03-19
I know that compiz has live previews or icons when the window is minimized when using alt-tab but icons are not shown when using the scale plugin. Unfortunately that screenshot isn't clear on whether any of the windows shown in the alt-tab box are minimized or not, what I want to know is how the compositor in metacity handles minimized windows? If metacity is able to display the window preview in alt-tab when it is minimized then compiz scale should be able to. Alternately it may do what the compiz alt-tab switcher does and only show an icon for a minimized window. If this is the case then I would like this functionality in compiz scale.

---

### Post by mirwin77 on 2008-03-22
I just realized this functionality was missing (scale plugin not able to deal with minimized windows) and would definitely like to see this added.  Another vote from me.  I'll be keeping my eye on the progress and thanks to any developers working on this.

---

### Post by HunterK on 2008-03-22
+1 for even just an icon w/ the scale plug-in.

---

### Post by realn on 2008-03-25
+10 for me, too

---

### Post by ryanhaigh on 2008-04-08
Temporary solution for those unwilling to wait and who use screen edges for scale. You will need [brightside](apt://brightside) (as compiz doesn't allow multiple bindings) and [wmctrl](apt://wmctrl).

Save the following in a file somewhere (I put mine in ~/.showall.py) or download the attachment and save it somewhere. Then after installing brightside run the configuration app brightside-properties and set the screen edge you use for scale to custom command and entering the location of the file you saved.

```

#!/usr/bin/python

import os
import sys

windows = []
command = 'wmctrl -a '


#place items you don't want activated on scale in this list
#some of these can't actually be 'restored' but it saves time
blacklist = ['applet','Panel','panel','avant','awn']

#the output of wmctrl -l has the hostname in it between
#the random stuff at the start and the window titles, get
#the hostname of the computer
host = os.popen('hostname').readline().strip() + ' '

#for all windows in the output of wmctrl -l -x
for window in os.popen('wmctrl -l -x').readlines():
    
    #check if it is in the blacklist
    for item in blacklist:
        if str(window).find(item) >= 0:
            print 'Window: '+window+' contains '+item+' in blacklist'
            window = ''
    #if not in the blacklist append to list of windows to be activated
    if window:
        windows.append(window.split(host)[1].strip())

#activate all windows in the list using wmctrl
for window in windows:
    fullCommand = command+' "'+window+'"'
    os.system(fullCommand)
    
sys.exit(0)

```


You will also need to make sure the file is executable (right click>permissions>allow executing as a program) or chmod +x ~/.showall.py if you put it where I have.

As you will notice it takes a little while for all the windows to pop up but at least you have them all again, If you are having things popup that you don't want (for me it was the notes applet) you can add an entry to the blacklist based on the line of output of ```
wmctrl -l -x
``` which corresponds to the window you don't want to 'restore'.

---

### Post by ryanhaigh on 2008-04-30
Just a follow up, while this appears to be working well there is an issue if you pick your window to quickly, to avoid this you can have brightside close the application when you leave the corner but there is no guarantee that all windows will have been activated in this case.

---

### Post by ehabh on 2008-05-28
thank you for a wonderful hack. Hacks like this make me proud to be a linux user :)

---

### Post by marian99us on 2008-07-03
> **flomar said:**
> hi,

i'm missing this plugin as well. Has anybody found a workaround to scale/expose all windows (even minimized)?

Flo

well!! 
a workaround is up for taking actually! 
use a very easy key to rotate the cube (by easy i mean a one hand keyboard short cut (i would suggest alt+arrow keys)) and when ever you want to go to your desktop just switch over to a desktop that is not hogged with windows, so it practically means, if you can call the minimized windows into being [ :) ] then just don't minimize them, 
come to think of it, it is not a work around the problem, it is work around the for the solution! :>D
cheers!

---

### Post by hyperair on 2008-07-03
That's similar the workaround I've been using. However, that increases Xorg's memory usage, as well as the memory usage of your GPU. I've noticed that sometimes, you must minimize windows or videos won't play on a relatively old nVidia card. 

The workaround I'm using uses the mouse instead of the keyboard. I set it so that when I scroll on the edges, it'll rotate the cube. So a flick followed by a turn of the scroll wheel turns the cube for me.

---

### Post by Duranxl on 2008-07-22
so any news?

---

