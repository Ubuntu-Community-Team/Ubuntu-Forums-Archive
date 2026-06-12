---
title: "Trouble Installing FTL from tarball"
date: 2013-05-23
forum: Gaming &amp; Leisure
---

### Post by vadertater on 2013-05-23
I got the tarball for the game "Faster Than Light" (really great game by the way) and I can't install it... I tried to follow these directions: [http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file](http://askubuntu.com/questions/25961/how-to-install-a-tar-gz-or-tar-bz2-file)

I moved the tarball to my desktop. Then I changed the directory:
```
cd /home/nate/Desktop
``` because ```
cd /home/nate/Desktop/ftl_faster_than_light-linux-1.03.1
``` didn't work... got a bash error cause apparently that doesn't exist. I tried it again with .tar.gz at the end.

With the current directory as my desktop, I then extracted the tar.gz using the following:

```
tar xvzf ftl_faster_than_light-linux-1.03.1.tar.gz
```
Output for above command:
```
FTL/data/x86/lib/libbass.so
FTL/data/x86/lib/libbassmix.so
FTL/data/x86/lib/libfreetype.so.6
FTL/data/x86/lib/libIL.so.1
FTL/data/x86/lib/libILU.so.1
FTL/data/x86/lib/libILUT.so.1
FTL/data/x86/lib/libpng12.so.0
FTL/data/x86/lib/libSDL-1.2.so.0
FTL/data/x86/lib/libstdc++.so.6
FTL/data/x86/lib/libz.so.1
FTL/data/x86/bin/FTL
FTL/data/amd64/lib/libbass.so
FTL/data/amd64/lib/libbassmix.so
FTL/data/amd64/lib/libILUT.so.1
FTL/data/amd64/lib/libfreetype.so.6
FTL/data/amd64/lib/libIL.so.1
FTL/data/amd64/lib/libILU.so.1
FTL/data/amd64/lib/libpng12.so.0
FTL/data/amd64/lib/libz.so.1
FTL/data/amd64/lib/libstdc++.so.6
FTL/data/amd64/lib/libSDL-1.2.so.0
FTL/data/amd64/bin/FTL
FTL/data/licenses/LGPL.txt
FTL/data/licenses/README-DevIL.txt
FTL/data/licenses/README-FreeType.txt
FTL/data/licenses/README-RapidXML.txt
FTL/data/licenses/README-SDL.txt
FTL/data/licenses/README-zlib.txt
FTL/data/resources/data.dat
FTL/data/resources/resource.dat
FTL/data/exe_icon.bmp
FTL/data/FTL
FTL/FTL_README.html
FTL/FTL
FTL/data/x86/lib/
FTL/data/x86/bin/
FTL/data/amd64/lib/
FTL/data/amd64/bin/
FTL/data/x86/
FTL/data/amd64/
FTL/data/licenses/
FTL/data/resources/
FTL/data/
FTL/

```

And a new folder (directory) popped up on my desktop. And nothing I do with that works out... the README says: "
Extract tar.gz file into a location of your choice. Run FTL script in root folder." 

So... what does that mean? and how do I do it? I already extracted the tar.gz

---

### Post by ajgreeny on 2013-05-23
You appear to have tried to cd into the folder that the archive contains before you had actually extracted it.

Extract it first then you can cd to the folder **Desktop/ftl_faster_than_light-linux-1.03.1** and should be able to run the script FTL from that

---

### Post by vadertater on 2013-05-24
Thanks. I figured it out. there was another script in there not labelled readme that explained it.

---

