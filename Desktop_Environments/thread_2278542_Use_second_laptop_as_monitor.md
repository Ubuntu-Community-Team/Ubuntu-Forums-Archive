---
title: "Use second laptop as monitor"
date: 2015-05-17
forum: Desktop Environments
---

### Post by devdlp on 2015-05-17
So my monitor i was using as a dual monitor blinks on/off now i wanna use my second laptop that also has ubuntu 14.04 on it as my replacement monitor. How do i use the second laptop as a monitor? What i need is to display whats going on on the 1st laptop on the second laptop so i can work on the 1st laptop using the second one because the 1st laptop screen is crack and is impossible to use, i have a display adapter connecting them both already i just dont now what to do in the settings to get this to work, or is it not possible?? Thanks in advance or the help guys!

---

### Post by Vladlenin5000 on 2015-05-17
Not possible.

---

### Post by Copper Bezel on 2015-05-17
At least not without disassembling both of them and making a mess. = .

---

### Post by SeijiSensei on 2015-05-17
I can see two possibilities, both using SSH.  One would be using the laptop to display textual sessions after connecting with SSH.  The other option is to use "[ssh -X]("http://www.cyberciti.biz/faq/linux-unix-tunneling-xwindows-securely-over-ssh/")" to connect with the laptop, then run graphical applications on the main machine.  They will then display on the laptop's screen.

---

