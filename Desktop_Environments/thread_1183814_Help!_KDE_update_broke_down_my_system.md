---
title: "Help! KDE update broke down my system"
date: 2009-06-10
forum: Desktop Environments
---

### Post by duott on 2009-06-10
I did apt-get upgrade on my Kubuntu Jaunty, it downloaded some KDE-related libs, and suddenly after the update hotkeys stopped working. I did a reboot and my interface is gone! 

Now it shows grey squares instead of user interface (background image, plasmoids and everything are gone), hotkeys still not working. The system, however, seems to be overall alive, because I still have the applications that were running before the reboot on my desktops, fortunately Opera being among them. I didn't launch the konsole before the reboot and so I cannot access it now and basically unable to launch or do anything.

Some quick help would be very much appreciated...

---

### Post by jlacroix on 2009-06-10
> **duott said:**
> I did apt-get upgrade on my Kubuntu Jaunty, it downloaded some KDE-related libs, and suddenly after the update hotkeys stopped working. I did a reboot and my interface is gone! 

Now it shows grey squares instead of user interface (background image, plasmoids and everything are gone), hotkeys still not working. The system, however, seems to be overall alive, because I still have the applications that were running before the reboot on my desktops, fortunately Opera being among them. I didn't launch the konsole before the reboot and so I cannot access it now and basically unable to launch or do anything.

Some quick help would be very much appreciated...

It sounds to me as though you've either upgraded to KDE 4.3 Beta (either intentionally or unintentionally) or some packages got removed.

You can try the following command:

```
sudo apt-get update && sudo apt-get -f install && sudo apt-get install kubuntu-desktop
```

If that does not work, use the failsafe option from the login window (I think that's what it's called) and do this:

```
mv ~/.kde ~/.kde_bak
```

After that restart and you'll be fine.

---

