---
title: "xterm + vnc = freeze"
date: 2006-04-27
forum: Desktop Environments
---

### Post by effo on 2006-04-27
I'm a Linux newbie who just have set up my Kubuntu 5.10. I have a problem running xterm when connecting to my Kubuntu using vnc. When I log in locally on the box, starting xterm is fine. But when trying to start it in a vnc session freezes the box for a couple of minues. When the box comes alive again, I just see "killed" on the prompt:
```
effo@kubuntu:~/.vnc$ xterm
Killed
```
Tailing /var/log/messages shows that there is no swap left:
```
Apr 27 16:47:42 localhost kernel: [4307719.721000] Free swap = 0kB
Apr 27 16:47:42 localhost kernel: [4307719.721000] Total swap = 1028152kB

```
I have used [this]("http://ubuntuforums.org/showthread.php?t=44836") instruction to make vncserver start kde. 

Any ideas of what I'm doing wrong?

---

