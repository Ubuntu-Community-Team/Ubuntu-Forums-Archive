---
title: "magnifying on startup"
date: 2011-03-14
forum: Desktop Environments
---

### Post by t3rrian_tr00pa on 2011-03-14
Hello,

I have this computer that loads up a magnifying glass sort of application on the right half of the screen during the log in.

ie. when choosing accounts and typing in the password screen.

So far:
I tried turning off visual assistance from start-up.
I also uninstalled compiz from the installed software.

Neither have seemed to have disabled it.

The Computer is running Ubuntu 10.04.1 with the latest updates.

Does anybody have any suggestions for me?

I will try to post a screen shot of it when I get time to.

Thanks,
TT

---

### Post by stinkeye on 2011-03-14
To turn off...
```
sudo -u gdm gconftool-2 /desktop/gnome/applications/at/screen_magnifier_enabled --type bool --set false
```

See here for disabling the selection at boot...[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10385617&postcount=13[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10385617&postcount=13")

---

### Post by t3rrian_tr00pa on 2011-03-14
thanks stinkeye,

I will try it out within in two weeks from now.

Cheers,
TT

---

### Post by t3rrian_tr00pa on 2011-06-09
it worked great! thanks

---

