---
title: "TightVNCserver Keyboard mapping problem after 9.04 Upgrade"
date: 2009-04-27
forum: Desktop Environments
---

### Post by rmccarri on 2009-04-27
Hi,
I recently upgraded to Ubuntu 9.04 on my desktop at home.  When  I went to VNC into it from work, the keyboard mapping was completely wrong.  Has anyone else experienced this and have found a fix?
Thanks!
Rob

---

### Post by rmccarri on 2009-04-27
Hi,
I was able to find a fix for this here:

[https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/108928/comments/13](https://bugs.launchpad.net/ubuntu/+source/control-center/+bug/108928/comments/13)

---

### Post by frostbite4783 on 2009-04-29
Hi, I too am looking for a solution to this very same problem.  Did that solutions work for you?  If so could you break it down in simpler terms, I felt that link was a little vague.

---

### Post by modernmojo on 2009-05-07
The link for the solution is a little vague. I tried to follow it, but it did not work.  Anybody else have a solution for this?

---

### Post by rmccarri on 2009-05-07
Hi everyone.
Sorry for the vagueness of the initial solution.  While that solution did work for fixing the keyboard mapping issue over VNC, it introduced an error for my regular gnome session locally.  However, I was able to find a fix that fixed the VNC issue without any errors:

Find your vnc xstartup file.  It's in /home/"your username"/.vnc directory.

Add the following line:

```
export XKL_XMODMAP_DISABLE=1
```

to make the file read:

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
```

I hope this works for everyone.

---

### Post by vectorm12 on 2009-05-07
I have no issues with the mapping of the keys whatsoever after updating to 9.04 however I do have an issue where the session suddenly stops accepting "£" via VNC. However if I go and type in the same character on the computer locally it starts to work via VNC again. I have no idea of how/why/when this happens. It seems to be completely random in my experience.

I've tried using Vista/windows7 beta 7077 with realvnc client as well as OS X 10.5.6 with realvnc when this issue does present itself. The only way of resolving the issue is by connecting a keyboard to the computer and make the input locally after that it starts to work again via VNC sessions as well.

Anyone seen this one before?

---

### Post by chakujitsu on 2009-05-17
> **rmccarri said:**
> Hi everyone.
Sorry for the vagueness of the initial solution.  While that solution did work for fixing the keyboard mapping issue over VNC, it introduced an error for my regular gnome session locally.  However, I was able to find a fix that fixed the VNC issue without any errors:

Find your vnc xstartup file.  It's in /home/"your username"/.vnc directory.

Add the following line:

```
export XKL_XMODMAP_DISABLE=1
```

to make the file read:

```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession
```

I hope this works for everyone.
Works like a charm! 
THANK YOU!

---

### Post by bemar on 2009-10-10
Worked for me. Thank you

---

### Post by ericaslakson on 2009-11-04
doesn't work for me.  I just another false mapping.

---

### Post by AaronBaruch on 2009-11-17
I have the same problem with ubuntu 9.10 here. My workaround was to install vnc4server instead of tightvncserver.

---

### Post by chakujitsu on 2009-11-19
Now on 9.10
Same fix stated by rmccarri (adding : export XKL_XMODMAP_DISABLE=1) worked again like a charm :))

---

### Post by Hoos-foos on 2010-01-20
Same here after I correctly typed O instead of 0 (O, not Zero).  duh
 
> **chakujitsu said:**
> Now on 9.10
Same fix stated by rmccarri (adding : export XKL_XMODMAP_DISABLE=1) worked again like a charm :))

---

### Post by ale3andro on 2010-04-06
Works for me too!
Thank you so much!

---

