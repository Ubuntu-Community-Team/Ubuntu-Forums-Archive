---
title: "My Compiz Cube Is Flat"
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by rhyguy on 2008-02-25
when i click alt+ctrl+down, i get a flat pane, with a skybox instead of a cube like other people

i'm using gutsy gibbon, plus compiz manager (no updates yet)

---

### Post by overdrank on 2008-02-25
> **rhyguy said:**
> when i click alt+ctrl+down, i get a flat pane, with a skybox instead of a cube like other people

i'm using gutsy gibbon, plus compiz manager (no updates yet)

Hi you can use this command to install the manager
```
sudo apt-get install compizconfig-settings-manager
```
Then you can use Advance desktop manager it will be located under system,preference. Choose the general options , desktop size set the horizontal virtual size to 4. Also make sure the rotate cube box is checked.

---

### Post by DpNo1 on 2008-02-25
> **rhyguy said:**
> when i click alt+ctrl+down, i get a flat pane, with a skybox instead of a cube like other people

i'm using gutsy gibbon, plus compiz manager (no updates yet)

hi,

try pressing Ctrl + Atl + Left Mouse Button(hold down)

---

### Post by markbusu on 2008-02-25
I think you might have not configured the Horizontal desktops... Have a look at the following tutorial:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

---

### Post by fracturedmorals on 2008-02-25
Ctrl+alt+down is a feature... It is sort of like the expo plugin.

What you're looking for is either ctrl+alt+left(or right), which switches desktops on the cube...

-or-

You can middle click on the desktop, itself and be able to manually rotate the cube.

---

### Post by vishzilla on 2008-02-25
Probably you have two workspaces! Four workspaces is what is needed for a cube

---

### Post by DUDE_2000 on 2008-02-25
> **vishzilla said:**
> Probably you have two workspaces! Four workspaces is what is need for a cube

Probably, you do det a flat plane when you only have two (Ive tried)
or you have them arranged in two layers.

---

### Post by rhyguy on 2008-02-25
i have 4 workspaces
if i press ctrl+alt+right it rotates like a cube with no zoom out, and ctrl+alt+down makes it zoom out, and the cube unfolds and becomes flat

---

### Post by Achtung on 2008-02-25
You need the "Rotate cube" plugin installed and checked to manipulate the cube.

If you haven't done so already, install the compizconfig-settings-manager through synaptic or using the command line: ```
sudo apt-get install compizconfig-settings-manager
```
Then, click System/Preferences/Advanced desktop settings.
Check "Rotate cube" if it is not checked.
Open the "Rotate cube" dialog. In the "General" tab, move the "Zoom" slider (the last one) to something like "0.3000". 
Open the "Actions" tab. Click the black arrow next to "General" to see which key combo to push to activate the cube (the default is ctrl+alt+left click). Activate your zoomed out cube view by pressing this key & mouse click combo, and move your mouse around to manipulate the cube (you don't even have to close the compiz-config settings manager). Remember to keep your finger on the mouse button! Release the mouse button to zoom back to one of the desktops.

---

### Post by militem on 2008-03-03
I have success by hitting ctrl+alt and then clicking the left mouse button and holding it down.  This moves it into the 3D realm, and as long as I continue to hold the mouse button, it stays there and I can rotate it with the mouse.

---

### Post by bellwells on 2008-03-04
I'm able to rotate the cube by holding down the scroll wheel on my mouse.  The mouse cannot be over or on an open window, however; it has to be off to the side.  Otherwise, I use the Ctrl+Alt+LM (RM).

---

