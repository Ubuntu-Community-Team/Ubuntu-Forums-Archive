---
title: "Xubuntu Set Above window management"
date: 2015-12-02
forum: Desktop Environments
---

### Post by lsutiger on 2015-12-02
I recently changed from Gnome to Xfce on my 14.04 install. One of the items I was using with Compiz is a window theme where I could set a window to always be above all windows, which was particularly helpful in my work.
Is there a way to do this in Xubuntu? I searched a bit and could not find something similar.

---

### Post by CantankRus on 2015-12-02
You can set up a keyboard shortcut to toggle the currently focused window "above".
Requires the installation of wmctrl (80kb).
```
sudo apt-get install wmctrl
```

As the command to execute for your chosen shortcut key use...
```
wmctrl -r :ACTIVE: -b toggle,above
```

***Re-reading your post, what you probably need is devilspie.
```
sudo apt-get install devilspie
```

This is how I would set gnote to be always on top.
Create a config file @ "$HOME/.devilspie/[COLOR="#FF0000"]gnote[/COLOR].ds"
```
(if (is (application_name) "[COLOR="#FF0000"]gnote[/COLOR]")
        (begin
                (above)
         )
 )

```


Substitute [COLOR="#FF0000"]gnote[/COLOR] with your application.

Then  put "devilspie" in your startups.

---

