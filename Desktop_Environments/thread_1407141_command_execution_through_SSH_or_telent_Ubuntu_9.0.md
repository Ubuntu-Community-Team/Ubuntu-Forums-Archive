---
title: "command execution through SSH or telent Ubuntu 9.04 not working."
date: 2010-02-14
forum: Desktop Environments
---

### Post by VGM on 2010-02-14
Hello..I have ubuntu 9.04..I am not able to do the following things through SSH or telnet to the ubuntu system which I can do directly on GNOME..

1)pc speaker beep by echo "\a"
2) playing a video on my on login.
3) play audio through aplay -q filename.wav

I have to do something like sudo loginname -c 'xterm -e "glxgears "' 
and sudo loginname -c 'gnome-terminal -x sh -c "echo -e "\a""'"'
and sudo loginname -c 'gnome-terminal -x sh -c "aplay -q horse.wav"' to make things work through telnet and SSH.

why I cant directly do all these thing through SSH...Why is it not working..?

---

