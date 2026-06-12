---
title: "Shift, Alt Keys Quit Working"
date: 2005-11-28
forum: Desktop Environments
---

### Post by schnarff on 2005-11-28
I've got a very weird problem with VMWare and X that I'm pretty sure isn't Ubuntu-specific (I had the same problem on RH 8 ); I'm asking about it here because this is one of the more friendly, helpful forums for desktop Linux I know of. :-)

Basically, when I'm running vmware-console, I occasionally get a message about failing to acquire a keyboard locak, asking if I want to override the lock. Irrespective of what I answer, the next thing I know my Shift and Alt keys have quit working altogether -- which is very frustrating since, for example, my password requires the use of the shift key, so I can't even sudo up to root to change system-wide settings (yes, I know I can do a lot of this from the GUI, but you get my point).

The strange thing is, I've dug all around in System -> Preferences -> Keyboard / Keyboard Shortcuts, and everything appears to be normal -- my keymap looks good, I don't see any weird settings, etc. I have no idea what's been changed, but there's no way to fix it shy of a reboot.

Has anyone ever experienced something similar, even without VMWare in the equation? Any ideas how to fix this?

Thanks,
Alex Kirk

---

### Post by moshen on 2005-11-30
I have this exact same problem and its driving me crazy!!  I have to log out of X and back in when this happens.  Have you or anyone found a solution?

---

### Post by kvdbreem on 2008-05-11
Hi guys.  I have a scenario to reproduce the problem.  It's not a solution but it does help anyone trying to solve it to narrow it down:

1.  with VMWare working and running Windows XP (haven't tried this with any other OS under vmware)
2.  Bring the mouse cursor over the vm 
3.  Hold down the left mouse button whilst holding down the CTRL+ALT keys and drag the mouse (anyone familiar with Compiz and the rotating cube will know why one would use that strange combination)

Shift, alt, and ctrl keys go caputz

---

### Post by kvdbreem on 2008-05-11
I googled the problem and found this URL:
[http://www.makesweet.com/bozo/2008/04/09/vmware-stops-shiftctrlalt-key-from-working/](http://www.makesweet.com/bozo/2008/04/09/vmware-stops-shiftctrlalt-key-from-working/)

Unfortunately, my method for reproducing the problem doesn't seem to be as repeatable as I'd thought.  The jist of the solution that the blogger on the url above suggests is that when the problem occurs you open a terminal and type 
```
setxkbmap
```

Of course, I've not had an opportunity to try the solution since I can't reproduce the problem now.

---

### Post by kvdbreem on 2008-05-11
I have managed to reproduce the malfunctioning key problem and then solve it using the command given by the blogger in my last post.

---

