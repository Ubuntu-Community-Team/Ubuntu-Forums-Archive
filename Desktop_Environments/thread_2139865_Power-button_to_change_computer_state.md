---
title: "Power-button to change computer state"
date: 2013-04-28
forum: Desktop Environments
---

### Post by Svante65 on 2013-04-28
I found this on this link: [https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login](https://help.ubuntu.com/community/Lubuntu/Boot_Install_Login)
[h=2]I want to bind the power-button to change computer state, how do I do it?[/h] In LXTerminal: 

leafpad ~/.config/openbox/lubuntu-rc.xmlLocate the <keyboard> section and add following lines. 

<keybind key="XF86PowerOff">      <action name="Execute">        <command>lubuntu-logout</command>      </action> </keybind>Now the power-button should call the shutdown menu, where you can choose the next state your computer should go to. 
To find the name for the <keybind key="<name>"> line of special keys like XF86PowerOff do: 

xev | grep "keycode"Which grabs the line with the name from xev. Just press the key you want to assign to find the name. 
[HR][/HR]
But I need in depth explanation to get it right.
As it is now, nothing happens when I push the Power-button. I want it to work like in Ubuntu.

---

