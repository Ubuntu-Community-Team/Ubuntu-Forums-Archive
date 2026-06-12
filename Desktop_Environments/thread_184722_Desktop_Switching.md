---
title: "Desktop Switching"
date: 2006-05-30
forum: Desktop Environments
---

### Post by rrsarge on 2006-05-30
I need to use RDP remote desktop in full screen mode, but unlike the native Windows version I can't minimize the screen.  So I'd like to leave a session running on another workspace desktop (GNOME) - is their a shortcut key for switching desktops?

Trying hard to get off the Windows crack and use Linux - but it's hard!!!

Thanks in advance!  ](*,)

---

### Post by nanotube on 2006-05-30
by default, ctrl-alt-leftarrow or ctrl-alt-rightarrow will switch you to one desktop over to the right or left. try those. though i am not sure they will work if you have a fullscreen app running, but try anyway. :)

---

### Post by rrsarge on 2006-05-30
Yeah, just tried that - no worky.  Does anyone know of a keyboard shortcut within the terminal server client?  I'm trying to assign a new shortcut in system preferences but every key combo gets forwarded to the windows system I'm connected to, with the exception of <ctrl> <alt> F1-F12...and I don't see where I can change those anywhere....

Stuck! ](*,)

---

### Post by nanotube on 2006-05-30
if you use gnome, you can change shortcuts is system>prefenences>keyboardshortcuts
if you are not running all 12 virtual consoles, maybe a ctl-alt-f12 will serve as a switch desktop shortcut?

---

### Post by rrsarge on 2006-05-30
I thought so too - but when I try to change the shortcut to <ctrl> <alt> F12 it actally switches to the console.  

Why can't there be a shortcut in the remote desktop app for this? arrgghh.

---

### Post by htimst on 2006-09-08
Have you tried CTRL-ALT-ENTER?  That switches the RDP terminal from full screen to windowed mode.

---

### Post by aa.ivanov on 2007-02-19
WOW!

That worked! 

How could I forget about ctrl-alt-enter!!??

Thanks a lot!

---

### Post by llnk on 2007-11-22
ctrl alt enter doesnt seem to work when the ubuntu screen resolution is the same as the RDP computer. Any way around this?

---

### Post by dustorm on 2007-12-05
I have the same issue, works great - cept getting out of the remote desktop on my laptop seems to require disconnecting.

CTRL-ALT-ENTER makes the whole screen flash for a brief second I see my ubuntu desktop but as soon as I let go it is back stuck within the remote desktop session.

Ideally I'd just like to minimize the remote desktop while I do other things

---

### Post by llnk on 2007-12-05
yep that's what's happening to me exactly. I've been running the RDP window at 800x600 resolution which is TORTURE! Nobody should have to run that low of a resolution!

VNC isn't an option for me. Is there any other RDP clients out there we can use to solve this problem!?

---

### Post by GJAman on 2008-01-20
> **nanotube said:**
> by default, ctrl-alt-leftarrow or ctrl-alt-rightarrow will switch you to one desktop over to the right or left. try those. though i am not sure they will work if you have a fullscreen app running, but try anyway. :)
> **rrsarge said:**
> Yeah, just tried that - no worky.  Does anyone know of a keyboard shortcut within the terminal server client?  I'm trying to assign a new shortcut in system preferences but every key combo gets forwarded to the windows system I'm connected to, with the exception of <ctrl> <alt> F1-F12...and I don't see where I can change those anywhere....

Stuck! ](*,)
Is there anyway to get ctrl-alt-leftarrow and ctrl-alt-rightarrow working while in fullscreen RDP? I like to have one RDP sesion on workspace 1 and one on workspace 2 so I can switch fast between RDP sessions

---

### Post by GJAman on 2008-01-20
> **GJAman said:**
> Is there anyway to get ctrl-alt-leftarrow and ctrl-alt-rightarrow working while in fullscreen RDP? I like to have one RDP sesion on workspace 1 and one on workspace 2 so I can switch fast between RDP sessions
Or is there a other hotkey program?

---

### Post by bucketoftruth on 2008-01-22
I solved this on my laptop by enabling ?something? which I can't find on my desktop machine.  I do CTRL-ALT-ENTER to unfocus the RDP session from full screen, then move my mouse to the upper right corner.  It then displays all windows in an expose style (snapshot of all windows zoomed out).  Then I can switch to other apps.

Unfortunately, I can't figure out how to configure this on my desktop.  I got to the commands through an old addon called "GL Desktop".  Unfortunately, GL Desktop doesn't work in 7.10.  It was a hold-over from 7.4 before I upgraded.  I still have the functionality but I can't change anything.

---

### Post by bucketoftruth on 2008-01-22
Ahha! I figured it out via [this thread]("http://ubuntuforums.org/showthread.php?t=590130&highlight=expose+desktop").  It's in the CompizConfig Settings Manager under Window Management/Scale.  Under Actions I set the "Initiate Window Picker" screen edge to TopRight.

Now, after I CTRL-ALT-ENTER I can hit the upper right corner to expose other open windows or the desktop.

---

