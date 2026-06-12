---
title: "Use sudo to open file"
date: 2005-05-12
forum: Desktop Environments
---

### Post by SteveF on 2005-05-12
Sometimes when I am using Nautilus to navigate my filesystem, I want to open some files in a text editor as root.  I right-clicked on the file and chose Open with other Application.  I chose Use custom Command.  I entered gnome-sude gvim and hit enter.  This opens gVim but the file is empty.  Actually it is trying to create a new file with the filename in single quotes.

For example to open test.tx, gVim shows the name as "'test.txt'".  Which makes me think it is trying to create a file called 'test.txt' as opposed to test.txt.

If I open the file the same way, but enter just gvim (without the gnome-sudo), the file opens correctly (but read-only if course).

Is there something I can type to prevent the system from adding the quotes?

Thanks,

Steve

---

### Post by BAshworth on 2005-05-12
If you look around, you can find a script to add the option to "open file as root" , or "open nautilus with root permission" to the Nautilus right-click menu.

Try 

[http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Misc/root-nautilus-here)

and

[http://ubuntuforums.org/archive/index.php/t-24008.html](http://ubuntuforums.org/archive/index.php/t-24008.html)

for info and alternatives.

---

### Post by SteveF on 2005-05-12
Thanks for the tip.  I went the script route (I don't feel comfortable having a Nautilus window as root - too easy for mistakes).  I modified the open to use gvim instead of gnome-open (my preference for editing).  Worked great.

Thanks again.

---

