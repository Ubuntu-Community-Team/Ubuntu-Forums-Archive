---
title: "Launch icon command in terminal window"
date: 2009-04-21
forum: General Help
---

### Post by dabbi2000 on 2009-04-21
I've got an icon on desktop which I want to open a terminal and then ssh log into another computer.
I've got the command line "ssh xxx....." and it opens a window, asks for password but then nothing - how do I add an option to run this in a terminal window?

---

### Post by sahabcse on 2009-04-21
I think some remote system mounted in your computer. For accessing other system
type in terminal

ssh username@ipaddress

---

### Post by James_Lochhead on 2009-04-21
If you create a bash file (call it any name, doesn't need a file type)

In the file type:

#!/bin/bash
ssh xxx...

Then go to the terminal...

cd Desktop
chmod +x <bash_file_name_here>

Then when you double click it you will get asked how to run it. You can choose run in terminal.

---

### Post by dabbi2000 on 2009-04-22
thx!

---

