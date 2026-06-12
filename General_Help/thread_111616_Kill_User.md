---
title: "Kill User"
date: 2006-01-02
forum: General Help
---

### Post by j-a-p on 2006-01-02
How can I force logout of another user?

---

### Post by schilcha on 2006-01-02
Quick and dirty:

Kill his shell OR restart X

---

### Post by j-a-p on 2006-01-02
Is that as find the PID for their shell and kill that?  It seems a bit crude. Is there not something that will gracefully logout the user?

---

### Post by schilcha on 2006-01-02
[QUOTE=j-a-p]Is that as find the PID for their shell and kill that?[/QUOTE]
Yes, I usually get the PID via "ps afx", but you can also use the system-monitor to get it.
[QUOTE=j-a-p]It seems a bit crude. Is there not something that will gracefully logout the user?[/QUOTE]
I'm sure, there is! (There always is an elegant way). But since I only use this to kill my own sessions, I'm satisfied that it works...

---

### Post by j-a-p on 2006-01-02
That'll do me for now.   Maybe someone else'll give some input.

Cheers.

---

### Post by Suger on 2006-01-02
Well, you could write a script that uses wall to send a message before logging them out, even leaves them some time.

---

### Post by j-a-p on 2006-01-02
Yeah but what if the user is not present to receive the message?

---

### Post by MkDiR on 2006-05-14
If the user is not there to recieve the message then he/she should not be logged in anyway and if they have been logged in for several days i think that is just abusing their privlages.

---

### Post by j-a-p on 2006-05-15
[quote=MkDiR]If the user is not there to recieve the message then he/she should not be logged in anyway and if they have been logged in for several days i think that is just abusing their privlages.[/quote]
 
Perhaps the person had a heart atttack and was unable to logoff at that time.  Then what?  Without visiting the computer physically.

---

### Post by Quirky on 2006-05-15
[QUOTE=j-a-p]Perhaps the person had a heart atttack and was unable to logoff at that time.  Then what?  Without visiting the computer physically.[/QUOTE]

In that case, I think reading any "please log off" message is the least of their worries!

---

### Post by j-a-p on 2006-05-15
[quote=Quirky]In that case, I think reading any "please log off" message is the least of their worries![/quote] 
It's me that wants to log them off.  I'll try elsewhere as this is a waste of my time.

---

