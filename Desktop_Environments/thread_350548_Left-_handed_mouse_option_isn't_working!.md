---
title: "Left- handed mouse option isn't working!"
date: 2007-01-31
forum: Desktop Environments
---

### Post by Minyaliel on 2007-01-31
This goes into here, right? In no Ubuntu flavour have I been able to make my laptop's touchpad actually switch from the standard right- hand set up when choosing the option for left- handed in the System Settings. It's very annoying, I'd really appreciate some help on this case. I haven't had the same problem with other distros.

---

### Post by frafu on 2007-02-01
Hello, 

As far as I have been told, it is a bug that is gnome-related. 

In fact, the software called onboard uses the left-handed mouse functionality, to switch between left click and right click; and that switch also does not work. Here is the corresponding thread: 
[http://ubuntuforums.org/showthread.php?t=280303&highlight=right+button](http://ubuntuforums.org/showthread.php?t=280303&highlight=right+button)

To be more precise, when using remotely, it does never work, however I have been told that it sometimes work when used on the local computer. 

You might try toggling the appropriate configuration option as described in the thread cited above. I don't think that it will help, but it could be worth a try. 

>  
I haven't had the same problem with other distros.
 

This might interest the developer of onboard. Could you please tell us, whether the other distros were also using gnome and what version of gnome? 

Thanks in advance and have a nice day. 

Francesco

---

### Post by Minyaliel on 2007-02-01
I'm using Kubuntu, actually. I've not experienced a problem with this in Gnome, it's KDE (using Gnome is not an option). I'm quite certain it worked in Mepis, it did work in DesktopBSD and MyahOS awell. That's those I can remember off the top of my head, there were more.

---

### Post by frafu on 2007-02-01
Hello, 

I have moved your thread to the Desktop Environment Forum, where it might have a better chance to get a reply; the Accessibility Forum being being intended for Assistive Technology issues. 

Have a nice day. 

Francesco

---

### Post by tweedledee on 2007-02-03
> **Minyaliel said:**
> In no Ubuntu flavour have I been able to make my laptop's touchpad actually switch from the standard right- hand set up when choosing the option for left- handed in the System Settings. It's very annoying, I'd really appreciate some help on this case. I haven't had the same problem with other distros.

I don't know why you're having a problem, but running
```
xmodmap -e "pointer = 3 2 1"
``` (extending the numbers higher as necessary for your mouse; an "xmodmap -pp" will display current) will swap your left & right-cilck buttons, which is really all the "left-hand" option does - at least for my mice.

---

### Post by Minyaliel on 2007-02-04
Didn't change anything, really. *sigh* At the moment, though, I'm using E17, perhaps that's the reason.

---

