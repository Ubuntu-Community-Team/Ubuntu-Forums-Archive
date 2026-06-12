---
title: "X server issues"
date: 2005-12-07
forum: General Help
---

### Post by WebDrake on 2005-12-07
Hello all,

One of the things I do on a regular basis is submit jobs to a computing cluster on my university network.  Often these jobs have to be "interactive".  What this means in practice is that a computer in the cluster submits a request to my X server, along the lines of,

```
export DISPLAY=my.ip.address:0
xterm
```

Using Windows XP this means using Cygwin/X, which, provided I have given an xhost + cluster.main.computer command, works fine: the xterm window pops up on my desktop.

However, I haven't been able to get this to work via Ubuntu.  Two possibilities spring to mind: one is that Firestarter is blocking the request, the other is that as a user I don't have the privileges to effectively use xhost (although no error message is generated when I give the xhost + command).

Any suggestions?  In addition, I seem to remember reading somewhere that the xhost + command is a rather crude way to give another machine access to your X server, so advice on any better way would be appreciated. :-)

Many thanks,

        -- Joe

---

### Post by 23meg on 2005-12-08
See your system log or the firestarter events tab (in its GUI) to make sure it's not blocking anything, and if it is, set the appropriate inbound policy.

---

### Post by WebDrake on 2005-12-08
Thanks for the ideas.  I set the correct policy for Firestarter; however, the problem remains.  I tried using the xhost + command with sudo to make sure it was correct; no difference.

I can't find anything in the system logs that seems to relate to this, but that may be my inexperience at dealing with Linux.  Can you point me more directly to what I should try looking at?

---

### Post by 23meg on 2005-12-08
I'm not sure, maybe you need to add yourself to a certain group to have the privilege, since the xhost command is meant for a single user environment only and may not work as intended in Ubuntu.

---

### Post by WebDrake on 2005-12-08
> maybe you need to add yourself to a certain group to have the privilege

So sudo won't get round that problem?

Is there an alternative way of allowing what I want---allowing a selected remote client to submit a request to my X server---other than the xhost command?

Thanks anyway for the helpful advice, I'm sure I'll get this sorted. :-)

---

### Post by 23meg on 2005-12-08
[QUOTE=WebDrake]So sudo won't get round that problem?[/quote]It may not, since it states in the manpage for xhost that it's meant for single user environments.
> 
Is there an alternative way of allowing what I want---allowing a selected remote client to submit a request to my X server---other than the xhost command?There must be. Take a look at the manpages of x and other x related utilities. Also search the x.org wiki and linuxquestions.org for an answer.

> Thanks anyway for the helpful advice, I'm sure I'll get this sorted. :-)You're welcome, just keep looking and you'll get to it.

---

### Post by WebDrake on 2005-12-15
Further to earlier comments, I found the following page:

[http://www.xs4all.nl/~zweije/xauth.html](http://www.xs4all.nl/~zweije/xauth.html)

However, following the xauth procedures listed here to set up a cookie for authorisation doesn't work.  I suspect this may be because of one of several reasons:

(i) The computer I want to access my account is a remote machine

(ii) The username is different between the different machines (mine & remote)

Can someone further advise, given that I'm not too good yet at understanding many of the script/authorisation issues of Linux? :-)

Many thanks,

        -- Joe

---

### Post by Steah on 2007-10-26
Not that this is a timely reply, but since the question was never answered...

By default Ubuntu disables listening by specifying -nolisten when starting the x server.  You can manually modify it in the startup rc files (look at /etc/X11/xinit/xserverrc) or use the graphical interface in gnome by deselecting the checkbox at: System->Administration->Login Window->Security->Deny TCP connections to Xserver.

After that, either the Xhost or Xauth should be able to enable clients to connect.

---

