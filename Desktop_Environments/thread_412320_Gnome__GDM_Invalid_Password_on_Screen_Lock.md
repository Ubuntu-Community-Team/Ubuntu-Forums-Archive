---
title: "Gnome / GDM: Invalid Password on Screen Lock"
date: 2007-04-17
forum: Desktop Environments
---

### Post by dibrom on 2007-04-17
Hello,
          I keep getting "Invalid Password" when my screen is locked.  I have recently installed Ubuntu 6.10 Cleanly and when my screen is locked, it keeps rejecting my password.  I've checked Capslock, I can't find any ambiguous keyboard / input settings in xorg.conf and I have used a terminal to change my password several times, no luck.

The only thing I have done that may have caused this is restore my:
/etc/passwd
/etc/group
/etc/shadow
/etc/gshadow

files from my previous installation (I didn't want to retype all my user information nor reenter all my passwords, I took care to make sure I did nothing crazy with the User and Group ID numbers).   Perhaps there is a better way to restore these in the future.

Any help is appreciated, I would like to be able to switch user again someday...

Thank you.

---

### Post by ponx on 2007-04-18
Hi,

I had the same issue recently and had know idea what the hell was going on, since if I did 'switch user' then log back in as myself, it brought me back to the screensaver lock screen - but then it worked...!?  Weird.

Anyway, I found something odd when I was typing into the URL field in my browser - some numbers were coming up instead of letters - it seemed my numlock was on (somehow, without me knowing it - laptop keyboard, obviously).

I think my keymap had changed when I started using a remote desktop which screwed up the key mappings.

I'll stop waffling now.... check keyboard setting in prefs. (and numlock, if a lappy kb)

Hope this helps a bit...

ponx

---

### Post by fakie_flip on 2007-04-22
Hey dibrom, I am having the same problem, and I also restored my shadow file. Did you ever find a solution? I noticed ubuntu has a /etc/shadow- file. I am not sure what that is, and why it is needed. I tried setting my keyboard preferences back to the default, and doing sudo dpkg-reconfigure gnome-screensaver.  The only time I have trouble with my password is when the screensaver comes on. Also I have tried changing my password from the command line using the passwd command and from the gui users-admin, but each time I do, users-admin still shows a password that is 8 characters long hidden by asterisks when I open it again no matter what the length of the password I change it to. I don't have a laptop keyboard. I am using a desktop.

---

### Post by dibrom on 2007-05-16
Sorry for my enormous lack or presence, 
I appreciate people help.

No resolve yet, I've checked my keyboard mapping and all is okay there.

I've given up on the matter and will research it in the future when I have time, though if any Linux guru's out there see this and have an idea, it would be much appreciated.

I suspect that I did something wrong or against-the-rules when restoring my passwords which seems to have broken Xorg or GDM.  I suspect that there might be a password hash cache somewhere else or the application which does the user switching doesn't have permission to access the password file.

Gary

---

### Post by lexpenrose on 2008-04-16
Hi , 

Had the same error recently. The short story : 
- Change the password using the System -> Preferences -> About Me -> Change Password using your initial password.

The long story : 

I installed Ubuntu using a UK style keyboard. I use SHIFT+digits as my password ( ie : SHIFT 1976 would be !(&" on the UK keyboard. ) 
I then changed my keyboard, and had trouble running programs and accessing stuff, so I thought let's reset the password so it works again ( coz on a US keyboard SHIFT-1976 is !(&@ instead of !(&"

I opened a terminal and sudo passwd and changed my password to the new layout. 
I locked my screen, came back and couldn't logon.Took me some time to figure out that I needed to use the System -> Preferences -> About me -> Change Password...

Hope it helps,
Lex

---

