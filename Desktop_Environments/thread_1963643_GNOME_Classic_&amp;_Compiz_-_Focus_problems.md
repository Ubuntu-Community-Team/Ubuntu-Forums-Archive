---
title: "GNOME Classic &amp; Compiz - Focus problems"
date: 2012-04-22
forum: Desktop Environments
---

### Post by -Robert- on 2012-04-22
I sometimes have to click twice in order to minimize/restore an application from the panel. The application just does not seem to get focus. The windows also "jump" to the left corner of the screen before they are being restored. Is this a familiar problem, and more important, does anyone know a solution?

Perhaps my description of the problem is not quite clear, so I recorded it:  [http://dl.dropbox.com/u/9387273/Linux/focus%20problem.ogv](http://dl.dropbox.com/u/9387273/Linux/focus%20problem.ogv)

---

### Post by kansasnoob on 2012-04-23
I'd try "renaming" the hidden dot files .compiz and .compiz-1 and then logging out and logging back in. 

Example:

Open your home folder and click on View > Show hidden. Then right click both .compiz and .compiz-1 and rename them something like .compiz_OLD and .compiz-1_OLD. Then log out and log back in.

If it's no better you can then just delete the new .compiz and .compiz-1, and then remove the "_OLD" from the originals.

I've sometimes found it necessary to do the same with .config, .gconf, or .gnome2.

---

### Post by -Robert- on 2012-04-23
Thanks for your reply. 
I tried your suggestion, but the problem remains. I even installed 12.04 in Virtualbox on another PC, it also has the exact same problem.

Does everything work normally for you in GNOME Classic?

---

### Post by -Robert- on 2012-04-24
I just did a complete new installation, hoping that would solve it. Well... it didn't.
GNOME Classic really isn't workable this way.

I'm using the proprietary driver (my graphics card is NVIDIA GeForce 8400 GS), and I didn't install any other programs. I only updated and installed gnome-shell (that also installs GNOME Classic).

Am I the only one who is experiencing these focus problems with GNOME Classic?

---

### Post by kansasnoob on 2012-04-24
That is why I've stuck with Metacity "classic (no effects)" in both my Oneiric guide:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

And my upcoming Precise guide:

[http://ubuntuforums.org/showpost.php?p=11835822&postcount=389](http://ubuntuforums.org/showpost.php?p=11835822&postcount=389)

I may give Compiz a closer look in a couple of months but right now I just have too much on my plate.

---

### Post by -Robert- on 2012-04-24
Classic (no effects), Unity and Unity (2D) work great, it's only Classic with compiz which has this irritating issue.
I also installed 12.04 on another PC with an ATI graphics card (and as previously mentioned in Virtualbox), exactly the same behavior.

Nice guides by the way. :)

---

### Post by kansasnoob on 2012-04-24
> **-Robert- said:**
> Classic (no effects), Unity and Unity (2D) work great, it's only Classic with compiz which has this irritating issue.
I also installed 12.04 on another PC with an ATI graphics card (and as previously mentioned in Virtualbox), exactly the same behavior.

Nice guides by the way. :)

I wish I had an answer for you but Compiz seems to be a mess ATM with anything but Unity. I'm sure someone will figure out how to deal with this if we're patient :)

---

### Post by coffeecat on 2012-04-27
*Thread moved to **Desktop Environments** at request of OP.*

---

### Post by -Robert- on 2012-04-27
> **coffeecat said:**
> *Thread moved to **Desktop Environments** at request of OP.*
Thanks again. :)

The earlier mentioned problem still exists. 
Another problem I experience is that when I use an application full screen, gnome panel appears.
GNOME Classic and Compiz just don't work as they should in 12.04, I hope someone has a solution.

---

### Post by kansasnoob on 2012-04-27
Still no answer but I noticed that enabling compositing in Metacity even makes a bit of a mess. Given my poor eyesight it doesn't matter much though :)

I have however noticed that there are a lot of Compiz updates available in "proposed" but I'm afraid to give it a try until I get caught up with some other issues. The list of updates is complex enough that I'd assume if it breaks things a reinstall may be needed :(

Rather off-topic but I copied my classic (no effects) post to this same section:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by -Robert- on 2012-04-27
> **kansasnoob said:**
> 
I have however noticed that there are a lot of Compiz updates available in "proposed" but I'm afraid to give it a try until I get caught up with some other issues. The list of updates is complex enough that I'd assume if it breaks things a reinstall may be needed :(
I tried to update compiz with the proposed packages (after first making a backup), but that didn't solve it either.

> **kansasnoob said:**
> Rather off-topic but I copied my classic (no effects) post to this same section:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)
If I were you I would ask a moderator to move it to Tutorials & Tips. Could be handy for a lot of people.

---

### Post by kansasnoob on 2012-04-27
> If I were you I would ask a moderator to move it to Tutorials & Tips. Could be handy for a lot of people.

I prefer keeping it in the DE section :)

---

### Post by -Robert- on 2012-05-02
Bump. :sad:

---

### Post by mohegan on 2012-05-06
The compiz package in proposed doesn't work better. So, I install the previous package from 11.10 and block updates for them. It's not a good solution but it's temporary.

- Download the packages from [http://packages.ubuntu.com](http://packages.ubuntu.com) in oneiric or oneiric-updates (compiz, compiz-core, compiz-gnome, compiz-plugins, compiz-plugins-default, compiz-plugins-main, compiz-plugins-main-default, compizconfig-backend-gconf, compizconfig-settingsmanager, libcompizconfig0, python-compizconfig, libdecoration0).

- Put the packages in the same directory and install them with this command : sudo dpgk -i *.deb

- Edit apt preferences to keep this packages : sudo gedit /etc/apt/preferences

- Copy this text :

```
Package: compiz
Pin: version 1:0.9.6+bzr20110929-0ubuntu6.1
Pin-priority: 1001

Package: compiz-core
Pin: version 1:0.9.6+bzr20110929-0ubuntu6.1
Pin-priority: 1001

Package: compiz-gnome
Pin: version 1:0.9.6+bzr20110929-0ubuntu6.1
Pin-priority: 1001

Package: compiz-plugins
Pin: version 1:0.9.6+bzr20110929-0ubuntu6.1
Pin-priority: 1001

Package: compiz-plugins-default
Pin: version 1:0.9.6+bzr20110929-0ubuntu6.1
Pin-priority: 1001

Package: compiz-plugins-main
Pin: version 1:0.9.6-0ubuntu4.2
Pin-priority: 1001

Package: compiz-plugins-main-default
Pin: version 1:0.9.6-0ubuntu4.2
Pin-priority: 1001

Package: compizconfig-backend-gconf
Pin: version 0.9.5.92-0ubuntu2
Pin-priority: 1001

Package: compizconfig-settings-manager
Pin: version 0.9.5.92-0ubuntu1
Pin-priority: 1001

Package: libcompizconfig0
Pin: version 0.9.5.94-0ubuntu2
Pin-priority: 1001

Package: python-compizconfig
Pin: version 0.9.5.94-0ubuntu3
Pin-priority: 1001

Package: libdecoration0
Pin: version 1:0.9.6+bzr20110929-0ubuntu6.1
Pin-priority: 1001
```

- Save and restart !

---

### Post by -Robert- on 2012-05-07
Thanks for your reply.

I tried your suggestion and installed the compiz packages from 11.10. It broke Unity (3D), but that's not a big issue. 

It works a bit better, the windows don't jump to the left corner of the screen anymore. The focus problem is not as bad as before, but it does still happen from time to time.

---

### Post by guipy on 2012-06-25
> **-Robert- said:**
> Thanks again. :)

The earlier mentioned problem still exists. 
Another problem I experience is that when I use an application full screen, gnome panel appears.
GNOME Classic and Compiz just don't work as they should in 12.04, I hope someone has a solution.

Hey Robert, i have the focus issue too...i hope someone [with more Ubuntu/GNOME knowledge than me :razz:] can solve this...because this is annoying !

About the fulscreen problem, you can solve it disabling the "Place  Window" plugin in the CCSM [Compiz config tool] ...for me it suffices...

---

### Post by hawthornso23 on 2012-07-07
I don't use window list in my panel any more. I use window shift switcher instead to maximise minimised windows. This method doesn't seem to have any problem maximising and getting focus so it looks to me like the problem is specifically with the window list panel menu item. 

I have my shift switcher linked to bottom RH corner.

[LIST]
[*]Move mouse to bottom RH corner
[*] use scroll wheel to select the window you want
[*]click or move mouse back to bottom RH corner and you are in business
[/LIST]
all without removing your hand from the mouse. Very convenient and fast.

---

