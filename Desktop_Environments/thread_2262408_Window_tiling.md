---
title: "Window tiling"
date: 2015-01-24
forum: Desktop Environments
---

### Post by chaaderf on 2015-01-24
Window tiling is something I'd like to do to organize my work flow better. However, it looks like I need some detailed guidance.

1) Is it possible to edit the ~/.config/openbox/lubuntu-rc.xml file a little bit? There exist already keyboard shortcuts to tile windows to up/down/left/right edge of the screen. But I'd also like to have a shortcuts for corners too. Is that possible to do and if so, how?

2) If the community here suggests to installing a tiling window manager, I'd like to have instructions how to do it and use it properly. It seems that I always mix up window manager, display manager and all this kind of stuff... :oops: Maybe someone could give me a short nutshell how these things are working? The loooong wiki articles what I've read about these haven't given me any clear idea what's going on here.

Thank you!

---

### Post by vasa1 on 2015-01-24
> **chaaderf said:**
> ... However, it looks like I need some detailed guidance.

...The loooong wiki articles what I've read about these haven't given me any clear idea what's going on here.

...

In brief, try Crunchbang. It has scripts for hot corners.

---

### Post by Dennis N on 2015-01-24
If you are open to considering a Ubuntu flavor other than Lubuntu, I have noticed in Ubuntu MATE that you can create keybindings for these window actions:

maximize
maximize horizontally
maximize vertically
minimize
move to center
move to corner NE
move to corner NW
move to corner SE
move to corner SW
move to side E
move to side N
move to side S
move to side W

With Lubuntu, I believe you are stuck with the four edges.

---

### Post by vasa1 on 2015-01-24
[https://github.com/corenominal/cb-wmhacks](https://github.com/corenominal/cb-wmhacks)

---

### Post by vasa1 on 2015-01-24
> **Dennis N said:**
> If you are open to considering a Ubuntu flavor other than Lubuntu, I have noticed in Ubuntu MATE that you can create keybindings for these window actions:

maximize
maximize horizontally
maximize vertically
minimize
move to center
move to corner NE
move to corner NW
move to corner SE
move to corner SW
move to side E
move to side N
move to side S
move to side W

With Lubuntu, I believe you are stuck with the four edges.Lubuntu users can edit lubuntu-rc.xml as described in the Openbox wiki. For example, I have the following code which meets my current needs:```
    <!-- Keybindings for window tiling -->
    <keybind key="W-Left">        # HalfLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>0</x><y>0</y><height>100%</height><width>50%</width></action>
    </keybind>
    <keybind key="W-Right">        # HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>-0</x><y>0</y><height>100%</height><width>50%</width></action>
    </keybind>
    <keybind key="W-Up">        # HalfUpperScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>0</x><y>0</y><width>100%</width><height>50%</height></action>
    </keybind>
    <keybind key="W-Down">        # HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>0</x><y>-0</y><width>100%</width><height>50%</height></action>
    </keybind>
    <keybind key="W-5">        # 50% width, height
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo"><x>center</x><y>center</y><width>50%</width><height>100%</height></action>
    </keybind>
    <keybind key="W-w">        # Center on screen
      <action name="MoveResizeTo"><x>center</x><y>center</y></action>
    </keybind>
    <keybind key="W-7">        # Top left corner
      <action name="MoveResizeTo"><x>0</x><y>0</y></action>
    </keybind>
    <keybind key="W-8">        # Top right corner
      <action name="MoveResizeTo"><x>-0</x><y>0</y></action>
    </keybind>
    <keybind key="W-9">        # Bottom right corner
      <action name="MoveResizeTo"><x>-0</x><y>-0</y></action>
    </keybind>
    <keybind key="W-0">        # Bottom left corner
      <action name="MoveResizeTo"><x>0</x><y>-0</y></action>
    </keybind>

```

---

### Post by vasa1 on 2015-01-24
[s][http://openbox.org/wiki](http://openbox.org/wiki)[/s] [http://openbox.org/wiki/?title=Help:Actions&oldid=3651](http://openbox.org/wiki/?title=Help:Actions&oldid=3651) (for Openbox **3.5** which is the version present in Lubuntu 14.04) has this:

---

### Post by Dennis N on 2015-01-25
@vasa1

Pretty cool. The first four I knew from the lubuntu-rc.xml file. Are the others in the wiki? I can't find the sections you show in the image at the moment. Anyway, maybe you would take a look at my question on how to "untile" the windows back to their original size in Lubuntu. If you drag them away from the edges, they just stay the same size - even if you close and reopen. Not desirable. By coincidence, I just raised the question yesterday Jan 23. 

[http://ubuntuforums.org/showthread.php?t=2262171](http://ubuntuforums.org/showthread.php?t=2262171)

In Xubuntu, when dragged they just pop back to their old size they were before the tiling, and if you unmaximize, they also return to the same position they were before tiling. Very nice. That's what I was hoping was possible Lubuntu.

I haven't looked at any Openbox documentation or otherwise learned about it. Wonder why they just don't stick all those extra ones you have in with the rest so everyone can use them?

---

### Post by vasa1 on 2015-01-25
I'm sorry! This is the correct link **for Openbox 3.5**: [http://openbox.org/wiki/?title=Help:Actions&oldid=3651](http://openbox.org/wiki/?title=Help:Actions&oldid=3651)

There's also documentation for Openbox 3.6 but Lubuntu 14.04 comes with Openbox 3.5.

I copied or modified stuff I found from there and from
[https://bbs.archlinux.org/viewtopic.php?id=93126](https://bbs.archlinux.org/viewtopic.php?id=93126)
and
[http://crunchbang.org/forums/viewtopic.php?id=13968](http://crunchbang.org/forums/viewtopic.php?id=13968)

I saw your question about untiling soon after you posted but because I couldn't say anything helpful, I kept quiet :(  I use the keyboard for moving or resizing windows. The wiki link has this:
```
 Unmaximize

Unmaximizes the window in the directions specified, and return it to its pre-maximized dimensions. 
```

But I've never used it.

---

### Post by Dennis N on 2015-01-25
@vasa1

Thanks very much for the links. I will be looking them over - especially the 'unmaximize' reference. That problem (untiling) is really an openbox issue, not Lubuntu's. I will just consider the untiling capability as "not yet implemented".

---

### Post by chaaderf on 2015-01-25
Thank you so much, vasa1! I'll edit the file and let's see how it goes. If it works, I'll also mark this thread as solved. Thank you! ^^

---

