---
title: "need help with tarball"
date: 2009-03-01
forum: General Help
---

### Post by phread59 on 2009-03-01
I need help unpacking a tarball.  I just can't seem to unpack a tarball.  Any help you fellows could give me would be great.  

Mark Shuman

---

### Post by taurus on 2009-03-01
What are you trying to install?  

See if you can unpack it from a terminal, assuming you have saved the file, whatever it is to your desktop, do

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf filename.tar.gz
-or-
tar xvjf filenamt.tar.bz2
```

---

### Post by Rallg on 2009-03-01
Not only could you do it via Terminal, in Ubuntu you should be able to double-click the file, which will open the archive manager application. That will allow you to extract the enclosed stuff.

However, if for some reason the file was obtained while you had root permissions, it may be that you are refused access due to a permission problem. Right-click the file, get its properties, permissions. Is it owned by root? Are you, the user, forbidden to do anything with the file? If that should be the case, then you probably want to change ownership to your username rather than root. In Terminal:

sudo nautilus

(In Kubuntu or Xubuntu it won't be nautilus). Navigate to the file, right-click, get properties, permissions, and change the owner. Then close the window and return to your usual Desktop. Now try double-clicking the file.

Another possibility is that the tar file was not properly downloaded. If it is missing a piece, you wil just have to get it again.

When you say that you cannot "unpack" a tarball, perhaps you mean that you have successfully extracted its contents, but don't know what to do with the resulting files? That is a different issue. The files could be installers, Java applications, or source code. You will just have to look for instructions, probably named README or INSTALL.

---

### Post by NIAC on 2009-03-03
I am new to ubuntu.  I have a down load of cursors in a tarball tar.gz file that I cannot seem to get to run.  I have tried with the terminal but had no luck.  Maybe I am not doing right.  Any help would be great.  The file name is 100252-Griffin Embers Cursors.tar.gz

---

### Post by 3rdalbum on 2009-03-04
Open the Appearance program. Click the "Theme" tab. Drag the .tar.gz file to the Appearance window to install the cursor theme. Click "Customise" and then go to the "Cursors" tab, and select the new cursor theme.

---

