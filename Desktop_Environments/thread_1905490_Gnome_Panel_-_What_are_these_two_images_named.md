---
title: "Gnome Panel - What are these two images named?"
date: 2012-01-07
forum: Desktop Environments
---

### Post by Scyntherei on 2012-01-07
Was customizing the look of my gnome panel, but can't for the life of me find these two images (Enlarged on either end of the picture). Anyone know where to find these 2 images?

---

### Post by Frogs Hair on 2012-01-07
That is the top panel in the Gnome Shell  and I don't see anything enlarged in the screen shot . The activities option doesn't  appear  in Unity .

---

### Post by Frogs Hair on 2012-01-07
The first screen-shot is the gnome shell and the second is unity .

---

### Post by Scyntherei on 2012-01-07
Hence why I said gnome and not unity. And the attachment thing seems to have shrunk my original image. anyways... looking for the two rounded corner things on either end of the panel.

v Different screenshot v

---

### Post by Frogs Hair on 2012-01-07
That is the shell theme , some are rounded and some are not . The default theme happens to be rounded . More  themes can be found here . [http://gnome-look.org/index.php?xcontentmode=191&PHPSESSID=2d05273f8e6cfd17f651e7f064044186](http://gnome-look.org/index.php?xcontentmode=191&PHPSESSID=2d05273f8e6cfd17f651e7f064044186)

---

### Post by Frogs Hair on 2012-01-07
I thought you were wondering why your panel didn't look like the one in the first screen shot and wasn't looking at the shell theme .


(Installing Downloaded Themes / Icons)

Install the Gnome Tweak Tool / Advanced Settings from the software center for making theme selections.  

(Single User) Create a .themes and .icons folder in home / hidden folders . Use Ctrl + H to open the hidden folder option in Nautilus .

(All Users) Use gksudo nautilus in the terminal to open the file system and navigate to / usr / share / themes or icons .

Download , extract the packages , and place the folders in either location making theme selections using Advanced Settings . Logout - in may be required .

---

### Post by nenadcvetkovic on 2012-03-06
Those are not images. Its CSS. If it's the default theme you are editing, look in /usr/share/gnome-shell/theme/gnome-shell.css and search for these lines:

.panel-corner {
    -panel-corner-radius: 10px;
    -panel-corner-background-color: black;
    -panel-corner-inner-border-width: 2px;
    -panel-corner-inner-border-color: transparent;
    -panel-corner-outer-border-width: 1px;
    -panel-corner-outer-border-color: #536272;
}

.panel-corner:active,
.panel-corner:overview,
.panel-corner:focus {
    -panel-corner-inner-border-color: rgba(255,255,255,0.8);
}

---

