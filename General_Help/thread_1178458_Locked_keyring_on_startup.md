---
title: "Locked keyring on startup"
date: 2009-06-04
forum: General Help
---

### Post by yonyz on 2009-06-04
> "Enter password for default keyring to unlock
_____________________________________________

The application 'Do' (/usr/bin/mono) wants access to the default keyring, but it is locked"

This message appears when I start Ubuntu (9.04). The application 'Do' is actually 'GNOME Do'.

How can I fix this?

---

### Post by pastalavista on 2009-06-04
I hate all the bother of keyrings. I usually just click 'cancel'.. or, when I don't have that option, I click 'always allow'

---

### Post by mcduck on 2009-06-04
> **yonyz said:**
> This message appears when I start Ubuntu (9.04). The application 'Do' is actually 'GNOME Do'.

How can I fix this?

Are you using automatic login, or have you changed your login password recently?

The keyring is used to store passwords, encryption keys and other security-related stuff. As long as your keyring password is the same as your login password the keyring will be unlocked automatically when you log in. If you use automatic login this won't happen, so you might want to set the keyring password to empty one (as you clearly aren't concerned about security, not using a login password..). Or if you use login password, but have change the password at some point, you need to change the keyring password as well for the automatic keyring unlocking to work.

The keyring password can be changed (or removed) in Applications/Accessories/Passwords and Encryption Keys. ON the Passwords-tab right-click the "Passwords:login"-keyring and select "Change Password".

---

### Post by yonyz on 2009-06-06
My Ubuntu IS protected by password. I use the same password for the Keyring, but I also have auto-login turned on.

Is it really not safe not to use a Keyring password?
What are the stored passwords, anyway? Isn't that just the Ubuntu login password?

---

### Post by directhex on 2009-06-06
> **yonyz said:**
> My Ubuntu IS protected by password. I use the same password for the Keyring, but I also have auto-login turned on.

Aha. That's the problem then. You can have a password-protected keyring whose password you enter on login, or you can have a passwordless keyring. You can't combine the two. The reason for this is that even though you are logged in automatically, the system doesn't actually know your password (it simply removes the need to enter one, temporarily). However, your keyring is *encrypted* using the keyring password, and as such, cannot be bypassed (i.e. there's no backdoor way to read values from it)

> Is it really not safe not to use a Keyring password?
What are the stored passwords, anyway? Isn't that just the Ubuntu login password?

Essentially your keyring combines a lot of different passwords into one place - e.g. passwords entered for wireless networks, or passwords entered for accessing remote servers via Nautilus, or passwords for your email accounts in Evolution.

---

### Post by jeromedavies on 2009-06-06
This worked for me, not sure what other people think of it.

Delete the following file

/home/<yourname>/.gnome2/keyrings/default.keyring 

If/when you are asked for a password for your keyring file, do not enter a password and ignore the warning about creating a keyring file without a password.

---

### Post by directhex on 2009-06-06
> **jeromedavies said:**
> This worked for me, not sure what other people think of it.

Delete the following file

/home/<yourname>/.gnome2/keyrings/default.keyring 

If/when you are asked for a password for your keyring file, do not enter a password and ignore the warning about creating a keyring file without a password.

You can remove the password from an existing keyring without losing values held inside it

---

### Post by yonyz on 2009-06-07
I've removed my keyring pass, since the only password I have is the login password, which, as I understand, is not stored inside the keyring. Am I right?

---

### Post by directhex on 2009-06-07
> **yonyz said:**
> I've removed my keyring pass, since the only password I have is the login password, which, as I understand, is not stored inside the keyring. Am I right?

You can see which passwords are in your keyring by going to Applications, Accessories, Passwords and Encryption Keys, Passwords tab, and expanding the "Passwords: login" value.

---

### Post by yonyz on 2009-06-07
That's my only password stored there:
gnome-do/GCalendar/GCalPreferences/Password.

---

### Post by yonyz on 2009-06-08
When I log out, an error message appears, saying: 'Authentication Failed'. 
I click OK, but it appears again and again and again...
I've restored my keyring password, restarted, but I still can't log back in after I log out.

---

