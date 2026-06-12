---
title: "Desktop items are not showing when I save to Desktop"
date: 2009-05-22
forum: Desktop Environments
---

### Post by Threelovemonkeys on 2009-05-22
Hi Ubuntu community. This is my first question to you. I have been us Ubuntu for about a year without much trouble.

However, today, whenever I save anything to the desktop,.. pdfs. .doc files and others, the file is not being presented as an icon on the desktop. However, I have found these files in the terminal window by navigating using the unix commands. The files are not listed as hidden and will be visible with a ls -1 command.

Any thoughts about this strange behavior?

I don't know if this is related, but I lost a file on the desktop that I saved last night. It just seemed to have disappeared. That file wasn't even present in the terminal. I had to retype the whole document. Not the same issue, but similar, and it occurred around the same time as the problem I've detailed above.

Thanks in advance for any thoughts,
Threelovemonkeys

---

### Post by ckonestroh on 2009-05-23
try this

Using gconf-editor go to apps>nautilus>desktop make sure volume list is checked....


good luck

---

### Post by mcduck on 2009-05-23
First thing to do would be restarting Nautilus. Press Alt-F2 and run "killall nautilus && nautilus".

Also, to find your files simply look in the "Desktop" directory inside your home.

---

