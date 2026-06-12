---
title: "{SMAPI for Stardew Valley Mods} Can't seem to get it to work..."
date: 2018-12-04
forum: Gaming &amp; Leisure
---

### Post by antlers-teeth05 on 2018-12-04
So I'm trying to Mod Stardew Valley. I downloaded SMAPI and extracted the files, unfortunately, I'm a novice at coding and can't figure out what this means. Nor what I am sposed to do.

#!/bin/bash
# Run the SMAPI installer through Mono on Linux or Mac.


# Move to script's directory
cd "`dirname "$0"`"


# get cross-distro version of POSIX command
COMMAND=""
if command -v command >/dev/null 2>&1; then
    COMMAND="command -v"
elif type type >/dev/null 2>&1; then
    COMMAND="type"
fi


# validate Mono & run installer
if $COMMAND mono >/dev/null 2>&1; then
    mono internal/unix-install.exe
else
   echo "Oops! Looks like Mono isn't installed. Please install Mono from [https://mono-project.com](https://mono-project.com), reboot, and run this installer again."
   read
fi

---

### Post by Perfect Storm on 2018-12-05
You shall run the file either
```
./filename
```

or

```
sh filename
```

you may want to make it executable by
```
chmod +x filename
```

---

