---
title: "Minimize on click"
date: 2014-04-26
forum: Desktop Environments
---

### Post by cranerja on 2014-04-26
I've read that minimize on click works in 14.04, but the only way I've seen is with ccsm. I'd rather not install that program. Is there a way to enable from the terminal?

---

### Post by grumblebum2 on 2014-04-26
You can enable the setting using **dconf-editor** @ the path org/compiz/profiles/plugins/unityshell launcher-minimize-window
Don't know how you would do it via command line though because the key has no schema.

**[COLOR="#FF0000"]Edit[/COLOR]**:Here we go this terminal command will enable...
```
gsettings set org.compiz.unityshell:/org/compiz/profiles/unity/plugins/unityshell/ launcher-minimize-window true
```

---

### Post by cranerja on 2014-04-26
Thank you so much!

---

