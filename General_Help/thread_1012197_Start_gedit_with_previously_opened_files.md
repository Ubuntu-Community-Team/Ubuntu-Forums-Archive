---
title: "Start gedit with previously opened files"
date: 2008-12-15
forum: General Help
---

### Post by blaise69 on 2008-12-15
Hi there.

I'm looking for an option or a plugin that will allow me to startup gedit with my previously opened files already loaded, instead of the usual glum looking untitiled file.

It's basically the same functionality that Firefox has when you set the option to "Show my windows and tabs from last time" under startup in preferences.

Has anyone come across this?  I think it would be really useful for me.

Cheers,

Blaise.

---

### Post by RHTopics on 2008-12-15
I don't know if a Plugin has been created for gedit to automatically bring up the last edited documents.  But out of curiosity I have created a python script to bring up the last document edited.

The script below when executed from a terminal window will find the last document edited by gedit and then execute gedit, bringing up that document.

I named the python script "gedit_last_doc.py" and placed in my "/home/RHTopics/bin" directory.  I changed the permission on the file to be executable by entering the command:

 ```
chmod +x gedit_last_doc.py
```

With that it can be executed from the terminal window by simply entering the command "gedit_last_doc.py".  

This python scripts works using Ubuntu 8.04 (Hardy). 

To make it more convenient to execute this script, using "Configuration Editor", I have assigned it to the shortcut key combination of Windows Key + r.

The script can be modified to bring more than just the last document.


```
#!/usr/bin/env python

import os
from xml.etree import ElementTree as ET

# change the file parameter for your user id.
recentFiles = ET.ElementTree(file='/home/RHTopics/.gnome2/gedit-metadata.xml')

lst = recentFiles.findall("document")

lastDocEditedTime = "0"
for item in lst:
    if item.attrib["atime"] > lastDocEditedTime:
        lastDocEditedTime = item.attrib["atime"]
        lastDocument = item.attrib["uri"]

os.system("gedit " + lastDocument + " &")

```

---

### Post by blaise69 on 2008-12-16
Wow, that's the kind of thing I was looking for, and certainly to have it open the last collection of open files is what I like the most.

I think Firefox does this using sessions.

Is it possible to package this as a plugin for gedit?

---

### Post by RHTopics on 2008-12-16
Talk about synchronicity ;), I believe I have found the Plugin you want.

[http://sourceforge.net/projects/geditautosaves/](http://sourceforge.net/projects/geditautosaves/)

By the registered date on it, looks like it has just come out.

Also,  the editor "Geany", by default, brings back your recently opened files.  It is a good editor, especially for editing code.

---

### Post by blaise69 on 2008-12-16
Funilly I had literally come across this plugin this morning, I also found the following.

[http://code.google.com/p/reopen-tabs-gedit-plugin/]("http://code.google.com/p/reopen-tabs-gedit-plugin/")

Which is an alternative and seems to offer a few more options with it also.

I'm trying them both out to see which suits better, but I'm certainly glad there is a solution to my problem.

:)

---

