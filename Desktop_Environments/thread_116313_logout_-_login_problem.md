---
title: "logout - login problem"
date: 2006-01-12
forum: Desktop Environments
---

### Post by iostream on 2006-01-12
I'm experiencing a strange problem here.

if I logout (KMenu --> LogOut --> End Current Session) and then try to login again I can't type in a login name or password. nothing happens, the cursor is there but no letters appear. But the keyboard seems to work (at least the LED's for NumLock etc. work, if I press the appropriate buttons).
I have to reboot the computer to login again.

thx in advance!

---

### Post by bulldogzerofive on 2006-01-13
**A couple short term workarounds to try:**

You could hit CTRL+ALT+Backspace to kill and restart the X server

Or you can hit CRTL+F4 to go to another terminal, log in and sudo restart X

**In the long term:**

Do you have a flashing coursor in the input box?  Maybe you just have to click on it...

It would also help us help you if you let us know if you are using kdm or gdm as you display manager.

Good Luck!

---

### Post by iostream on 2006-01-13
first of all thx for the short workarounds, i will try them immediatly.

second: yes, there is a flashing cursor and I use kdm.

---

### Post by bulldogzerofive on 2006-01-17
It could be a lot of things... the first step would be to localize the issue.  Since the X server is what controls the keyboard, mouse, and screen, i would guess that the problem resides there.  Go to the kontrol center and select gdm as your display/login manager.  Then, try to cause the lockup.  If it still happens, then we probably need to take a closer look at how well X plays with your setup.  If that stops it, then we should look at kdm, me thinks.

Are you having any issues with X that could be related?  Screen resolution or something?

A little disclaimer, i am far from an expert on this stuff.  If anybody knows better please speak up!

Good Luck!

---

### Post by zachariah on 2006-01-25
Just to let you know you're not alone iostream, I am having this exact same problem: Logout (end session) for one user, you get the Kubuntu splash screen inviting you to type in the next username and password, but the system will not accept any input from the keyboard.

Mouse is still working fine, pointer moves and selects things on screen ( so I can turn off). Ctrl-alt-backspace doesn't work, nor does ctrl-alt-del. 

I've looked all through the settings on Kcontrol and cannot find any way to change from kdm to gdm. any hints?

---

### Post by iostream on 2006-01-26
well, seems my problem is gone, after I reinstalled the whole system. (not BECAUSE of this... :) )

---

