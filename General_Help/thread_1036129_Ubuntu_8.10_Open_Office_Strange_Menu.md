---
title: "Ubuntu 8.10 Open Office Strange Menu"
date: 2009-01-10
forum: General Help
---

### Post by dwanders on 2009-01-10
I am experiencing a strange occurrence with OpenOffice on one of my three Ubuntu 8.10 computers. I have built three PC's (two for my kids and one for me) and when my daughter went to use OO for home work - she was presented with the Messed up image I have attached. 

After searching Google and these forums, I have tried, adding all kinds of oo additional packages and fonts, I have also tried removing the .openoffic directory from /home, uninstall-ed and reinstall OO all with no luck. I have a clone of my original build, but would to save that as a last resort if possible. 

Any help with this is appreciated.

---

### Post by dadozgb on 2009-01-10
> **dwanders said:**
> I am experiencing a strange occurrence with OpenOffice on one of my three Ubuntu 8.10 computers. I have built three PC's (two for my kids and one for me) and when my daughter went to use OO for home work - she was presented with the Messed up image I have attached. 

After searching Google and these forums, I have tried, adding all kinds of oo additional packages and fonts, I have also tried removing the .openoffic directory from /home, uninstall-ed and reinstall OO all with no luck. I have a clone of my original build, but would to save that as a last resort if possible. 

Any help with this is appreciated.

Can you look at ~/.xsession-errors or /var/syslog for some kind error that will give you a hint what is going on? This is just a guess but did you installed java.

---

### Post by abn91c on 2009-01-10
you have to remove this file to fix the menus ```
sudo apt-get remove openoffice.org-gnome
```

---

### Post by alzie on 2009-01-10
I did some searching and found some similar problems. There is a bug that affects older nVidia cards using the 96 series drivers here: [https://bugs.launchpad.net/ubuntu/+s...96/+bug/294076](https://bugs.launchpad.net/ubuntu/+s...96/+bug/294076)

A quick workaround for this is to set Visual Effects to "none" in your Appearance Preferences.

This should work until the bug is fixed.

I hope this helps

---

### Post by dwanders on 2009-01-10
have tried sudo apt-get removeing:

openoffice.org-gnome
openoffice.org-kde (based on another post)
openoffice.org-gtk < just for giggle

nada - even after reboot and deleting .openoffic from home - the menus look the same as in the screen shot. 

I will look for some thing in xerrors or syslog for anything

---

### Post by dwanders on 2009-01-10
Sweeeeeet - that did the trick alzie! This has been buggin me for a couple a days and I was just about ready to drop a clone on it. 

Thanks a TON!

---

