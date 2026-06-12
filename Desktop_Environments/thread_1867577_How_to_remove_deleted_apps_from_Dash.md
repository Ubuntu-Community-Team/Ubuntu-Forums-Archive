---
title: "How to remove deleted apps from Dash?"
date: 2011-10-23
forum: Desktop Environments
---

### Post by JayKav on 2011-10-23
I had a manually installed copy of Eclipse when I upgraded from 10.04 to 11.10. I deleted Eclipse but a '?' icon labelled as Eclipse is still showing in Dash home. How do I remove it?

---

### Post by galacticaboy on 2011-10-23
> **JayKav said:**
> I had a manually installed copy of Eclipse when I upgraded from 10.04 to 11.10. I deleted Eclipse but a '?' icon labelled as Eclipse is still showing in Dash home. How do I remove it?

try 
```
sudo apt-get autoclean autoremove
```

---

### Post by JayKav on 2011-10-23
> **galacticaboy said:**
> try 
```
sudo apt-get autoclean autoremove
```

That removed the '?' from the icon but it's still there. Clicking on it doesn't do anything.

---

### Post by JayKav on 2011-10-23
Searched all files under /usr for the string "Eclipse". Only found one. Removing it had no effect.

Tried ccsm, thinking it might have some unity options. Unfortunately just running ccsm (didn't actually change any settings, even temporarily) wrecked the desktop. The top menu bar disappeared and there were no icons on the left. It also caused shutdown to hang.

unity --reset just produced a series of GL errors (unable to bind image to texture etc.). Also a "this should never happen, you probably ought to file this as a bug". Didn't say what the bug was though.

Re-installed 11.10 over the existing installation. That cured the shutdown problem but no change to the desktop. Unfortunately I opted for auto-login so I lost the chance to disable unity. 

Re-installed 11.10 a second time with auto-login disabled. Unity 2D works but not the regular unity. However it speeds up remote desktop considerably so I think I'll be staying with the 2D version.

Still have the unused icon in Dash. The '?' came back after the re-install.

Will post the ccsm issue again with a more descriptive title.

---

### Post by jerrycal on 2011-10-23
> **JayKav said:**
> Searched all files under /usr for the string "Eclipse". Only found one. Removing it had no effect.

Tried ccsm, thinking it might have some unity options. Unfortunately just running ccsm (didn't actually change any settings, even temporarily) wrecked the desktop. The top menu bar disappeared and there were no icons on the left. It also caused shutdown to hang.

unity --reset just produced a series of GL errors (unable to bind image to texture etc.). Also a "this should never happen, you probably ought to file this as a bug". Didn't say what the bug was though.

Re-installed 11.10 over the existing installation. That cured the shutdown problem but no change to the desktop. Unfortunately I opted for auto-login so I lost the chance to disable unity. 

Re-installed 11.10 a second time with auto-login disabled. Unity 2D works but not the regular unity. However it speeds up remote desktop considerably so I think I'll be staying with the 2D version.

Still have the unused icon in Dash. The '?' came back after the re-install.

Will post the ccsm issue again with a more descriptive title.


Why don't you try to install gnome-desktop and see if you can remove the icons in that.

---

### Post by JayKav on 2011-10-23
> **jerrycal said:**
> Why don't you try to install gnome-desktop and see if you can remove the icons in that.

Brilliant. Thanks! Why didn't I think of that?

---

