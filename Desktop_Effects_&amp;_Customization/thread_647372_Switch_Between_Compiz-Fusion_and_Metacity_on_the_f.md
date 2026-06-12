---
title: "Switch Between Compiz-Fusion and Metacity on the fly"
date: 2007-12-22
forum: Desktop Effects &amp; Customization
---

### Post by SnakeByte29 on 2007-12-22
I just installed Gutsy on my laptop, which had previously been running Feisty) and I've started using Compiz-Fusion for the first time in stead of Beryl. What I was wondering is if there is a way to switch between Compiz-Fusion and Metacity as a window manager on the fly, like I used to be able to switch between Beryl and Metacity whenever I wanted with the Beryl settings manager that sat in the Notification Area. The reason I want to be able to do this is that some fullscreen programs (specifically Unreal Tournament 2004 and other games) work much better in Metacity than Compiz. Can anyone help?

---

### Post by z0mbie on 2007-12-22
You can assign shortcuts to do the following in** /apps/metacity/keybinding_commands** with **gconfig-editor**:

```
metacity --replace
```

and

```
compiz --replace
```

Then assign a key for those shortcuts respectively under **/apps/metacity/global_keybindings** with **gconfig-editor**.

---

