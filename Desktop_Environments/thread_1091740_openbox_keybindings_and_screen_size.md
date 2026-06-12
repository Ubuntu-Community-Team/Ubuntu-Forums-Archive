---
title: "openbox keybindings and screen size"
date: 2009-03-09
forum: Desktop Environments
---

### Post by starfry on 2009-03-09
Hello openbox users!

I an trying to write key bindings to resize my windows. To do this properly I need to know the width of the screen. For example:
```

    <!-- Put the window in the bottom right corner -->
    <keybind key="W-Next">
      <action name="Raise" />
      <action name="UnMaximizeFull" />
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>-0</y>
        <width>960</width>
        <height>600</height>
      </action>
    </keybind>

```

Now, here I have hard coded the width and height to be half the screen width and height, which is fine if I know the screen size is 1920x1200.

What I want is a way of saying, for example, <width>screenwidth/2</width>

Is this possible at all?

thanks.

---

### Post by kapital on 2009-08-27
I am curious about this too! It would be nice to make my shortcuts future proof.

---

