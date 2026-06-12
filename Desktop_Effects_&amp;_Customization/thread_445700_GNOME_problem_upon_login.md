---
title: "GNOME problem upon login"
date: 2007-05-16
forum: Desktop Effects &amp; Customization
---

### Post by lmp3 on 2007-05-16
i am running Ubuntu 7.04 on a Thinkpad Z60. and am having the following problem.

all seems fine when i boot the machine, but immediately after i log in GNOME seems
to wait a very long time (several minutes) before showing the desktop, and i get the
following error message:

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply,
the message bus security policy blocked the reply, the reply timeout expired, or the network
connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

it is obviously a problem with GNOME, by i do not know how to proceed from here.

can you tell me how to diagnose what is wrong and how to fix it?

THANKS in advance for your help...!

---

### Post by Mrkluky on 2007-05-16
I'v got the same prolem on a fujitsu-siemens laptop Amilo m3438g 
with 6.04 Dapper running upon a fake raid (dmraid).
(When I was running 6.10 Edgy on the same machine but with no raid setups I never experienced the problem)
For me the login time for GNOME is unpredictable since sometimes start up in few seconds but most of the time it takes several minutes. 
Since recently this retard presented every time I reboot and login
I _Never_ get this problem while logging into KDE or XFCE. 
I've read that creating another user and logging in with it could solve the issue but:
first, I created the main user and a new group for this user from command line with this
commands (It's impossible to create the user during Ubuntu installation on a fake raid):

#groupadd luca
#useradd -g luca -G adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin  -m luca

And I don't know if this is the right manner of doing that. I just wanted to make it work.
Second the graphical screen System>administration>users and groups  shows up just blank after asking for password and I have to force exit from it.
Said that my question is simple:
Which is/are the command/s to create user or user and group just as Ubuntu installer were doing that?

Please, I need your help !!!

---

### Post by granjerox on 2007-06-22
I have the same problem. Its really weird because at the beginnings my gnome boots quite good. I think it happens after installing some software, and i supouse it's related with compiz. I haven't seen any error messages.

Anyone knows why??

---

