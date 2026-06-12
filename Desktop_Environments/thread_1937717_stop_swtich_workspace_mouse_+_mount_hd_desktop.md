---
title: "stop swtich workspace mouse + mount hd desktop"
date: 2012-03-08
forum: Desktop Environments
---

### Post by overkill22 on 2012-03-08
1)how can i disable switch workspace with the weel of the mouse ? (i have no mouse but trackpad so it is very unusefull)

2) when i put in a usb stick how can i see the hd mounted on a desktop ? (now i must open pcmanfm)

thank you

---

### Post by chestnyh on 2012-03-18
1. To disable try this:
go to ~/.config/openbox and find in lubuntu-rc.xml or lxde-rc.xml lines with
```

      <mousebind button="Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>

```
and delete or change these commands.
2. There is a tab Volume Management in preferences of pcmanfm. Enable all 3 items and hd will be mounted automatically with pop-up window.

---

### Post by overkill22 on 2012-03-19
> **chestnyh said:**
> 1. To disable try this:
go to ~/.config/openbox and find in lubuntu-rc.xml or lxde-rc.xml lines with
```

      <mousebind button="Up" action="Click">
        <action name="DesktopPrevious"/>
      </mousebind>
      <mousebind button="Down" action="Click">
        <action name="DesktopNext"/>
      </mousebind>

```and delete or change these commands.
2. There is a tab Volume Management in preferences of pcmanfm. Enable all 3 items and hd will be mounted automatically with pop-up window.

thank you,
i deleted all the function with desktopnext and previous (also mosuebind button= A+Down and similar) did i do right ?

---

