---
title: "how to add more themes in Ubuntu Netbook Remix?"
date: 2009-05-09
forum: Desktop Environments
---

### Post by dwl99 on 2009-05-09
Is there a way to add more themes to the standard ones?  In Ubuntu Netbook Remix there doesn't seem to be a Themes icon displayed anywhere, just a Switch Desktop one. Thanks!

---

### Post by coffeecat on 2009-05-09
I haven't tried this yet - netbook not booted up atm - but this *might* work. Switch desktop to the standard desktop. Then right-click on desktop, choose 'Change Desktop Background' and select the theme tab. You should now be able to install extra themes by the usual drag and drop method. Whether they 'stick' when you go back to the nbr desktop, I don't know. Perhaps you could let us know. :)

By the way - I assume you're using the 'official' Jaunty nbr, not one of the 3rd party Ubuntu remixes. If so, you might find that some themes don't install correctly in Jaunty. I believe this is an upstream gnome issue - some of the APIs seem to have changed in the latest Gnome used in Jaunty. I've had errors installing older GTk themes on a standard Jaunty desktop, and some older icon themes don't display all the icons properly, defaulting back to standard Gnome ones.

Hopefully, that won't be a problem if you install extra themes from the limited selection available through the repos.

---

### Post by dwl99 on 2009-05-09
Thanks, it looks as if this will allow a choice from a limited number of themes. I downloaded the Murrina Aero theme & copied it to the usr/share/themes folder but it doesn't appear as an option when I try to change themes.

---

### Post by Brandon Williams on 2009-05-09
To change the theme, go to 'Preferences->Appearance' in the netbook-launcher.

To install a new theme on a single user system, just put it in ~/.themes/. If it's a gnome or gtk compatible theme, it should show up in the selector. You _might_ have to log out and log back in to see it.

---

### Post by Brandon Williams on 2009-05-09
I found that theme on gnome-look.org and downloaded it to test. It came as a .zip file, which seems strange, since gnome expects .tgz files. No problem:
```
$ unzip Murrina-Aero.zip
$ tar zcf Murrina-Aero.tgz Murrina-Aero
```

With that done, click the 'Install...' button in 'Preferences->Appearance' and select the .tgz file. It will be installed in the correct location and a dialog will appear asking if you would like to apply the new theme.

---

### Post by dwl99 on 2009-05-10
Thanks, all sorted now. I wonder why it was zipped? :confused:

---

