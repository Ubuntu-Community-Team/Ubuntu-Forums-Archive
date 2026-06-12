---
title: "classic panels"
date: 2014-01-21
forum: Desktop Environments
---

### Post by cmcanulty on 2014-01-21
I have gnome flashback which I have reinstalled 3x in the last day and still can't add top panels with alt+rt cl I am about to give up. is there a way to purge it and start over?

---

### Post by cmcanulty on 2014-01-21
I ahve gnome flashback which I have reinstalled 3x in the last day and still can't add top panels with alt+rt cl I am about to give up. is there a way to purge it and start over? I get the add to panel dialog OK but nothing actually adds

---

### Post by Frogs Hair on 2014-01-21
Try Windows/Super Key +Alt + RC.

---

### Post by ibjsb4 on 2014-01-21
Try

Super + Alt + right click

---

### Post by cmcanulty on 2014-01-21
like  I said I get the add to panel dialog with alt+rt cl but nothing will actually add I need to purge it somehow, completely uninstall from synaptic did nothing to fix it

---

### Post by ibjsb4 on 2014-01-21
A complete purge in terminal is:

```
sudo apt-get remove --purge gnome-panel
```

Which to my understanding is the same thing 'completely remove' in synaptic will do.

Can you pull up any panel context menus?

And the above key combination has worked for others, don't understand why you will not try it.

---

### Post by cmcanulty on 2014-01-21
I guess that is better than completely remove as it found 3 files still but doesn't fix it. As I said I get the right cl menu OK it just won't add anything I hate unity so I guess I am stuck with xfce even though I love classic

---

### Post by ibjsb4 on 2014-01-21
Try reinstalling 

gnome-panel-data

---

### Post by coffeecat on 2014-01-21
Threads merged.

---

### Post by cmcanulty on 2014-01-21
didn't work, any other ideas

---

### Post by ibjsb4 on 2014-01-21
You can try resetting gnome-panel/gnome-session with gconf/dconf settings.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+gnome-panel+12.04&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+gnome-panel+12.04&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+gnome-session-fallback+12.04&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=reset+gnome-session-fallback+12.04&sa=Search&cof=FORID:9)

A long shot ..
Do you have any PPAs that could be messing with you; running a custom theme?

---

### Post by cmcanulty on 2014-01-21
4th reinstall did it, what a 48 hr hassle!

---

