---
title: "when try to open desktop folder: /home/asus/Desktop does not exist"
date: 2020-10-29
forum: Desktop Environments
---

### Post by abelito8 on 2020-10-29
I accidentally moved the desktop folder somewhere and now when I try to access it it reads   /home/asus/Desktop does not exist.  All the icons are still visible on the desktop but I cannot access them...if I click on any of them it reads  Unable to run the command specified. The file or folder /home/asus/Desktop/Official-Final-Programme-19-June-1-1.pdf does not exist.  how to restore the filder?

---

### Post by TheFu on 2020-10-30
Is this a trick question?
Put it back.

Lacking that, create a directory in the same place, with the same name.

There are ways to search for file system objects.

There are ways to tell the GUI to consider the "desktop" to be located somewhere else too. That is dependent on the GUI used.

---

### Post by VMC on 2020-10-30
Go look for it: ```
[FONT=monospace][COLOR=#000000]find ~  -type d -name Desktop
```[/COLOR]
[/FONT]

---

### Post by ActionParsnip on 2020-10-30
What is the output of:
```

sudo file /home/asus/Desktop

```

---

### Post by abelito8 on 2020-10-31
Thank you, it worked, I used the command and found out that I had moved it to Music....I managed to put it back simply by dragging it into the home folder and no TheFu, it was not a tricky question :-) thank you

---

