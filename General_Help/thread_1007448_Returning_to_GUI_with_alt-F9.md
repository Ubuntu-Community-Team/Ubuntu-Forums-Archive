---
title: "Returning to GUI with alt-F9"
date: 2008-12-10
forum: General Help
---

### Post by Thrasyllus on 2008-12-10
Don't know if this has been posted on before. Don't know if it's a bug or an "undocumented feature." But when I go to a virtual TTY terminal with ctrl-alt-Fn (n=1 to 6) and then try to return to the X window with alt-F7 - which has always been the standard procedure - I get a blank, black screen. The first time it happened I rebooted to get back to the GUI. Then a friend told me to use alt-F9 instead the next time this occurred - and lo! alt-F9 does the trick. It's as if the function keys got swapped.
 
Alt-F7 worked all the time for me until a couple of days ago, but my friend says he encountered the same problem a while ago with Feisty Fawn. I'm still on Gutsy.

---

### Post by Titan8990 on 2008-12-10
Also, restarting gdm should take you to it:


sudo /etc/init.d/gdm restart

---

### Post by Thrasyllus on 2008-12-10
> **Titan8990 said:**
> Also, restarting gdm should take you to it:

sudo /etc/init.d/gdm restart
Ah, that's good to know, thanks! But since a restart is not really required - alt-F9 takes me back to my GUI session exactly as I left it - I guess what I'm really asking is: has the team deliberately moved the old alt-F7 keyboard operation to alt-F9, or is this a bug introduced by a recent update?
 
Is there an "I'm not sure if this is a bug" forum?

---

### Post by Thrasyllus on 2008-12-11
> **Thrasyllus said:**
> I guess what I'm really asking is: has the team deliberately moved the old alt-F7 keyboard operation to alt-F9, or is this a bug introduced by a recent update?
 
Is there an "I'm not sure if this is a bug" forum?
Well, to answer my own question, no - alt-F7 works as long as it works... Today I always get back from a TTY screen to the GUI with alt-F7. It seems that alt-F9 works only when alt-F7 doesn't.
 
So what is going on here?

---

