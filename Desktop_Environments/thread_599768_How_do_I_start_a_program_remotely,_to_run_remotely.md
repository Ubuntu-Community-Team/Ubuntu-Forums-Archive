---
title: "How do I start a program remotely, to run remotely?"
date: 2007-11-01
forum: Desktop Environments
---

### Post by hagfish on 2007-11-01
Hello you all

I have a Gutsy setup at home, and a Mac at work. I already have a ssh server set up on Gutsy, and can run apps from home using a system like [this]("http://ubuntuforums.org/showthread.php?t=169966").

My problem is that my wife is at home e-mailing me stuff, and I want to chat to her using Pidgin. I could ring her or e-mail her and ask her to launch Pidgin, but it would be easier for me just to log in to my home machine, and launch Pidgin so that it runs in HER session, on HER desktop. Is there a simple command that will do this? I am thinking something along the lines of (having logged into my home rig):
us@gangees:~$ pidgin DISPLAY=0:0 [something to specify the user]

Cheers

---

### Post by jfordwashere on 2007-11-01
This worked for me, First ssh into the box, and run:

export DISPLAY=:0.0
sudo pidgin


-jack

---

### Post by hagfish on 2007-11-04
Thanks, Jack. I tried that, and this is what I got:
> us@orinoco:~$ export DISPLAY=:0.0
us@orinoco:~$ sudo pidgin
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(pidgin:6116): Gdk-CRITICAL **: gdk_display_get_name: assertion `GDK_IS_DISPLAY (display)' failed
Pidgin 2.2.1

** (pidgin:6116): WARNING **: cannot open display: unset
"ps ax | grep pidgin" shows that Pidgin has not launched.. :(

---

### Post by neilengineer on 2007-11-04
How about login using:

ssh -X
or ssh -Y

---

### Post by jfordwashere on 2007-11-05
hagfish,

Hmm, two things come to mind First, whatever account your wife is using has to be logged in to the desktop. Second, when you ssh into the box, you have to use that same account.

Was that the scenario you were testing?

-jack

---

### Post by hagfish on 2007-11-05
> **jfordwashere said:**
> hagfish,

Hmm, two things come to mind First, whatever account your wife is using has to be logged in to the desktop. Second, when you ssh into the box, you have to use that same account.

Was that the scenario you were testing?

-jack

I am ssh-ing into the machine while she is logged in using a desktop, and we are both logged in using the same username:
> 
us@orinoco:~$ who
us       tty7         2007-11-06 12:49 (:0)  (this would be her)
us       pts/0        2007-11-06 13:55 (my external URL) (this would be me)


I am wanting Pidgin to pop up on HER desktop (tty7?) - I already have AdiumX running on my own machine. Thanks for following this up :)

---

### Post by jfordwashere on 2007-11-06
Well I'm stumped. The only other thing I can think to try is instead of "export DISPLAY=:0.0", try "export DISPLAY=:0" (note: both these methods work for me). I'm not really sure what the second number in the "0:0" pair is.


-jack

---

