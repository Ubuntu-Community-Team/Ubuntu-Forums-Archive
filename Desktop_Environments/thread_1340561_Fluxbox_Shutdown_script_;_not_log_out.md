---
title: "Fluxbox Shutdown script ; not log out"
date: 2009-11-28
forum: Desktop Environments
---

### Post by flux_user on 2009-11-28
Hello I thought I would post a quick script that can be used to logout and shutdown the system for the Fuxbox users. 

There were 2 or 3 shutdown scripts on the Fluxbox Wiki; I took bits and pieces that I liked from each script and combined them into my own variation.

Shutdown happens after clicking "Ok" without a password prompt.  The only thing you needs is zenity; which I think is installed by default; well, fluxbox is also needed.  :-)


```
#! /bin/bash

# Date: Nov. 12, 2009
# Purpose: Shutdown Fluxbox


zenity --question --text "Are you sure you want to shutdown?"

if [[ $? -eq 0 ]]
then
    gdmflexiserver -a -c 'SET_LOGOUT_ACTION HALT'
    kill -TERM $(xprop -root _BLACKBOX_PID | awk '{print $3}')
fi

```

Just added into your $HOME/.fluxbox/menu  .  Make sure you use the full path to the script in the menu entry.  Here is my menu entry:

```
[exec] (Shutdown Now) {$HOME/.scripts/really.shutdown.sh}
```

---

