---
title: "Is it possible to take over an already active console?"
date: 2007-10-15
forum: Desktop Environments
---

### Post by CyberAngel on 2007-10-15
Hello,
Is it possible to take over an already active console on a machine without a graphical desktop environment?

e.g. I am on a machine and I am starting something on tty0.
I am leaving this tty opened because it is doing a job and I am leaving.
I want to take over and control this console from another pc after some time.
Is that possible?

Something similar of what x11vnc or krfb does on the desktop environments.

Thanks.

---

### Post by krunge on 2007-10-15
> **CyberAngel said:**
> Hello,
Is it possible to take over an already active console on a machine without a graphical desktop environment?

e.g. I am on a machine and I am starting something on tty0.
I am leaving this tty opened because it is doing a job and I am leaving.
I want to take over and control this console from another pc after some time.
Is that possible?
The 'linuxvnc' program that is either in the LibVNCServer or linuxvnc package can.  Run something like:
```
linuxvnc 1
```
for tty1. x11vnc is also able to do this:
```
x11vnc -rawfb console
```
but does so less reliably because it depends on the configuration of /dev/fb to work properly.

---

### Post by gaussian on 2007-10-15
> **CyberAngel said:**
> Hello,
Is it possible to take over an already active console on a machine without a graphical desktop environment?

e.g. I am on a machine and I am starting something on tty0.
I am leaving this tty opened because it is doing a job and I am leaving.
I want to take over and control this console from another pc after some time.
Is that possible?

Something similar of what x11vnc or krfb does on the desktop environments.

Thanks.

"screen" (part of standard GNU utilities) is your friend here.

---

### Post by CyberAngel on 2007-10-15
> **krunge said:**
> The 'linuxvnc' program that is either in the LibVNCServer or linuxvnc package can.  Run something like:
```
linuxvnc 1
```
for tty1. x11vnc is also able to do this:
```
x11vnc -rawfb console
```
but does so less reliably because it depends on the configuration of /dev/fb to work properly.

The first one does the job!!!! (linuxvnc 1)
Thank you very much :)

---

### Post by CyberAngel on 2007-10-15
> **gaussian said:**
> "screen" (part of standard GNU utilities) is your friend here.

Is it easy for you to give me an example of how to do the same thing using screen?
Just for knowing :)
linuxvnc that krunge mentioned does the job so easily :)

```
sudo apt-get install linuxvnc
```
run as root "linuxvnc 1" to view the tty1 console.

---

### Post by gaussian on 2007-10-15
> **CyberAngel said:**
> Is it easy for you to give me an example of how to do the same thing using screen?
Just for knowing :)
linuxvnc that krunge mentioned does the job so easily :)

```
sudo apt-get install linuxvnc
```
run as root "linuxvnc 1" to view the tty1 console.

Basically, "screen" command starts a new shell environment that works just like your basic shell environment except you can by hot-keys (ctrl-a-ctrl-d, I think) detach from that environment and leave it running on the background. After you detatch from the screen session you are free to log off from your account, go to another computer, ssh in and then given commend screen -r -d (IIRC?) to reattach to the screen session. It is really handy and a standard tool in *nix environments.


For more, see "man screen". What I have described is just the very basics.

---

