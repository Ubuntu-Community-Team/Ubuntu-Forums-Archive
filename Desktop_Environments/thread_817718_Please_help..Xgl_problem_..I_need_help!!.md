---
title: "Please help..Xgl problem ..I need help!!"
date: 2008-06-03
forum: Desktop Environments
---

### Post by N3um0rin on 2008-06-03
Xsession.unable to launch "/usr/bin/startxgl.sh" Xsession --- "/usr/bin/startxgl.sh" Not found ; falling back to default session

I get this error when i log onto the xgl session...Im sure its a simple fix..but im still a n00b at it..help the poor little n00b please?

---

### Post by F4l3 on 2008-06-04
> **N3um0rin said:**
> Xsession.unable to launch "/usr/bin/startxgl.sh" Xsession --- "/usr/bin/startxgl.sh" Not found ; falling back to default session

I get this error when i log onto the xgl session...Im sure its a simple fix..but im still a n00b at it..help the poor little n00b please?
try this:
- Ctrl + Alt + F1 (this will change your screen)
- sudo chmod 777 /usr/bin/startxgl.sh (this will gave you the power to exec that script)
- Ctrl + Alt + F7 (it restore your X server as main window)
- Ctrl + Alt + Back (this will restart your X server)
I think this will work :)

---

### Post by N3um0rin on 2008-06-04
No i dont think it worked..xgl now just doesnt show the error and goes back to normal kde...=\

---

