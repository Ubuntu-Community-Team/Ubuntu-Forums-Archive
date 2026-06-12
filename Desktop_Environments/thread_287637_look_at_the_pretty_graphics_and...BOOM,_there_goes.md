---
title: "look at the pretty graphics and...BOOM, there goes my computer"
date: 2006-10-29
forum: Desktop Environments
---

### Post by nashattan on 2006-10-29
Ok, so like many others I was enjoying the wonderful 3D effects of beryl on the newly released Edgy Eft.  Ran into the standard problem with the menu bar flickering and never really worked that out, but that's not the issue here, sadly.  After playing with all the settings for a while and screwing up, I finally got comfortable with it.  I was changing the opaqueness and content of my top and bottom panels when it, for some reason, crashed.

Badly.

Now, when I try to load up the regular session I can see the panels but not click on anything in them.  I'm in the "Failsafe Gnome" session right now where the panels are simply not there.  Since all my easy access to applications have gone out the window (I don't have desktop shortcuts), I'm doing everything from the terminal.  Does anyone have any idea as to what the hell happened?  I've looked around and haven't seen any case similar to this before.

What information/screenshots do you need me to post?

---

### Post by phersotty on 2006-10-29
try restoring your /etc/X11/xorg.conf file.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by nashattan on 2006-10-29
Ok, restored xorg.conf and nothing happened.  Also, I just found out that when I run "gnome-panel" it pops up with this little error message:

"I've detected a panel already running, and will now exit."

Any ideas as to where that "other" panel is coming from?

---

### Post by metalsam on 2006-10-29
try:

```

sudo ps -A

```

and look at hte processes to see if gnome-panel is already there.

---

### Post by CatKiller on 2006-10-29
I was reading the other day how having the panels with any transparency at all was causing crashes with the driver they were using. I can't remember if that was with Beryl, or just using Metacity.

**killall gnome-panel** *should* get rid of your existing panel process.

---

### Post by nashattan on 2006-10-29
Ok, so when I ps -A there is a gnome-panel listed as running, but when I try to kill it with either killall or kill XXXX, the unresponsive panels go away, and then come right back half a second later.  I guess I need a way to edit the transparency option from the terminal?  Anyone know how to do that?

---

### Post by nashattan on 2006-10-29
Update: ok, so I launched beryl-manager and disabled the window decorator, killed the panel, and still nothing.  Then I added p:gnome-panel:100 to the window opacity settings, killall, still nothing.  So I think I need to just reset to a default panel somehow. Anyone know what file the panel changes are saved in?

---

### Post by CatKiller on 2006-10-29
> **nashattan said:**
> Anyone know what file the panel changes are saved in?

I **think** that if you run **gconf-editor** and navigate to the /apps/panel/toplevels/<*panel number>*/background/opacity key, you can change it to 65535 to have it fully opaque. This information is also included in an XML file somewhere in your Home folder if you end up having to do it from the command line.

---

### Post by nashattan on 2006-10-29
Well, changed the opacity, also changed the color back to #FFFFFF, but it still doesn't do anything but sit up at the top and look ugly.  What's weird is the bottom panel displays windows normally, but just doesn't do anything when I click on it.

---

### Post by CatKiller on 2006-10-29
There should be more than one entry to change - at least one for each panel. So you've changed the one at the top, but not at the bottom.

EDIT: It must be said, I really can't remember whether the people who were having the crashes were running Beryl/Compiz or not, and I don't know what failsafe Gnome turns off.

---

### Post by nashattan on 2006-10-29
No, I changed them both, but still nothing.  I did discover that when I do killall gnome-panel several times in a row it actually *stays* "dead".  Then, when I start it back up I get an error message: > Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -4 and height 24

Which makes me think that I somehow changed an object on the panel to have a negative width...though I don't know how I did it or how to fix it.

---

### Post by nashattan on 2006-10-29
*bump*

Surely someone must know what this error message means....

---

### Post by nashattan on 2006-10-29
So I managed to fix this by completely resetting the panel.  For anyone else that ever has this problem, or for anyone interested, I did ```
rm -r ~/.gconf/apps/panel
```
Then I restarted gnome.  Works fine now.

Thanks for your help, CK.

---

### Post by CatKiller on 2006-10-29
> **nashattan said:**
> Thanks for your help, CK.

No worries. And thanks for finding out which directory to remove to reset the panel. A few people have asked, so I'll remember that.

---

