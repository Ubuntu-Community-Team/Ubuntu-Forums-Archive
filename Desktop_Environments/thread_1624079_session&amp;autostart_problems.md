---
title: "session&amp;autostart problems"
date: 2010-11-17
forum: Desktop Environments
---

### Post by dawnlove on 2010-11-17
I'm running xubuntu 10,04 32b. When I put a apt. into sessions&startup autostart and I reboot the apt. wants to load twice. For Quodlibet I just removed it from autostart and all is good. But cairo-dock I have in autostart "cairo-dock -o" and cairo-dock number two {that loads} needs to be told "open GL" or not, so removing from autostart won't fix.
 The question is how do I stop cairo-dock #2 from auto starting?
many thanx for any help

---

### Post by tom4everitt on 2010-11-18
Sorry, I don't get it. Why can you not just remove the items from the auto-start list?

---

### Post by dawnlove on 2010-11-18
> **tom4everitt said:**
> Sorry, I don't get it. Why can you not just remove the items from the auto-start list?
when I remove from autostart it auto starts anyway {with out the openGL option} and I think I need to edit something to stop this I'm sure but I don't know what? thanx for response

---

### Post by tom4everitt on 2010-11-18
Oh, I see. I don't know enough about xubuntu to know of any other place to edit other than the place you are already referring to. Are you sure you have removed all instances of cairo-dock from there? Could it be that it is started by some other application that is auto-started? It would certainly look like bad design if not all the users auto-starts were handled from the same place. 

Uninstalling cairo-dock is not an option? Or, if you don't mind an ugly solution, you could auto-start a script that kills the cairo-dock. It should suffice with the one line: 
```

killall cairo-dock

```

---

