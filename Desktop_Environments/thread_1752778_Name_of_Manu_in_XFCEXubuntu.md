---
title: "Name of Manu in XFCE/Xubuntu"
date: 2011-05-08
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-05-08
If I center click my mouse on the Xubuntu desktop, a menu pops up which allows me to choose between multiple workspaces.

I'd like to know the name of this menu so that I can also create a keyboard shortcut. Does anyone know?

---

### Post by Frogs Hair on 2011-05-08
Menus for xfce can be found in /etc/xdg/menus . I could not find a specific name only that it is not referred to as a context menu . I found  much information about editing menus in xfce , but nothing about what they are called .

---

### Post by neu5eeCh on 2011-05-08
Thanks Frogs, that's a good lead. I'll try assigning random menus to a random keystroke and maybe I'll stumble across the correct one.

---

### Post by Toz on 2011-05-08
The:
```
xfdesktop --windowlist
```
command will popup this menu.

---

### Post by neu5eeCh on 2011-05-10
> **Toz said:**
> The:
```
xfdesktop --windowlist
```command will popup this menu.

Briliant! Just saw your response. Thankyou. I've got it set up under Super-Shift-Z. 

Not to look the gift horse in the mouth, but I wonder if I could bind this key combination to my center mouse button? I'm trying btnx but it doesn't seem to bind?

---

### Post by Toz on 2011-05-10
By default it is bound to the middle mouse button. Does yours not bring it up when clicked?

EDIT: I mean the windowlist is bound to the middle button, not the key combination.

---

### Post by neu5eeCh on 2011-05-10
> **Toz said:**
> By default it is bound to the middle mouse button. Does yours not bring it up when clicked?

EDIT: I mean the windowlist is bound to the middle button, not the key combination.

Only on the desktop, but not in any app window. This is why I wanted a key combination.

---

### Post by Toz on 2011-05-10
> **VTPoet said:**
> Only on the desktop, but not in any app window. This is why I wanted a key combination.

Oh, ok. Have a look at xbindkeys.

1. Install it:```
sudo apt-get install xbindkeys
```

2. Create initial config file:```
xbindkeys --defaults > $HOME/.xbindkeysrc
```

3. Edit ~/.xbindkeysrc and add to the end of the file:```
"xfdesktop --windowlist"
b:2
```

4. Re-read the configuration file:```
kill -HUP `pidof xbindkeys`
```

5. Test. (b:2 is the middle mouse button - press it anywhere to bring up that menu). If you want this to work on every login, add xbindkeys to your autostart.

---

### Post by ManualSparrow on 2011-05-10
Can you bind it to a window corner?

---

### Post by Toz on 2011-05-10
> **ManualSparrow said:**
> Can you bind it to a window corner?

Not that I know of. The xfdesktop command doesn't offer that option. You might want to have a look at xdotool - [http://www.semicomplete.com/projects/xdotool/](http://www.semicomplete.com/projects/xdotool/)

---

### Post by neu5eeCh on 2011-05-11
> **Toz said:**
> 
**4.** Re-read the configuration file:```
kill -HUP `pidof xbindkeys`
```5. Test. (b:2 is the middle mouse button - press it anywhere to bring up that menu). If you want this to work on every login, add xbindkeys to your autostart.

Beautiful. 

Everything worked as advertized except for the last command. At first, I couldn't sort out what was wrong. Just logged out and back in.

But shouldn't the command be "killall"?

```
killall -HUP xbindkeys
```

---

### Post by Toz on 2011-05-11
Yes, either way will work. I guess I do it the first way out of old habits. 

Curious why the first one didn't work for you. Did you enclose the "pidof xbindkeys" part in the accent character (the one below the tilde)?

---

### Post by neu5eeCh on 2011-05-11
> **Toz said:**
> Yes, either way will work. I guess I do it the first way out of old habits. 

Curious why the first one didn't work for you. Did you enclose the "pidof xbindkeys" part in the accent character (the one below the tilde)?

I just tried it again, thinking if I received an error I would forward it. Copied and pasted as before. It worked this time.

I have no explanation? :confused: None. But that's good.

---

