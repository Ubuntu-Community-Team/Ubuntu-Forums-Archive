---
title: "Where are file associations controlled?"
date: 2006-08-16
forum: Desktop Environments
---

### Post by drlock on 2006-08-16
I am running xubuntu, which by default associates *.odt with AbiWord. I want to change the file association to point to OpenOffice.  I can find an odt file and change Open With in the properties ([http://www.ubuntuforums.org/showthread.php?t=233306&highlight=file+association](http://www.ubuntuforums.org/showthread.php?t=233306&highlight=file+association)), but what I really want to know is where is the config file that controls this?

I want to know so that I can change defaults like this system wide, not just for my account.

Thanks

---

### Post by sblanzio on 2006-08-16
I was looking for an answer to questions similar to yours, and I found some answers here:

[http://www.fedoraforum.org/forum/archive/index.php/t-26875.html](http://www.fedoraforum.org/forum/archive/index.php/t-26875.html)

expecially where it says:
> 
-> /usr/share/applications/defaults.list
This file contains the applications which cause a double-click success. All Mime types will point to a desktop file.

-> /usr/share/applications/[application_name].desktop
This is the file where "defaults.list" will point to. One of the most important things inside this file is the entry "MimeType=".

-> /usr/share/applications/mimeinfo.cache
Contains information in similar form shown for file "defaults.list" in same directory. This file contains ALL associations given to a mime type. There is no need for a specified order of desktop files (see XMMS example lateron)

-> /usr/share/mime (Directory)
This directory contains several information. The sub-directories - excluding packages - contain information about given mime types. You'll see that many mime types already exist.
The packages directory contains the DATABASE calles freedesktop.org.xml!

-> /usr/share/mime/globs
This file contains the file extensions, associated to the mime-types.


maybe it can be useful :)



bye!

sblanzio

---

### Post by drlock on 2006-08-16
Thanks, that helps.

---

