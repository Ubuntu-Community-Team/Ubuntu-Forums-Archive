---
title: "&quot;sudo shutdown now&quot; does not fully shut off computer"
date: 2009-01-21
forum: General Help
---

### Post by Agent ME on 2009-01-21
My computer can shut down fine if I click through any menus to do so. But if I shutdown using the shutdown command in a terminal (sudo shutdown now), the computer will begin to turn off as usual, log me out, and start the shutdown progress bar.

Except that the progress bar goes the wrong way (it starts filling with yellow towards the right, like it does when you turn on the computer, instead of "draining" from the right like it should on shutdown), and then it stops in the last half-inch, and stays there forever.

Pressing anything on the keyboard doesn't do anything - trying to switch terminal windows (ctrl+alt+f#) causes the screen to screw up and zoom in on part of the word 'ubuntu' in the shutdown screen. I have to hold the power button of my laptop and force it to shutdown that way to get anything to happen.

I'd like to be able to fix this, because I've written shell scripts in the past to do some long-running task and then shutdown, and I come back to the computer the next day to see it frozen in the last part of the shutdown process.

---

### Post by coiax on 2009-01-21
Possibly if you included the -P switch in shutdown, asking for a power-down rather than a halt? I generally do that as a matter of course.

---

### Post by Agent ME on 2009-01-22
Oh, that sounds like that's the problem.


What's the point in bringing a system down but not powering it off (like it seems 'shutdown' does by default)?

---

### Post by Prospero2006 on 2009-01-22
sudo poweroff will also work.

---

