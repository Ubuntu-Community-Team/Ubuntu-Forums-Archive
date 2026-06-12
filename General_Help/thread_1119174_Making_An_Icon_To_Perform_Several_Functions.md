---
title: "Making An Icon To Perform Several Functions"
date: 2009-04-07
forum: General Help
---

### Post by s1mp13m4n on 2009-04-07
Hello everyone.  I have been using Linux now for a couple of months and have learned a bit and really enjoy using it.  I have something that I would like to try and do but do not know how to carry it out.  What I would like to do is either type a command in the terminal or click an icon on the desktop that will lock the screen and also turn off the monitor all in one command or click.  If it is possible I would also like to do the same in reverse with having the monitor come on with a keyboard stroke or command and then I could continue to type my password to unlock the screen.  Is something like this doable?  I am new to Linux and do not have any programing or shell script experience yet.  Thank you for the help and guidance.

---

### Post by aeiah on 2009-04-07
well you could write a script that did the first part, but its a lot harder to get it to wait for you to press a button again to unlock.

you'd be better off just locking the screen the normal way. i dunno if your monitor turns off with locking or not

---

### Post by s1mp13m4n on 2009-04-07
Thank you for the help.  I have an Acer V223W LCD monitor and a Chembook laptop with an NVIDIA 8600GT 512MB video card if that helps any.  Yeah I could just click on lock screen from the system menu and that is fine, I was just thinking of a way to be a bit geeky thats all.  I have not figured out how to make the monitor turn off rather than just display a blank screen when it goes into screen saver mode.  If you do not use the computer for lets say 30min then I want the monitor to turn off rather than stay active and display a blank screen.

---

### Post by sdennie on 2009-04-07
Not exactly what you are describing but certainly much easier.  If you hit Ctrl-Alt-L, your screen will lock.  If you first go to System->Preferences->Power Management, you can set the monitor to turn off 1 minute after the screen saver has come on.

---

### Post by flibit on 2009-04-07
ya, i agree with the last post, it would be easiest to write a shell script to do this.  Sure it would be cool but is it really worth it?  i think it would be easier to just lock the screen the normal way.  but hey, have fun :)

---

### Post by s1mp13m4n on 2009-04-07
ok thank you, all is done.  I will do that.  Thanks for the help.

---

