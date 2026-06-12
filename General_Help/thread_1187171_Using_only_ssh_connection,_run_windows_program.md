---
title: "Using only ssh connection, run windows program"
date: 2009-06-14
forum: General Help
---

### Post by TayfuN on 2009-06-14
I have a problem, how can I run windows program, having only ssh connection ? Maybe somehow I can install VNC or other Remote Desktop programs ? I'm using Ubuntu Server Edition 8.04.

Thanks.

---

### Post by whitethorn on 2009-06-14
Just a couple questions, are you trying to connect to a different computer with windows on it?  If so then you could use rdesktop

```
rdesktop ip.to.windows.pc
```

If you want to run a windows program in linux, then you can use wine.  Look for it in synaptic,

---

### Post by TayfuN on 2009-06-14
I need connect from windows to Linux. I can't connect to Linux anything with, except SSH. There is no grafic-interface like Gnome or KDE. So I need somehow to install it with console, and install Remote Desktop with that, I could connect to Linux from Windows.

---

### Post by Celauran on 2009-06-14
Unless I'm missing something, why not just SSH in from Windows using something like PuTTy?

---

### Post by TayfuN on 2009-06-14
Yes and how with PuTTy run windows application ?

---

### Post by TayfuN on 2009-06-14
Any other ideas ?

---

### Post by solitaire on 2009-06-14
> **TayfuN said:**
> I need connect from windows to Linux. I can't connect to Linux anything with, except SSH. There is no grafic-interface like Gnome or KDE. So I need somehow to install it with console, and install Remote Desktop with that, I could connect to Linux from Windows.


So you want to control the Linux box via Windows?
& 
Linux box does not have a GUI installed so it's only command line.

A program like PuTTY will give you access to the command line via SSL with no issues. (I use PuTTY in my nokia E63 to get access to the command line of my Ubuntu box.)

You can't use Remote Desktop because the Linux box does not have Gnome or KDE (the GUI) installed.

 
The Best you'll get is a web based interface like "WebMin" [http://www.webmin.com/](http://www.webmin.com/) (there probably are other admin products avalible) that you can access vie IE or Firefox to control the Server.

Otherwise you're stuck with the command line interface untill you install KDE or Gnome onto the Server.

---

### Post by Chronon on 2009-06-14
> **TayfuN said:**
> Yes and how with PuTTy run windows application ?

I don't understand this bit.  You say you want to connect from Windows to Linux via SSH.  Someone mentioned to use something like PuTTY and you replied with the above.  Why do you have Windows applications on your Linux box that you need to run from Windows?

---

### Post by TayfuN on 2009-06-15
I said I can connect to server via SSH (PuTTy) and I installed Gnome GUI, so maybe now I can access (somehow) to server with remote (and with GUI) to server from Windows box ?

---

### Post by sedawk on 2009-06-15
Hello!

Yes, you can login via ssh from Windows to Ubuntu and run graphical
applications that show the window on your Windows box!

HowTo:

You need a X11 Server running on your windows box!

There are commercial ones and there is one that once
was free but now is commercial again (if you are lucky
you find older free version on the web).
But I recommend to install free (!) cygwin with X. This
not only gives you a unix like environment on your windows
box, but it also gives you ssh and X.
(You can even run sshd to connect from Linux back to your Windows box).

[http://www.cygwin.com](http://www.cygwin.com)

After installing cygwin with ssh and X(11) you start cygwin
and in the console you enter "ssh -X username@your_linux_box".
Now running your graphical applications should show the windows on your
windows box (e.g. test with xclock).

Have fun!

---

