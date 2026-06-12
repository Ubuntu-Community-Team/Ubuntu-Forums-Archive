---
title: "how do I get the dock to stay on the screen?"
date: 2012-03-05
forum: Desktop Environments
---

### Post by blackturbokitty on 2012-03-05
It seems the dock hides out by default and then surprises me when my mouse is hanging out there for too long. It's annoying. How do I make the dock stay on the screen all the time? I tried searching the forum but no one else seems to be bothered by this.

---

### Post by bogan on 2012-03-06
Hi!, **blackturbokitty**.

Two easy ways:

first: run ccsm >Desktop>Unity-Plug-In and set 'Hide' to 'Never'

second: run 'MyUnity'>Launcher>behaviour and set to 'Fixed'

'compiz config settings manager' is available from Software Center.

You can find 'MyUnity' from Google.

Chao!, **bogan**.

---

### Post by blackturbokitty on 2012-03-06
I dont understand. The interface provides no options. Are there any commands I can type into BASH? So far that's the only way to get anything useful working in this and I'm totally lost with that.

---

### Post by stinkeye on 2012-03-06
> **blackturbokitty said:**
> I dont understand. The interface provides no options. Are there any commands I can type into BASH? So far that's the only way to get anything useful working in this and I'm totally lost with that.

Terminal command to set the unity launcher to never hide...
```
gconftool-2 --type int --set "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode" 0
```



To reset to default use...
```
gconftool-2 --unset "/apps/compiz-1/plugins/unityshell/screen0/options/launcher_hide_mode"
```

---

### Post by blackturbokitty on 2012-03-07
I tried that a couple times, even tried with sudo, though that didnt work. Though thanks for trying.

Is it possible to put a different window manager onto ubunto? I find the interface kind of cumbersome and limiting.

---

### Post by dupek64 on 2012-03-31
Download "MyUnity". Play with settings.

---

