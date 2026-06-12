---
title: "Show window contents while dragging (16.04.4 LTS)"
date: 2018-07-14
forum: Desktop Environments
---

### Post by citizensnips on 2018-07-14
A few days ago, Ubuntu inexplicably stopped showing window contents while dragging.  This feature was enabled by default since the initial installation, but now all I see when I drag a window is a transparent maroon box.  How can I restore this feature?  I've done a search already but was not able to find a setting that changes this.  I am using the default window manager and my installation was done using the default settings.

---

### Post by citizensnips on 2018-07-19
[FONT=arial]I have no idea how my window drag/resize behavior was changed, but here is the fix:[/FONT]

[FONT=arial]1. Install the CompizConfig Settings Manager:[/FONT]

```

[FONT=courier new]sudo apt-get install compizconfig-settings-manager[/FONT]

```

[FONT=arial]2. Run the CompizConfig Settings Manager[/FONT]

```

[FONT=courier new]ccsm[/FONT]

```

3. Go to: Window Management -> Resize Window -> General -> Default Resize Mode and change it to Normal.
4. Go to: Window MAnagement -> Move Window -> Appearance -> Default Moving Window Mode and change it to Normal.

---

