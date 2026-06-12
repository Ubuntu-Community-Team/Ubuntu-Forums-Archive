---
title: "lock screen - correct password refused"
date: 2017-05-12
forum: Desktop Environments
---

### Post by alabamatoy2 on 2017-05-12
Ubuntu 16.04.2, Unity....  Screensaver blanks, then locks screen as expected.  wiggle mouse,  get password prompt, but it wont accept correct password.  Only recourse  is a) reboot or b) switch user, log back in with same user/password.  I  have followed the suggested fixes [here]("https://askubuntu.com/questions/128785/lock-screen-password-incorrect"), but no joy, same result.
```
sudo chown root:shadow /etc/gshadow 
sudo  chown root:shadow /etc/gshadow- 
sudo chown root:shadow /etc/shadow 
sudo  chown root:shadow /etc/shadow-
```
the gshadow and shadow files were all set as  root:root before, but the fix made no difference. The checkpaswd was  correct already.

Any help or suggestions would be appreciated.

---

### Post by TheFu on 2017-05-13
Have you changed or added a new language since this problem started?

Sometimes different locales will provide characters in a different character-set. This prevents the passwords from being encrypted with the same input as the original, so the encrypted comparison fails.  

I don't know that this is the problem, just something to check out.

---

### Post by alabamatoy2 on 2017-05-13
No language changes or additions, unless it was part of a patch that I did not realize...

---

### Post by IanW on 2017-05-16
Checked your shift lock?

---

### Post by sp40140 on 2017-05-16
Just like "shift lock". Also, check the "Function lock" as well. Especially if you are on laptop.

---

### Post by alabamatoy2 on 2017-05-16
Yes, and yes.  Entering the exact same set of keystrokes on login works fine, wont work on screensaver unlock.  Verified on multiple users.

---

### Post by ajgreeny on 2017-05-16
> **alabamatoy2 said:**
> Yes, and yes.  Entering the exact same set of keystrokes on login works fine, wont work on screensaver unlock.  Verified on multiple users.
Do you mean that no user can escape from the screensaver or screenlock?
What is it that you verified on multiple users?

---

### Post by alabamatoy2 on 2017-05-16
> **ajgreeny said:**
> Do you mean that no user can escape from the screensaver or screenlock?
What is it that you verified on multiple users?

"Escape", if you mean simply enter password and return to work, correct, none can.

The same behavior - the user can log in, let the screensaver go to lock, and the correct password is not accepted to unlock.  User can "switch user", log back in, and start over....but cannot unlock from screensaver.

---

### Post by TheFu on 2017-05-16
LANG and locale environment - that's where I'd start.

---

### Post by alabamatoy2 on 2017-05-18
Getting nowhere...  Some patches related to language were not completely installed, installed those, nothing changed, same behavior.

I did find this in the syslog:
```
May 18 13:02:18 pcname org.gnome.ScreenSaver[1415]: ** (gnome-screensaver:1583): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
May 18 13:02:18 pcname org.gnome.ScreenSaver[1415]: ** (gnome-screensaver:1583): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
May 18 13:07:45 pcname org.gnome.ScreenSaver[1400]: ** (gnome-screensaver:1563): WARNING **: Couldn't register with accessibility bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
May 18 13:07:45 pcname org.gnome.ScreenSaver[1400]: ** (gnome-screensaver:1563): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
```

Is this my problem?  Searching for "accessibility bus" does not seem to be bringing up much of anything that seems relevant.

---

### Post by sp40140 on 2017-05-18
Is it a laptop? or desktop?
Have you tried to switch the keyboard?
Just throwing an idea.

---

### Post by alabamatoy2 on 2017-05-22
Its a desktop.  Tried other keyboards, all behave same way.

I need to get this fixed, I have locked my account a couple times trying to resolve it.  Apparently the password entries against the locked screensaver, even though it is not accepting the correct PW, still countd against the "3 strikes yer OUT" setting locking the admin account for an hour.

---

### Post by Vik Vasilev on 2017-07-05
I'm having the same issue - did you get it fixed?

---

### Post by alabamatoy2 on 2017-07-05
> **Vik Vasilev said:**
> I'm having the same issue - did you get it fixed?

No, have been unable to fix it.

---

