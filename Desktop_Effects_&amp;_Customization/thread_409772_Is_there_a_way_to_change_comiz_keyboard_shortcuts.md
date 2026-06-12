---
title: "Is there a way to change comiz keyboard shortcuts?"
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by dr_d12 on 2007-04-14
Hi all,
I have two "extra" arrow keys on my X40 that I use to switch between workspaces. I used Xmodmap to assign them as F21 and F22, then used the keyboard shortcuts preferences to set them for switching workspaces. With compiz on, this doesn't work. 

Is there a way to get "F21" to mean  "CTRL+ALT+Arrow left"? 

(I tried interchanging F21 with Ctrl+Alt+arrow left in my Xmodmap file but to no avail)

Thanks for your help,
Dave

---

### Post by dr_d12 on 2007-04-16
So, here is how i got the thinkpad "back" and "forward" keys to switch Compiz workspaces:

I already had an .Xmodmap file in my home directory that says:
```

keycode 234 = F21
keycode 233 = F22

```
and a startup program in my session running $HOME/.Xmodmap

All I needed to do is to run
```

gconf-editor

```
find apps/compiz/plugins/rotate/allscreens/options/

right click and edit 
/rotate_right_key from '<Control><Alt>Right' to 'F22'
/rotate_left_key from '<Control><Alt>Left' to 'F21'

Voila. One key to flip the cube instead of 3.
-Dave

---

