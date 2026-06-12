---
title: "disable certain hacks on gnome-screensaver"
date: 2010-04-05
forum: Desktop Environments
---

### Post by me13221 on 2010-04-05
I'm trying to come to terms with 'gnome-screensaver' instead of xscreensaver, and I'm wondering-- how do I tell gnome-screensaver to disable certain lame screensavers when it's doing random mode?  in particular, I have no F-spot photos so a screensaver consisting of an error message telling me "you have no F-Spot photos" is lame.  Other ones use 3d-accel effects that my hardware doesn't support, so they just slow everything to a crawl- which is embarrassing if I have apple users over.

also, gnome-screensaver should adopt the xscreensaver convention that upon stopping the screensaver, the one that was most recently playing is selected in the screensaver config panel.

---

### Post by Barriehie on 2010-04-09
> **me13221 said:**
> I'm trying to come to terms with 'gnome-screensaver' instead of xscreensaver, and I'm wondering-- how do I tell gnome-screensaver to disable certain lame screensavers when it's doing random mode?  in particular, I have no F-spot photos so a screensaver consisting of an error message telling me "you have no F-Spot photos" is lame.  Other ones use 3d-accel effects that my hardware doesn't support, so they just slow everything to a crawl- which is embarrassing if I have apple users over.

also, gnome-screensaver should adopt the xscreensaver convention that upon stopping the screensaver, the one that was most recently playing is selected in the screensaver config panel.

I'm running Debian but your setup should be very similar...  Look in **~/.gconf/apps/gnome-screensaver/** and find a file named **%gconf.xml**.  It should, if you've got random selected, have an xml defined list of all the screensavers it will choose from.  I did mine that way and then deleted all but two of the screensavers.  After logging out and selecting a new session when logging back in it took effect and now it's only either of the two I left in the file.  Here's my file:

**~/.gconf/gnome-screensaver/%gconf.xml**
```

<?xml version="1.0"?>
<gconf>
        <entry name="idle_activation_enabled" mtime="1270734914" type="bool" value="false">
        </entry>
        <entry name="idle_delay" mtime="1270270838" type="int" value="20">
        </entry>
        <entry name="power_management_delay" mtime="1270737118" type="int" value="60">
        </entry>
        <entry name="lock_enabled" mtime="1270537925" type="bool" value="false">
        </entry>
        <entry name="themes" mtime="1270821166" type="list" ltype="string">
               <li type="string">
                        <stringvalue>screensavers-footlogo-floaters</stringvalue>
                </li>
                <li type="string">
                        <stringvalue>screensavers-debian-floaters</stringvalue>
                </li>
       </entry>
        <entry name="mode" mtime="1270821166" type="string">
                <stringvalue>random</stringvalue>
        </entry>
</gconf>
```

HTH

---

### Post by jejones3141 on 2010-04-16
To the best of my knowledge, you don't have to come to terms with gnome-screensaver if you don't want to. At least as of Karmic Koala, you can safely uninstall gnome-screensaver and install xscreensaver without being told that ubuntu-desktop has a dependency on gnome-screensaver. To whoever made this possible: my eternal, if belatedly discovered, gratitude. Words do not exist to describe the extent to which I despise gnome-screensaver's denial of nearly all configurability to the individual user and the way in which it was imposed as a *fait accompli*.

---

