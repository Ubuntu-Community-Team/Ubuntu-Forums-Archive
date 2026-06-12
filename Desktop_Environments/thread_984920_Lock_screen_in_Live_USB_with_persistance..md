---
title: "Lock screen in Live USB with persistance."
date: 2008-11-17
forum: Desktop Environments
---

### Post by decrypt on 2008-11-17
Hi,
I created a new user in Ubuntu 8.10 live usb with password and disabled the ubuntu account. Using the new account, when I try to lock screen, the scree blacks out and reappear again when i move the mouse. There are no password prompt to unlock the screen.

---

### Post by ajgreeny on 2008-11-17
I'm not sure I follow what you have done, or are trying to do, but you do realise, I presume, that all changes you make while running the live CD are lost when you reboot.

I have never used the live CD in this way, but just to try out my hardware, but is there a reason for you using the live CD and not a properly installed system?

EDIT: Ignore this, I've just noticed you're using a usb install, not a live CD

---

### Post by C.S.Cameron on 2008-11-17
Lock screen is the same for me as you mentioned.
Log out requires a password to get back in if you uncheck auto login under login window.

---

### Post by firecat53 on 2008-12-10
Anyone solve this yet? I'd like to be able to lock the screen when I walk away from the computer, but that function seems to be disabled. I can set a password for user 'ubuntu' and create a new user with a password, but the screen will not lock using either the keyboard - ctrl-alt-L or the Lock screen option under system.

Thanks!
Scott

---

### Post by slainemc on 2009-03-06
> **firecat53 said:**
> Anyone solve this yet? I'd like to be able to lock the screen when I walk away from the computer, but that function seems to be disabled. I can set a password for user 'ubuntu' and create a new user with a password, but the screen will not lock using either the keyboard - ctrl-alt-L or the Lock screen option under system.

Thanks!
Scott
Hi I have the same problem, did you solve that? Thanx

---

### Post by nikhilsinha on 2009-04-13
Having the same problem.
Created a Live Persistent USB using Linux Mint 6 but this problem is there even after creating a seperate user.

---

### Post by krisrowland on 2009-04-14
> **firecat53 said:**
> Anyone solve this yet? I'd like to be able to lock the screen when I walk away from the computer, but that function seems to be disabled. I can set a password for user 'ubuntu' and create a new user with a password, but the screen will not lock using either the keyboard - ctrl-alt-L or the Lock screen option under system.

Thanks!
Scott

I've got a quick solution to this problem. It won't fix the fact that the native Ubuntu screen locker doesn't ask for a password, but it will allow you to securely lock your screen. I've written about it on my bLog [HERE]("http://krisrowland.wordpress.com/2009/04/06/screen-lock-with-xlock-on-persistent-live-usb-ubuntu-810-intrepid/"). Basically I installed a third-party screenlocker: *xlock*. It's a nice compromise.

Ideally this shouldn't be an issue, but it seems the devs removed the password-protection functionality (since about Edgy or so) as many users seemed to be able to lock themselves out of their own sessions (not knowing the default su password - strange but true).

I came across this non-locking issue after installing a persistent live USB install of Ubuntu 8.10 Intrepid (as I think most of you here have probably done). Hope this idea helps. If you're interested, check out my other posts on my resizable persistent live usb install [HERE]("http://krisrowland.wordpress.com/2009/04/02/persistent-resizable-live-ubuntu-810-install-on-a-usb-drive/"). I've got it working as good as any permanent install, now.

Cheers,
Kris

---

### Post by txspaderz on 2010-10-27
After spending the better part of half an hour researching this problem, I stumble upon this thread.

Thanks for the pointer Kris!

---

### Post by linuxninja39 on 2012-09-13
I'm not running 12.04, I'm stunned that this problem has not been resolved yet!

---

