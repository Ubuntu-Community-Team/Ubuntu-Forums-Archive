---
title: "bigger mouse pointer?"
date: 2013-10-07
forum: Desktop Environments
---

### Post by bbmak on 2013-10-07
Hi,
I want to know are there anyway to make the mouse pointer bigger in Lubuntu 13.04? The pointer in my desktop is so small and my screen is big.

---

### Post by Dennis N on 2013-10-07
Rather than make the existing mouse cursor larger (not possible in Lubuntu), you have to install a mouse cursor theme that provides larger cursors.

A source for extra cursor themes is **gnome-look.org**. Select "x11 Mouse Themes" from the menu on the left. 

I use this one which provides five colors and four sizes (including large and huge):

[http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027](http://gnome-look.org/content/show.php/Flatbed+Cursors?content=52027)

To install: download, extract the folder(s) for the cursor(s) you want to use, and follow the steps here for each:

[http://ubuntuforums.org/showpost.php?p=11929215&postcount=17](http://ubuntuforums.org/showpost.php?p=11929215&postcount=17)

Since that old post cannot be edited, this is some additional explanation:

There is no 'dash' in Lubuntu, so you find the galternatives program in the main (applications) menu under System Tools, listed as "Alternatives Configurator".

Where it says 'Create cursor.theme file if needed' it is a text file and looks like this:

```

    [Icon Theme]
    Inherits=Theme-Name
```

**Theme-Name** is the exact name you find on the theme's folder. Create it and save it inside the theme's folder. 

For Lubuntu, after using galternatives as described in the post, also select the cursor theme in the Customized Look and Feel dialog and log out and back in. It should be working then.

---

### Post by bbmak on 2013-10-07
Are there a ready-made package that allow you to add to "customize look and feel" in Lubuntu?
I am just a normal average user, and I don't want to do too much technical work.

---

### Post by zombifier25 on 2013-10-08
Try [this suggestion](http://bbs.archbang.org/viewtopic.php?pid=23727) and see if it works.

---

### Post by Dennis N on 2013-10-08
> **zombifier25 said:**
> Try [this suggestion](http://bbs.archbang.org/viewtopic.php?pid=23727) and see if it works.

Thanks, sounded promising, so I tried this with the default DMZ white cursor theme and it works partially - in some places (in Firefox), the cursor is large (set to 48 in desktop.conf) but in others (over the panel) it reverts to small (18?). I tried the same experiment with a different cursor, and it did not change size at all. In the test I selected DMZ white in both the alternatives setup and in the Customized look and feel. In all cases, did log out and in after any modifications.

Initial conclusion is DMZ white is capable of changing size by modifying that desktop.conf file, but not uniformly. 

If anyone want to experiment further with this approach, the file to modify is **[FONT=Courier New]/home/<user>/.config/lxsession/Lubuntu/desktop.conf[/FONT]**

Meanwhile, the process in post #2 will give you a uniform cursor which is large in size.

---

### Post by Dennis N on 2013-10-08
> **bbmak said:**
> Are there a ready-made package that allow you to add to "customize look and feel" in Lubuntu?
I am just a normal average user, and I don't want to do too much technical work.

If you copy the folder for any downloaded mouse cursor theme to /usr/share/icons it will show up for selection in "Customized Look and Feel". It used to be (before 12.04) that this was all that was needed to change the cursor theme and everything worked great. Now, with later releases, you may not get the same cursor everywhere if that is all you do. For example, one cursor will appear over Firefox window and another over the panel. So, the additional use of galternatives is to fix that problem. 

I have yet to see another way around this "dual cursors" problem in Lubuntu without galternatives (but would be interested if there is). 

The default cursor (DMZ white) has been set up correctly to appear everywhere the same, but I have not seen a way to uniformly increase its size. The little experiment in post #5 did enlarge it in some places for DMZ white, but not everywhere.

---

### Post by Dennis N on 2013-10-08
One additional thought:

Did you try the "install" button on the Mouse Cursor tab in Customized Look and Feel to install the downloaded cursor theme? I haven't tried that recently to see if it might now replicate the whole process of post #2 to correctly install a different cursor. If it did, that would be great.

More:

See Post #12 for test of install button and observations.

---

### Post by Cycledoc on 2013-10-08
I'm having the same issue.  Find it amazing that Ubuntu has not provided a simple way to do this.

---

### Post by Cycledoc on 2013-10-08
Found this nice tutorial.  Easiest approach yet.
[http://www.youtube.com/watch?v=Yxfa2fXJ1Wc&noredirect=1](http://www.youtube.com/watch?v=Yxfa2fXJ1Wc&noredirect=1)

---

### Post by bbmak on 2013-10-08
> If you copy the folder for any downloaded mouse cursor theme to /usr/share/icons it will show up for selection in "Customized Look and Feel". It used to be (before 12.04) that this was all that was needed to change the cursor theme and everything worked great. Now, with later releases, you may not get the same cursor everywhere if that is all you do. For example, one cursor will appear over Firefox window and another over the panel. So, the additional use of galternatives is to fix that problem. 

I have yet to see another way around this "dual cursors" problem in Lubuntu without galternatives (but would be interested if there is). 

The default cursor (DMZ white) has been set up correctly to appear everywhere the same, but I have not seen a way to uniformly increase its size. The little experiment in post #5 did enlarge it in some places for DMZ white, but not everywhere.


Thank you for the detail reply. I guess I just stick with the tiny mouse pointer on the screen.

---

### Post by bbmak on 2013-10-08
> I'm having the same issue. Find it amazing that Ubuntu has not provided a simple way to do this.

yes, this is so lame.

---

### Post by Dennis N on 2013-10-09
Tested the install button as mentioned in post #7.

Tested the "install" button on the [FONT=Courier New]Preferences > Customized Look and Feel > Mouse Cursor[/FONT] dialog. It is not necessary to extract the cursor folder from the archive - it is done for you. I assume it does them all if there are more than one. The application closed (crashed?) when the install button was clicked, but the cursor was installed, into [FONT=Courier New]~/.icons[/FONT], not [FONT=Courier New]/usr/share/icons[/FONT]. If you want root applications (like Synaptic) to use it, the cursor theme folder (or a copy) should be in the latter. Then, selected the new cursor in the dialog. The result is you still have two cursors - the new one, and the one that is set in the alternatives system as default (appears on desktop, window title bars, panels) while the new one shows inside some application windows (Firefox, Libre Office). 

You still need to use galternatives to setup the new cursor into the alternatives system and set it as default to fix this dual cursor problem. (Also can be done in the terminal with update-alternatives). 

*Tested in Lubuntu 12.10 with new cursor AeroM.*

---

