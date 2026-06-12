---
title: "Terminal customizing"
date: 2009-05-02
forum: General Help
---

### Post by tenmilez on 2009-05-02
I SSH a lot into another machine and I would like to set it up so that the title of the window/tab changes based on whether I'm connected to another machine or not and to change the background color settings as well so that it's more noticable which machine I am affecting. There's only one machine I connect to so it's not a big deal if the settings would apply whenever I connect to any machine.

---

### Post by Brandon Williams on 2009-05-02
Changing the window/tab title can be done with echo. This command line:
```
echo -ne "\033]0;Hello World\007" && sleep 10
```
changes the title to "Hello World" and then pauses for 10 seconds so that you can see that it changed.

Just remove '&& sleep 10' from the command line and replace "Hello World" with whatever you want the title to be. You have to make sure that the machine you connect in to doesn't override this title, though.

You can write yourself a wrapper script to set the title for you before running ssh. It would look something like this script, which just sets the title to the full list of command line arguments for ssh:
```
#!/bin/sh
echo -ne "\033]0;$*\007"
exec ssh "$@"
```

I don't know how to set the color dynamically. Hopefully someone else will comment on that.

---

### Post by geirha on 2009-05-02
I have the following two lines at the end of ~/.bashrc on all hosts that I ssh to. It picks one of 15 colors based on the hostid (all the 16 ansi colors, except black since I use a black background in the terminal), and sets the hostname portion of the prompt to that color. Some hosts get the same color, but in general I get a different color for each machine.
```

host_color=$(( 0x$(hostid) % 15+1))
export PS1='\[\033[00;32m\]\u\[\033[01;32m\]@\[\033[0$((host_color<8?0:1));3$((host_color%8))m\]\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;$(($?==0?0:31))m\]\$\[\033[0m\] '

```

---

### Post by tenmilez on 2009-05-02
This is awesome. I just decided to go with a black background which makes the colors of the hostname stand out a lot more. 

I noticed something weird though. Sometimes the $ is white (I set the theme to be white on black in the terminal settings) and sometimes it's red. 

This is what I ended up adding

```
host_color=$(( 0x$(hostid) % 15+1))
export PS1='\[\033[00;32m\]\u\[\033[01;32m\]@\[\033[0$((host_color<8?0:1));3$((host_color%8))m\]\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;$(($?==0?0:31))m\]\$\[\033[0m\] '
echo -ne "\033]0;MORGAN-DESKTOP\007"
```

---

### Post by geirha on 2009-05-02
> **tenmilez said:**
> 
I noticed something weird though. Sometimes the $ is white (I set the theme to be white on black in the terminal settings) and sometimes it's red. 


Ah, yes. I recently added this part,

'\[\033[01;$(($?==0?0:31))m\]\$\[\033[0m\] '

complements of this thread: [http://ubuntuforums.org/showthread.php?t=1145400](http://ubuntuforums.org/showthread.php?t=1145400)

It colors the $ red if the previous command failed.

Replace it with '\[\033[0m\]\$ ' if you want it to always be white.

---

