---
title: "Methinks Gnome goofed up my Unity"
date: 2014-09-26
forum: Desktop Environments
---

### Post by vcell on 2014-09-26
I loaded Gnome Desktop to my wife's laptop. She didn't like it so continued to boot in Unity. However, suddenly Unity doesn't display the items on the desktop (she doesn't keep a clean-desktop) even though all the items are still in the Desktop folder. Also, right-click no longer works on the desktop.

I removed Gnome with the following:[INDENT]sudo apt-get remove gnome
sudo apt-get remove ubuntu-gnome-desktop
sudo apt-get remove gnome-shell
sudo apt-get remove gnome-tweak-tool[/INDENT]

While Unity is now the only desktop, the issue with the desktop items and right-click are not resolved. Any ideas?

---

### Post by deadflowr on 2014-09-26
What does
```
gsettings get org.gnome.desktop.background show-desktop-icons
```
show?
true or false
if false try
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```
see if that helps.

Alternatively, you can install the graphical frontend dconf-editor
```
sudo apt-get install dconf-tools
```
or search dconf editor in the software center.
then open the program and follow the path above org > gnome > desktop > background, then in the main window will be "show-desktop-icons"
clicking(maybe doubleclicking) on the line will allow you to enter in a new value. Or click on the reset to default button.
then close when done.
Again, see if that helps.

---

### Post by vcell on 2014-09-27
Thank you! *gsettings set org.gnome.desktop.background show-desktop-icons true* did the trick. I'm officially out of the dog house with the missus.

Sorry for the late response. After posting last night had to leave for a gig I played downtown. Great gig, and now my wife's laptop does what she wants. Oughta be a good weekend.

---

