---
title: "Problem with using zip files"
date: 2006-09-22
forum: Desktop Environments
---

### Post by kuhi on 2006-09-22
Consider doing the following:

1. Open a zip file (double click)
2. Open some file from within this zip
3. Make some changes in to this file and the save
4. Close everything

Result at least for me is that all changes made are lost.  I did some googling and it seems that there is no way to recover lost data with ext3 filesystem?

---

### Post by Jussi Kukkonen on 2006-09-22
> I did some googling and it seems that there is no way to recover lost data with ext3 filesystem?
Deleted files? It would be pretty difficult: The address pointers (or whatever they're actually called) are actually zeroed... The only chance would be some kind of low level "grepping" of the whole disk (if you know some distinguishing string in the file). I don't know how to actually do that.

---

### Post by nikhilk on 2006-09-22
I do not think it is possible to edit a file present inside a zip archive and save the changes inplace.
What I mean is if you want to edit a file in a zip archive you probably have to extract it first, otherwise it is temporarily exracted (maybe in "/tmp") so the changes won't be reflected.

---

### Post by kuhi on 2006-09-22
At least for me it is possible to make changes in files inside zip
and also possible to save those changes as well.

Could you please confirm this.  If so I will report it as a bug.

---

### Post by nikhilk on 2006-09-22
Sorry I am not at my home machine right now.
But on the machine I am using (FC4 with KDE) I cannot see the contents of any text file inside a zip archive when opened in gvim!
Kate opens the file fine and I can make changes but when I try to save I get error "Writing to tar not supported". Some idiot has messed up kedit here so I cannot try that.
Which editor are you using?

---

### Post by kuhi on 2006-09-22
Its ubuntu dapper

Im using nautilus and file-roller for viewing zip files.  Problem is that user is granted write access to tmp directory where files are temporarily extracted.  Hence you can make changes there and when file-roller closes. Poof they are gone.

---

### Post by kuhi on 2006-09-22
Ok, I reproduced this on another installation of dapper.  So Im going to file this as a bug.

---

