---
title: "Lock screen without screensaver running"
date: 2010-05-07
forum: Desktop Environments
---

### Post by Gekitsuu on 2010-05-07
Is there an easy way to lock my computer screen without a screensaver running? What I'm trying to do is basically fire up a web browser or terminal window that I want to watch/monitor but lock my screen so that it can't be changed unless you know the password to log in as that user.

---

### Post by powerofpi on 2010-05-07
What is wrong with clicking the power icon and hitting "Lock Screen"?

---

### Post by Gekitsuu on 2010-05-07
When you do that the screen goes black, I'm trying to get the desktop environment to lock but continue to display the desktop.

---

### Post by d3v1150m471c on 2010-11-29
bump, i'd also like to know how to do this.

---

### Post by Gekitsuu on 2010-12-02
I never did find a solution and I quit looking but if someone has one I could still use it.

---

### Post by stinkeye on 2010-12-02
> **Gekitsuu said:**
> I never did find a solution and I quit looking but if someone has one I could still use it.

```
sudo apt-get install xtrlock
```


From xtrlock manpage....
```
 xtrlock locks the X server till the user enters their password at the keyboard.

       While  xtrlock  is running, the mouse and keyboard are grabbed and the mouse cursor becomes a padlock.  Output displayed by X programs, and windows put up
       by new X clients, continue to be visible, and any new output is displayed normally.

       The mouse and keyboard are returned when the user types their password, followed by Enter or Newline.  If an incorrect password is  entered  the  bell  is
       sounded.  Pressing Backspace or Delete erases one character of a password partially typed; pressing Escape or Clear clears anything that has been entered.

       If too many attempts are made in too short a time further keystrokes generate bells and are otherwise ignored until a timeout has expired.

       The  X  server  screen  saver  continues  to operate normally; if it comes into operation the display may be restored by the usual means of touching a key
       (Shift, for example) or the mouse.
```

Just create a launcher with **xtrlock** as the command and
to unlock (no dialogue window) type in password and hit enter.

---

### Post by Dave_L on 2010-12-02
Thanks for the post about *xtrlock*.  I've been locking the session to prevent my cats from messing things up, but xtrlock works better for that  purpose. :biggrin:

---

### Post by stinkeye on 2010-12-02
[[IMG]http://img811.imageshack.us/img811/1812/proncat.jpg[/IMG]](http://img811.imageshack.us/i/proncat.jpg/)

---

### Post by Gekitsuu on 2010-12-02
Thanks stinkeye that's purrrfect!

---

### Post by stinkeye on 2010-12-03
One thing I just found out is easystroke (mouse gestures) still works when
the screen is locked.
This is handy because I have a gesture setup to in put my password (yes I'm lazy)
```
xdotool key p a s s w o r d Return
```

I just need to perform the gesture and the screen is unlocked.
Might be useful if you want to run a command while the screen is locked.

---

### Post by notebookshopper on 2010-12-03
You explained the topic very well. The contents has provided meaningful information, thanks for this wonderful post.

Thanks :)

---

### Post by Gekitsuu on 2010-12-03
That's pretty cool, It would be useful then I could setup different work spaces and use mouse gestures to switch between them very nice!

---

