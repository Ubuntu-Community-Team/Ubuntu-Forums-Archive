---
title: "desktop effects help"
date: 2007-07-08
forum: Desktop Effects &amp; Customization
---

### Post by Lunatrix on 2007-07-08
i turned it on and now my whole screen is white, can anyone help me? like tell me a keyboard shortcut or something like that?

---

### Post by Lunatrix on 2007-07-08
noone can help me?

---

### Post by kingof1981 on 2007-07-08
ctrl+alt+backspace

if that doesn't work...
log you into tty1 with ctrl+alt+F1  your choises can be between  (F1-F6)

then
apt-get autoremove gdm
apt-get install gdm
reboot

or install mc and start mc i tty1
and fix it from there...

---

### Post by Lunatrix on 2007-07-08
it says im not root when i try the first command, but i am lol

---

### Post by Lunatrix on 2007-07-08
so what should i do?

---

### Post by Sonicgoo on 2007-07-08
Add sudo to all commands

then
sudo apt-get autoremove gdm
sudo apt-get install gdm
reboot

---

### Post by Lunatrix on 2007-07-08
k ill try the sudo thing.

---

### Post by Lunatrix on 2007-07-08
the second command doesent work, it said there is no package avaliable or something around those lines.

---

### Post by Lunatrix on 2007-07-08
great now linux doesent start up normally. it just goes straight into ALT+CTRL F1-F6

---

### Post by Sonicgoo on 2007-07-08
Try this:

sudo aptitude install ubuntu-desktop

found on the following thread

[http://ubuntuforums.org/showthread.php?t=491100](http://ubuntuforums.org/showthread.php?t=491100)

---

### Post by Lunatrix on 2007-07-08
nope, still dunt work.

---

### Post by Lunatrix on 2007-07-08
all i have to say is that that screwed my computer over.

---

### Post by Lunatrix on 2007-07-08
unless theres a way to get it back or reverse that move.

---

### Post by Lunatrix on 2007-07-08
why is it now that im having like a FATAL ERROR he doesent respond?

---

### Post by Sonicgoo on 2007-07-08
now try 

sudo /etc/init.d/gdm start

more info here:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Lunatrix on 2007-07-08
i just reinstalled linux and that seamed to work lol. but if you can look at my new post. thanks!

---

