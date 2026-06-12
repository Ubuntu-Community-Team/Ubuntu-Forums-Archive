---
title: "Launch an application instead of desktop"
date: 2008-05-08
forum: Desktop Environments
---

### Post by Son of Silas on 2008-05-08
I have built a Xubuntu Hardy PC, that I would like to boot directly into the application Wah!Cade, rather than a full blown desktop. The application has a forum that has many threads detailing how to do this although they don't seem to apply to Xubuntu. An example of one such set of instructions is:
> there is a way to start the system with wahcade. I did it the following way:
You need the program mingetty.
Then in the /etc/inittab file you will find lines like
Code:
1:23:respawn:/sbin/getty 38400 tty1

I changed this line starting with 1 (there are six of it for every shell you get with alt + f* keys) to
Code:
1:23:respawn:/sbin/mingetty --autologin username tty1

where username is the user who starts the x-system.
Then edit the ~/.xsession file so that the last line says something like
Code:
Eterm -e wahcade -f
if you use Eterm as an X-Terminal. 

I don't seem to have a /etc/inittab file (nor would I know what one did even if i did have one).

Can someone please tell me how I bypass Xfce and just boot directly into an application? (preferably in words of one syllable ;-) )

Thanks

---

### Post by apoth on 2008-05-08
You'll need a window manager, you can't just boot an application (I'm pretty sure I'm right in saying).

What might suit you though is to load a no-frills WM (maybe fvwm, or a box, perhaps openbox) and as soon as that loads have a script run the application fullscreen. I'd start by installing openbox and see what you think of it.

---

### Post by Son of Silas on 2008-05-08
I come from a Windows background. I remember years ago at college they had windows 3.11 PCs that they modified the shell to be 'clock' so the windows clock was the first thing that came up. Can I do that with Xubuntu? Instead of the GUI being the XFCE desktop, it's my application?

---

### Post by Son of Silas on 2008-05-08
> **apoth said:**
> You'll need a window manager, you can't just boot an application (I'm pretty sure I'm right in saying).

What might suit you though is to load a no-frills WM (maybe fvwm, or a box, perhaps openbox) and as soon as that loads have a script run the application fullscreen. I'd start by installing openbox and see what you think of it.

I've installed openbox... But have no idea what to do next? How do I create/load a script?

---

### Post by spupy on 2008-05-08
Create a file in your home dir, named ".xinitrc". In it write:
```
exec programname
```
You have to setup the OS to NOT start GDM at startup. You get instead a consol login. Enter your username and password, then type
```
startx
```
Your program should start. No window managers needed.
If you need any details on this, just ask.

---

