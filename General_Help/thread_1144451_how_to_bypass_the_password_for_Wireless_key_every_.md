---
title: "how to bypass the password for Wireless key every time at boot up"
date: 2009-04-30
forum: General Help
---

### Post by liketofindoutwhy on 2009-04-30
Ubuntu 9.04 will always ask for the password so as to access the Wireless key (WEP) so as to establish connection.

Can it be made so that it won't ask every time at boot up time?  thanks.

---

### Post by spiderbatdad on 2009-04-30
you should be able to do this graphically under Accessories >> Passwords & Encryption Keys. Under the password tab. Right click and select properties...reset the the password to match your login password.

---

### Post by liketofindoutwhy on 2009-04-30
> **spiderbatdad said:**
> you should be able to do this graphically under Accessories >> Passwords & Encryption Keys. Under the password tab. Right click and select properties...reset the the password to match your login password.

thanks, seems like if i change the password there, i am changing the password for the wireless access... the "keyring" password will still need to be obtained by asking me in a dialog window every time ubuntu boots up...   and since i used the login password for the wireless access, the wireless won't work.

---

### Post by spiderbatdad on 2009-05-03
Sorry that didnt work out. Unlocking the keyring at login and using gdm seems to be a difficult combination. It isnt as smooth as one would hope.
I think this works for me because I used encryptfs previously to encrypt my /home, and in the process, modified /etc/pam.d/common-auth.

Now, I think jaunty offers to encrypt home for you at the time in installation, at least mine did. Anyway even on a new laptop, I am not asked to unlock the keyring at login and wireless keys for several networks are stored and automatically connected when I use those networks. I hope you get this figured out...and here's to bumping your post up.

---

### Post by Bigneil on 2009-05-03
when i log in i have to unlock the keyring for internet access too.   but, this only started when i set ubuntu to bypass the normal log-in screen. looks like one or the other LOL.

---

### Post by spiderbatdad on 2009-05-03
> **Bigneil said:**
> when i log in i have to unlock the keyring for internet access too.   but, this only started when i set ubuntu to bypass the normal log-in screen. looks like one or the other LOL.

definitely the case. I assumed the user was trying to have gdm login unlock the keyring when the user logs in. Maybe I was wrong?

---

