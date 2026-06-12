---
title: "Action to toggle workspaces/desktops in Lubuntu"
date: 2016-02-25
forum: Desktop Environments
---

### Post by Daniel_Rosehill on 2016-02-25
Hi guys,

I'm trying to set up a key binding in my lubuntu-rc.xml to toggle between my two work-spaces.

There are already pre-configured options for moving to the workspace to the left or the right, but I want to map a key to a  toggle option to display the other work-space than the one currently open (or if there were three or more workspaces to keep switching between all of them without hitting a 'stop' on either end).

I think what I need is some action along the lines of: if on workspace one, action is show workspace two. If on workspace two, action is show workspace one, etc.

This behavior isn't one of the [default keybindings.]("https://help.ubuntu.com/community/Lubuntu/Keyboard")

Is there a way to configure this?

---

### Post by vasa1 on 2016-02-25
I don't use workspaces but have you tried changing *<wrap>no</wrap>* to *<wrap>yes</wrap>*?

```
    <!-- Keybindings for desktop switching -->
    <keybind key="C-A-Left">
      <action name="GoToDesktop">
        <to>left</to>
        <wrap>yes</wrap>
      </action>
    </keybind>

```Run *openbox --reconfigure* to make changes to lubuntu-rc.xml take effect. 

Now, if you keep pressing *C-A-left*, you'll cycle through all available workspaces (desktops). I'm not sure this is what you asked for but it's based on what I read here: [http://crunchbang.org/forums/viewtopic.php?id=35258](http://crunchbang.org/forums/viewtopic.php?id=35258).

BTW, I'd think that *toggle* refers to alternating between two states or options.

---

### Post by Daniel_Rosehill on 2016-03-01
Sorted (turning on the wrap tag).

Thanks a lot!

---

### Post by vasa1 on 2016-03-01
Welcome!

---

