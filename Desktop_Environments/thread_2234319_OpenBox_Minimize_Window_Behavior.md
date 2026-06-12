---
title: "OpenBox Minimize Window Behavior"
date: 2014-07-14
forum: Desktop Environments
---

### Post by Sir_Sword on 2014-07-14
I've noticed in that in OpenBox if I press CTRL + Space, it causes the current window to minimize.  This tends to get in the way of some games.  Is there some way to change this behavior?

---

### Post by grumblebum2 on 2014-07-14
Have you looked at the openbox wiki? [http://openbox.org/wiki/Help:Bindings](http://openbox.org/wiki/Help:Bindings)
I believe the minimize shortcut is called "Iconify".

eg you may see similar in the rc.xml....
  ```
<keybind key="A-F3">
      <action name="Iconify"/>
  </keybind>
```

---

### Post by Sir_Sword on 2014-07-14
> **grumblebum2 said:**
> Have you looked at the openbox wiki? [http://openbox.org/wiki/Help:Bindings](http://openbox.org/wiki/Help:Bindings)
I believe the minimize shortcut is called "Iconify".

eg you may see similar in the rc.xml....
  ```
<keybind key="A-F3">
      <action name="Iconify"/>
  </keybind>
```

Thanks for replying.  I looked through /etc/xdg/openbox/rc.xml and there were no minimize or iconify bindings set for control or "C" in this instance.  I searched through the whole fine and nothing in there explains the CTRL + Space behavior I'm experiencing.  I don't have a local ~/.config version of the OpenBox configs so I know that's not causing it either.

---

### Post by bapoumba on 2014-07-14
Just to note that <ctrl><space> changes the keyboard layout here, that is the default ibus input method switch. No custom shortcuts. The only shortcut a <space> is involved in is the following in both /home/bapoumba/.config/openbox/rc.xml and /home/bapoumba/.config/openbox/lubuntu.rc.xml (runing lubuntu 14.04), which works :

```
 <keybind key="A-space">
      <action name="ShowMenu">
        <menu>client-menu</menu>
      </action>
    </keybind>
```

Iconify is a mouse action, which does work too (I use it often) :
```
<context name="Iconify">
      <mousebind button="Left" action="Press">
        <action name="Focus"/>
        <action name="Raise"/>
      </mousebind>
      <mousebind button="Left" action="Click">
        <action name="Iconify"/>
      </mousebind>
    </context>
```

As you have mentioned games, would one of them have changed your shortcuts ?

---

### Post by Sir_Sword on 2014-07-14
After doing more experimenting, it would appear that pressing CTRL + Space when using a program in a window doesn't really do anything, but for some reason CTRL + Space when using a full screen OpenGL application causes strange behavior.

For instance, in Steam Source games it causes the game to minimize.  In Minecraft, it causes the game to exit full screen and start running in a small window.  However the Minecraft settings still say they're set for full screen and if I exit Minecraft and reload it it goes back to full screen.

---

### Post by grumblebum2 on 2014-07-14
You could do as in the wiki and copy the file from /etc/xdg/openbox/rc.xml to ~/.config/openbox/rc.xml
then edit **~/.config/openbox/rc.xml** and [COLOR="#FF0000"]comment out[/COLOR] the **ShowMenu** keybind ...
```
[COLOR="#FF0000"]<!--[/COLOR]  <keybind key="A-space">
    <action name="ShowMenu"><menu>client-menu</menu></action>
  </keybind> [COLOR="#FF0000"]-->[/COLOR]
```

---

