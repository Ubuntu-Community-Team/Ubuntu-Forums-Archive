---
title: "xfce4 on vnc"
date: 2005-10-14
forum: Desktop Environments
---

### Post by Fitti on 2005-10-14
Hello,

I use Gnome in the physycal desktop but I want to use xfce4 in a virtual desktop using vncserver. I installed vncserver but when I start the vncserver the desktop's loaded is gnome. I created the file ~/.vnc/xstartup with: 

#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startxfce4 &

But nothing happend.

What is the problem?


Sorry for my english, Fitti.

---

### Post by Stormy Eyes on 2005-10-14
Did you do **chmod +x ~/.vnc/xstartup** to make the script executable? Chances are that your box thinks that the xstartup script you just wrote is still a plain text file and not a shell script.

---

### Post by Fitti on 2005-10-14
[QUOTE=Stormy Eyes]Did you do **chmod +x ~/.vnc/xstartup** to make the script executable? Chances are that your box thinks that the xstartup script you just wrote is still a plain text file and not a shell script.[/QUOTE]

Yes, I did. :???:

---

### Post by Stormy Eyes on 2005-10-14
Question: is this virtual desktop you have in mind on the same physical machine as your GNOME desktop? If so, just run **gdmflexiserver** at a prompt, or select "New Login" from "Applications -> System" to run a second GDM login screen. You can then select XFCE from the sessions menu, and switch between sessions with CTRL+ALT+F7 and CTRL+ALT+F8. I use this often when tricking out my desktop.

---

### Post by Fitti on 2005-10-14
[QUOTE=Stormy Eyes]Question: is this virtual desktop you have in mind on the same physical machine as your GNOME desktop? If so, just run **gdmflexiserver** at a prompt, or select "New Login" from "Applications -> System" to run a second GDM login screen. You can then select XFCE from the sessions menu, and switch between sessions with CTRL+ALT+F7 and CTRL+ALT+F8. I use this often when tricking out my desktop.[/QUOTE]

No, I will use the virtual desktop from others computers.

Thanks ;)

---

### Post by Stormy Eyes on 2005-10-14
OK. Try [this howto.](http://ubuntuforums.org/showthread.php?t=42941) I use it when I have to do work on my wife's computer so that I don't have to kick her off.

---

### Post by nilfilter on 2005-10-15
[QUOTE=Fitti]#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startxfce4 &[/QUOTE]
My ~/.vnc/xstartup file consists of a mere three lines:
```
#!/bin/sh
unset SESSION_MANAGER
startxfce4 &
```I guess you will need to add the *unset SESSION_MANAGER* option. Also, make sure the user you want to connect with has a vnc password.

---

### Post by ubunaut on 2008-05-05
> **Fitti said:**
> Hello,

I use Gnome in the physycal desktop but I want to use xfce4 in a virtual desktop using vncserver. I installed vncserver but when I start the vncserver the desktop's loaded is gnome. I created the file ~/.vnc/xstartup with: 

#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startxfce4 &

But nothing happend.

What is the problem?


Sorry for my english, Fitti.

Hmm well it seems strange that you had to create the file ~/.vnc/xstartup since it should be made for you, i recommend installing vnc4server with: sudo apt-get install vnc4server
then run it (just type vnc4server) and the ~/.vnc/xstartup file should be made for you.

to use xfce4 just replace the last line (twm &) with startxfce4 & (like you did)

here is my ~/.vnc/xstartup 

```
#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
startxfce4 &

```

this is using vnc4server on ubuntu 8.04 desktop i386

---

