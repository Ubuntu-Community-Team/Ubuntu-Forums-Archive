---
title: "xterm not working from a MacBook Pro laptop"
date: 2007-09-04
forum: Desktop Environments
---

### Post by spawnlcd on 2007-09-04
Hi Everyone!

      I am new to Ubuntu, and I am trying to access it via a xterm from a MacBook Pro laptop, but I am running into issues. Here is the output of my problems:

**spawn@linux-sec-test:/etc/init.d$ export DISPLAY=localhost:0.0**

**spawn@linux-sec-test:/etc/init.d$ xhost +**

***xhost:  unable to open display "localhost:0.0"***

**spawn@linux-sec-test:/etc/init.d$ xterm**

***xterm Xt error: Can't open display: localhost:0.0***

**spawn@linux-sec-test:/etc/init.d$ tinyca2**

***Gtk-WARNING **: cannot open display:   at /usr/lib/perl5/Gtk2.pm line 63.***

I can't seem to start any X program from my Ubuntu server on my Mac.

I have the following settings under /etc/ssh/sshd_config

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

I am running Ubuntu version 6.x server, with the following:

Linux linux-sec-test 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

What I am I doing wrong? :confused:

Thanks,

Rafael

---

### Post by kidders on 2007-09-06
Hi there,

> **spawnlcd said:**
> **spawn@linux-sec-test:/etc/init.d$ export DISPLAY=localhost:0.0**

You probably won't be able to start X applications on a remote display without tweaking its security settings ... which usually requires root privs.

> **spawnlcd said:**
> I can't seem to start any X program from my Ubuntu server on my Mac.Setting a remote host's DISPLAY environment variable to "localhost" forces applications to use the host's *own* X server. Are you sure you posted the right terminal output?

---

### Post by spawnlcd on 2007-09-07
> **kidders said:**
> Hi there,
You probably won't be able to start X applications on a remote display without tweaking its security settings ... which usually requires root privs.

How is that done? Sorry, I am very new to linux.



> **KIDDERS said:**
> Setting a remote host's DISPLAY environment variable to "localhost" forces applications to use the host's *own* X server. Are you sure you posted the right terminal output?

Yes, I think so, I tried this on a ubuntu desktop, and it works, but not on my Mac.

---

### Post by kidders on 2007-09-07
Hmmm... I can imagine something like it working on a Mac or Linux box you're sitting in front of, but not one you're logged into remotely. After all, your Linux box wouldn't last 10 seconds if there were a way to hijack its X server with nothing more than a few commands.

If you *really* want to allow remote display hijacking, you could try starting your X server with the "-ac" switch, but there are no circumstances in which doing so would be a good idea.

I presumed from your original post that you were trying to start remote applications on a *forwarded* X display. Sorry about that.

---

### Post by gnack on 2007-10-09
> **spawnlcd said:**
> 
      I am new to Ubuntu, and I am trying to access it via a xterm from a MacBook Pro laptop, but I am running into issues. Here is the output of my problems:

**spawn@linux-sec-test:/etc/init.d$ export DISPLAY=localhost:0.0**
**spawn@linux-sec-test:/etc/init.d$ xhost +**
***xhost:  unable to open display "localhost:0.0"***
**spawn@linux-sec-test:/etc/init.d$ xterm**
***xterm Xt error: Can't open display: localhost:0.0***

I can't seem to start any X program from my Ubuntu server on my Mac.

What I am I doing wrong? :confused:


I don't know if you've solved this yet, but to run an X application remotely from your Linux host on your MacBook, you need a X11 server running on your MacBook and DISPLAY should be set to the MacBook's address (if ssh X11 forwarding is working properly, DISPLAY will be set automatically).

I don't know how to run a X11 server in OS X but if you get that running then you should be able to just log into linux-sec-test and launch your X applications without changing any environment variables (you might posslby need to `xhost +` on the MacBook depending on it's default access restrictions).

---

