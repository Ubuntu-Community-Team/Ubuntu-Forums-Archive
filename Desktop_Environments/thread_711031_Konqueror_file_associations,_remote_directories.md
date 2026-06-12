---
title: "Konqueror file associations, remote directories"
date: 2008-02-29
forum: Desktop Environments
---

### Post by barna on 2008-02-29
I managed to add a new mime type (image/hpgl   *.plt,*.hpg,*.hpgl) to mozplugger and to handle it with the external application 'hpglview' swallowed. 
In Konqueror this new mime/type shows up, in the 'Description' field I can see 'Netscape MozPlugger 1.8.0 handles QuickTime and Window' meaning that konqueror has imported this from mozplugger. The 'Application preference order' was empty, so I added here 'hpglview' as well. Now, if I click on a .plt file in my local home directory, konqueror opens it correctly with the application hpglview. However, if I try to open a file accessed via webdavs://, konqueror pops up the dialogue 'Open with', and I have to specify hpglview. Also, the Type of the file in the Properties window is shown as Unknown, whereas the Type for local files is shown as 'Netscape MozPlugger 1.8.0 Handles QuickTime and Windows Media Player Plugin'. So I guess the problem's origin is that the type is not recognized in case of webdavs://.  Why does konqeuror not take the Type from the extension .plt? Can I set it up to do so?
Thanks
D

---

