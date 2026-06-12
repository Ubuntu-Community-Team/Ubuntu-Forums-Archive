---
title: "KDE restart options for GRUB not working"
date: 2007-05-15
forum: Desktop Environments
---

### Post by Takis on 2007-05-15
Howdy all,

I've told KDE to use GRUB as my boot loader and for the past couple of distros I've been able to open the Logout menu, hold down Restart and then select which OS I'd like to boot into. Muy useful. Since upgrading to Feisty and having the old Logout menu replaced with the one with giant buttons, I can still see the OS selection menu but if I choose anything, KDE just sits there. The mouse is responsive but the screen is greyed out and I can't do anything via the GUI. I can cut across to a different virtual terminal, log in and reboot manually, but it doesn't boot into the OS I selected. Any ideas?

---

### Post by DrCox on 2007-05-17
Hey there!

I'm having a very similar, if not exactly the same, problem. When choosing an item from the restart drop down menu, the screen goes gray and nothing happens.
However, by hitting ESC, I can return to KDE and keep on working normally. But the whole Log Out thing in the KMenu doesn't work anymore after that. I then have to shutdown via console commands.

I'm running a freshly installed Kubuntu 7.04 on a Samsung X20 laptop...

---

### Post by Takis on 2007-05-18
> **DrCox said:**
> I'm having a very similar, if not exactly the same, problem.
Actually, I just tested out what you describe and we have the same problem. I never would have thunk of that ESC key...

---

### Post by DrCox on 2007-05-19
Well, in a German-speaking forum ([http://forum.ubuntuusers.de/topic/92779/?highlight=]("http://forum.ubuntuusers.de/topic/92779/?highlight=")) I found another guy having this issue.

So I'd say this might well be a general bug. More people out there having experienced that kind of trouble? Is anyone aware of a bug report concerning this? At first glance I've found none, but I haven't had the time to look more carefully yet.

---

### Post by mattydee on 2007-11-15
I came across this post from a google search. I am using Slackware and am having a similar problem. Holding down restart and selecting an OS just brings me back to the main KDE login screen. 

If this is happening with across different platforms, maybe its a KDE/Grub configuration issue...

---

### Post by mattydee on 2007-11-15
This appears to be a bug in KDE:

[http://bugs.kde.org/show_bug.cgi?id=63800](http://bugs.kde.org/show_bug.cgi?id=63800)

---

### Post by Whiffle on 2007-11-15
Hmm i didn't know you could do that, so I tried it on my slackware laptop...it works. Hmm.

My only idea is to make sure you have grub or lilo checked in kcontrol>system administration > Login manager, under the Shutdown tab.  And make sure you're using KDM.  No ideas other than that.

---

### Post by mattydee on 2007-11-16
> **Whiffle said:**
> Hmm i didn't know you could do that, so I tried it on my slackware laptop...it works. Hmm.

My only idea is to make sure you have grub or lilo checked in kcontrol>system administration > Login manager, under the Shutdown tab.  And make sure you're using KDM.  No ideas other than that.

Are you using grub or lilo?

---

### Post by toon on 2008-01-22
Any idea if this will be fixed in 3.5.9? It would be a _great_ thing to have working since I reboot to wintendo to play games now and then and waiting for grub to come up (or not seeing it in time..) is very annoying.

---

### Post by gizmobay on 2008-07-18
I'm having this problem as well. If I do a grub-reboot x, it'll reboot into the desired OS. When I do a grub-reboot, it prompts me for yes or no to reboot. I suspect this is where the problem is occurring. I would guess the restart pulldown is issuing a grub-reboot command but it's waiting for the yes or no and since you're in GUI mode you can't enter yes or no thus it hangs. I notice there's some options you can add to grub-reboot but they're not in the man page.

---

