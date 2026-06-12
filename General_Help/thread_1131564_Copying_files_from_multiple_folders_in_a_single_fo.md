---
title: "Copying files from multiple folders in a single folder &amp; renaming according to folder"
date: 2009-04-20
forum: General Help
---

### Post by fadman_12 on 2009-04-20
I'm trying to figure out a way to copy several pictures that I have organized in multiple folders in a single folder into a single folder. That part is easy. But does anybody know how to copy those pictures and add to the filename the name of the folder that they are located in? I've looked all over and I cant figure out how to make a bash command for that. Thanks

---

### Post by cybergalvez on 2009-04-21
this should work, copy this to copyImages

```

#!/usr/bin/env python

import os
from glob import glob
from shutil import copy
import sys

def copyfiles(copyto, p):
    d = glob(os.path.join(p, '*')) # get all a list of files
    for f in d:  # step through it
        if os.path.isdir(d): # if its a directory do it again
            copyfiles(copyto, f)
        else:
            if f.lower().endswith('jpg'):  # if its an image rename and copy 
                image = os.path.basename(f)
                dir = os.path.dirname(f)
                end_dir = os.path.split(dir)
                new_name = os.path.join(copyto, '%s_%s' % (end_dir, image))
                # copy the image file
                copy(f, new_name)
                
                
if __name__ == '__main__':
    if len(sys.argv) < 3:
        print 'Usage copyImages <startingPath> <copytoPath>'
    else:
        copytoPath == os.path.abspath(sys.argv[2])
        startingPath = os.path.abspath(sys.argv[1])
        if (os.path.exists(copytoPath) and os.path.exists(startingPath)):
            copyfiles(copytoPath, startingPath)
        else:
            print 'Either %s or %s do not exist' % (startingPath, copytoPath)

```

---

### Post by kaibob on 2009-04-21
I came up with the following shell script. I suspect awk would be a better choice to extract the name of the directory (i.e. $DIRNAME), but I don't know how to do that. Anyways, a bit of a kludge, but I tested this and it does work.

```
#!/bin/bash

find /source/directory -iname '*.jpg' -type f | while read FILE ; do
DIRNAME=$(echo "$FILE" | rev | cut -d '/' -f2 | rev)
FILENAME=$(basename "$FILE")
cp "$FILE" "/target/directory/${DIRNAME}-${FILENAME}"
done
```

You have to change /source/directory and /target/directory in the above.

---

