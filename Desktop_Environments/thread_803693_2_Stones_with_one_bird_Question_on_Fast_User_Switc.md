---
title: "2 Stones with one bird: Question on Fast User Switching; KDM+GDM"
date: 2008-05-22
forum: Desktop Environments
---

### Post by rolandixor on 2008-05-22
I'll be to the point.
Fast user switching works great, until one of us needs to log out.
Once anyone logs out, I'm presented with a black screen, and have to restart, as the regular Key combos don't work.

Secondly, is it possible to use both KDM and GDM in any way?
what I mean is, how to I choose which one to use for logging in?

---

### Post by MaindotC on 2008-05-22
At the login screen in the lower left there should be an option to "select session".  Click that, and the window that appears should allow you choose between GDM or KDE.

---

### Post by rolandixor on 2008-05-22
hehe...
thanks but that's not what I mean.

GDM and KDM are for logging in, not the desktop itself.

---

### Post by rolandixor on 2008-06-08
bumb

---

### Post by louieb on 2008-06-08
For switching user I use Ctrl+Alt+F7 (or F8 ...)
you can use the **finger** command to to find who is logged on to what TTY

I haven't had a problem when logging off it just switches back to the last user. (I use  GDM btw)

---

### Post by Xiong Chiamiov on 2008-06-09
> **rolandixor said:**
> hehe...
thanks but that's not what I mean.

GDM and KDM are for logging in, not the desktop itself.
If you're asking about changing which display manager's login screen to use, then run one of the two commands and choose the default that you want:
```

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure kdm

```
If you want to change which one to log into, then that is what strAlan described.

---

### Post by rolandixor on 2008-06-09
Thanks!
I know about the reconfiguration thingy... I thought there was another way (because of the fact that they both say you can choose not to have them check for a default X server...

-Lou, if you don't mind my short hand,

I don't get that same result with fast user switching.
I guess I'll give it a try again...

actually upgrading GDM right now :-)

---

### Post by asrai on 2008-06-11
> **rolandixor said:**
> I'll be to the point.
Fast user switching works great, until one of us needs to log out.
Once anyone logs out, I'm presented with a black screen, and have to restart, as the regular Key combos don't work.


I'd love to help you with the first one, but I'm having the same problem here.  I'm running Hardy (gnome) with an ATI mobility radeon X600 card and the 8.4 driver installed via envy-ng.  I have effects enabled but it has happened when effects have been disabled.  The problem only occurs when my husband and I are both logged in and one of us logs out.  

I also get a black screen but am able to move the mouse (can see the cursor moving) however there is no response to ctrl-alt-backspace or to alt-f2 metacity --replace.  I can only do the alt-prt screen REISUB to reboot the computer.

---

### Post by rolandixor on 2008-06-11
Someone needs to take this seriously. I don't mind needing a password to login and all that, but the fast user switching ability is something that XP almost does flawlessly (just don't do it when flying on Microsoft's on Flight Sim; they're so dum they're own programmes don't work with their own OS!)...

If ubuntu is to make windows afraid, this needs to be solved, and fast.

---

### Post by rolandixor on 2008-06-20
asrai, sometimes this happens also when you have locked your system, but those times you can log in after moving the mouse.

I found some info somewhere about adding the option for always restarting GDM, but I can't seem to find out how to add that in GDM's config file!
Any one know how?

---

### Post by rolandixor on 2008-07-12
okay. still no solution for me. I can get GDM to always restart, but still not sure what causes this...
any ideas?

---

