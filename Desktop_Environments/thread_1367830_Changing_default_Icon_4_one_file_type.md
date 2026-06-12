---
title: "Changing default Icon 4 one file type?"
date: 2009-12-30
forum: Desktop Environments
---

### Post by sandman3838 on 2009-12-30
Hello

My question and I hope it's a simple one, has to with changing the icon of a particular file.

Depending in the Icon theme one chooses most of the system icons will change.
All the Folder, OpenOffice, Txt, GZ, BZ2, and TAR (to name a few) Icons will change.

Now lets say you want to just change or replace one particular file type like all the GEDIT file icons or all the TAR icon files?  I want to change the Icon assigned to a file type.

Is such a thing possible?  Is there a program for this?

Thank you all for your help.

---

### Post by mister_playboy on 2009-12-31
Right click an icon of the file type you want to change and pick Properties.

When the Properties box opens, click on the icon itself in the upper left and you'll have a chance to choose a custom icon.

As far as I can tell, all the icons installed to your system can be found in the many folders in /usr/share/pixmaps and /usr/share/icons.

---

### Post by sandman3838 on 2009-12-31
Thanks for the reply!

What your suggesting will change the one icon image for that paticular file!  That's a no brainer, I got that.

My issue is how do I change image icon it for ALL the Gedit files.

In Ms Windows there was Folder Options/ File Types.  Here I don't know, I starting to think that it can't be done.

Thanks for the input.  All take all I can get right now.

All the best.

---

### Post by mister_playboy on 2010-01-01
Hmmm... I thought it worked system wide for all files of that type.

Sorry about that.

---

### Post by mister_playboy on 2010-01-02
I found a GUI program to do this:

```
sudo apt-get install assogiate
```

You can find it as Applications > System Tools > File Types Editor after installation.

Filetypes such as .tar and .bz2 are listed under "Multipurpose Files" and are found as "x-tar", "x-bzip2", etc.

Right click and pick "Edit", then choose a default icon. :)

---

### Post by sandman3838 on 2010-01-02
Thank you!  Thank you! So very much!  That was it!  

Great Job!   mister_playboy

---

