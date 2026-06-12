---
title: "&quot;Open Terminal Here&quot; rightclick menu"
date: 2005-06-04
forum: Desktop Environments
---

### Post by ante0 on 2005-06-04
Didnt know where to post this, but thought here would be a good place.
Ok, so I figured out how to make a 'Open Terminal here' script, didnt think it would work at first, but it did =)
To start with you would need Gnome, next copy this code:

#!/bin/bash
gnome-terminal
Paste it into a textfile, and save in  /home/yourname/.gnome2/nautilus-scripts/
name it whatever you want, Terminal could be a good name =)
Then use chmod +x filename in a terminal.

Now when you rightclick in a window, go to scripts and click Terminal, that opens up a terminal with the dir set to the dir where you opened it.
Kinda good, right?! =P

---

### Post by GrumpySimon on 2005-06-04
Excellent :)

--Simon

---

### Post by Majlo on 2005-06-05
Or add backport repository and type 

*sudo apt-get install nautilus-open-terminal* 

Open in terminal is direct in right click menu

---

### Post by nickless on 2005-06-05
Thios thread would be better placed in Customization Tips & Tricks as a How-to :)

---

