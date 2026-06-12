---
title: "how to handle hang-ups"
date: 2006-07-17
forum: Gaming &amp; Leisure
---

### Post by nickless on 2006-07-17
First of all: This is what I do, I have no idea if this is the best solution or good at all. Please tell my if you know a better way!:-k 

After my little brother was able to produce a hang-up in tremulous I figured there must be a better way to solve them then just pushing the restart button. :D Thats too much windows-style... 

And there is! Often the hang-up is not freezing the whole system.
First I push CTRL+ALT+F2 simultaniously to enter tty2. There I can enter the console and start a new session by entering username and password.
Now type ```
ps -e
``` it will show you a list of the running processes. Alternatively you can type ```
top
```, but for these tasks I like ps more. You will see something like this (I shortened it, yours will be a lot longer):
```
 PID TTY          TIME CMD
 4742 ?        00:00:00 run-mozilla.sh
 4748 tty1     00:02:10 conky
 4749 ?        00:04:40 swiftfox-bin
 4759 tty1     00:00:00 gnome-pty-helpe
 4760 pts/0    00:00:00 bash
 4761 pts/1    00:00:00 bash
 4766 ?        00:00:00 gconfd-2
 4790 ?        00:00:00 kio_file
 4843 pts/0    00:00:00 bash
 4846 pts/0    00:00:00 su
 4847 pts/0    00:00:00 bash
 5275 tt1      00:00:00 tremulous
 5281 pts/1    00:00:00 ps

```
Now we will kill the frozen program. If the process has an short name like in my example tremulous we can simply type:```
killall tremulous
``` But sometimes the process has a rather long name, then it is faster to use the PID, type kill and then the PID:
```
kill 5275
```
If everything went right you should be able to get back on your desktop. 
Now push CTRL+ALT+F7 and you get back to tty7, where normaly your desktop is running. Everything should be like you left it before entering the game. Maybe you have deleted some of the tty's to speed up your boot, then your desktop will probably be on the last tty you have. In this case I believe you know which tty it is. (You can also just try F1-F7 to find it :D)

Well sometimes it didn't help and I have no idea why :D E.g. When sauerbraten freezes and I kill the process like that I get a black screen when I get back to tty7. In cases like that you can get around the restarting sometimes by pushing CTRL+ALT+BACKSPACE only restarting your X-desktop. Another option is to go to tty1 with CTRL+ALT+F1 and stop the X-session with CTRL+C. Last option for me is restarting from console with ```
sudo shutdown -r now
``` always better than using the restart button on your computer.

Hope this will help some of you and you have learned maybe a bit more about your system, I know I have :D
If you know something that works better or find mistakes please tell me :). Im sorry for my bad english :o

EDIT: Updated, thx simplyw00x
[quote=simplyw00x]Also, if your mouse and keyboard are unresponsive you can sometimes recover by SHH'ing to your computer and killing the offending process from there. To fix games that don't return the resolution to normal, run `xrandr -s 0`, and to recover from an unreleased mouse/keyboard grab, run another app that grabs it, like frozen-bubble.[/quote]

---

### Post by mozetti on 2006-07-17
Thanks -- I had just defaulted to using the shutdown -r command from tty1. Now I'll have another option before I resort to that.

---

### Post by simplyw00x on 2006-07-17
ps -e is easier to read and doesn't require a sudo bash unless you run your games as sudo. Also, if your mouse and keyboard are unresponsive you can sometimes recover by SHH'ing to your computer and killing the offending process from there. To fix games that don't return the resolution to normal, run `xrandr -s 0`, and to recover from an unreleased mouse/keyboard grab, run another app that grabs it, like frozen-bubble.

---

