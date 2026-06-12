---
title: "Default file manager is... Rhythmbox?!"
date: 2013-03-29
forum: Desktop Environments
---

### Post by Trippmeister on 2013-03-29
It's quite weird: under some circumstances, a folder tries to open in *Rhythmbox* instead of Nautilus. For example, if I download something in either Firefox or Chromium and choose "open containing folder", it tries to open the folder in Rhythmbox (which, obviously, does not work). Same happens if I try to open something in Gnome-Do.

Possibly useful information:
[LIST]
[*]Ubuntu 11.04 (Yeah, yeah, I know. Don't judge me!)
[*]Gnome 2.32.1
[*]Rhythmbox 0.13.3
[*]Nautilus 2.32.2.1
[/LIST]

Has anyone else seen this problem, or know how to fix it?

---

### Post by Frogs Hair on 2013-03-30
Right  click on the folder and select open with another application or open with and set nautilus default from the menu. In the case of a  media file they can be opened with a media player , but normally you have yo select this option from the context menu  if there is more than one application available to play the file.  I don't know why this would change by it's self .  I have not used Gnome Do only Synapse .

---

### Post by Trippmeister on 2013-03-30
Doesn't work. I've tried it (several times, because I keep forgetting that it didn't work the last time!) and for folders there's no option to set the default application.

I'm wondering whether there's maybe a setting in gconf that I can change to fix it - anyone know? I've searched for "default" and "preferred" but the former only turns up default settings for specific applications, while the latter turns up nothing at all.

---

### Post by Krytarik on 2013-03-30
From my earlier post on our blog here:

[http://www.tuxgarage.com/2012/03/folders-not-opened-with-file-manager.html](http://www.tuxgarage.com/2012/03/folders-not-opened-with-file-manager.html)
> This can be easily fixed by just removing any custom associations - whether intended or not! - for the MIME type "inode/directory" from the concerning configuration files.

In *any* version of Ubuntu, run this command:
```
sed -i '/inode\/directory/d' ~/.local/share/applications/mimeapps.list
```
In any version *prior to Natty 11.04*, additionally run this, just to be sure:
```
sed -i '/inode\/directory/d' ~/.local/share/applications/defaults.list
```
Regards.

---

