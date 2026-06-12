---
title: "Remote Desktop not working"
date: 2006-08-13
forum: Desktop Environments
---

### Post by muruke on 2006-08-13
Hey all, I'm having problems getting the remote desktop working in dapper. I have set up remote desktop in the control panel to allow users to connect and control my desktop also requiring a passwork. That dialog tell me to use vncviewer luke:0 to connect to the desktop.

Using that command I get connection refused. Same with the :1 or :2 etc. Running ps -A | grep vino shows that vino-server is running when the computer is first turn on, then the first vncviewer luke:0 returns ReadFromRFBServer: rdr::EndOfStream. Then any connection try after that returns connection refused and ps -A has vino-server running.

Any ideas why vino-server would die, or why I can not connect to my desktop? This is basicly a clean dapper install with quinn XGL packages, though the remote desktop has not worked since I installed.

I have also let through prt 5900 etc through my router to my computer.

Hope someone has some ideas. Thanks.

Luke

---

### Post by its_me_gb on 2006-08-13
have you tried using your external ip, rather than the pc's name?

---

### Post by muruke on 2006-08-13
Yes I have. Same results

---

### Post by dannyboy79 on 2006-09-01
if you are trying to connect from outside your internal network than you will need to forward port 5900 to whaterver ip address the box your try to connect to within your router configuration. if you're trying to connect from within your local network than I have no id? I am trying to set this up and have just startig reading about this but I did however read what I have just informed you of.

---

