---
title: "&quot;Unknown application name&quot; shown on LibreOffice's Unity global menu"
date: 2018-05-12
forum: Desktop Environments
---

### Post by tomecorphic on 2018-05-12
Hi

Does anyone know an effective way to fix or workaround the &#8220;Unknown  application name&#8221; label on the LibreOffice (5.4 and 6.0) global menu in Unity? 
It  seems to be occurring since 16.10 and the only partially successful "solution" I  found is to launch the apps from the LibreOffice action center and open files from the inside. I even pointed the .desktop files to extra-simple bash scripts that start the Libreoffice action center and then the desired app, but it does not work in every case: for example, if I consecutively double-click more than one document. 
Therefore if I want to open two or three documents at the same time, I will have to launch two or three empty windows of the chosen suite app and open the documents from within, otherwise those actions will trigger the "Unknown application name" label which occupies space and as a consequence some menus will be hidden from the panel.

It's present in Snap and Flatpak too, but it does not happen in 16.04 and Ubuntu MATE  18.04 (mate-applet-appmenu).

 Bug report is here:
[https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/15892155]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/1589215")

---

### Post by mc4man on 2018-05-12
This should workaround the issue.
```
cp  /usr/share/applications/libreoffice-writer.desktop  ~/.local/share/applications/
```
Then open the copied .desktop in a text editor, ex. with gedit
```
gedit  ~/.local/share/applications/libreoffice-writer.desktop
```
scroll down to about line 219 & remove this line & space it occupied,  StartupWMClass=libreoffice-writer
save, try..

If it works see if any ill-effects of having that line removed, I've seen none.

edit: note that making this edit to the .desktop in /usr/share/applications location wil not work, it needs to be moved (copied) as shown..
Also if icon is pinned to launcher, remove, then add back after the above

---

### Post by tomecorphic on 2018-05-12
Thanks!
That's really a nice trick, ingenious! How did you get to it? [IMG]https://ubuntuforums.org/images/smilies/icon_cool.gif[/IMG]

I've been testing it: I had to delete the original .desktop entries in /usr/share/applications to avoid duplicates.
It seems to be working without side-effects; the only glitch I  encountered is that when you open the suite applications one after  another in parallel, their global menus may show the wrong app names and  windows can be erroneously grouped together, as a direct effect of the  StartupWMClass line deletion. But I guess that it's an edge-case...

I'll keep playing with it, but if I don't find negative effects this may be considered a fair compromise. [IMG]https://ubuntuforums.org/images/smilies/icon_wink.gif[/IMG]

EDIT: after a full reboot I realized I'd better put back original  unaltered .desktop files in /usr/share/applications because the icons  were missing and behaviour was awkward. Now the wrong appname glitch may  still occur but the windows grouping seems right.

---

### Post by mc4man on 2018-05-12
My use of libreoffice is basically just the writer & can't remember last time opening the main suite..
As far as the 'workaround', started with a barebones .desktop in .local/share/applications, it worked fine
Then kept adding actionable lines from orig. till it went bad.

As far as the orig. in /usr... I didn't bother to remove as same name .desktops in .local/.. always take precedence.
Why this works no clue & why the .desktop can't be in /usr for this to have effect no idea either..

Edit: Thought maybe name shouldn't be there (in global menu), but it's actually a menu item. Most apps don't do that..

---

### Post by tomecorphic on 2018-05-12
> **mc4man said:**
> Edit: the name really shouldn't be there at all, seems libreoffice is one of the few where something shows up. So real fix would be to see only menu items..

Exactly, it is erratic and so far Libreoffice is the only (buggy?) program that shows it... 
Anyway with the workaround I needed to *directly* drag the Dash shortcut onto the Unity launcher (not simply locking to it) to get rid of that awful menubar label. Launching it from terminal or keyboard shortcut does not seem to work.

EDIT: gtk-launch libreoffice-writer is fine.

---

### Post by mc4man on 2018-05-13
Probably from the convoluted way LO works, /usr/bin/libreoffice is a symlink to soffice which runs soffice.bin All the progs are just options, i.e. --writer , --calc, ect.
As far as WM_CLASS the windows 'declare' it anyway so not sure of the value of it being set in the .desktop..
(- see with xprop WM_CLASS > click on any open LO window
One could likely remove the line from all the .desktops in the LO family though they can't be in /usr/.. ( didn't try /usr/local/share/applications/

---

### Post by tomecorphic on 2018-05-13
Yes, I did xprop WM_CLASS just after the modifications and it was unaffected.
Removing the files from /usr/share/applications and rebooting will cause a mess, at first glance maybe they have to stay there for some reason...

---

### Post by Sigma1 on 2018-11-18
Just a pointer. mc4man's trick worked, but I also had to apply the same thing as root to /usr/share/applications/libreoffice-writer.desktop
That seems to have sorted the problem out for the present.

---

