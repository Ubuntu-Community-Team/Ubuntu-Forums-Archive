---
title: "Overlay scrollbars are turning me away from Ubuntu"
date: 2017-07-06
forum: Desktop Environments
---

### Post by James Wilde on 2017-07-06
Unity was bad enough.  Now I'm getting tired of trying to make overlay scrollbars work satisfactorily.  I'm using 16.04.

I've tried a number of the suggestions to be found with a quick search.  Things using dconf and gconf I'm prepared to use and maybe adding a config file here or there, but I'm not prepared to go editing program files.

I would like a simple option in - presumably - dconf that I can check or uncheck.  Is there one?

---

### Post by Frogs Hair on 2017-07-06
Have tried removing them ? logout or restart would be required to see changes. 

 ```
sudo apt-get remove overlay-scrollbar
```

To reverse changes.

```
sudo apt-get install overlay-scrollbar
```

---

### Post by mc4man on 2017-07-07
I may be misinterpreting this but I believe the current overlay scrollbars are now from gnome/gtk3 (built-in). Ubuntu dropped their version prior to 16.04. (So not a "Ubuntu" deal..
The overlay-scrollbar* packages are for gtk2 only.
If that's the case then the only way to change would be via a theme or don't use a gnome based *buntu

---

### Post by James Wilde on 2017-07-07
Logout didn't fix it.  Restart didn't fix it.  Good try but no cigar.  :D

---

### Post by James Wilde on 2017-07-07
> **mc4man said:**
> I may be misinterpreting this but I believe the current overlay scrollbars are now from gnome/gtk3 (built-in). Ubuntu dropped their version prior to 16.04. (So not a "Ubuntu" deal..
The overlay-scrollbar* packages are for gtk2 only.
If that's the case then the only way to change would be via a theme or don't use a gnome based *buntu

Thanks for taking the time to reply, Mc4man.  Can you give me a little more detail on a) 'via a theme' and b) how not to use a gnome based buntu?

---

### Post by QIII on 2017-07-07
Hello!

For official Ubuntu flavors without GNOME, look at:

Kubuntu (uses KDE)

Lubuntu (uses LXDE)

Ubuntu Budgie (uses Budgie)

Ubuntu MATE (uses MATE)

Xubuntu (uses Xfce)

So there are a number of choices.

Cheers!

---

### Post by monkeybrain20122 on 2017-07-07
Just use a different DE. There is no "overlay scrollbar" in current Ubuntu releases except 14.04, it is a gnome scrollbar.

---

### Post by again? on 2017-07-08
Add **GTK_OVERLAY_SCROLLING=0** to your */etc/environment* file.

This terminal command will do it for you.
```
echo "GTK_OVERLAY_SCROLLING=0" | sudo tee -a /etc/environment
```
Log out.

Tested and works in Ubuntu 16.04 and UbuntuGnome 17.04.

---

