---
title: "Can not open file in gedit, please help"
date: 2005-10-20
forum: Desktop Environments
---

### Post by Chris100 on 2005-10-20
I am running ubuntu 5.10 with all the updates applied. I have a very weird problem: I can not open a file with gedit. Here is the details:

1) Run Applications->Accessories->Text Editor, then click the open file button from the toolbar, "gedit" hangs forever (> 5 minutes) and I have to exit by force quit. Use menu file->Open... gives the same. Use the drop down menu next the file open button works well and File->open location also gives a dialog.

2) If I run "sudo gedit", I can open file as expected.

3) Double click in file browser works well. Drag a file from file browser into gedit also works.

3) The same behavior for totem.

Any advice is appreciate,

Chris

---

### Post by dspp on 2005-10-20
Did you try adding a new launcher for gedit? 

With Synaptic or apt uninstalling and reinstalling is easy, so you might try that as well.

---

### Post by eitan on 2006-04-24
i have the same problem.  i was hoping upgrading to dapper would fix this but it did not.  in my experience, this problem is shared across applications that use the gtk apis.  file-open in gedit or gnumeric for example both exhibit this.  epiphany is starting to do similar things to me.

---

