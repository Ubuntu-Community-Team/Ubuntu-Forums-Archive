---
title: "Non-reordering &quot;alt-tab&quot; application switcher"
date: 2009-07-05
forum: Desktop Environments
---

### Post by tlgrok on 2009-07-05
Hello,

One thing I have never liked about MS Windows, Metacity and Compiz's [alt-tab application switchers]("http://en.wikipedia.org/wiki/Alt-Tab") is that they order application in a "most recently used" order. I would much rather have a static, not-constantly-reordered list. Is there a keyboard-driven application switcher which presents such a list for Gnome?

(Ideally, the order in which applications are presented should be that in which they are displayed in the gnome-panel "Window List" widget, but I'll settle for any arbitrary order.)

Much obliged,

tlgrok

---

### Post by ljubomirjosifovski on 2009-10-19
Have you found anything?

Does anyone know of a way to use keyboard left/riight/up/down or mouse when traversing the list?

thanks,

---

### Post by tlgrok on 2009-10-20
Not yet. I mostly gave up.

---

### Post by ljubomirjosifovski on 2009-10-20
Thanks, and excuse my igorance pls, newcomer to gnome here.

How do people with say 30-40 open windows switch between them using alt-tab? Presume noone is patient to press tab 20 times in a row to get to the right window?

---

### Post by tlgrok on 2009-10-20
I hear your plight. I have no perfect solution, but I can offer you these bits of advice:

[LIST]
[*]Use Compiz. Compiz offers alternative window switchers - most notably, [Scale]("http://wiki.compiz-fusion.org/Plugins/Scale").
[*]Use [multiple workspaces]("http://library.gnome.org/users/user-guide/stable/overview-workspaces.html.en") (desktops). I believe the default for Alt-Tab on Metacity (Gnome without Compiz) is to switch between windows only in the current workspace, and Compiz can be configured either way. You can also set shortcuts (such as "WinKey+1", "WinKey+2") to switch between different workspaces.
[*]Use in-program multiplexing. 20 windows sound like an awful lot. If you browse multiple websites, use [Firefox's tabs]("http://support.mozilla.com/en-US/kb/Tabbed+browsing"). If you have multiple terminal sessions open, use [Gnome Terminal's tabs]("http://library.gnome.org/users/gnome-terminal/stable/gnome-terminal-get-started.html.en#gnome-terminal-more-windows"), or, better yet, [[COLOR=black]GNU Screen[/COLOR]]("http://www.gnu.org/software/screen/").
[*]Use a different window manager. Before migrating to Ubuntu, being an Arch Linux, I used [ratpoison]("http://www.nongnu.org/ratpoison/"). This allows for [easy, keyboard-based window switching]("http://www.nongnu.org/ratpoison/doc/Manipulating-Windows.html#Manipulating%20Windows"). Note that ratpoison is very hardcore, and is only for the extremely dedicated. But you may like it all the same, or find some other WM to your liking. Note, however, that by switching window manager you'll lose a lot of Ubuntu and Gnome goodies.
[/LIST]
HTH.

---

### Post by ljubomirjosifovski on 2009-10-20
Thanks tlgrok, most helpful.

---

### Post by ljubomirjosifovski on 2009-10-21
> **tlgrok said:**
> 
I would much rather have a static, not-constantly-reordered list. Is there a keyboard-driven application switcher which presents such a list for Gnome?

(Ideally, the order in which applications are presented should be that in which they are displayed in the gnome-panel "Window List" widget, but I'll settle for any arbitrary order.)


Seems superswitcher ([http://code.google.com/p/superswitcher/](http://code.google.com/p/superswitcher/)) does exactly what you want? Quote:

"Super-Up and Super-Down cycles through all windows in the current workspace in a fixed order"

Was doubtuful the .deb provided will work oob (is from 2007), but it did, and seems I am a happy convert to superswitcher now.

cheers,

---

### Post by ivotron on 2010-06-03
In case someone else find it useful, I've modified superswitcher to have the Alt-k (or Alt-y) and Alt-j (or Alt-o) mapped to Super-Up and Super-Down (I'm used to use vim key-bindings everywhere I can).

I'm used to tabbed interfaces (Firefox, Thunderbird, Vim, Terminal, etc) and like to navigate through them with keyboard shortcuts (the ones mentioned above as you can presume), so it's more intuitive for me to see the contents of the taskbar as "tabs" of the current workspace.

Hence, I like to order the items contained in the alt-tab interface (the opened windows focus-list) by its taskbar ordering rather than in a "last-used" fashion.

If someone finds this useful, I can send the modified version of superswitcher

---

### Post by p_rynhart on 2010-06-16
Is there any way I can get an "OS X" style application switcher for Gnome, i.e. one that will only present one instance on an application (when there are multiple Windows of this application open).  I prefer the application centric model used by OS X (rather than the document centric one used by Windows and (apparently) Gnome).

---

### Post by avl555 on 2011-02-13
See:
[http://www.uzbl.org/wiki/metacity-tabs](http://www.uzbl.org/wiki/metacity-tabs)

Because I hadn't found it in the first place, and I didn't like it, I have written my own script:
```

#!/usr/bin/python

import sys, os

def getlist():
    windows = []
    for line in os.popen('wmctrl -l'):
        fields = line.split()[:2]
        if fields[1] == '-1': # panel? At least no real display
            continue
        windows.append(int(fields[0], 16))
    return windows

def currentwin():
    return int(os.popen('xdotool getactivewindow').read().strip())

if __name__ == '__main__':
    # don't use windows[0], that's the desktop (always?)
    windows = getlist()[1:]
    current = currentwin()
    print repr(windows)
    print repr(current)
    index   = windows.index(current)
    if len(sys.argv) != 2 or sys.argv[1] not in ['left', 'right']:
        print '''
browserswitch option
option:
    left:   move one to the left
    right:  move one to the right
    help:   this help message
'''
        exit()
    option = sys.argv[1]
    if option == 'left':
        newwin = windows[index-1]
    else:
        if index+1 == len(windows):
            # the rightmost window, switch to the leftmost window
            newwin = windows[0]
        else:
            # normal behaviour
            newwin = windows[index+1]
    os.system('wmctrl -ia %s' % hex(newwin))

```Copy the code, save it to a file called 'browserswitch.py' in your home directory (use gedit or the like, not OpenOffice.org Writer or so), add two shortcuts (System -> Preferences -> Shortkeys?) with command '/home/*username*/browserswitch.py left' and the same with right, with keys you like (for example, Ctrl+alt+PageUp and Ctrl+alt+PageDown) and enable the execution bit for that file (Right-click on the file -> Properties -> Rights -> Enable execute ? or `chmod +x browserswitch.py`).

Edit: this iterates over all windows, and the order is fixed, i.e. it is not changed when they are changed in the "Window list".

---

