---
title: "Window Maximizing when it touches the top bar"
date: 2017-10-25
forum: Desktop Environments
---

### Post by septantrionalis on 2017-10-25
I recently upgraded my install from 17.04 to 17.10.  Since then, whenever I move the window up so that it touches the top bar, the window maximizes.  Additionally, whenever the window touches the left side, it tiles to the left side and and tiles to the right when I touch the right side.  I desperately want to disable this feature.  I've read one solution to use ccsm and navigate to "Windows Management->grid->corners/edges" then set everything to "None".  I've done that and nothing happens.  In fact, I even tried disabling the "grid" option entirely and still nothing.

When I log in, I select the "Ubuntu" option for the windows manager.  I've also installed "GNOME" and selected that when logging in, but I get the same behavior.

Does anyone have any ideas on how I can disable this feature?

---

### Post by deadflowr on 2017-10-25
Ubuntu (the selection name at login) at the is now gnome-shell at login, so the old compiz methods will not work.
Try this
```
dconf write /org/gnome/mutter/edge-tiling false
```

EDIT:
also check to see if another settings is set as well, since it might override the mutter setting,
for that look at
```
dconf read /org/gnome/shell/overrides/edge-tiling
```
if false okay, if true try changing that to false as well.
```
dconf write /org/gnome/shell/overrides/edge-tiling false
```
I don't think it should matter though, it seems to be ineffective as long as the mutter setting is off.
(Or it is for me)

---

### Post by ajgreeny on 2017-10-25
Just out of interest I have tried this using dconf-editor on my system of 17.10 running as a VM in VBox as a wayland session, and nothing I do seems to stop that maximisation of windows when they are moved up to the top of the screen. Very annoying in my opinion.

I am sure there must be a way to do it but so far I have not managed to find it

---

### Post by septantrionalis on 2017-10-25
Agreed.  I find it very annoying.  I want to move a window out of my way real fast and end up maximizing it or resizing it instead.

deadflowr, you're a life saver!  You're suggestion worked.  

For the record :

"dconf write /org/gnome/mutter/edge-tiling false" didn't do anything.
"dconf read /org/gnome/shell/overrides/edge-tiling" returned nothing.
"dconf write /org/gnome/shell/overrides/edge-tiling false" made it work.

"dconf read /org/gnome/shell/overrides/edge-tiling" now returns false.

---

### Post by ajgreeny on 2017-10-25
I will try it using the cli as it appears that the GUI dconf-editor is not able to do the same thing for some reason.

---

### Post by ajgreeny on 2017-10-26
I have now tried the cli commands and still it does not stop this behaviour.

I usually use Xubuntu and it is much easier in that to stop this "snap" to top window edge in the settings of that, but perhaps this is a symptom of the removal of many gnome settings that seems to have happened lately.

I'll be interested to hear any other ideas anyone might have.

---

### Post by &amp;KyT$0P# on 2017-10-26
@ajgreeny: This worked for me -

1) Install [FONT=Courier New]dconf-editor[/FONT]

2) From the dock on the left, open dconf-editor

3) Go to org > gnome > mutter

4) set **edge-tiling** to OFF

5) It should work now.

I use "Ubuntu on Xorg" session, but this seems to remain effective under "Ubuntu" session.

---

### Post by ajgreeny on 2017-10-27
Halogen2, that is what I did at first but it did not work, as I mentioned in post #3, so I am a bit baffled.
I wonder if being a VM is having any bearing on my situation.

---

### Post by deadflowr on 2017-10-27
> I wonder if being a VM is having any bearing on my situation.

Now, you're running the wayland session in a vm. Okay.
What about an Xorg session?

Same result?

---

### Post by ajgreeny on 2017-10-27
Yes, it was same result whether on wayland or xorg.

However, I have just checked again in dconf-editor and found that the /org/gnome/mutter/edge-tiling was back to being on, so either I thought I had changed it and hadn't done so, or it changed back in some way.

Whatever, it is now working as I wanted and the edge tiling effect has gone, hopefully for ever.

---

