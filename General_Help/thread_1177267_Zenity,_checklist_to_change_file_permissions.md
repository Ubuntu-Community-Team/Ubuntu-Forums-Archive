---
title: "Zenity, checklist to change file permissions"
date: 2009-06-03
forum: General Help
---

### Post by rick71 on 2009-06-03
I have a long list of files in different directories. I'd like to be able to set permissions on them such as: chmod o+r /path/to/file. I have a checklist dialog, but I can't figure out how to generate variables, and then change the permission of the selected files. I assume there should some kind of loop. (if/then, while, for/nex).

This my script so far. There are about 100 more files:


#!/bin/sh

chap=$(zenity --width 400 --height 600  --title "Test Selection" --text "Please select chapters" --list --checklist --column "Select" --column "Chapters" False "Discovering Computers Chapter 1" False "Discovering Computers Chap 2" False "Discovering Computers Chap 3" False "Discovering Computers Chap 4" False "Discovering Computers Chap 5" False "Discovering Computers Chap 6" False "Discovering Computers Chap 7" False "Discovering Computers Chap 8" False "Discovering Computers Chap 9" False "Discovering Computers Chap 10" False "Discovering Computers Chap 11" False "Discovering Computers Chap 12" False "Discovering Computers Chap 13" False "Discovering Computers Chap 14" False "Discovering Computers 15")

Can any give me some pointers?

Also, I notice several posts have the word code, followed with a box containing their code. How do you so this?

Any and all help appreciated.

---

### Post by rick71 on 2009-06-03
I have changed to a radio list, and want to select just one file, for now. However, it seems like the "if" is ignored, and al the chmod commands are being executed. No mater which selection I make, the file permissions ar being set on both files. Can anyone tell me whats wrong:

```

#!/bin/sh

chap=$(zenity --width 400 --height 600  --title "Test Selection" --text "Please select chapters" --list --radiolist --column "Select" --column "Chapters" False "DC1" False "DC2" False "DC3" False "DC4" False "DC5" False "DC6" False "DC7" False "DC8" False "DC9" False "DC10" False "DC11" False "DC12" False "DC13" False "DC14" False "DC15")

echo $chap
if DC1="$chap"; then chmod o+r test1.txt
  fi
if DC1="$chap"; then echo "$chap Opened"
  fi
if DC2="$chap"; then chmod o+r test2.txt
  fi
if DC2="$chap"; then echo "$chap Opened"
  fi

echo Done
exit 0

```

---

