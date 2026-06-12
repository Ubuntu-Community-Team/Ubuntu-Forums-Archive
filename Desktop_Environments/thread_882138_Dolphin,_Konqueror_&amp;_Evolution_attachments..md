---
title: "Dolphin, Konqueror &amp; Evolution attachments."
date: 2008-08-06
forum: Desktop Environments
---

### Post by ghostdog on 2008-08-06
Hello, 

I decided to betray KDE and use evolution out of personal taste. 

Setting the default application under system setting is not enough, since Email attachments cannot be sent through evolution, since it keeps looking for kmail due to the servicemenus.(wish these could be customized at user level)

In any case I decided to do a little digging and found a few solutions (I do not know the syntax for attaching multiples files for evolution, it found simplify this)

This is what I did, I looked in kde-apps and found [this]("http://www.kde-look.org/content/show.php/Attach+MULTIPLE+Files+-+Evolution?content=13308"), downloaded and proceeded first to edit mail_as_attachment.desktop use by the dolphin service menu.

sudo vi /usr/share/apps/d3lphin/servicemenus/mail_as_attachment.desktop

and placed python script in /usr/bin.

This is how my service menu file looks like:

```
[Desktop Entry]
Encoding=UTF-8
ServiceTypes=all/allfiles
Actions=mail_as_attachment

[Desktop Action mail_as_attachment]
Name=Mail as Attachment...
Name[de]=Verschicken als Anhang...
Icon=mail_send
Exec=mail_evol.py %U
X-Ubuntu-Gettext-Domain=desktop_dolphin
```

Everything works fine in Dolphin, I can email multiple attachments, but only if the path has no spaces.

Here is the python script:

```
#!/usr/bin/python

import sys
import os

files = sys.argv[1:]


commandline = 'evolution mailto:?attach=' + "'" + files[0] + "'"
files.pop(0)
for i in files:
    commandline = commandline + '\&attach=' + "'" + i + "'"

os.system(commandline)
```

There is also a bash script that causes the same behavior:

```
#!/bin/sh
# Part of attach_to evolution
# Juan Manuel Jaramillo
# jmboris@hotmail.com


CheckedFile="$[0-9]"

evolution mailto:?attach="$CheckedFile"

```

Anyone can shed some light on this?

---

