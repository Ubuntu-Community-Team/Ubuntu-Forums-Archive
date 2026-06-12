---
title: "Gtk warning"
date: 2015-06-28
forum: Desktop Environments
---

### Post by napapon on 2015-06-28
Hi,

I am using ubuntu 14 LTS and when I source .tcshrc file which contains this line

alias newwin xfce4-terminal --show-toolbar --display=display --command=tcsh

afterward I typed newwin i got an error (xfce4-terminal:3397): Gtk-WARNING **: cannot open display: display

I have to start xfce4-terminal first and issue the above command in terminal

Is there any way I can starts xfce4 terminal without this running around.

thanks for your comments.

---

### Post by tgalati4 on 2015-06-28
Open a terminal and examine

```
env
```

Perhaps you need a Display:=0.0 in your .tcshrc file.  There may be other environment variables needed as well.  That is why you need to examine your environment variables in the environment that is working correctly.

Since the xorg (X11) graphics server can address 10 different displays, you need to tell it which display to send the output to.  I'm going to guess that the switch --display=display should be --display=0 or --display=:0.0, but you can play with it.  I'm also going to guess that you can leave off the --display switch and it will default to :0.0.  I'm not running xfce, so you will have to experiment.

[http://docs.xfce.org/apps/terminal/command-line](http://docs.xfce.org/apps/terminal/command-line)

---

