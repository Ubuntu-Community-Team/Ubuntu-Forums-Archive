---
title: "New butons for Nautilus"
date: 2005-06-21
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-21
This might be the wrong place for this one. I have some scripts which are awesome. They're currently in my Nautilus scripts menu. But really they'd be better suited as buttons. 

Open terminal here
Open search here

Is there anywy of doing that? I already looked in gconf and there's no way to add new bits. 

Cheers guys, you're stars

---

### Post by jcooper on 2005-06-22
I believe the only way to "extend" Nautilus is via plugins (i.e. writing software). Some existing applications add entries to the right-click menu, though I'm not sure exactly how.

---

### Post by jnoreiko on 2005-06-22
Huh.
I don't even *see* a scripts menu. It's mentioned in the help file, but nothing on the screen!

---

### Post by Dave_is_sexy on 2005-06-22
It's not shown until you put a script in the scripts folder. 

the scripts folder is @ ~.gnome2/nautilus-scripts

Essential scripts include:

TERMINAL HERE
```

#!/bin/bash
    if [ -n "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
        set $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
        if [ $# -eq 1 ]; then
            destination="$1"
            # Go to file's directory if it's a file
            if [ ! -d "$destination" ]; then
                destination="`dirname "$destination"`"
            fi
        else
            zenity --error --title="Error - Open terminal here" \
               --text="You can only select one directory."
            exit 1
        fi
    else
        destination="`echo "$NAUTILUS_SCRIPT_CURRENT_URI" | sed 's/^file:\/\///'`"
    fi
    
    # It's only possible to go to local directories
    if [ -n "`echo "$destination" | grep '^[a-zA-Z0-9]\+:'`" ]; then
        zenity --error --title="Error - Open terminal here" \
           --text="Only local directories can be used."
        exit 1
    fi
    
    cd "$destination"
    exec x-terminal-emulator
```

SEARCH HERE
```

    cd $NAUTILUS_SCRIPT_CURRENT_URI
    exec gnome-search-tool
```

OPEN AS ROOT
```
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done
```

---

