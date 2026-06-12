---
title: "Zsnes - Full-screen becomes window after about 10 minutes and ubuntu freezes"
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by Jean Of mArc on 2008-05-26
I am able to run zsnes just fine in ubuntu. I run it full-screen, and it runs great for about 10 minutes, when suddenly it escapes full-screen mode and becomes a window. Then it just hangs there, and I cannot continue using it, nor anything else within gnome. My only escape is Ctrl-Alt-Backspace.

I try running it in KDE, and it works, but I would prefer to be using gnome normally, so it's no fun to have to log out and then into KDE just to play a game every time.

Any ideas?
Thanks!

---

### Post by Sleaka J on 2008-05-26
Turn off compiz.

Your screensaver is kicking in after 10mins and causing a fullscreen game to go to a window and stops responding. It's a well known problem and there doesn't seem to be a way to use compiz and play games at the same time.

Compiz is another name for "Advanced Desktop Effects" located in System -> Preferences -> Appearance -> Visual Effects.

---

### Post by shinkaide on 2009-04-13
*[COLOR="Silver"]Erhm... Apologies for replying to an old thread (I searched around a bit before deciding to reply to this one instead of creating a new one)[/COLOR]*.

I'm experiencing the same problem on 8.04, and I was just really curious if this problem has been solved?

---

### Post by adzik on 2009-04-13
Have you tried using snes9x instead with the GUI?
Although I haven't personally played with snes9x in a while, there are a couple options you can try to see if it addresses your screen saver issue.

[http://www.snes9x.com/phpbb2/viewtopic.php?t=3703](http://www.snes9x.com/phpbb2/viewtopic.php?t=3703)
[this seems like it was specifically built to address some graphical issues in linux]

Or stick to the latest snes9x with one of the basic GUIs that are in the repos, such as snes9express. If you choose to give it a go, let us know what happens.

---

### Post by wingnux on 2009-04-13
> **Jean Of mArc said:**
> I am able to run zsnes just fine in ubuntu. I run it full-screen, and it runs great for about 10 minutes, when suddenly it escapes full-screen mode and becomes a window. Then it just hangs there, and I cannot continue using it, nor anything else within gnome. My only escape is Ctrl-Alt-Backspace.

I try running it in KDE, and it works, but I would prefer to be using gnome normally, so it's no fun to have to log out and then into KDE just to play a game every time.

Any ideas?
Thanks!

Try disabling your screensaver ;)

---

### Post by shinkaide on 2009-04-13
> **wingnux said:**
> Try disabling your screensaver ;)
I have done that and it works quite nicely indeed.

It just seems like such an indirect, rudimentary solution to a problem that I'm really curious about; I've tried fiddling with the zsnes options within the terminal but nothing doing, really. 

I'd like to know if there was a solution that involved correcting a value or a setting within zsnes or compiz, if you will. Just sayin'. :D

---

### Post by Steve.G on 2009-11-30
Just recently ran into this issue after I installed got some controllers, and I couldn't figure out why.. but after reading this it makes sense.. and I wasn't seeing it when I used the keyboard to control.

Thanks for this

---

