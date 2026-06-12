---
title: "Extract Zip to &lt;folder&gt;"
date: 2005-11-06
forum: Desktop Environments
---

### Post by kverde on 2005-11-06
How could I add a Right-Click context command to extract a given ZIP file to the folder of the same name as the ZIP file?  7-Zip on Windows and WinZip on windows allowed this convenient configuration--I imagine Linux folks figured out something similar?

All that exists in the default installation is *Extract Here*.

---

### Post by morphodone on 2006-04-05
I'm wondering the same thing...

I know this can be done in kde but what about gnome?

The 'extract here' option is okay, but sometimes the file doesn't get
extracted into its own file.  Then you have many different files and folders
laying around...

---

### Post by btnheazy03 on 2006-04-27
It's a huge inconvenience for me as well .. . WinRAR/Zip and even Ark has it, so I wonder why File Roller doesn't .. .

---

### Post by louis_nichols on 2006-04-28
Well... it's not that simple. Linux doesn't have a unique system for shell entries, like windows does. But it's doable with all file browsers that support scripts. You just write a script that does it and put it, for example, in the nautilus scripts folder. Fot the gui you can use zenity, or kdialog or others.

I guess they haven't done this in Linux because command line tools extract stuff to a folder of choice pretty easily, and many Linux users are CLI fans.

---

### Post by bicchi on 2006-05-05
I am not sure if this is what you are looking for. 
Save the following python script in: ~/.gnome2/nautilus-scripts
Name the file something like: "Extract Archive Here"
```

#!/usr/bin/env python

import os
import urllib
import urlparse

uris = os.environ['NAUTILUS_SCRIPT_SELECTED_URIS'].split('\n')[:-1]

for uri in uris:
	unquoted_uri = urllib.unquote(uri)
	path = urlparse.urlsplit(unquoted_uri)[2]
	dirname = os.path.dirname(path)
	command = 'file-roller -e "%s" "%s"' % (dirname, path)
	os.system(command)

```
Make the file executable: chmod +x  "Extract Archive Here"

Now just right click on top of a zip/gz/tar file and select: Scripts ->  Extract Archive Here
Hopefully that is what you are looking for. :D

---

### Post by louis_nichols on 2006-05-06
[QUOTE=bicchi]I am not sure if this is what you are looking for. 
Save the following python script in: ~/.gnome2/nautilus-scripts
Name the file something like: "Extract Archive Here"
```

#!/usr/bin/env python

import os
import urllib
import urlparse

uris = os.environ['NAUTILUS_SCRIPT_SELECTED_URIS'].split('\n')[:-1]

for uri in uris:
	unquoted_uri = urllib.unquote(uri)
	path = urlparse.urlsplit(unquoted_uri)[2]
	dirname = os.path.dirname(path)
	command = 'file-roller -e "%s" "%s"' % (dirname, path)
	os.system(command)

```
Make the file executable: chmod +x  "Extract Archive Here"

Now just right click on top of a zip/gz/tar file and select: Scripts ->  Extract Archive Here
Hopefully that is what you are looking for. :D[/QUOTE]

Thanks for the script, man! I think I have some uses for it.

However, what I believe they were asking is quite different. It's like: right-click on the archive and select an option like "extract archive to..." and then a GUI pops up for choosing the path were the archive should be extracted. Or, even easier, extract archive.zip directly to a folder called archive/ in the same folder where they are, via an option called "extract to "archive" ". So, if the archive contains a set of files, they will safely lie in their own folder and not clog the current folder.

---

### Post by bicchi on 2006-05-06
I think this is what you want but with a shell script instead of using python. The script uses zenity to put a box on the screen where the user selects the destination directory of the file to be extracted. Just follow the steps I gave above but instead name this script "Extract Archive to..." 

```

#!/bin/bash
extract_to=`zenity --file-selection --directory \
	--title="Select the destination directory for $*"`
if [ "$extract_to" ]; then 
	file-roller -e $extract_to $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
fi

```

---

