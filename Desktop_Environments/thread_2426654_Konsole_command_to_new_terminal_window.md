---
title: "Konsole command to new terminal window"
date: 2019-09-11
forum: Desktop Environments
---

### Post by shag00 on 2019-09-11
I am attempting a small script to open a terminal window which in turn opens a second window but I cannot seem to enter any further data or commands into the second window from the script even though the second window has focus, that is if I press the enter key, or any other key, that input appears in the second window. During my tests I have attempted to use the echo command to see what happens and what happens is that, the second window spawns and has focus and is awaiting input. Upon closing the second window the echo command output appears in the first window. The top screenshot is the first window and the bottom one is the second?

[ATTACH=CONFIG]284002[/ATTACH]

Using this code:

```
#!/bin/bash
echo "TEST"
konsole --hold --workdir ~/.wine/drive_c/"Program Files"/DTS/MAS-SAS -e bash -c  "WINEPREFIX=~/.wine wine cmd"; echo dtshd.exe
```

So my question is, how do I get the script to input data into the second (bottom) window.

---

### Post by Skaperen on 2019-09-11
does it need to be done in a window?  if not, there are many ways to input to a shell session in the background.  i use **[COLOR=#0000cd][FONT=courier new]screen[/FONT][/COLOR]** to do that in my scripts.

---

### Post by Skaperen on 2019-09-11
is that wine or are you VMing Windows?

---

### Post by shag00 on 2019-09-12
Unfortunately it needs to be done in that window, starting the program from any other location causes it to run improperly. Yes, it is wine.

---

