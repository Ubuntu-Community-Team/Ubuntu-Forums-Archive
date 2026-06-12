---
title: "How to embed comands in a programstarter"
date: 2006-03-14
forum: Desktop Environments
---

### Post by bengtfalke on 2006-03-14
Today I finally succeeded in getting my beautiful Sony Vaio VGN-TX1XP connecting to Internet with bluetooth and GPRS on my SonyEricsson P910i.... fantastic!

Next task is to embed the commands I have to type in a terminal window in some kind of script that I can start by clicking on an icon on the desktop.
Can someone please point me in the right direction whee I can find a similar example.

Another thing... I start the bluetooth connection with: pon gprs
How do I end the connection from Ubuntu and not from the phone?

---

### Post by kaamos on 2006-03-14
Applications->Accessories->Terminal
```
sudo gedit /usr/local/bin/myscript
```
insert:
> #!/bin/bash
#

your first command
your second command
and so on..
```
sudo chmod +x /usr/local/bin/myscript
```
Then just create a launcher for the command "myscript".

Hope this helps.

---

### Post by bengtfalke on 2006-03-14
Thanks mate... you were quick. I was just going to edit my post and say that I found out how, even though I did it in a somwhat other way.....:)

---

