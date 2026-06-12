---
title: "Nautilus toolbar gone"
date: 2011-11-10
forum: Desktop Environments
---

### Post by Jmckeen on 2011-11-10
Hi, Recently I was working with Nautilus (Ubuntu's file manager) and I accidentally unchecked the "main toolbar" option leaving me barley any control (I already had the "menu bar" option off) Is there any way to get the controls back? :(

                Jmckeen

---

### Post by BillyBoa on 2011-11-10
I don't understand exactly what is happening but you can open again nautilus opening a terminal with "ctrl alt  T" and then write 

```
nautilus
```

---

### Post by Jmckeen on 2011-11-10
Here is a screenshot to show what I mean.

(Yes I do have a theme.)

---

### Post by Orfintain on 2011-11-10
once you have opened said teminal you can type gnome-panel to bring back gnome-panal. Is that what you mean ?

---

### Post by Jmckeen on 2011-11-10
Not sure. I mean the Back/Forward buttons and the navigation bar thing.

---

### Post by Frogs Hair on 2011-11-10
If that is Nautilus Elementary on Classic Ubuntu try right clicking up near the title bar and see if a context menu opens . I thought there was a right click customize option .

---

### Post by Jmckeen on 2011-11-11
Nope, now that there are no toolbars at the top its either *really* hard to find the right spot or there is none to right click. I'm stumped :(

---

### Post by BillyBoa on 2011-11-11
Try something else

hit ctr H to see your hidden files and go to /home/.config/nautilus
and rename the directory nautilus to e.g. nautilus1
Then log of, log on and use nautilus to see if the configuration was killed. If not rename again the directory to it's original name and ask for another solution.

---

### Post by Frogs Hair on 2011-11-11
did you try restarting nautilus  ```
nautilus -q
```

Here is a post about Elementary Nautilus with some of the key bindings and features described .[http://www.webupd8.org/2011/03/install-nautilus-elementary-2322-in.html](http://www.webupd8.org/2011/03/install-nautilus-elementary-2322-in.html)

I discovered two posts on different forums describing the same problem . One person had to reinstall nautilus and the other was using an incompatible theme and was unable restore hidden items because the right click context menu would not work .

---

### Post by stinkeye on 2011-11-11
For 11.10...
In terminal
```
gsettings set org.gnome.nautilus.window-state start-with-toolbar true
```
Will bring it into view on the fly even with nautilus open.

---

