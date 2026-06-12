---
title: "problem with start up"
date: 2009-01-27
forum: General Help
---

### Post by Ht228 on 2009-01-27
whenever I log into my ubuntu 8.04 partition it just seems to crash.

the desktop loads up (sort of) but I can't seem to open any of my programs. I'm not really sure how to describe it, it just seems to only load up part of the way and then do nothing more.

Its not a hardware problem because the windows partition works fine, but ubuntu seems to just reach a point in loading up and decides that its not having any more.

anyone have any similar problems or know any solutions? I'd rather avoid reinstalling, but that seems to be the only solution left.

---

### Post by dcstar on 2009-01-27
> **Ht228 said:**
> whenever I log into my ubuntu 8.04 partition it just seems to crash.

the desktop loads up (sort of) but I can't seem to open any of my programs. I'm not really sure how to describe it, it just seems to only load up part of the way and then do nothing more.

Its not a hardware problem because the windows partition works fine, but ubuntu seems to just reach a point in loading up and decides that its not having any more.

anyone have any similar problems or know any solutions? I'd rather avoid reinstalling, but that seems to be the only solution left.

You have to be far more specific with the problem if you want any useful assistance.

---

### Post by Ht228 on 2009-01-28
Hey dcstar, I figured I might have that problem

The thing is I don't really know how to describe what's going wrong... 

I'll write out what happens:

I boot up. The grub boot screen, choose ubuntu 8.04

normal boot screen, everything normal, log in screen

log in fine, everything's normal, even the little tribal drums thing

now starts the problems. 

my desktop will be there - the wallpaper, the icons, the taskbars - all normal. the problem is that i can't seem to click on any of them. or if i open a folder that i've got on the desktop then it'll open but as soon as i do anything else, it'll freeze.

I wish I could diagnose the problem better, but in my limited knowledge (which is probably wrong), it looks like ubuntu it only loading part of the way then stopping all activity.

hope this is enough to get someone to help, but I realize that its probably a write off

---

### Post by GepettoBR on 2009-01-28
> **Ht228 said:**
> Hey dcstar, I figured I might have that problem

The thing is I don't really know how to describe what's going wrong... 

I'll write out what happens:

I boot up. The grub boot screen, choose ubuntu 8.04

normal boot screen, everything normal, log in screen

log in fine, everything's normal, even the little tribal drums thing

now starts the problems. 

my desktop will be there - the wallpaper, the icons, the taskbars - all normal. the problem is that i can't seem to click on any of them. or if i open a folder that i've got on the desktop then it'll open but as soon as i do anything else, it'll freeze.

I wish I could diagnose the problem better, but in my limited knowledge (which is probably wrong), it looks like ubuntu it only loading part of the way then stopping all activity.

hope this is enough to get someone to help, but I realize that its probably a write off

It seems to me that the problem might be with Nautilus. Try reinstalling it via the command-line

When the login screen appears, pres Ctrl+Alt+F1 to go to a command-line only login (you can return to the GUI with Ctrl=Alt+F7). 

Login.

Type ```
sudo apt-get install --reinstall nautilus
```
Type your password.

When it's done, go back to your regular environment with Ctrl+Alt+F7 and try logging in.


I hope this fixes your problem.

---

