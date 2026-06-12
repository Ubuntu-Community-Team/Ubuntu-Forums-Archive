---
title: "tighvnc  on ubuntu 9.10"
date: 2010-02-17
forum: Desktop Environments
---

### Post by unix1adm on 2010-02-17
I need to get the code to run a tightvnc client form a ubuntu system to a red hat one. 

I wen tot th epackage manager but dont see the pacakge. 
xtightvncviewer looked for this and tight vnc etc. Nothing comes up...


Any help is appreciated.

---

### Post by unix1adm on 2010-02-17
I know tightvnc uses the ssh connection to tunnel. What other client does that that I could use that is native to Linux/Ubuntu repos etc?


May be i am not asking the right question here.

I need a secure VNC solution over SSH.
I have a system that i remote into and need a secure gui desktop on occasion.

I use tightvnc over putty at work in windows. Works fine.
I have putty on my Ubuntu system and that works. What I am missing is the secure VNC piece of the puzzle

---

### Post by unix1adm on 2010-02-19
no one has any idea on this?

---

### Post by LepeKaname on 2010-02-19
I personally recommend "grdc" as VNC client. You can setup SSH tunneling and other protocols as well. Try it.

Install:  sudo aptitude install grdc

---

### Post by unix1adm on 2010-02-24
thank you i will give that a try.

---

