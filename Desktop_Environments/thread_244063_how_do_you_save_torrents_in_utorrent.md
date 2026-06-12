---
title: "how do you save torrents in utorrent"
date: 2006-08-25
forum: Desktop Environments
---

### Post by onlybui on 2006-08-25
I read the how to but I don't understand how I can acess "h:\" 


I get this error message after I just type in utorrent

[email]onlybui@onlybui-desktop:~/.wine[/email]/drive_c/Program Files$ utorrent
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\ onlybui\\Application Data"'.
err:imagelist:ImageList_LoadImageW Error loading image!
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not regist ered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
err:imagelist:ImageList_LoadImageW Error loading image!
err:imagelist:ImageList_LoadImageW Error loading image!
fixme:listview:LISTVIEW_SetColumnOrderArray iCount 16 lpiArray 0x33edd8
fixme:keyboard:UnregisterHotKey (0x3002a,1): stub
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not regist ered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:keyboard:UnregisterHotKey (0x3002a,1): stub
fixme:shell:BrsFolder_OnCreate flags 50 not implemented
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\onlybui\\Desktop"'.
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\onlybui\\Desktop"'.

Im not to sure how to tranlate the only drive I have is \media\sdb5 to save files

Can I save files in utorrent on a linux drive?

---

### Post by onlybui on 2006-08-25
:) 

Figure it out

I had to have sudo access...

---

### Post by orb9220 on 2006-08-25
thanks to 505:

Yes, it is possible launch the torrent automatically. You need a special script.

Steps to get it:
1. Open a terminal
2. Type
Code:

sudo gedit /usr/bin/utorrent

3. Paste the following text
Code:

#!/bin/sh cd ~/.wine/drive_c/Program\ Files/utorrent if [ "$1" != "" ]; then var="`echo $1 | sed 's/\//\\\/g'`" var="Z:${var}" wine utorrent.exe "$var" else wine utorrent.exe fi

Modify the path to the utorrent directory where needed
4. Save and close Gedit
5. Type
Code:

sudo chmod a+x /usr/bin/utorrent


You can now launch utorrent from anywhere by typing 'utorrent' (no .exe)
To open .torrents automatically from firefox set the utorrent file as the default program.
Reply With Quote

---

### Post by onlybui on 2006-08-25
Yup I did that but I have one problem now my download speeds are super slow... 

utorrent is telling to use a different port and I do and same error message
...

---

### Post by onlybui on 2006-08-25
Ok I have everything fix thx....

---

