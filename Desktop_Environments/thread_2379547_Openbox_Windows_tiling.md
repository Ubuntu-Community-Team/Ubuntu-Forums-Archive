---
title: "Openbox Windows tiling"
date: 2017-12-06
forum: Desktop Environments
---

### Post by thanekrios on 2017-12-06
I love Lubuntu, my only beef is with** Openbox** that doesn't provide **Windows tiling** (maybe that's not the right name for it? What I mean is _when you drag your window to the left of the screen, and it automatically fills half the screen_, or when you drag it to one of the corners and automatically fills 1/4 of the screen).

I would appreciate any help you can provide. Thank you very much.

---

### Post by vasa1 on 2017-12-06
Openbox is a stacking window manager. However, with a little effort and compromise, you can get close to what you want. You can definitely get there with the keyboard.

You need to look at *~/.config/openbox/lubuntu-rc.xml*. The keyboard section should have something of relevance.

Two links of interest:
[https://pclosmag.com/html/Issues/201011/page09.html](https://pclosmag.com/html/Issues/201011/page09.html)
and
[https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse](https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse) (for an older Lubuntu but you get the idea)

---

### Post by ditsara on 2017-12-07
You can set hotkeys to tile windows into specific positions. For example, I use the following to map Win + left/right bracket to cover the left / right half of the screen:

```

    <keybind key="W-bracketright">
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>50%</width>
        <height>100%</height>
      </action>
    </keybind>
    <keybind key="W-bracketleft">
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>50%</width>
        <height>100%</height>
      </action>
    </keybind>

```

Further reference: [http://openbox.org/wiki/Help:Actions](http://openbox.org/wiki/Help:Actions)

---

### Post by vasa1 on 2017-12-07
And from my old notes, this is what I used:```
    <keybind key="W-Left">        # HalfLeftScreen
      <action name="Unmaximize"/>
      <action name="MoveResizeTo"><x>0</x><y>0</y><height>100%</height><width>50%</width></action>
    </keybind>
    <keybind key="W-Right">        # HalfRightScreen
      <action name="Unmaximize"/>
      <action name="MoveResizeTo"><x>0</x><y>0</y><height>100%</height><width>50%</width></action>
    </keybind>
    <keybind key="W-Up">        # HalfUpperScreen
      <action name="Unmaximize"/>
      <action name="MoveResizeTo"><x>0</x><y>0</y><width>100%</width><height>50%</height></action>
    </keybind>
    <keybind key="W-Down">        # HalfLowerScreen
      <action name="Unmaximize"/>
      <action name="MoveResizeTo"><x>0</x><y>0</y><width>100%</width><height>50%</height></action>
    </keybind>
    <keybind key="W-5">        # 50% width, height
      <action name="Unmaximize"/>
      <action name="MoveResizeTo"><x>center</x><y>center</y><width>50%</width><height>100%</height></action>
    </keybind>
    <keybind key="W-w">        # Center on screen
    <action name="MoveResizeTo"><x>center</x><y>center</y></action>
    </keybind>

```Just make sure to back up your original and to run```
openbox --reconfigure
```each time you edit and save the file to make sure there aren't any parsing errors and to make the changes take effect at once without having to log out.

---

### Post by thanekrios on 2017-12-07
Outstanding! Seems like I am keeping Lubuntu after all. I guess I should have read the documentation first. Thank you!

PS: Is there a program with a GUI available to see all of this commands?

---

### Post by thanekrios on 2017-12-07
Ok this is what it looks like now:

```
<keybind key="W-a">
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-s">
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
<keybind key="W-z">
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-x">
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>-0</y>
        <width>50%</width>
        <height>50%</height>
      </action>
    </keybind>

```

Thank you all!

Just in case:

W+a sends it to the top left side
W+s to the top right side
W+z to bottom left side
W+x to bottom right side

---

### Post by again? on 2017-12-07
> **thanekrios said:**
> PS: Is there a program with a GUI available to see all of this commands?
[HOW TO CREATE AND EDIT KEYBOARD SHORTCUTS IN LUBUNTU (OPENBOX)]("http://www.webupd8.org/2016/07/how-to-create-and-edit-keyboard.html")

---

### Post by thanekrios on 2017-12-09
Thank you! I appreciate all the help! :)

---

