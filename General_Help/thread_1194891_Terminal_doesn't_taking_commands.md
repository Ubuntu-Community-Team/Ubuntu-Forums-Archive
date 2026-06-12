---
title: "Terminal doesn't taking commands"
date: 2009-06-23
forum: General Help
---

### Post by Mortos on 2009-06-23
I Installed Ubuntu on my PC, but the terminal is not taking commands. I'm typing command, hit enter, but then nothing happens, the cursor just moves down row. What Might be the problem ?

---

### Post by Closed_Port on 2009-06-23
> **Mortos said:**
> I Installed Ubuntu on my PC, but the terminal is not taking commands. I'm typing command, hit enter, but then nothing happens, the cursor just moves down row. What Might be the problem ?

What command are you typing?

---

### Post by Mortos on 2009-06-23
For an example:

"Top"
"Free"

---

### Post by Closed_Port on 2009-06-23
Strange.

Are you working in a graphical environment, for example Gnome?
Do you get any error-messages (like command not found, etc.)?
Are you typing the commands the way you posted them or in lower case, as you should? free, top

---

### Post by Mortos on 2009-06-23
Yes, I'm in graphical environment, and I type the commands correctly. Could it just be bad installation ? My System is very old:

RAM:256 DDR
CPU: 1.6 Ghz Athlon
Drive 30 Gb free

---

### Post by Closed_Port on 2009-06-23
I must confess I'm stumped.

Some things you could try to find out what the problem might be.

- Try xterm and see if it works there (Press Alt+F2, type xterm)
- Go to a nongraphical terminal and see if it works there (Press Ctrl+Alt+F1, log in and test it. To get back: Ctrl+Alt+F7)
- Try a bash builtin, to see if somehow free and top weren't installed correctly. For example pwd.

And sorry for asking again, but you really don't get any kind of error message?

---

### Post by Mortos on 2009-06-23
Nop, no error message. Thank you I'll try your proposal

---

