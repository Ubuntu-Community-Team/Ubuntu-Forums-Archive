---
title: "Unity in Ubuntu 13.04. Can't get desktop icons to turn off."
date: 2013-10-15
forum: Desktop Environments
---

### Post by pNzKE6H on 2013-10-15
Hey all, first post here on the forum. Well after some extensive trial and error, and googling my issue, I cannot get the three default desktop icons to go away

I have tried using dconf-editor, desktop icons are unchecked in there (under background), I cannot find any options in gconf-editor that will help me.

I have also installed Unity Tweak Tool and it says they are already turned off but they are still there... What's the deal :confused:
[IMG]https://dl-web.dropbox.com/get/dconf.png?w=AACsFfp8OmPD3oS2xQRrnmjfHTM90kimN_KiQk25SsDNnQ[/IMG]
[IMG]https://dl-web.dropbox.com/get/tweaktool.png?w=AADy_PlpwoFE0mBHOBJDvNsrKTFZQ_00XYE1aJZ4a4SPjA[/IMG]

---

### Post by deadflowr on 2013-10-15
I'm guessing you tried loading images, but I can't see them.
So I'll ask, what icons are stuck on the desktop?

Have you looked in the home folder, Desktop folder?
To see if you can remove them from there.

---

### Post by pNzKE6H on 2013-10-15
Well, its just the three that come with the install, Computer, home, and Trash. Right-clicking on them in any of those folder locations and on the desktop, send to trash is grayed out.. I mean theyre just shortcuts, so why is is such a big deal to just delete them?

---

### Post by deadflowr on 2013-10-15
Odd, since there shouldn't be any icons on the desktop(as opposed to the launcher on the leftside).
The only icon I ever have on my desktop is the install icon during a live session from the try ubuntu from the install cd.

You might a want to look into install [unsettings]("http://www.omgubuntu.co.uk/2012/11/unsettings-a-comprehensive-tweaking-tool-for-unity")

Though, in reality, a clear picture is worth a thousand words.

---

### Post by pNzKE6H on 2013-10-15
> **deadflowr said:**
> Odd, since there shouldn't be any icons on the desktop(as opposed to the launcher on the leftside).
The only icon I ever have on my desktop is the install icon during a live session from the try ubuntu from the install cd.

You might a want to look into install [unsettings]("http://www.omgubuntu.co.uk/2012/11/unsettings-a-comprehensive-tweaking-tool-for-unity")

Though, in reality, a clear picture is worth a thousand words.

Installed unsettings, crashes on open, so that route seems totally useless...
[ATTACH=CONFIG]246984[/ATTACH]

For your convenience, i attached a picture of what i had done first...

---

### Post by deadflowr on 2013-10-15
And you've tried resetting the defaults in unity-tweak-tool?
Worst case is the launchers would need to be re-added to the launcher.
And functions you made would need to be re-tweaked.

---

### Post by stinkeye on 2013-10-15
> **pNzKE6H said:**
> Installed unsettings, crashes on open, so that route seems totally useless...
[ATTACH=CONFIG]246984[/ATTACH]

For your convenience, i attached a picture of what i had done first...

Do you have nemo installed which may have taken over desktop handling from nautilus.
Check via terminal...
```
gsettings get org.nemo.desktop show-desktop-icons
```

---

### Post by pNzKE6H on 2013-10-16
> **stinkeye said:**
> Do you have nemo installed which may have taken over desktop handling from nautilus.
Check via terminal...
```
gsettings get org.nemo.desktop show-desktop-icons
```

So I ran this command and found that it was set to true, i tried setting it to false but it physically made the desktop area disappear entirely (no way to right click on desktop and wallpaper is not present)

What would I even do at this point?

---

### Post by stinkeye on 2013-10-16
> **pNzKE6H said:**
> So I ran this command and found that it was set to true, i tried setting it to false but it physically made the desktop area disappear entirely (no way to right click on desktop and wallpaper is not present)

What would I even do at this point?

Run....
```

gsettings set org.nemo.desktop show-desktop-icons false

gsettings reset org.gnome.desktop.background **show-desktop-icons**

dconf reset -f /org/gnome/nautilus/desktop/
```

You need to set **show-desktop-icons** with the gnome setting for the right click desktop menu.
In 13.04 by default nautilus will not display the desktop shortcuts, so the last dconf command sets that section back to default.

May need to kill nautilus...
```
nautilus -q
```
and then restart by simply opening your nautilus file browser.

Also check in startup applications you **don't** have a **nemo** entry and
**do** have a **Files** (or nautilus) entry with the command as **nautilus -n** .

No need to uninstall nemo.
I use it here as my default browser because it still has compact view.

---

