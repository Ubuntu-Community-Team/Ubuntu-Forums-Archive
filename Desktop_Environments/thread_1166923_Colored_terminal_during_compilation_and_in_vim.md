---
title: "Colored terminal during compilation and in vim"
date: 2009-05-22
forum: Desktop Environments
---

### Post by crazy ivan on 2009-05-22
Hi guys, as far as I know, ubuntu only ships with colored "ls" in the terminal. So I changed the following section of my "~/.bashrc"

```
# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
# force_color_prompt=yes
```

to 

[HTML]# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
force_color_prompt=yes
export TERM=xterm-256color[/HTML]

And now I obtain 
```
ivan@ivan-laptop:~$ tput colors
256
```

and its all full of colors.. Except for the things I needed

1) VIm
2) a makefile we use for compiling our project in colors... 

```
export blue='\E[34;47m'
export endBlue='\033[0m'
export StartHeader=$(redWhite)"\033[1m
export StartHeader_green=$(whiteGreen)"\033[1m
export StartHeader_red=$(whiteRed)"\033[1m
export EndHeader=\033[0m"
```

the latter still producing stuff like :
```
-e \E[31mCollecting all source code information...
```


I've kinda ran out of ideas #-o

---

### Post by crazy ivan on 2009-05-22
hmm actually I removed the "export TERM" line again, since it makes the real terminals (Accessible by "Ctrl+Alt+F Number") display the "/home" line twice and crash after a while.. 

Also I would not recommend the solutions from 
[http://push.cx/2008/256-color-xterms-in-ubuntu](http://push.cx/2008/256-color-xterms-in-ubuntu)
since they break the entire xsession for me...

---

### Post by blue13130 on 2009-05-22
To get colour in vim you have to create a file called ~/.vimrc with the line "syntax on"

```
sanjay@acer:~$ cat ~/.vimrc 
syntax on
```

---

### Post by crazy ivan on 2009-05-22
Also one needs to have the package "vim-full" installed ^^ Thanks.

Any ideas about the Makefile?

---

