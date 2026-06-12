---
title: "Ubuntu 7.10: Gnome lost &quot;open with&quot; configuration"
date: 2007-11-15
forum: Desktop Environments
---

### Post by deigote on 2007-11-15
Hi. 

Don't know why but Gnome has lost all the "Open with" configuration. Each file icon in Nautilus is now a blank page and when I try to open anyone, appears the "which program do you want to open with?" menu.

I haven't touch any configuration file, I can do some "avanced stuff" in Linux , but I'm quite lost with Gnome's configuration, so any tip or help will be very appreciated.

Cheers

---

### Post by jpietari on 2007-11-17
It sounds like your registry is messed up.  I don't know how you would go about fixing it, but these are the steps to see your file association:

1. open run dialog
2. type in gconf-editor
3. Navigate to /desktop/gnome/thumbnailers

You should have a bunch of entries for each file type,

---

### Post by deigote on 2007-11-17
Thanks for answering :)

I looked this entry of gconf and its look ok, but I think that this menu is just for the thumbnailers, the file previews, not for the "open with...".

Anyway, I also lost the thumbnails :( and the entries you pointed look ok...

Is there any way to reset some parts of the gconf without loosing the rest? Because I'd like to keep the desktop, panel and stuff....

---

### Post by deigote on 2007-11-17
Ok, I don't think is Gnome.. I created a new user and the same happens: no thumbs, cannot open any file:confused:

---

### Post by jpietari on 2007-11-17
1. Can you manually change the file association by:
Right-click file->Properites->Open With->choose application

2.  Could environment variables not be set when you start-up?

If these don't fix it then I'm out of ideas.  Maybe move your data to a different partition and re-install...:-(

---

### Post by jpietari on 2007-11-17
I've searched on the web and I can't figure out how Linux associates which application opens a file.  It is in the registry in Windows.  

I wonder if changing your icon set would get some of your icons back...

---

### Post by deigote on 2007-11-20
I'll try to... I'm a bit scared with this problem because some files are thumbnailed in some directories but not in other directories (even if they are the same type of file), and when I'm writing a file (for example a text file with GEdit) I get some "I/O error" in the console (the message is a little longer, but has no info at all), although the file is written well...

I'm afraid that the hard disc is starting to fail...:( anyway I'll try more things (I'm out of time right now, but I didn't forget your advices).

Thanks!

---

