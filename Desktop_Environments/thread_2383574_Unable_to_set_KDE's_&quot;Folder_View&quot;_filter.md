---
title: "Unable to set KDE's &quot;Folder View&quot; filter"
date: 2018-01-26
forum: Desktop Environments
---

### Post by accounts0 on 2018-01-26
As is detailed in the attached screenshot I set the filter dialog to hide files matching *Thumbs.* but its not happening. Unfortunately the screenshot tool doesn't catch the content of the expanded folder view list, but there are Thumbs.db & Thumbs.db.encryptable listed in there, as well as trash.desktop, which I'd also like to hide should I ever figure out how to make the filter work.

---

### Post by vasa1 on 2018-01-26
How do you get to Folder View Settings?

Also, what version of Plasma do you have? *plasmashell --version* should show that.

Edit: I found out how. One must first enable "Folder View" on the desktop. Then right-click on the desktop, etc.

I don't use Folder View at all. So no icons on my desktop.

---

### Post by accounts0 on 2018-01-26
> **vasa1 said:**
> How do you get to Folder View Settings?

Also, what version of Plasma do you have? *plasmashell --version* should show that.

[FONT=monospace][COLOR=#000000]$ plasmashell --version[/COLOR]
plasmashell 5.5.5

Right Click 'Folder View' widget's icon > Folder View Settings > Filter[/FONT]

---

### Post by vasa1 on 2018-01-27
Have you considered updating plasma, etc by adding the kubuntu-backports repository? The Plasma version in that is said to be a significant improvement over what was initially shipped. I installed it quite some time ago.

[https://www.kubuntuforums.net/showthread.php/72006-Latest-round-of-backports-PPA-updates-include-Plasma-5-10-2-for-Zesty-17-04?p=401636&viewfull=1#post401636](https://www.kubuntuforums.net/showthread.php/72006-Latest-round-of-backports-PPA-updates-include-Plasma-5-10-2-for-Zesty-17-04?p=401636&viewfull=1#post401636) 

Even though the title mentions Artful, the specific post has to do with Xenial.

---

### Post by accounts0 on 2018-01-27
> **vasa1 said:**
> Have you considered updating plasma, etc by adding the kubuntu-backports repository? The Plasma version in that is said to be a significant improvement over what was initially shipped. 

I'd consider that if it ends up that the problem I face is from it not working properly, rather than just me not setting it right. Even still I'm not sure I'd want to go through updating so much just to remove 3 entries in a menu that are mere annoyances. Thanks for the info however.

---

### Post by vasa1 on 2018-01-27
BTW, which program are you using to capture screenshots? Even though I'm using Kubuntu, I like gnome-screenshot better.```
Name=WholeScreen GSS
CommandURL=gnome-screenshot -p -f /home/vasa1/Dropbox/Screenshots/"GS$(date +%Y%m%d%H%M%S)".png
Key=Meta+Ctrl+W

Name=Active GSS
CommandURL=gnome-screenshot -wp -f /home/vasa1/Dropbox/Screenshots/"GS$(date +%Y%m%d%H%M%S)".png
Key=Meta+Ctrl+A

Name=Delayed GSS
CommandURL=gnome-screenshot -p -d 10 -f /home/vasa1/Dropbox/Screenshots/"GS$(date +%Y%m%d%H%M%S)".png
Key=Meta+Ctrl+D

Name=Interactive GSS
CommandURL=gnome-screenshot -a -f /home/vasa1/Dropbox/Screenshots/"GS$(date +%Y%m%d%H%M%S)".png
Key=Meta+Ctrl+I

```If you use the delayed option, you can initiate the screen capture while having ten seconds to open menus or dropdowns or whatever you want.

Then, you can use gwenview to crop the image to show just what you want so that the image is easily visible, keeping in mind the constraints imposed by the forum's size limitations.

---

### Post by accounts0 on 2018-01-27
> **vasa1 said:**
> BTW, which program are you using to capture screenshots?

Spectacle- & when I hit the Print Screen button on my keyboard, the menu is indeed active. For some reason it's ignored though.

Maybe I'll try another one day, not a priority at the moment.

---

### Post by accounts0 on 2018-01-27
Yea that didn't go well at all. Not in menu & crashes the display briefly when I run it at cli.
```

$ gnome-screenshot
** Message: Unable to use GNOME Shell's builtin screenshot interface, resorting to fallback X11.

```

---

### Post by vasa1 on 2018-01-27
> **accounts0 said:**
> Yea that didn't go well at all. Not in menu & crashes the display briefly when I run it at cli.
```

$ gnome-screenshot
** Message: Unable to use GNOME Shell's builtin screenshot interface, resorting to fallback X11.

```
I get that as well, but the screenshot _is_ captured. Did you check in the destination folder you set? And did you use the code I provided (modified to your needs)?

I don't run just *gnome-screenshot*.

Edit: if you want, try```
gnome-screenshot -i
```for *interactive*. You'll get a dialog windoe.

---

### Post by accounts0 on 2018-01-27
No, Spectacle just works, its rare I need that menu so whatever. Maybe one day when I'm up to spending more time on it. I just wanted to try it in case it was a quick fix. Oh, well.

---

### Post by accounts0 on 2018-01-27
As a workaround, I've added a "." to the names of the files I aim to not see. The "Trash" directory is still reachable via the Dolphin sidebar entry. The 2 "Thumbs.db" files weren't recreated upon selecting thumbnail view of a .jpg in the Desktop directory when viewed in Dolphin where thumbnail view was selected. Will see if it survives a reboot, or if anything else unexpected recreates un-hidden "Thumbs.db" files again.

---

