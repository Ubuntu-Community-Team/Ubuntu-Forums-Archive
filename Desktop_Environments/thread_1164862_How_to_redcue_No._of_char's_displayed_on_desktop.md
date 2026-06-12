---
title: "How to redcue No. of char's displayed on desktop?"
date: 2009-05-20
forum: Desktop Environments
---

### Post by alfoldem on 2009-05-20
Hi all, 

Hoping someone can help shed some light on this.
Im fairly new to Linux and have been using Ubuntu 8.04 for around 2 months - overall really pleased to have made the switch from Windows!

One minor point that is annoying me is how the file names are displayed on my desktop.
If i save or download a file or folder to my desktop the entire file name is displayed beneath the icon
e.g. filenameisreallyreallyreallylong.doc

I would like to display less char's
e.g. filenameis... 
this is how my files were handled by default in windows.

The reason for this is the alignment of files / folders on my desktop seems to be affected as some names are longer than others.

Is there a way to specify or restrict the number char's displayed in the file name?

Any help appreciated.

---

### Post by Minsky on 2009-05-20
Sorry, double post

---

### Post by Minsky on 2009-05-20
I'm using Intrepid 8.10 but the procedure should be the same. Open a terminal window and type **gconf-editor**. In the left hand pane of the window that opens double click on **apps**, scroll down and double click on **nautilus**. Select **icon_view**, this will display a list of keys in the large right hand pane.

Right click on **text_ellipsis_limit** and select **Edit Key...**. In the small window that opens, click on the value in the large box (I think 3 is the default value), and then click on **Edit**. Enter **1** as the value, then click **OK** and **OK** again. Your filenames will be truncated to fit on one line. I've got no idea how to further restrict the length of the filename. Hope this helps.

---

