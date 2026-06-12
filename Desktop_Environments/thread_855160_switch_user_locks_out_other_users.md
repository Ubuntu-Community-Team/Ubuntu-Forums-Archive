---
title: "switch user locks out other users"
date: 2008-07-10
forum: Desktop Environments
---

### Post by Warren MacEvoy on 2008-07-10
The "switch user" feature is broken on my ubuntu system at home:  The problem is created by using the "switch user" feature in the following simple way:

1. my son logs in,

2. my wife wants to use her account, so she picks "switch user" to log into her account

3. When she's done, she logs out of her account.

Now there is a locked screen asking for my son's password.  Nobody can use the computer without knowing my son's password.

Right there on the lock panel is a "switch user" button, but it does not work.  The only choice that seems to work is to type in my son's password and choose "unlock"

Is this a "feature" and if so, why don't any of the other buttons do anything?

This does not make sense to me.

---

### Post by ph8 on 2008-07-10
It sounds like your switch user button doesn't work, but should. 

Mine works, i've just tested it.

As you may know the default desktop session is on ctrl+alt+F7 - it appears that when i use switch user it creates a new session on ctrl+alt+F9 - try pressing the switch user button, waiting a minute, then holding down ctrl+alt+F9 to see if you get to a new session.

Otherwise i recommend checking your GDM / X logs in /var/log/gdm and posting them here, or in a bug report at [www.launchpad.net](www.launchpad.net) for developers to look at

---

### Post by pyromanic123boom on 2008-08-12
not to dig up an old thread, but I just knew exactly what you need to do.

Warren MacEvoy- when the screen is stuck at that point, (when you need to type in your son's password,) the mouse doesn't work for some reason. Just use the TAB key to change boxes, and hit enter for a click.

---

### Post by Endolith on 2008-11-11
> **pyromanic123boom said:**
> 

Warren MacEvoy- when the screen is stuck at that point, (when you need to type in your son's password,) the mouse doesn't work for some reason. Just use the TAB key to change boxes, and hit enter for a click.

Doesn't work for me.  Both mouse and keyboard can press the "Switch User" button, but pressing it does nothing.  The screensaver just starts, and then moving the mouse opens the same locked screen window.

---

### Post by valmarmoritz on 2008-11-14
I cured my Nvidia problems similar to Your's following the lead of [phaed]("http://ubuntuforums.org/member.php?u=20487") who found the solution by using [Envy]("http://albertomilone.com/nvidia_scripts1.html"). Good luck!

---

### Post by jxk7581 on 2009-02-25
Resurrecting this old thread on my new PC. Just purchased a Dell Mini 12 with Hardy Heron. I've been using Intrepid on my home made desktop with no issues.

On Hardy however, I am having the similar problem that Warren described. Only I am never able to switch user. If my screen saver activates or I choose lock screen, pressing the "Switch User" button causes the screen to flash and drop right back to my current session password prompt. I can only log back in to my current session and never switch users.

Looking for a solution for this for the last week hasn't gotten me anywhere. 

One a side note, I noticed a difference in the fast-user-switch-application in Hardy & Intrepid. I like the Intrepid version as it incorporates the current session user name with the power off button. There are also other choices available in a dropdown in Intrepid that aren't in Hardy. If you have any ideas on how to get the Interpid version in Hardy, I would appreciate it.

---

### Post by cdunham on 2009-11-22
> **Endolith said:**
> Doesn't work for me.  Both mouse and keyboard can press the "Switch User" button, but pressing it does nothing.  The screensaver just starts, and then moving the mouse opens the same locked screen window.

Seeing this same thing on Karmic. No keyboard, no mouse. Happens with my wife's account and mine (whomever starts second after a reboot), but not my son's. Video is i915. Google doesn't turn up anything useful (other than this thread, and some rant that doesn't give many specifics...)

Anyone find a fix for this? It used to happen in previous versions, but was happily not in Jaunty. Looking forward to seeing this regression fixed...

---

