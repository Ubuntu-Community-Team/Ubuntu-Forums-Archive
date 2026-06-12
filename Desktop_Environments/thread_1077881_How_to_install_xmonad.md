---
title: "How to install xmonad?"
date: 2009-02-22
forum: Desktop Environments
---

### Post by Seine on 2009-02-22
Hello. I've been keen to try out xmonad, but I can't get it to work.

Naively I've tried aptitude install xmonad ... then logging in again with the xmonad session. I'm greeted with a background coloured wall of nothing.

I've also tried running xmonad from within gnome. That made my gnome flavoured windows jump around and disabled my keyboard and mouseclicks. (though mouse movement and CTRL_ALT_BACKSPACE still worked).

Can anyone help me please?
Thanks!

---

### Post by snova on 2009-02-22
> **Seine said:**
> Naively I've tried aptitude install xmonad ... then logging in again with the xmonad session. I'm greeted with a background coloured wall of nothing.

Because that's all it is. It's a tiling window manager. It's not a desktop environment, there's no desktop at all in fact.

[http://xmonad.org/](http://xmonad.org/)

---

### Post by nebajoth on 2009-03-27
No, I'm having the same problem.  I believe the problem is probably that the key bindings file hasn't been compiled into the binary yet... so the display is working, but its not responding to keyboard shortcuts.  Which is kind of a problem.

---

### Post by LordRifter on 2009-07-01
I'm having the same problem, starting xmonad from within Gnome works great, but if I log into a Xmonad session it completely ignores the keyboard. 

'Mod - Shift - Return' does nothing.

---

### Post by tacitdynamite on 2009-07-03
Same problem here.

---

### Post by tacitdynamite on 2009-07-03
I believe I have the same issue as others here. I actually switched from windows xp + cygwin w/ ratpoison to linux so I could have some better tiling wms and better support of cli, but so far my efforts to install either xmonad or awesomewm in jaunty have resulted in nothing. 

I've tried installing xmonad in synaptic and then restarting, logging in with xmonad, and alt-shift-enter, alt-shift-p, windows-shift-enter, windows-shift-p, ctrl-alt-backspace, all these do absolutely zilch.  

I've also tried terminal commands
killall metacity; xmonad &
with gnome up and running, and the result is a confusing mess of xmonad managed tiles on top of a bunch of gnome windows that I can't see, and the error message " xmonad: X11 error: BadAccess (attempt to access private resource denied), request code=28, error code=10
," and the mod-shift-enter key command doesn't open up a new terminal, then, either.

What's strange is that I've also installed awesome wm and when I start a new login with that, the only key command that does anything is mod4+space; mod4+enter ALSO does not open a terminal, etc.

wtf?

Are icewm, wmii, ion easier to install?

---

### Post by tacitdynamite on 2009-07-03
BTW how do you delete a post? I've edited my one post to have information from my other posts, but now I can't delete my other posts.

---

### Post by kurtis99 on 2009-07-04
> xmonad: X11 error: BadAccess (attempt to access private resource denied), request code=28, error code=10It means thatr another Window Manager is running.

To solve this problem first you should create file *~/.xsession* with following lines
```
export WINDOW_MANAGER=xmonad
exec gnome-session
```(without "--purge-delay=3000", this option didn't worked for me)

then using **gconf-editor** you should change following values
in *desktop -> gnome -> applications -> window_manager*
you should find option named _current_ and change it's value from _metacity_ to _xmonad_
then in *desktop -> gnome -> session -> required_components *find option _windowmanager_ and change it from _matacity_ or _xmonad_ to _gnome-wm_ !!! Only with this option xmonad loaded properly.

After all this actions, you should reboot and start normal GNOME session - xmonad will be intergrated in Gnome.

---

### Post by HALsaves on 2010-01-03
[http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome]("http://www.haskell.org/haskellwiki/Xmonad/Using_xmonad_in_Gnome")

...much better info than any of the advice in this thread.

---

