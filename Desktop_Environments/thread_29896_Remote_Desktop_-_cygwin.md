---
title: "Remote Desktop - cygwin"
date: 2005-04-26
forum: Desktop Environments
---

### Post by cwjam on 2005-04-26
I am trying to connect to a remote desktop on my ubuntu box from a windows machine running cygwin.

I have followed this guide, [http://www.ubuntulinux.org/wiki/HowToCygwinX](http://www.ubuntulinux.org/wiki/HowToCygwinX), and I can get to the login screen but after I login the screen stays brown, i can see & move the cursor from the linux box.

It appears the nautilus is not booting up and im just stuck with a brown desktop and cant do anything.

Anybody got any ideas?

Cheers!


P.S. System works fine when I login at the machine itself!

---

### Post by cwjam on 2005-04-26
ok have a bit of an update,

After about 10mins of the brown screen gnome loads up (very slowly)

it is unworkable though!

---

### Post by cwjam on 2005-04-26
is this a gnome issue? I have looked at other discussions where gnome seems to stall after the login screen.

My problem is that it works fine logging in from the machine but give me problems when i try to log in remotly

any help? thanks

---

### Post by cwaldbieser on 2005-04-26
How do individual X apps work?  For example, open up your Cygwin terminal, run /usr/X11r6/bin/startxwin.sh to get the xterm, and in the xterm issue a

$ ssh -Y -l username hostname_or_ip

Once you log into the remote machine, type 

$ gedit

or some other graphical app.  Does that seem to perform any better?  I have had some oddball results when trying to run the entire desktop over Cygwin, and the performance is somewhat less than stellar.

---

### Post by cwjam on 2005-04-27
This is the login message I get:

```
Warning: No xauth data; using fake authentication data for X11 forwarding.
Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have mail.
Last login: Wed Apr 27 10:09:10 2005 from 192.168.1.5
/usr/bin/X11/xauth:  /home/colm/.Xauthority not writable, changes will be ignored
colm@ubuntu:~$ 
``` 
Then when i run "gedit" I get this:

```
X11 connection rejected because of wrong authentication.
The application 'gedit' lost its connection to the display localhost:10.0;
most likely the X server was shut down or you killed/destroyed
the application.
```

---

### Post by cwjam on 2005-04-27
OK have more of an update.

Just added a new user account - seems that root had over written the .X files in my home directory, I can now run gedit fine as you say.

I would really like to be able to be able to have the same setup as, [http://www.ubuntulinux.org/wiki/HowToCygwinX](http://www.ubuntulinux.org/wiki/HowToCygwinX) , any ideas why gnome stalls?

---

