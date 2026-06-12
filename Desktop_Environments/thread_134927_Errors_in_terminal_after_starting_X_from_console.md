---
title: "Errors in terminal after starting X from console"
date: 2006-02-22
forum: Desktop Environments
---

### Post by guano on 2006-02-22
Hello all,

a few days ago I decided to give up on Gnome and start using OpenBox. Really light and fast. Today I decided to go a little further and stoped using gdm. Now my machine starts in the console, and I put a "startx" in bashrc so it will start automatically when I log in.
So far so good.
The thing is that now, when I open a terminal, I get this:

```
xauth:  creating new authority file /home/guano/.serverauth.9302
X: user not authorized to run the X server, aborting.
xinit:  Server error.

```

I guess it is related with permissions, but which file to chmod?
thanks

---

### Post by jchau on 2006-02-22
When you say:
> The thing is that now, when I open a terminal, I get this:
do you mean that when you open a terminal window in X?

If you try to run startx while an instance of X is already running, you get the error:
> X: user not authorized to run the X server, aborting., so it sound to me like you already have X running.  

If the above is correct, you shouldn't change any permissions.  A simple fix is to just remove the line from your .bashrc.  It isn't so hard to type in ```
startx
```.  I mean, you already typed your user name and passwd.  

Also, if you care about security, & like features like being able to lock your screen, I suggest you run ```
exec startx
``` instead.  This will log out your user when X closes.  This way, if u lock ur X session, another user cannot simply Ctrl+Alt+F1, Ctrl+C, and get full access to your account.

---

### Post by RAOF on 2006-02-22
X needs to be run with root privs.  So, in order to actually run "startx", you'd need to "sudo startx" instead.

---

### Post by jchau on 2006-02-22
> X needs to be run with root privs. So, in order to actually run "startx", you'd need to "sudo startx" instead.

really? that's strange.  I disabled gdm a short while ago, and "startx" without the sudo works fine.  

The problem the original poster had was that since startx was in his .bashrc, every time he opens a bash shell (whether initial login, a second login, or opening xterm/gnome-terminal), he tries to startx again.  However, since he has a limited number of X displays, he can't open another instance of X.  

You'd probably get the same errors if you try to start X twice.

---

### Post by RAOF on 2006-02-22
[QUOTE=jchau]really? that's strange.  I disabled gdm a short while ago, and "startx" without the sudo works fine.  

The problem the original poster had was that since startx was in his .bashrc, every time he opens a bash shell (whether initial login, a second login, or opening xterm/gnome-terminal), he tries to startx again.  However, since he has a limited number of X displays, he can't open another instance of X.  

You'd probably get the same errors if you try to start X twice.[/QUOTE]
Whoops.  You're totally correct.  I should've read that more carefully :oops:

X does need to be run as root, but if startx works without sudo I suppose that the script must be setuid root...

---

### Post by guano on 2006-02-22
Thanks jchau. That did it, I was trying to start the terminals from within X (BTW, thanks for the tip about 'exec startx', didn't know that).
RAOF: exec startx (or just startx) works fine for me, without sudo.

Since now I am working in an environment which doesn't have the "shutdown" or "reboot" option in its menus, I dig a llittle on google and find a solution, adding a group, using visudo to allow this group to 'sudo shutdown' without password and put it in the Openbox menus.
If you'd like, take a look at:

[http://www.ubuntuforums.org/showthread.php?p=762618#post762618](http://www.ubuntuforums.org/showthread.php?p=762618#post762618)

all the best

---

### Post by jchau on 2006-02-22
:cool: You're welcome. Glad to help (since I spent a few days getting Ubuntu to work without GDM.) 

For more insight from my problems, see [My problems with blank screens after lid close]("http://www.ubuntuforums.org/showthread.php?t=134319").  :KS

---

