---
title: "Restoring Alt + Tab to switch between windows of current Workspace"
date: 2011-10-15
forum: Desktop Environments
---

### Post by blavthefaur on 2011-10-15
The default use of Alt + Tab in 11.10 really threw me for a loop, but here's how I restored the Application Switcher to switch between windows on the current Workspace only.

First, in CompizConfig > Desktop > Unity plugin > Switcher (second tab), disable the 'Key to start the switcher'. Next, in CompizConfig > Window Management, enable the Static Application Switcher plugin. If asked, disable any conflicts with the Unity plugin.

After this, Alt + Tab should only switch between the windows on your current Workspace.

---

### Post by vankich on 2011-10-17
I'm wondering where did you find CompizConfig. Cannot see it in System Settings, nor can find it with the Natty search tool.

---

### Post by Mobby on 2011-10-17
To get CompizConfig do...

```
sudo apt-get install compizconfig-settings-manager
```

I've not tried this in 11.10 yet but it certainly works in 11.04 and earlier and it sounds like the tool works happily in 11.10.

Once installed open Unity's dash (superkey/"Windows" Button ;)) and start typing "compiz" you should see the tool then.

Cheers,
Mobby

---

### Post by vankich on 2011-10-18
Yeap. Worked just well, but this disables the cool Compiz switcher.

It will be really nice if we have option to make the Compiz switcher to switch programs for the current workspace or globally.

---

### Post by erny on 2011-11-20
> **blavthefaur said:**
> The default use of Alt + Tab in 11.10 really threw me for a loop, but here's how I restored the Application Switcher to switch between windows on the current Workspace only.

First, in CompizConfig > Desktop > Unity plugin > Switcher (second tab), disable the 'Key to start the switcher'. Next, in CompizConfig > Window Management, enable the Static Application Switcher plugin. If asked, disable any conflicts with the Unity plugin.

After this, Alt + Tab should only switch between the windows on your current Workspace.
Excellent, works well. I don't miss the unity switcher, I use:
 - alt+tab: switch between windows of the same workspace
 - ctrl+alt+tab: switch between windows of all workspaces
 - ctrl+alt+left/right/up/down: switch between workspaces
 - alt+º (key above tab): switch between windows of same application (type)
 - super+w: expose all windows of all workspaces
 - ctrl+alt+up: expose all windows of current workspace

Thanks a lot.

---

