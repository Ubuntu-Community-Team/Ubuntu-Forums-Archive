---
title: "Lost desktop display but not taskbars"
date: 2009-03-01
forum: Desktop Environments
---

### Post by MacDuff on 2009-03-01
Running Ubuntu 8.04 and last time I started the computer I did not have the normal desktop.  Both top and bottom taskbars appeared but nothing in the center panel.  

The taskbars work normally but the background has disappeared and no icons appear on it.  I just have a blank panel.

Right clicking in the center panel does nothing.

I tried restarting and repairing the system but that did not work.
I also tried re-installing the gnome desktop and that did not fix the problem.  I still cannot see my normal desktop.
 
Can anyone give me any suggestions as to how to restore my desktop to "normal"

Thanks

---

### Post by gettinoriginal on 2009-03-02
You can try this:
Alt F2 and enter ```
gconf-editor
```, then applications, nautilus, preferences, and be sure that "show desktop" is checked.

---

### Post by orethrius on 2009-03-02
I think the operative question here is whether the OP is referring to a missing desktop picture, or a complete lack of desktop icons where there should be some.

---

### Post by MacDuff on 2009-03-03
> I think the operative question here is whether the OP is referring to a missing desktop picture, or a complete lack of desktop icons where there should be some.
The answer to the above is "all of the above"  The desktop picture, background color and all icons were missing, but both taskbars, upper and lower, were in place and intact.

I had tried the suggestion made by getinoriginal (gconf-editor) when it happened but could not find any way to force the desktop to display the missing icons & picture.  I used the machine for several days with the missing desktop and having received no answers from forum members to my question, at that point, decided yesterday to do a system re-install.  When I started the computer with the missing desktop this morning, to my surprize the desktop was fully restored to its original appearance.

This happened several months ago but when I re-started the computer, the missing desktop re-appeared.  Obviously there is something wrong somewhere.  If anyone has any other ideas about what may be happening and how to check and/or fix the problem, it would be much appreciated.

Thanx

---

### Post by ambdeep on 2009-03-03
I suffer form a smiler problem......but it gets fixed automatically when i log out and log in again. It has happened several times..if there is a permanent solution please post.
Thanks in advance!!!!!

---

### Post by orethrius on 2009-03-03
It almost sounds like the drive with the icons isn't being mounted properly.  Can you post the results of a couple commands?

```
xterm -e 'sudo fdisk -l > ~/fdisk.log'
```

```
xterm -e 'cat /etc/fstab > ~/fstab.log'
```

The respective files should be fdisk.log and fstab.log in your home directory.

---

### Post by celticbhoy on 2009-03-03
Are you running compiz from svn, or any wallpaper changers or similar ??

---

