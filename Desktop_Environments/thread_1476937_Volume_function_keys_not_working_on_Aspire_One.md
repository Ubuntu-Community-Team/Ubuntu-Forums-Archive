---
title: "Volume function keys not working on Aspire One"
date: 2010-05-08
forum: Desktop Environments
---

### Post by Pickel on 2010-05-08
Hi,
As the topic indicates i cannot get the volume keys to work on my aspire one A110L with lubuntu.
The other function keys work and i can change the volumen on the applet itself by clicking it. 
Could someone help me or point me in the direction of a thread that has solved this.

This question was only valid for lubuntu or LXDE environment.

---

### Post by Pickel on 2010-05-09
Ok so i found the solution.
I needed to add an .Xmodmap in the home directory.
```

keycode 121 = XF86AudioMute
keycode 122 = XF86AudioLowerVolume
keycode 123 = XF86AudioRaiseVolume

```

and add the following to the .config/openbox/lubuntu-rc.xml

```

   <keybind key="XF86AudioMute">
      <action name="Execute">
       <command>amixer sset Master toggle</command>
      </action>
    </keybind>
     <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
       <command>amixer sset Master 5%+</command>
      </action>
    </keybind>
     <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
       <command>amixer sset Master 5%-</command>
      </action>
    </keybind>

```


I think i consider this a bug so i will file it.

---

### Post by zoomy942 on 2010-05-25
> **Pickel said:**
> Ok so i found the solution.
I needed to add an .Xmodmap in the home directory.
```

keycode 121 = XF86AudioMute
keycode 122 = XF86AudioLowerVolume
keycode 123 = XF86AudioRaiseVolume

```

and add the following to the .config/openbox/lubuntu-rc.xml

```

   <keybind key="XF86AudioMute">
      <action name="Execute">
       <command>amixer sset Master toggle</command>
      </action>
    </keybind>
     <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
       <command>amixer sset Master 5%+</command>
      </action>
    </keybind>
     <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
       <command>amixer sset Master 5%-</command>
      </action>
    </keybind>

```


I think i consider this a bug so i will file it.

can you go through how you did that (making the file and all that) so I can do it too?  I love lubuntu but i have the same problem as you.

---

### Post by zoomy942 on 2010-05-27
bump?

---

### Post by zoomy942 on 2010-05-29
bump..  anyone?

---

### Post by Pickel on 2010-08-21
hi zoomy942

Sorry i didnt see your questions earlier.

When i worked on another computer with lubuntu i found that i didn't need to add the .Xmodmap file.

You need to modify the
 .config/openbox/lubuntu-rc.xml 
thou.
Since you ask i assume you are not too used to vi and command line editing so i will go through the steps via gui tools.

1: open the file browser
2: issue ctrl+h to allow it to show your hidden files
3: there should be a folder .config in your home directory, open it
4: open the folder openbox
5: right click on the lubuntu-rc.xml file and select open with a nd select a text editor, i think leafpad is default in lubuntu.
6: Find the line <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative when not using gnome-power-manager or xfce4-volumed) -->
7: Add the code described in post #2 that should be added in this file below the <!-- Keybindings for Multimedia Keys and LCD Backlight (alternative when not using gnome-power-manager or xfce4-volumed) --> line
8: save
9: exit and reboot, i know you could probably reload lxde but rebooting is simpler.
10: try it out, should work now.

---

### Post by rafaelcarvao on 2010-09-16
dont install lxde-settings-daemon, this will break the default lxde session

---

