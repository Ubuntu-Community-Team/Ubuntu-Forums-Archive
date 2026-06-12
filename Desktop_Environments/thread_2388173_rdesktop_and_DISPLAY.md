---
title: "rdesktop and DISPLAY"
date: 2018-03-29
forum: Desktop Environments
---

### Post by ulrichmuc on 2018-03-29
I use  rdesktop to open a desktop on a remote computer. Local and remote run ubunto 16.4, mate-desktop
When I click Mate Terminal, I get a terminal; so far so good.
The pertinant Desktop-File contains "Exec=mate-terminal".

However, when I try to start mate-terminal (or any other program with GUI) from the command line, I get 

Invalid MIT-Magic-COOKY-1 keyFailed to parse arguments: Cannot open Display:

echo $DISPLAY gives :0.0

So why can the Desktop-file call mate-terminal, but I can not?

How can I fix this?

---

