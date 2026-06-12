---
title: "Add a launcher question"
date: 2009-05-08
forum: Desktop Environments
---

### Post by matheuzzy on 2009-05-08
I have a XAMPP (LAMPP) installed and i want to create a launcher in my top panel that will start my lampp

the normal way to start my lampp is to open a terminal and type:

sudo ./opt/lampp/lampp start

I've tried to make a start_apache.sh

#/bin/bash
sudo ./opt/lampp/lampp start

and put this stat_apache.sh in command field from "add Launcher"
...but it doesn't work. I am a noob Ubuntu user (and linux in general) ..pls help

---

### Post by djbushido on 2009-05-08
You forgot an "!"
Should be #!/bin/bash, otherwise the /bin/bash file is viewed as a comment.
Try that.

---

### Post by matheuzzy on 2009-05-09
Thank you! it still doesn't work completly.. but it's ok for now.. I 2xclik the script and I am propted "Run", "Run in terminal", "Display"..  and it;s ok if I run it

---

### Post by MurkMenthaa on 2009-05-09
See if putting "_sh_ stat_apache.sh" in launcher properties does it.
If not, go to Behaviour tab in nautilus preferences and choose "Run executable text files", see if that works.

---

