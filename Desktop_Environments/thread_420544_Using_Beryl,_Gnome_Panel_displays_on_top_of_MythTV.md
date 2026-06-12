---
title: "Using Beryl, Gnome Panel displays on top of MythTV"
date: 2007-04-23
forum: Desktop Environments
---

### Post by sgfaulkner on 2007-04-23
I remember reading another post about this problem, but I couldn't seem to find it.  I am using Beryl and I would like to have mythtv running in one of the desktops.  The problem is that the gnome panels display over the top of the mythtv program no matter what I try and change.  Any idea how I could fix this?  I recall some people saying before that this was due to beryl

---

### Post by sowdog on 2007-06-18
I'm having this issue as well. I'd prefer not having to set the gnome panel to autohide but instead have mythtv display above gnomepanel or to hide gnomepanel when mythtv starts. Does anyone have a solution?

---

### Post by sander2 on 2007-07-06
i'm having the same issue too. did you find a solution?

---

### Post by alef13 on 2007-07-14
I'm having the same issue... I tried a lot of set ups but none worked.
When I start mythfrontend, gnome panels (top and bottom) stays on top of mythtv.

---

### Post by jd65pl on 2007-07-21
I also have this issue, the only solution I have found is to change the window manager to Kwin if i'm using kde or metacity if I'm using gnome in the beryl settings manager. I would be very interested in a better solution tho.

Thanks

J

---

### Post by smidgey on 2007-08-19
I have the same problem running compiz fusion. The road I have taken to fix it for now is to replace the mythfrontend command with a script that switches window managers before and after mythfrontend is run.

**Note: This is for a gnome/compiz system. should work pretty much identically for beryl, except you would replace "compiz" with "beryl" I guess.**

**Open up a terminal & rename the existing mythfrontend command**
```
sudo mv /usr/bin/mythfrontend /usr/bin/mythfrontend.2
```

**Create a new mythfrontend**
```
gksudo gedit /usr/bin/mythfrontend
```

**Copy/Paste this in**
```
metacity --replace &
/usr/bin/mythfrontend.2
compiz --replace &
```
**Then save and close gedit**

**Set executable permissions on the new command**
```
chmod a+x /usr/bin/mythfrontend
```

**Job's done.**

---

### Post by kah00na on 2007-08-25
This worked for me with a fresh install of Ubuntu (7.04).  Don't expect to be spinning the Compiz Desktop cube when you do it this way though.  After you exit mythTV, the compiz is turned back on so all is as it was before you started mythTV.

---

### Post by jurth on 2007-10-01
Hi

I solved the problem with enabling hiding of the panels via gconftool-2, and setting hide size to zero. And after quitting MythTV the settings are set back to normal. 
Here are the script, that hides two panels:

```
gconftool-2 --set "/apps/panel/toplevels/panel_1/auto_hide" --type boolean true
gconftool-2 --set "/apps/panel/toplevels/panel_0/auto_hide" --type boolean true

gconftool-2 --set /apps/panel/toplevels/panel_1/auto_hide_size --type integer 0
gconftool-2 --set /apps/panel/toplevels/panel_0/auto_hide_size --type integer 0

mythfrontend 

gconftool-2 --set "/apps/panel/toplevels/panel_0/auto_hide" --type boolean false
gconftool-2 --set "/apps/panel/toplevels/panel_1/auto_hide" --type boolean false

gconftool-2 --set /apps/panel/toplevels/panel_1/auto_hide_size --type integer 6
gconftool-2 --set /apps/panel/toplevels/panel_0/auto_hide_size --type integer 6
```


/Jonas

---

### Post by superm1 on 2007-10-13
There's actually a much cleaner way to get around this problem.

If you are using compiz fusion, the option is enabled by default, otherwise see the attached screenshot from CompizConfig Settings Manager.

The Legacy Fullscreen Support option works disables MythTV from being compiz accelerated.  This will also give better performance when watching videos.

---

### Post by sgfaulkner on 2007-10-19
superm, im actually running the latest build of compiz-fusion and I still have this problem when that option is enabled.  I don't really want to use a script to disable compiz, as I have mythtv runnin on a seperate project and I would like to still have compiz on my desktop

---

### Post by superm1 on 2007-10-19
> **sgfaulkner said:**
> superm, im actually running the latest build of compiz-fusion and I still have this problem when that option is enabled.  I don't really want to use a script to disable compiz, as I have mythtv runnin on a seperate project and I would like to still have compiz on my desktop
Did you try looking in the compizconfig settings manager for that setting?  Is it enabled?  (On gutsy for my fresh install it was)

---

### Post by sgfaulkner on 2007-10-19
Yep, it is checked.  I just tried messing with the GUI settings in myth and still couldn't get it to work.  Its interesting, im actually using mythtv on a second screen that doesn't have a gnome panel.  I can see why when I use it on my main screen the gnome panel might appear over it.  In this case mythtv is getting confused somehow and thinking a gnome panel exists on the second display when it actually doesn't

---

### Post by Lackofabox on 2008-02-16
I stumbled into this problem when I disabled "Workarounds" in the CompizConfig settings.    
Re-enabling Workarounds fixed it for me.
Who would have guessed that the Workarounds actually did anything?

---

### Post by Bjoeboo on 2008-05-18
> **jurth said:**
> Hi

I solved the problem with enabling hiding of the panels via gconftool-2, and setting hide size to zero. And after quitting MythTV the settings are set back to normal. 
Here are the script, that hides two panels:

```
gconftool-2 --set "/apps/panel/toplevels/panel_1/auto_hide" --type boolean true
gconftool-2 --set "/apps/panel/toplevels/panel_0/auto_hide" --type boolean true

gconftool-2 --set /apps/panel/toplevels/panel_1/auto_hide_size --type integer 0
gconftool-2 --set /apps/panel/toplevels/panel_0/auto_hide_size --type integer 0

mythfrontend 

gconftool-2 --set "/apps/panel/toplevels/panel_0/auto_hide" --type boolean false
gconftool-2 --set "/apps/panel/toplevels/panel_1/auto_hide" --type boolean false

gconftool-2 --set /apps/panel/toplevels/panel_1/auto_hide_size --type integer 6
gconftool-2 --set /apps/panel/toplevels/panel_0/auto_hide_size --type integer 6
```/Jonas


Where can I put that mythfrontend exit script so it unhides my panels upon quitting mythfrontend?   Those other methods mentioned  in this thread don't work for me in fedora.

---

