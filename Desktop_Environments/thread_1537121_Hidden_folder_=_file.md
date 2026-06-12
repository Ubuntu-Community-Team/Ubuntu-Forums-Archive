---
title: "Hidden folder = file?"
date: 2010-07-23
forum: Desktop Environments
---

### Post by josephrockz4 on 2010-07-23
So, I have a sort of strange dilemma.
I had all these files on my desktop and I wanted to put them in a hidden folder. I put them all in a folder, then renamed that folder ".desktop" and tried to hide/unhide it with ctrl+h. It didn't work. So I moved it to my home folder. Didn't work there either, and I accidentally deleted it. Moved it out of the trash and back onto the desktop, but now it's no longer a folder. Now it's a file. I can't open it, since when I do, it says "Cannot display .desktop [return] The file is of an unknown type."
What.
How do I fix this?

---

### Post by clrg on 2010-07-23
That's because .desktop is a registered filetype. Nautilus thinks its a file of the type .desktop and therefore does not try to handle it as a folder. You wouldn't name a folder .odt either, would you.

Open a terminal and navigate to the directory where the "file" is located. Verify the name of the "file" with 'ls -l'. Make sure its really a folder with 'file .desktop'. **If** it is a folder, rename it with 'mv'. For example 'mv .desktop myfolder'.

If you want to make a hidden folder, name it .hiddenfolder or .pr0n or whatever, but don't use file extensions. It does work with "normal" programs such as ls, tar, etc. but not with Nautilus.

---

