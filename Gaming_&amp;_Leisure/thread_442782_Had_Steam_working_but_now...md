---
title: "Had Steam working but now.."
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by RobotAlligator on 2007-05-13
Well i got steam running now, but two new errors are happening

Font won't load.(When steam opens there is nothing to read)  I get some error saying it cant access c/windows/system32 and steam loads anyways


I closed and tried starting again and now i get Fatal Error, Could not load bin/vgui2.dll

---

### Post by B. Gates on 2007-05-13
The problem you're having is that Program Files has a space in the folder name. Without additional measures, the terminal will assume everything after the space is a parameter for Wine, and it won't automatically join the two halves together.

If you want to use something that has spaces, surround the path using double quotes:

wine "/home/tux/.wine/drive_c/Program Files/Steam/Steam.exe"

That should work.

---

### Post by aoanla on 2007-05-14
Or, of course, you can "escape" the space by prepending a \ to it.

so

wine /home/tux/.wine/drive_c/Program\ Files/Steam/Steam.exe

should also work. (This is also useful in general, if you create a file with a special character in the name, like # or *, etc.)

---

### Post by RobotAlligator on 2007-05-14
edit bump

---

