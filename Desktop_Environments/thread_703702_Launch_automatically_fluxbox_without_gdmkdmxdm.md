---
title: "Launch automatically fluxbox without gdm/kdm/xdm"
date: 2008-02-21
forum: Desktop Environments
---

### Post by dfodor on 2008-02-21
Hi!

I do not want to use any of the graphical display managers for logging in but would like to start fluxbox automatically if I type my login name and password. I tried to make ~/.xinitrc with 
```

exec /usr/bin/startfluxbox

```
and
```

/usr/bin/startfluxbox

```
 contents but I have to start fluxbox by typing startx. I also tried to edit ~/.Xresources but it also did not help. 

Any idea?

Daniel

---

### Post by afoglia on 2008-02-21
I do not recommend this.  You will have problems if you ever try to log in remotely (via ssh or telnet) or try to log into one of the other terminals (via Ctrl-Alt-F2 through Ctrl-Alt-F6), or any other session where a graphical interface is not allowed.

But, since you asked...

You'll need to add startx to the last line of the startup script for your shell.  I believe the default shell is bash, in which case, the file .bash_profile in your home directory gets executed.  Add "startx" as the last line to that.  If it's a different shell, read the man pages for that shell to find the name of the startup file.  For tcsh, it's .tcshrc, for zsh I believe it's .zshrc.

Scripting gurus could probably tell you how to check to see if a graphical interface will work even before startx is called, or to add a timer so you could cancel the startx before it's run, but I'm not that good.

---

### Post by kerry_s on 2008-02-22
put this in your ~/.bash_profile

```
if [ `tty` = "/dev/tty1" ]; then
startx
fi
```

that will startx when you login.

in debian i use rungetty to auto log me in, but ubuntu doesn't use /etc/initab and i cant remember where you put it in ubuntu.

```
1:2345:respawn:/sbin/rungetty tty1 --autologin user
```

"user" would be your log in name, you have to install rungetty(apt-get install rungetty)

just look at your boot stuff i'm sure you can find were the tty's are started from, you only need to change tty1.

---

### Post by mali2297 on 2008-02-22
I would put these last lines in my ~/.profile (which is independent of the shell):
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
  startfluxbox
fi

```

---

### Post by dfodor on 2008-02-25
Hey, thanks for the answers. Adding these lines to my .bash_profile it worked properly. However, if I do not have a display manager, the programs start slower. I press the keys for starting a terminal (e.g., Mod4 and t) then it starts about 10 seconds later. This is not a problem if I have a display manager. Interesting heh? 
Now I am trying to install SLIM instead of gdm. 

Have a nive week

Daniel

---

### Post by mali2297 on 2008-02-26
> **dfodor said:**
>  However, if I do not have a display manager, the programs start slower. I press the keys for starting a terminal (e.g., Mod4 and t) then it starts about 10 seconds later. This is not a problem if I have a display manager. Interesting heh? 


I think that gdm has a function to prefetch programs and thus reduce startup times. As an alternative, you can install the package **preload**. Once installed, it will run automatically in the background.

---

