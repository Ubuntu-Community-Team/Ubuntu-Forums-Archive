---
title: "ugly gray theme with sudo applications"
date: 2007-04-01
forum: Desktop Environments
---

### Post by haricharan on 2007-04-01
I am getting an ugly gray theme when i use gksudo b4 applications.. I found a similar thread but that didn;t help me either.... [http://www.ubuntuforums.org/showthread.php?t=294961](http://www.ubuntuforums.org/showthread.php?t=294961)

The commands entered were

 [IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=28705&stc=1&d=1175424081[/IMG]

First Command

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=28706&stc=1&d=1175424168[/IMG]

Second Command

[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=28707&stc=1&d=1175424275[/IMG]

How do i solve this??

---

### Post by adam.tropics on 2007-04-01
To make your themes match, from a terminal, do
```

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts
```

---

### Post by Boni2k on 2007-04-01
After this is solved... Could you tell me what console you are using?
It's so full of colors :)

---

### Post by haricharan on 2007-04-01
cool..it works...the problem i had was that the .themes, .fonts, and .icons folder already existed in the root folder. So i couldn't create a link with the same name. What i did i have given below
```
sudo rm -rf /root/.fonts
sudo rm -rf /root/.icons
sudo rm -rf /root/.themes
sudo ln -s /home/<username>/.fonts /root/
sudo ln -s /home/<username>/.icons /root/
sudo ln -s /home/<username>/.themes /root/
```

and it works now...thank you :D

---

### Post by haricharan on 2007-04-01
> **Boni2k said:**
> After this is solved... Could you tell me what console you are using?
It's so full of colors :)

Its just the normal gnome-terminal with some modifications to the .bashrc file. I got ideas from this thread [http://www.ubuntuforums.org/showthread.php?p=2325771]("http://www.ubuntuforums.org/showthread.php?p=2325771")  and [http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/]("http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/"). If you want I could provide what modification i did to get my prompt like this. I shall post the wallpaper and send you the link.

---

### Post by Boni2k on 2007-04-01
I'd be glad if you could pass me your lines of code. The syntax looks too ugly for me, so could you delete the second line and the date for me?

So that only boni:~/workspace$ is written in there?

Many thanks, Boni

---

### Post by haricharan on 2007-04-01
I believe thats the default prompt. follow the instructions in the thread...the thread is just for colors..you should be able to get it.

```
gedit ~/.bashrc
```
Comment out all the lines from the comment that says "set a fancy prompt" and case "$TERM" to the immediate esac line. And add this line after the commented part
```
PS1="${debian_chroot:+($debian_chroot)}\[\033[1;31m\]\u\[\033[1;36m\]:\[\033[1;33m\]\w\[\033[1;36m\]$ \[\033[0m\]"
```
This gives the username in red color and path in yellow.
The one below shows the code for my prompt.
```
PS1="${debian_chroot:+($debian_chroot)}\[\033[0;36m\][\[\033[1;32m\]\$(date +%b\ %d)\[\033[0;36m\], \[\033[1;35m\]\$(date +%H\:%M:%S)\[\033[0;36m\]]\[\033[1;31m\] \u\[\033[1;36m\]:\[\033[1;33m\]\w\[\033[1;36m\]$ \[\033[0m\]"
```

---

### Post by haricharan on 2007-04-01
Wallpaper [http://ubuntuforums.org/g/index.php?n=227](http://ubuntuforums.org/g/index.php?n=227)

---

### Post by Boni2k on 2007-04-02
Thank you, it's perfect :)

I actually needed to edit /etc/bashrc.conf (or something like that) instead, but it works!

---

