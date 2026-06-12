---
title: "I think my settings are gone"
date: 2008-03-21
forum: Desktop Environments
---

### Post by Radiobuzz on 2008-03-21
Hi all, it's me, the guy that brakes everything.

It all started yesterday when I saw there was a new version of AWN. I wanted to upgrade it but since I've installed the old version manually I added the new repos and upgraded from there. It all worked good until I realised none of the applets were working. None. I saw there was a guy with a similar problem and all he did was uninstall AWN and delete files that were left behind scattered all over the drive. I did that too, but then I realised that awn-core-applets-bzr didn't wanted to leave. I couldn't uninstall that package using neither apt-get, aptitude nor synaptic. I don't remember exacly all the errors that I got but they all pointed to a file in /var/lib/gconf/defaults.

So then I find this magical solution which was to rename that folder, so I did "sudo mv /var/lib/gconf/defaults /var/lib/gconf/defaults.bak", then uninstalled the applets (which worked) and then upgraded aptitude (which installed the new AWN). Everything worked great but I thought that I should get back that "defaults" thing so I moved back default.bak to default. I thought that it worked but I hadn't rebooted until today. Now, when I log into Ubuntu I get an error regarding gnome-power-management, the icons on the main menu aren't showing, the speed of the mouse cursor is way faster, my keyboard is behaving weird, the font in the terminal is huge, the "log out" button doesn't show me the screen to choose what action to take but simply takes me back to the login screen, and lots of other small but weird errors. Oh, and regarding AWN, it also behaves weird because for example if I click on the terminal applet it appears to be working but it doesn't show! I mean, there is an invisible rectangle on the screen but if I put my mouse above that the cursor changes into the one that's used on any text field.

Obviously I think it's related to gconf, so I went to that folder and I see something weird. Under /var/lib/gconf there are two folders: debian.defaults and defaults. Inside defaults there are only three folders: apps, schemas AND defaults.bak! Inside this last folder there are lots of XML files, (%gconf-tree-x) which were the files that were giving me problems when I wanted to uninstall AWN. So anyway, what happened? Where are those files supposed to be? I tried renaming "defaults.bak" to "defaults", rebooted and everything kept the same. I've also tried copying the files in .bak to /var/lib/gconf/defaults and it also didn't help.

I'll appreciate if anyone could help me, because even if I can use the computer it don't fell quite right.

EDIT: Oh! One last thing, I opened Nautilus using the terminal so I could access the defaults.bak folder, and I see that it gives me a warning:

--- Hash table keys for warning below:
--> &#65533;&#65533;&#65533;/var/lib/gconf/defaults/defaults.bak

(nautilus:5776): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

---

### Post by Radiobuzz on 2008-03-21
Pleaaaaaaaase.

---

### Post by Radiobuzz on 2008-03-22
Do this means I have to reinstall? I really don't want to do it unless is necessary :(.

---

### Post by Radiobuzz on 2008-03-22
This is the exact error I get when login in:

The configuration defaults for gnome power manager have not been installed correctly.

I'm no expert but I think it's basically telling me that it can read Gnome Power Manager's configuration, which I'm sure it's stored in /var/lib/gconf/defaults. And I'm sure the rest of the configurations for other Gnome aspects can't be read as well. I've copied every %gconf-tree-x file from defaults.bak to defaults and it's still the same.

Help!

---

### Post by Radiobuzz on 2008-03-22
I have formatted. I really appreciate all your help :).

---

