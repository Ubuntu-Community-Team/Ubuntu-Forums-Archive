---
title: "How to pop up window on desktop from SSH session"
date: 2009-06-12
forum: General Help
---

### Post by dr_pressure on 2009-06-12
Hi folks,

Here's the deal. I want to play a little joke on one of my colleagues. Specifically this involves sshing into their desktop machine (as root if necessary), and popping up a window or something like that.

Whenever I try to open a GUI program over an SSH session, it says it cannot open the display. How do I tell it to open the display of the user who is logged on to the desktop?

Also is there an easy way to pop up a message on the screen? (If not I can write my own)


Thanks for reading, any suggestions would be appreciated!!

---

### Post by colau on 2009-06-12
> **dr_pressure said:**
> Hi folks,

Probably [here]("http://www.google.com/linux?hl=en&q=How+to+pop+up+window+on+desktop+from+SSH+session&btnG=Search")

---

### Post by sedawk on 2009-06-12
Have a look at the programs "xsnow" or "xpenguins" ;-)

First you have to know the correct DISPLAY variable.
If someone is working on the local screen most likely
it is "DISPLAY=:0.0" (or is it "DISPLAY=0.0").

You need permissions to write to his/her screen.
If you are not allowed to do that (the default nowadays)
you have to be root. If root is not allowed to write
to DISPLAY 0.0 you have to switch to the other user account
with "sudo <user>". Afterwards set the DISPLAY and try again.
(I do not recommend to mess around with "xhost" to alter
 any permissions!).

For good reasons X security is much better than a few years
back. In bad old times it was much simpler, e.g. from
any machine in the network (that runs X) you could do a
DISPLAY=<remote_machine>:0.0 and send windows to any
(unprotected) machine.

Check out your company regulations first. Impersonating
someone by hijacking his/her account (sudo <user>) can get you fired
in some companies!

---

### Post by dr_pressure on 2009-06-12
@sedawk 

Thanks a bunch buddy, that set me on the right track!!

The way to do it is:

export DISPLAY=:0.0

After trying a bunch of different combos I had the idea to open a terminal on the desktop and see what $DISPLAY was set to.

Edit: Also I will look into the possible repercussions of doing this. Thanks again mate.

---

