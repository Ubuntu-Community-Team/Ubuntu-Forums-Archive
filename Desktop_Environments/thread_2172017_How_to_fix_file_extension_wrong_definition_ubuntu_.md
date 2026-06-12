---
title: "How to fix file extension wrong definition ubuntu 10.04"
date: 2013-09-02
forum: Desktop Environments
---

### Post by grandixximo on 2013-09-02
I have a file with extension .hal which is seen as a CAD drawing file, i have draftsight installed, the .hal file it's actually a text file so i need to open it with gedit, but if i set to open the .hal file with gedit, then all my .dxf file cannot open to draftsight, but they'll try open with gedit.

I would like to remove ubuntu from thinking .hal files are CAD drawings, because they are not, .dxf files open with draftsight, .hal files with gedit.

I hope there is somewhere to set this extensions settings, please help!

---

### Post by Dennis N on 2013-09-02
In the file manager, right-click on one of the .hal files. In the menu, select Properties. In the Properties dialog is a box "Open With" where you can select an application for this type of file.

---

### Post by grandixximo on 2013-09-03
> **Dennis N said:**
> In the file manager, right-click on one of the .hal files. In the menu, select Properties. In the Properties dialog is a box "Open With" where you can select an application for this type of file.


Yes i know how to do that, but there is a problem, i have two file extensions hal and dxf.

HAL is a simple text file type, but is recognized as a CAD drawing file type

DXF is a CAD drawing file type and is recognized properly

Now if like you said i change to Open HAL files with gedit, i see on the top "change program to open CAD drawing files with", problem is hal is not a CAD drawing file type, it'a a text file type.

changing to open HAL files with gedit changes my dxf files too, so i cannot open DXF with draftsight any longer.

There must be somewhere where it's written for example that DXF DWG 3GS are CAD drawing files, while TXT INI HAL README are text files, i need to change that.

Because changing the open with changes also the wrong files extensions.

I need to change the connection between file extensions and file types, not the program to open the file types with.

---

