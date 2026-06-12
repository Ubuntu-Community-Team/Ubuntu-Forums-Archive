---
title: "terminal death"
date: 2009-04-17
forum: General Help
---

### Post by rexless on 2009-04-17
That sounds redundant.... anyway here's the queston.

I've noticed this since I first tried Ubuntu 7 and it's the same in 8.10
I use SSH regularly and often just open the terminal window for command-line access.  I ssh directly to whatever machine I'm working on using: ssh [email]username@domainname.com[/email]

What I'm finding happens regularly is that the ssh session locks / freezes / dies.  This will happen at any time and is quite debilitating.  Does anyone know why this would be happening?

---

### Post by toupeiro on 2009-04-17
> **rexless said:**
> That sounds redundant.... anyway here's the queston.

I've noticed this since I first tried Ubuntu 7 and it's the same in 8.10
I use SSH regularly and often just open the terminal window for command-line access.  I ssh directly to whatever machine I'm working on using: ssh [email]username@domainname.com[/email]

What I'm finding happens regularly is that the ssh session locks / freezes / dies.  This will happen at any time and is quite debilitating.  Does anyone know why this would be happening?

Just to clarify, unless you have DNS or an accurate /etc/hosts file, you are likely not going to get name resolution with SSH, and this will cause you grief.  If you have an entry in /etc/hosts, but are on DHCP, its likely your destination machines IP has changed.  This will cause you grief.  Some new <enter favorite brand here> broadband routers have the capability of holding DNS records for the machines they are servicing.  Check your routers config for this, or use static addresses rather than DHCP, and this may help your connection issues.  If you don't know how to do this, indicate that here, and we can troubleshoot it further.

-T.

---

### Post by rexless on 2009-04-17
Hi toupeiro,

Thanks for the reply.  I guess I didn't explain very well.
I have no problem connecting to the machines I work on, they are remote and on dedicated IP addresses so that's all fine.

The problem is on my Laptop, the actual terminal (command prompt) "window" that I'm using to do the outgoing SSH connection in freezes.  For example, I could SSH into one of my remote servers and type "ls -al" and part way through the directory listing my terminal locks.  I don't get the full feedback from the remote server and I can't do anything in the window.  I have to close the window and start again.

It's intermittent so I do get some things done, but every once in awhile it locks up and is quite frustrating.  I don't experience this on my CentOS boxes or in Putty... just in the terminal window using command-line to connect to my remote servers.

thx

---

### Post by toupeiro on 2009-04-18
For some troubleshooting techniques, try the following:

1) In a separate window, keep a constant ping going to the machine you are connecting to.  See if you drop pings when the freeze up happens.  SSH will lock up for a specific amount of time, specified in an ssh_config file, when a network connection is lost.

2) Which terminal are you using?  The default gnome-terminal? Konsole, or are you kicking back your own xterm?  make sure your $TERM variable is xterm in whatever you are using.  Certain terminal emulations can cause problems with scrolling text.  If you are using one of the default gnome terminals, you should be fine.  To eliminate this as a possibility, try going to a different TTY level (ctrl-alt-F4) and running ssh there.  If it does not lock up there, it could be terminal related.  to get back to your GUI, press ctrl-alt-F7

3)  Putty, i believe, uses its own ssh client, but it does use the config in /etc/ssh.  Try running: 

> sudo dpkg-reconfigure openssh-client
 and/or 
> sudo dpkg-reconfigure openssh-server 
to essentially try to repair your installed openssh client and server.  this should rewrite a default ssh_config and sshd_config.

Make sure you have restarted the ssh daemons on your remote machines as well.

---

### Post by rexless on 2009-04-20
I was using the gnome default terminal.  After reading your reply I setup a quick launch icon for xterm and so far that has been reliable!

Your suggestions are top notch... If the xterm doesn't work out I'll try the ping test and reconfigure... thanks!

---

