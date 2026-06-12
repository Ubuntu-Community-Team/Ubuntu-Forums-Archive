---
title: "The command for the start button grabc"
date: 2018-03-10
forum: Desktop Environments
---

### Post by sanbl4 on 2018-03-10
Excuse my English, Google will help me. 
There is a grabc programmer that determines the color and the result shows in the console. What command should I write in the start button?
That the program was registered in the console at start and after clicking on the chosen place result was registered in the terminal window...

---

### Post by again? on 2018-03-10
You can use xterm's hold option.
eg
```
xterm -hold -e "/usr/bin/grabc"
```

P.S
There are GUI alternatives to grabc.
[LIST]
[*]gpick
[*]gcolor2  (not available after Ubuntu 16.04)
[/LIST]

---

### Post by sanbl4 on 2018-03-10
thank you, took advantage of gpick;)

---

### Post by sanbl4 on 2018-03-10
although, the quick start button also works):P:p

---

### Post by again? on 2018-03-10
No problem.
If you use python pip you can also install a simpler dialog.
```
pip install -U pycolorsel
```

---

