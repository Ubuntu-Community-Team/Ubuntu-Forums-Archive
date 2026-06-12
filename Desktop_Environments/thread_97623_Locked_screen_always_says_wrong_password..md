---
title: "Locked screen always says wrong password."
date: 2005-12-01
forum: Desktop Environments
---

### Post by Eproxus on 2005-12-01
Hi!

When locking my screen I cannot unlock it because it always says wrong password. And yes, I have checked capslock and tried different keyboard layouts. I sure I'm typing the right password. Can I fix this somehow?

Thanks in advance!

---

### Post by Iandefor on 2005-12-01
If you hit [CTRL]+[ALT]+[BACKSPACE] it forces X to restart even if the screen is locked.

---

### Post by Eproxus on 2005-12-01
Hmm, that wasn't really the answer I hoped for :-/. I know how to kill X. That doesn't really keep my session does it?

---

### Post by Iandefor on 2005-12-01
Sorry. Dunno how else to help you.

---

### Post by teaker1s on 2005-12-01
please add to the bug [here]("https://launchpad.net/malone/bugs/4737")

I believe it's a combination of gnome or more likely xkb as I had the known xkb bug then the same happened to me

---

### Post by Eproxus on 2005-12-02
I'm running KDE. But I have my own xkb layout though...

---

### Post by RichGuk on 2005-12-03
What version of KDE are you running?

I had this problem untill I reset my password using "passwd". Give it a try.

---

### Post by horsedick on 2005-12-03
I have this problem as well now, I have to start a new session. :mad:

---

### Post by mfarquhar on 2005-12-03
[QUOTE=Iandefor]If you hit [CTRL]+[ALT]+[BACKSPACE] it forces X to restart even if the screen is locked. Security flaw or Feature? You decide![/QUOTE]

when it starts back up your session is gone right? i mean no one can sneak onto your session this way can they?:???:

---

### Post by Iandefor on 2005-12-03
> when it starts back up your session is gone right? i mean no one can sneak onto your session this way can they?:???: 
Meh... good point. I take back the "Security flaw/feature?" thing then.

 BTW, I like your signature.

---

### Post by iceportal on 2007-11-06
I'm having trouble too. I wanted to play with John the Ripper (password cracker) on my system, so I did the following:

1.) Backup the /etc/shadow file to /etc/shadow.bak
2.) Use passwd to change the passwords of each account to various new passwords
3.) cp the new /etc/shadow to /home/iceportal/passwords.txt
4.) mv /etc/shadow.bak /etc/shadow (to restore the originals)

This seemed to work, but glitched a little, so I went ahead and (as root) reset my passwords back to their original values by typing "passwd ***" for each account (where *** is the account name). This worked, and I could log into my accounts again. But for some reason, now, when I lock my screen, my password won't work. I can click "switch user" instead, and enter the same username and password and I can log in fine, so the password is right, but it's not accepted by the lock-screen password dialog.

Halp?

---

### Post by Eproxus on 2007-11-07
Well, the first thing I would try is to restore all the files and passwords and then reboot and restart everything, if you haven't tried that already.

---

