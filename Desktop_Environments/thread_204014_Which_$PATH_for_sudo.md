---
title: "Which $PATH for sudo?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by ubuntuuser on 2006-06-26
Hi all,

I have just solved a problem that bothered me for a few days ([see here]("http://ubuntuforums.org/showthread.php?t=203414")), but the solution left an interesting question that I am unable to answer. I had a wrong soft link in /usr/bin, and whenever I did ```
sudo *wronglink*
```it didn't work as expected. But whenever I called the program as regular user or as root, everything worked fine. The reason was that the target of that wrong link was at the first place of $PATH of my user and of root, so my PC didn't look in /usr/bin but just executed the target directly. I don't know why, but when I use sudo together with that specific command, my PC tries to execute the soft link, so I guess when I use sudo, the $PATH of my user and of root are not used. My question is now: Does the sudo command have a seperate $PATH set somewhere? If so, where?

I hope I made myself clear. If you don't understand, read my other thread, that will make things clear.

Thanks in advance.__

---

### Post by rbalfour on 2006-06-26
what link are you using.

sudo uses the root path info.

ie.

$ sudo ping [www.google.com](www.google.com)

Then you enter the password.
starts to ping google.

can you post exactly what you are doing?

---

### Post by Ramses de Norre on 2006-06-26
This is what I found: no real difference exept the games thing and a different X11 folder, no differences in /usr/bin though..
```
ramses@icarus:~$ sudo echo $PATH
Password:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
ramses@icarus:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
ramses@icarus:~$ sudo -i
root@icarus:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@icarus:~# exit
logout
ramses@icarus:~$ sudo -s
root@icarus:~# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

```

---

### Post by ubuntuuser on 2006-06-26
I'm sorry if I confused you, after a reboot everything works as expected. Anyway, thanks for trying to help.

---

