---
title: "Second X server"
date: 2009-04-25
forum: General Help
---

### Post by anandamide on 2009-04-25
Hey people
OK, sorry if I'm being a bit dumb here, but I'm trying to initiate a second X session on tty8 (or wherever, to be honest...). 

I've tried:

[FONT="Courier New"]$ startx --:1[/FONT]

which gives

[FONT="Courier New"]xauth: (stdin):2:  unknown command "6de5074cf4161c118b08a5b59c0e2b1d"
xauth: (stdin):3:  unknown command "6de5074cf4161c118b08a5b59c0e2b1d"

X: user not authorized to run the X server, aborting.[/FONT]

So moved on to:

[FONT="Courier New"]$ sudo startx --:1[/FONT]

which results in

[FONT="Courier New"]xauth: (stdin):2:  unknown command "6de5074cf4161c118b08a5b59c0e2b1d"
xauth: (stdin):3:  unknown command "6de5074cf4161c118b08a5b59c0e2b1d"

X: warning; process set to priority -1 instead of requested priority 0

Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 

 ddxSigGiveUp: Closing log[/FONT]

Same goes for whichever display number I request, or if I specify

[FONT="Courier New"]startx --DISPLAY:1[/FONT]

Any ideas?

---

### Post by dsjstc on 2010-12-30
I'm sure you've already solved this, but others will stumble on your post.  

The -- terminates the client arg list, so you need a space after it.

---

