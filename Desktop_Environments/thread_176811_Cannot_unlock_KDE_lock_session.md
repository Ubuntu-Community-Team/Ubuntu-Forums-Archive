---
title: "Cannot unlock KDE lock session"
date: 2006-05-15
forum: Desktop Environments
---

### Post by jhosley on 2006-05-15
I recently changed my user password and now when I do a lock session and then go to unlock it says unlock denied.  I tried using the old password and that doesn't work either, I have no problem logging-in however with the new password.
Does anyone know how I can the Lock/Unlock session synced back up with my user's password?

Thanks,
Jamie

---

### Post by kb3hkg on 2006-05-15
first off, are you positive you are typing the password correctly?

---

### Post by jhosley on 2006-05-15
Hahaha, yeah I was putting in the right password (that was first thought, maybe my fat fingers were failing me).
I was able to get this working again.  From Konsole I ran kcheckpass and put in the new password (received no authentication failure here or anything).  
Then I locked the session to try a test, entered the new password at the prompt and oila! the session unlocked.
So I'm not sure what happened here, but with some googling around I found users who also ran into this problem when changing a password under 3.5.+.

---

### Post by elamericano on 2006-05-15
I heard the same thing, but that the problem was not experienced when changing the password with the passwd command from the terminal. Whenever something similar happens to me, I try to find a non-masked field to be sure I'm typing what I think I'm typing. I love those "unmask" checkboxes that you see in some apps - that way you can say with certainty, "Yes, I typed the right password."

---

### Post by xeen on 2006-05-21
I have exactly the same problem, I cannot unlock my KDE locked session.
Kubuntu Breezy KDE 3.5.2

With kcheckpass, I get the following when I type in my user passwort (yes, it is correct):

user1@client1:~$ kcheckpass
Password:
Authentication failure

What should I do to get the unlocking of the KDE sessions work again?

---

### Post by brecht on 2006-05-23
Hi all,

I had the same problem on breezy badger.. Somewhere on the internet I found the solution: 
*[INDENT]sudo chmod 4755 /usr/bin/kcheckpass[/INDENT]*
After upgrading to dapper drake, the same problem appeared and, luckely, the aforementioned solution still works..

Ciao!
Brecht

---

### Post by Tragos on 2006-05-23
[QUOTE=brecht]I had the same problem on breezy badger.. Somewhere on the internet I found the solution: 
*[INDENT]sudo chmod 4755 /usr/bin/kcheckpass[/INDENT]*[/QUOTE]

Grazie, brecht!

Worked for me too.

---

### Post by rvfh on 2006-05-27
Guys, I don't like this.

I have Dapper on a number of machines and kcheckpass works without being suid root on all but one. There must be a good reason why this fails, and we should try and find it.

I'll use your 'solution' as a last resort if I can't find the root of the problem though, as it _does_ work for me too, so thanks for that.

---

### Post by rvfh on 2006-05-27
I did a bit of research and /var/log/auth.log says (amongst other things):
May 27 20:45:59 localhost unix_chkpwd[19463]: check pass; user unknown

After that, a bit of Google led me to bug 45368 in Malone, with the solution:
sudo chgrp shadow /etc/shadow

---

### Post by Wr8EYilK8Y on 2006-05-28
I'm keeping that one on my Linux Toys (drivers, tools, etc) CD-ROM. I had this problem too and that cleared it up right away

---

### Post by mlegare102 on 2006-06-29
Thanks for the tips above. I also couldn't unlock a session and was getting authorization failures (the password was typed correctly :).

After digging around for kcheckpass, I found that the one being used for validation was the one in my /home/<user>/kde3.5.3, which I recently rebuilt. I tried to sudo chmod it as above but that didn't fix it. I deleted it and pointed to the original version in /opt/kde3/bin and that soved it!!

Finally, I can lock my screen properly instead of hiding under another tty.

Mick

---

