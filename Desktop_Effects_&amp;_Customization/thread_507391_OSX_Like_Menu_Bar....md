---
title: "OSX Like Menu Bar..."
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by erbag on 2007-07-22
How do I get my Ubuntu Fiesty to have a OSX like Menu bar?

---

### Post by theonlykman on 2007-07-22
by menu bar, do you mean something like [this]("http://njpatel.blogspot.com/")?

---

### Post by andrewsomething on 2007-07-23
> **erbag said:**
> How do I get my Ubuntu Fiesty to have a OSX like Menu bar?

If you mean a dock (like in the above link) AWN is the way to go. 

If you mean the way the top panel in OSX reacts to the open program, try searching the forums for "universal menubar." This is what I found quickly: [http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868)

Personally, I don't like it much, but it's possible...

---

### Post by aysiu on 2007-07-23
Use KDE and enable the "universal toolbar" option in KControl.

You can access KControl by pressing Alt-F2 and typing ```
kcontrol
``` The rest of the details are in the attached screenshot.

**You must be using KDE for this to work.**

---

### Post by Ianman on 2007-07-23
Maybe this will help?
[http://www.taimila.com/?q=node/11](http://www.taimila.com/?q=node/11)

---

### Post by Espreon on 2007-07-23
If you want a dock like Leopard's do this (You hafta have Compiz,Compiz-Fusion or Beryl active to use AWN):

Fire up a terminal and enter this:

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg -O- | sudo apt-key add -
```
 -If it does not eventually respond with an OK than do this:

```
wget http://download.tuxfamily.org/3v1deb/DD800CD9.gpg
```

Then goto: System>Preferences(or Administration, if forgot which one)>Software Sources

Hit the authentication tab (only do this if the first command did not respond with an OK): hit import and select the file named: DD800C9.gpg

Now hit the 3rd Party Software tab and:

enter these:

```
 deb http://download.tuxfamily.org/3v1deb feisty eyecandy
```

```
 deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Now close it and hit reload.

Now fire up a terminal and enter this:

```
sudo apt-get install avant-window-navigator libawn0
```

Once installed goto: Applications>Avant Window Navigator

If everything went right you should only see a transparent black dock, but we are not done yet!

Goto: Applications>System Tools>Configuration (if you don't see it goto System>Prefrences>Main Menu and on the new window goto System Tools and check the check box next to configuration).

Look for Icon Offset (in the avant dropdown) and set it to 15, and look for something like bar angle and set it to 30. And viola!

---

### Post by erbag on 2007-07-23
I think I'm being misunderstood...I don't want the 'mac dock' but the 'mac menu bar' see attached files...I've been to Laura Taimila's website and I'm having a problem following.

I'm being told to look for the Gnome Menu Editor...but have no clue where to find it or not useful search results on the web.

I also understand that if I want a mac like dock I have to install Compiz

---

### Post by andrewsomething on 2007-07-23
> **erbag said:**
> I think I'm being misunderstood...I don't want the 'mac dock' but the 'mac menu bar' see attached files...I've been to Laura Taimila's website and I'm having a problem following.

I'm being told to look for the Gnome Menu Editor...but have no clue where to find it or not useful search results on the web.

I also understand that if I want a mac like dock I have to install Compiz

Check out this thread for hacking it into gnome [http://ubuntuforums.org/showthread.php?t=241868](http://ubuntuforums.org/showthread.php?t=241868)

It's much easier in KDE. See aysiu's post above.

---

### Post by erbag on 2007-07-23
Are you saying that though I'm using a GNOME based interface I can use a KDE toolbar?

---

