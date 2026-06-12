---
title: "Desktop Interface will not load"
date: 2014-07-10
forum: Desktop Environments
---

### Post by chris260 on 2014-07-10
Hi all, 

I am using Ubuntu 12.04.4 LTS on a Lenovo x220i.

For some reason when I boot the machine and log into the desktop I am bounced back to the login screen, I am able to log in through the CLI with the same user (after pressing Ctrl, Alt + F1) but not the GUI.

When logging in as Guest the desktop GUI works fine (I am on it now).

Does anyone have a suggestion as to where I can look for the root cause of this error and fix it?

The only thing that was recently upgraded is VMware Workstation but that should not load on login, I have found threads pointing to removal of NVidia proprietary drivers but I am not running them.

Thanks

C

---

### Post by deadflowr on 2014-07-10
post the output for
```
ls -la .Xauthority
```
as is, do not add anything else.

---

### Post by mooreted on 2014-07-10
Do you see anything in dmesg?

Try typing startx

Are you running Unity, Gnome, KDE?

What video card do you have?

My VMWare Player runs processes in the background even when not running. You might try removing VMWare Workstation to see if that is the cause.

---

### Post by chris260 on 2014-07-11
Thanks to you both,

I am at work right now so will get that information when I get home.

What command can I use to remove VMware Workstation or is there a script in the install path that I can run to remove it?

Cheers

C

---

### Post by chris260 on 2014-07-14
Hi deadflowr, 

Output of ls -la .Xauthority is:
*-rw------- 1 root root 52 Jul 6 11:15 .Xauthority*

Any clues there?

Cheers
C

---

### Post by chris260 on 2014-07-14
Hi moorted, 

startx returns:
[I]xauth: error in locking authority file /home/chris/.Xauthority
xauth: error in locking authority file /home/chris/.Xauthority

Fatal server error:
Server is already active for display 0
   If this server is no longer running, remove /tmp/,X)-lock and start again

(EE)
Please consult the The X.Org Foundation Support as [http://wiki.x.org](http://wiki.x.org) for help
(EE)
No protocol specified
No protocol specified
xinit: giving up
xinit: unable to connect to X server: Resource is temporarily unavaliable
xinit: server error
xauth: error in locking authority file /home/chris/.Xauthority[/I]

I'm using Gnome, graphics card is just integrated "Intel HD" - I have not installed any third party drivers

Cheers

C

---

### Post by steeldriver on 2014-07-14
you need to fix the permissions on your ~/.Xauthority, or (easier IMHO) simply remove it (a new one will be regenerated on next successful startup). Once you're logged in to the Ctrl-Alt-F1 virtual terminal, do

```

rm $HOME/.Xauthority

```

then Ctrl-Alt-F7 back to the GUI and try again.

---

### Post by chris260 on 2014-07-14
Hi all,

I seem to have resolved this by running: 
*#sudo mv /home/chris/.Xauthority /home/chris/.Xauthority* and logging in again.
Corrupt config file perhaps?

Cheers, 

C

---

### Post by chris260 on 2014-07-14
Hi steeldriver, 

Exactly what I did (except I moved it just in case).

Thanks for the reply.

C

---

