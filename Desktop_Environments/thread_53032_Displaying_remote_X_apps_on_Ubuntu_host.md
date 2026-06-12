---
title: "Displaying remote X apps on Ubuntu host"
date: 2005-07-29
forum: Desktop Environments
---

### Post by naaman on 2005-07-29
I am trying display X apps running on my headless server (twix) on my Ubuntu host (naaman).  I have tried the standard method of achieving this:

(on Ubuntu host)
```
xhost +twix
```
(on server)
```
export DISPLAY=naaman:0.0
```
However, when I go to run an app, I get the following:

```
naamanc@twix:~$ mozilla-firefox

(firefox-bin:4717): Gtk-WARNING **: cannot open display:
```
&

```
naamanc@twix:~$ xfterm4
xterm Xt error: Can't open display: naaman:0.0
```
I am running Firestarter firewall and I have turned it off to rule it out, however, that makes no difference.  I did note that when it was on, the initial attempt at displaying firefox on 'naaman' did come up as a blocked packet.  I have subsequently added a rule to allow that port in from 'twix'.

I am unsure why this is not working.

---

### Post by amohanty on 2005-07-30
is naaman (ubuntu host) listed in the server's host file /etc/host

AM

---

### Post by kvidell on 2005-07-30
You can also try this:

```
you@naaman$ ssh -X twix
you@twix$ xlogo
```

That's all you have to do and it should automagically do all the X forwarding for you.
*xlogo* is a good app to run to test X forwarding.
- Kev

**Note**: The option X is to be uppercase! Lowercase "x" will *disable* X forwarding. Uppercase X enables it.

---

### Post by naaman on 2005-07-30
Cheers kvidell,

Another tip for beginners is to edit /etc/ssh/sshd_config on the SSH server (in my case 'twix') to allow X11Forwarding (if needed).  Then issue a HUP to the sshd process for it to re-read it's config.

```
naamanc@twix:~$ ps -ef | grep sshd
root      2323     1  0 Jul29 ?        00:00:00 /usr/sbin/sshd
...
naamanc@twix:~$ sudo kill -HUP 2323
naamanc@twix:~$ ps -ef | grep sshd
root      4966     1  0 15:33 ?        00:00:00 /usr/sbin/sshd
```
The last command was to ensure that sshd continued to run after issuing the HUP.

NOTE: Ubuntu turns on X11Forwarding by default, however, twix is running Debian Etch which turns it off by default.

---

