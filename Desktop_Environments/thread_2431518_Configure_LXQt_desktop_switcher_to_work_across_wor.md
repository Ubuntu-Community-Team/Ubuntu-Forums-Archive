---
title: "Configure LXQt desktop switcher to work across workspaces?"
date: 2019-11-17
forum: Desktop Environments
---

### Post by qajaq on 2019-11-17
I installed Lubuntu 18.04 a few months ago, after several years of using Kubuntu in various LTS versions. The LXQt desktop is taking some getting used to, but for the most part, I can learn to use the differences -- except for one. In all KDE environments, when I use the Alt-Tab key to switch from one application to another, I can make the move regardless of which workspace (I usually have seven) I'm in and which one the target application is in. For example, if I'm writing something in a LibreOffice Write file in workspace #1, I can use (in KDE) the Alt-Tab key-combination to switch to Firefox in workspace #2. In the Lubuntu installation, the Alt-Tab combination will only allow me to switch among whatever applications I have open in the same workspace (in this example, workspace #1).

I haven't found a way to switch among applications globally in Lubuntu's LXQt. Is it possible? Or should I try installing a different desktop environment? Or will I have to give up on Lubuntu if I want this functionality?

---

### Post by Dennis N on 2019-11-17
> when I use the Alt-Tab key to switch from one application to another, I can make the move regardless of which workspace...
Great question, and the answer is not easy to find. Lubuntu uses an .xml file to configure this (and many other things) Here's how to change Alt-Tab to switch between all desktops (workspaces):

You must edit parts of the file **~/home/.config/openbox/lxqt-rc.xml**

Find and edit this section in the file to fix Alt-Tab. The line in red needs to be added:
 
```
   
<keybind key="A-Tab">
      <action name="NextWindow">
        [COLOR="#FF0000"]<allDesktops>yes</allDesktops>[/COLOR]
        <finalactions>
          <action name="Focus"/>
          <action name="Raise"/>
          <action name="Unshade"/>
        </finalactions>
      </action>
</keybind>

```

Also do the edit that follows to fix Alt+Shift+Tab:

```
 <keybind key="A-S-Tab">
      <action name="PreviousWindow">
        [COLOR="#FF0000"]<allDesktops>yes</allDesktops>[/COLOR]
        <finalactions>
          <action name="Focus"/>
          <action name="Raise"/>
          <action name="Unshade"/>
        </finalactions>
      </action>
 </keybind>

```
Now it's ready to go!

---

### Post by qajaq on 2019-11-17
Beautiful! So simple and elegant, for all that it's so obscure. It works a charm -- ***thank you!***

---

