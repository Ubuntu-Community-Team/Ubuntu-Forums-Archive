---
title: "Lost Default Nautilus Enviroment"
date: 2011-05-29
forum: Desktop Environments
---

### Post by CyberNeT85 on 2011-05-29
Hi it seems my default nautilus environment has gone haywire.

If anyone knows how to reset the defaults?
Please see attached for screen shot.

Thanks.

Alex

---

### Post by wildmanne39 on 2011-05-29
> **CyberNeT85 said:**
> Hi it seems my default nautilus environment has gone haywire.

If anyone knows how to reset the defaults?
Please see attached for screen shot.

Thanks.

AlexHi, we need to know what version of ubuntu you are running? and the specs of your system.Type
```
lspci
```so we can see the video adapter and such that you are using. How old is this system is it a laptop or desktop?

---

### Post by djchandler on 2011-05-29
Did you log on to Gnome (Unity desktop) or Gnome Classic? If you just upgraded to 11.04 (natty), the default is the Unity desktop.

If you're on the Unity desktop, the menu items are in the top panel. Move your pointer up there and you'll see them. Under "edit" you will find "preferences." Try editing your preferences.

---

### Post by CyberNeT85 on 2011-05-29
Sorry, Running Ubuntu 11.04 natty, unity.

I was tinkering with themes and i think i messed it up. But i've reverted to default Ambiance theme.

Ta

---

### Post by wildmanne39 on 2011-05-29
> **CyberNeT85 said:**
> Sorry, Running Ubuntu 11.04 natty, unity.

I was tinkering with themes and i think i messed it up. But i've reverted to default Ambiance theme.

TaHi, ok and be careful if you enable effects or you will break unity and have to reset. Use this link if you want effects. [http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html) would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.

---

### Post by Krytarik on 2011-05-29
It seems like you installed Nautilus Elementary alongside with the theme you were trying.

Check that via "Help -> About".

If so, and you want to revert to the default version of Nautilus included by the official repos:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:am-monkeyd/nautilus-elementary-ppa
```Then restart Nautilus:
```
killall nautilus
```Greetings.

---

