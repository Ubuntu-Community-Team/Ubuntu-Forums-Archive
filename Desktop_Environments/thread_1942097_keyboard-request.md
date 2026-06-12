---
title: "keyboard-request"
date: 2012-03-16
forum: Desktop Environments
---

### Post by clarenceweaver on 2012-03-16
in 11.10 upstart keyboard-request is mapped to Alt-UpArrow but so is something else in Unity because it only works correctly in a console. In a pseudo-term it just returns an upper case A

my script in /etc/init/alt-up-arrow.conf is 

start on keyboard-request
task
exec wall ~/now

the file is a simple text file

Anyone have any ideas on how to remap keyboard-request or remap Alt-Up-Arrow?

---

