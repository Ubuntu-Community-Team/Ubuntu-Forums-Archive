---
title: "How to disabling password screen or choose home folder encryption"
date: 2010-11-24
forum: Desktop Environments
---

### Post by castro1 on 2010-11-24
Two questions concerning the "insert your password screen" that pops up after some minutes of inactivity:  1) How can I disable it, if I don't want it to pop up anymore? (maybe on startup, but not after inactivity)  2) If it is not disabled: During the installation of Ubuntu, it is asked whether the password chosen will be used only to unlock the screen or also to unencrypt the user's home folder. Supposing the user chose the former option, how can he currently go back and choose to also have encryption? Also: is this encryption good? Is encrypting the home folder enough to protect personal data from eventual laptop theft?

---

### Post by tom4everitt on 2010-11-24
Question 1 is easy enough. Go to:

System -> Preferences -> Screensaver

and uncheck "lock screen when screensaver is active". 

Whether password is required for login is set independently in System->Administration->Users and Groups, it is called 'Automatic login', I think. 


Question 2:
Yes, it should provide protection of your data. Easiest is probably to create a new user account (System->Administration->Users and Groups again), where there should be such an option.

---

### Post by castro1 on 2010-11-25
1. Screensaver thing: solved, thanks.  2. Encryption: hmmm, there really is no other way than adding a new user and moving everything? I had this feeling that this should be a simple checkbox somewhere (or a simple terminal command).  Is this encryption bypassable in any way? As good as the top alternatives? Any references about it that I could have a look?  Thanks again.

---

### Post by tom4everitt on 2010-11-25
1. Excellent :)

2. Umm, I don't know of any checkbox; if there were one, shouldn't it be in 'Users and Groups' then? And I didn't see any. 

I don't have any references on the quality of the encryption, but I'm sure you can find something if you google. Otherwise just start a new thread about only that. 

But I think it is pretty safe: I mean, the data is encrypted right? But then of course it is always possible to break an encryption with enough computational power. But as I said, I don't have any reference on how good it is. 

Hope you'll find something! Good luck!

---

### Post by castro1 on 2010-11-28
Will do that, thank you.

---

### Post by Megaptera on 2010-11-28
For encryption you could look at TrueCrypt:

[http://www.truecrypt.org/](http://www.truecrypt.org/)

---

