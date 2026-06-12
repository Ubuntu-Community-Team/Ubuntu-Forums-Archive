---
title: "Suspend Not Working? New Ubuntu User"
date: 2014-02-21
forum: Desktop Environments
---

### Post by No Name/NoName on 2014-02-21
I just installed Ubuntu 13.10 yesterday on my laptop to test switching over from Windows. Forgive the newb question (if it is one). 

My understanding of suspend is its similar to sleep on windows. When I use suspend my laptop powers down as it did with Windows 7. When I start it up again with the keyboard it an identical process to restart. I log in with password for encrpyted hard drive wait for 30 seconds to process, then log in for the user account. After logging all programs have been closed with a similar startup time as restart. I assuming this isn't how suspend should work.

This is a major pain, because suspend unmounts my truecrypt folder, plus closes all programs
_________

On windows whatever was running or files opened stayed in session memory after waking up.

My question is this a suspend bug and its not working the way it should? If so how do I fix this?

or 

Is there a way to make suspend work like sleep on Windows if its not a bug? (where don't have to reopen programs and remount truecrypt folder).

---

### Post by egeezer on 2014-02-23
I suspect the encryption is requiring a re-login with password.  You might try:
```
sudo pm-suspend
```
Whether that direct command will bypass whatever is requiring the login, I don't know - but at least it is a direct way to Suspend.

---

### Post by No Name/NoName on 2014-02-24
The password to relog in is good (I want that). The problem is its closing all my programs when I wake up my laptop its acting as a full restart instead of suspension. My theory is the wake up process is causing a restart somehow.

---

