---
title: "Cannot access Ubuntu GUI"
date: 2008-12-19
forum: General Help
---

### Post by folkestad on 2008-12-19
Hello!

Had some problems concerning sound on my ubuntu setup, so I completly removed all ALSA from the synaptic. restarted the computer to install the ALSA again, but never got that opertunity. 

When i start my computer now, everything is normal until the Ubuntu loading status bar screen is finished. Then usually the logon screen would have come, but not anymore. only thing i get is a fullscreen Terminal window, where i can type in login information to get the ability to type commands. have tried recovery mode but nothing. what should i do to get into ubuntu again?

---

### Post by Titan8990 on 2008-12-19
To start the GUI from a tty terminal:


sudo /etc/init.d/gdm start


If it fails, you should get an error message that you can post here.

---

### Post by folkestad on 2008-12-19
Not sure what a tty terminal is, new in this game! 

Tried the command [HTML]To start the GUI from a tty terminal:


sudo /etc/init.d/gdm start


If it fails, you should get an error message that you can post here. [/HTML]

But i tried the command on the only screen i can reach, but i got no respons on it. 

"ubuntu hang "kinit: No resume image, doing normal boot… " cannot log on" is the last message i get

---

### Post by folkestad on 2008-12-19
Not sure what a tty terminal is, new in this game! 

[HTML]To start the GUI from a tty terminal:


sudo /etc/init.d/gdm start


If it fails, you should get an error message that you can post here. [/HTML]

But i tried the command on the only screen i can reach, but i got no respons on it. 

"ubuntu hang "kinit: No resume image, doing normal boot… " cannot log on" is the last message i get

---

### Post by folkestad on 2008-12-19
Not sure what a tty terminal is, new in this game! 

[HTML]To start the GUI from a tty terminal:


sudo /etc/init.d/gdm start


If it fails, you should get an error message that you can post here. [/HTML]

But i tried the command on the only screen i can reach, but i got no respons on it. 

"ubuntu hang "kinit: No resume image, doing normal boot… " cannot log on" is the last message i get.

---

### Post by Titan8990 on 2008-12-19
So you are never presented with a log in screen? The TTY terminals are the command line places with no GUIs. I was under the impression that is what you were getting to.

---

### Post by folkestad on 2008-12-19
No, i cannot see no log in screen. before the log in screen usually appears i get a fullscreen-like terminal window wich i cannot close, just like DOS

---

### Post by folkestad on 2008-12-19
and since i cannot go online from the text mode, i cannot download new packs.

---

