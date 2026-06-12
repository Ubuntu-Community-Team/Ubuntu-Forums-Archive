---
title: "XFCE desktop icons huge and no wallpaper"
date: 2015-06-25
forum: Desktop Environments
---

### Post by chinleybrewer on 2015-06-25
Recently, I've noticed my desktop icons have frequently been rearranged - it's been rather annoying but I ignored it.

Now for some unknown reason my wallpaper is missing and my icons are really large and do not all fit on the screen - the ones that do not fit are bunched across the right hand side of the screen.  I'm assuming this has something to do with a recent update because it's been fine for years before this.

I've checked in the desktop preferences and tried changing wallpaper to no effect.  I've also tried changing icon size to no effect.

I have xubuntu 14.04.2 LTS.

Any ideas?

---

### Post by ajgreeny on 2015-06-25
What screen resolution are you using, and is your problem related to that being incorrect for the native screen resolution?  What graphics hardware do you have with which driver, and have you had a recent upgrade of that?

The movement desktop icons is a real nuisance and the only way I have found to stop it happening is to set the ~/.config/xfce4/desktop/icons.screen* files as immutable, meaning they can not be changed or deleted in any way.

First delete any such files you already have, then arrange your icons as you want them, and finally run command ```
sudo chattr +i .config/xfce4/desktop/icons.screen*
```
If you do ever need to rearrange the icons you will have to remove the immutable flag with ```
sudo chattr -i .config/xfce4/desktop/icons.screen*
```
Occasionally if you add another icon or file to the desktop you will find that some icons have temporarily moved but a click on the desktop to focus it and hit F5 and all will move back again.

I don't really use desktop icons any more but an autohide panel on the left hand side full of launchers, but if you want to keep desktop icons that is the one thing that works.

---

### Post by chinleybrewer on 2015-06-25
> **ajgreeny said:**
> What screen resolution are you using, and is your problem related to that being incorrect for the native screen resolution?

1366 x 768
It's not been changed and has worked for the last 2 or more years at least.
Firefox and all other apps work fine with resolution as I'd expect.

> **ajgreeny said:**
> What graphics hardware do you have with which driver, and have you had a recent upgrade of that?

I've not deliberately upgraded anything - just let the update tool get on with things.

> **ajgreeny said:**
> The movement desktop icons is a real nuisance and the only way I have found to stop it happening is to set the ~/.config/xfce4/desktop/icons.screen* files as immutable, meaning they can not be changed or deleted in any way.

I've not been overly bothered about the icons moving but at the moment the desktop is pretty much unusable :-(

Tried deleting the icons.screen files - no difference...

---

### Post by Bashing-om on 2015-06-25
chinleybrewer; AJ - Hello;

A thought, as we do not have much yet to work with:
The directory where Xfce stores the configurations of the panel is
/home/user/.config/xfce4/panel/
Just erasing it and logging out and in will restore the defaults configurations that your xubuntu ships in.

Then see what the situation is ?

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe, not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jonners59 on 2015-06-25
> **chinleybrewer said:**
> Recently, I've noticed my desktop icons have frequently been rearranged - it's been rather annoying but I ignored it.


Interesting problem.  I too have had this on a couple of machines.  I resolved it on one by using Settings -->Desktop and used the last tab "icons"
I am assuming you have done this.  I have to say not worked on all.

I too have found that since 14:10 xfce has been a nightmare from a desktop perspective.  There are a number of bugs out regarding icons and layout changing on reboot.  I shall watch with interest how this gets fixed.  Bashing-on is the best.  Helped me out many a time.

[COLOR=#000000]ajgreeny
[/COLOR]Great tip.  I shall try those two.

---

### Post by chinleybrewer on 2015-06-25
> **Bashing-om said:**
> chinleybrewer; AJ - Hello;

A thought, as we do not have much yet to work with:
The directory where Xfce stores the configurations of the panel is
/home/user/.config/xfce4/panel/
Just erasing it and logging out and in will restore the defaults configurations that your xubuntu ships in.

Then see what the situation is

Unfortunately it made no difference to the desktop - the panel launchers were all missing (or rather then were there but blank) but the desktop looked the same...

I wonder if a small picture may help?

[[IMG]http://i71.photobucket.com/albums/i126/eskimobob_2006/desktop-problem.png[/IMG]](http://s71.photobucket.com/user/eskimobob_2006/media/desktop-problem.png.html)

It's hard to see right but the folder icons on the desktop are much larger than they should be.

One potential clue?? - before I log in, when the login box is shown, the screen has the correct wallpaper - only once I have logged in does it turn black.

---

### Post by ajgreeny on 2015-06-25
What happens if you rename the ~/.config/xfce4 folder and start again configuring your desktop?

That should give you the default xubuntu/xfce desktop layout as a start, and you will then need to put everything back to what you want, but it should not take too long, depending on how complicated your setup is.

Just to check a few things, can you show us the output of ```
ls -l .config
```to check that all is owned by you as user.

---

### Post by chinleybrewer on 2015-06-25
> **ajgreeny said:**
> What happens if you rename the ~/.config/xfce4 folder and start again configuring your desktop?

That should give you the default xubuntu/xfce desktop layout as a start, and you will then need to put everything back to what you want, but it should not take too long, depending on how complicated your setup is.

Well, it definitely changed - it put up the message about it being the first time run and asked me to choose default or one panel.  The desktop still was the same though :-(

> **ajgreeny said:**
> Just to check a few things, can you show us the output of ```
ls -l .config
```to check that all is owned by you as user.

Checked that and definitely all owned by me :-)

Still no further forward - how frustrating...

A thought just occurred to me.  A few days ago while viewing files in Nemo, a little message appeared in Nemo saying something about the icon cache needing to be fixed - not those exact words.  Is that a clue as to what has happened with the icons on the desktop?

---

### Post by Jonners59 on 2015-06-26
For my penny's worth.  Icons are stored here on my machines...
```
/usr/share/pixmaps/
```
and they come in different sizes.  Could the config be pointing at the wrong place?
Also check that your "Appearance" settings match "Desktop" settings.  I had an issue where it had changed from 96dpi in one, caused probs.

---

### Post by chinleybrewer on 2015-06-26
> **Jonners59 said:**
> For my penny's worth.  Icons are stored here on my machines...
```
/usr/share/pixmaps/
```
and they come in different sizes.  Could the config be pointing at the wrong place?
Also check that your "Appearance" settings match "Desktop" settings.  I had an issue where it had changed from 96dpi in one, caused probs.

Thanks - checked those files and they look like valid images.
The dpi setting is still at 96dpi.

Any other ideas :-(

---

### Post by Jonners59 on 2015-06-28
I knew I had this myself but could not fathom out where and how.  It was on my PC I call mediaserver.  I am currently having major and very annoying issues with video cards and the latest kernel on this and all my other machines.  So trying to fix this machine yesterday reminded me of the incident.

I found that the problem occurs when you have the standard Ubuntu Unity install with the other versions.  And I found that if I chose xUbuntu at login it worked and if I chose xfce i got the large icons in panel and some other places/apps too, but not all.  So i suggest, if not tried already trying out xUbuntu and xfce.....

---

### Post by chinleybrewer on 2015-06-28
> **Jonners59 said:**
> So i suggest, if not tried already trying out xUbuntu and xfce.....

Tried that several times already without luck.

STOP PRESS

Just sorted it after reading [here]("http://askubuntu.com/questions/451847/desktop-icons-not-showing-up-in-xubuntu-and-i-cant-right-click-on-the-desktop") about clearing the sessions:
rm -R ~/.cache/sessions/*

That seems to have worked :-)

Many thanks for all you suggestions.

---

### Post by Bashing-om on 2015-06-28
chinleybrewer; Outstanding .

Good job there.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

