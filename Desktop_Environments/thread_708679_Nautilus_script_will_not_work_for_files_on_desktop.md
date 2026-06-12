---
title: "Nautilus script will not work for files on desktop"
date: 2008-02-26
forum: Desktop Environments
---

### Post by Aanidaani on 2008-02-26
Hey guys. I recently installed a nautilus script in my ~/.gnome2/nautilus-scripts folder to convert image files to the jpeg format. The script runs fine when I right-click on image files in any folder but on my desktop. If I try to right-click on something on my desktop, I see and can execute the script (it runs without error), but no file is actually created. I tried refreshing the desktop, but nothing appears.

Here is the code for my script:
```
#!/bin/bash

scriptname=`basename $0`
# Determine image type to convert to based on the name of the script
newext=`echo $scriptname | sed 's/convert.to.\(.\+\)/.\1/'`

for image in "$@"; do
    # Determine target image name
    target=$(echo $image|sed 's/\(.*\)\..\+/\1/')$newext
    echo "$image -> $target"
    convert "$image" "$target"
done

```

Is there something I need to change in my permissions? I've already set up read and write for all users and I've made the script executable. Any help would be greatly appreciated. :(

---

