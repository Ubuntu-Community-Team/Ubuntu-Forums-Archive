---
title: "use wine and foxit, and customized command"
date: 2009-02-18
forum: General Help
---

### Post by patiobarbecue on 2009-02-18
windows application Foxit reader can let me add annotation to a PDF file. For easy use, I added a file "foxit" under /usr/bin
#!/bin/bash
wine /path-to-foxitreader.exe $1

and chmod 755 of the file "foxit"

now in a terminal I can type in "foxit myfile.pdf" and open it. However I cannot figure it out how to make it work in the Right Click menu. I set the customize command to "foxit", and only got a pop-out window reminding me the usage of foxit reader. So what does the Gnome pass to the command when I double click a pdf file? If it is the filename being clicked, it should work. No idea how to figure it out. Any help is appreciated.

---

### Post by patiobarbecue on 2009-02-19
Ok, the correct way to write the script is:

#!/bin/bash
wine /Path-TO/FoxitReader.exe `winepath -w "$*"`

Now you can you it in the customized command.

please note the way wine  handles parameters, instead of the one ($1) I used in the previous post.

---

