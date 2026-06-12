---
title: "Entering Keyring everytime Ubuntu starts"
date: 2009-06-16
forum: General Help
---

### Post by joelop on 2009-06-16
Hello All,

Everytime I boot Ubuntu I'm asked to enter keyring if I want my wireless card to connect me to internet; I know there must be a way to stop this, can anybody help me please?

J.

---

### Post by days_of_ruin on 2009-06-16
> **joelop said:**
> Hello All,

Everytime I boot Ubuntu I'm asked to enter keyring if I want my wireless card to connect me to internet; I know there must be a way to stop this, can anybody help me please?

J.

Are you automatically logging in? Or do you have to type in your password first?

---

### Post by joelop on 2009-06-17
> **days_of_ruin said:**
> Are you automatically logging in? Or do you have to type in your password first?

Yes, automatically, I don't have to type my password after starting Ubuntu, does it make any change?

---

### Post by VMC on 2009-06-17
Read this [BLOG]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/") before you decide what to do. If it's just your home computer and your not sharing with anyone else, it makes perfect sense/

---

### Post by mcduck on 2009-06-17
> **joelop said:**
> Yes, automatically, I don't have to type my password after starting Ubuntu, does it make any change?

N0, it doesn't make any difference in 9.04. In older Ubuntu versions you were specifically asked to create the keyring password, while 9.04 automatically sets it to same as your login password.

Anyway, the problem here is that the keyring is normally unlocked automatically at the same time when you log in with your password. But with automatic login that isn't possible, so the keyring remains unlocked and asks for password when any program tries to access it.

This can be easily solved, just set the keyring password to empty and the keyring manager won't ask for it any more.

To do this, go to Applications/Accessories/Passwords and Encryption keys, and on the Passwords-tab right-click the "passwords:login"-keyring and select "Change password". Type in your old password but leave the fields for new one empty.

(..or re-enable the password login for better security. ;))

---

### Post by joelop on 2009-06-17
> **mcduck said:**
> To do this, go to Applications/Accessories/Passwords and Encryption keys, and on the Passwords-tab right-click the "passwords:login"-keyring and select "Change password". Type in your old password but leave the fields for new one empty.

Hey! It worked!! :p Thanks a million!

> **mcduck said:**
> (..or re-enable the password login for better security. ;))

But why? Is there a real good reason to do this? As one can read in the blog VMC mentioned: 

"*_If the PC were in an office somewhere with a bunch of random co-workers always around_, I’d be more concerned.  But this thing is in my house behind a locked door.  So for me, for this particular PC, I see little if any harm in removing one minor security barrier.*"

And if later on I want to set it up for not logging in automatically, is there an easy way of doing it?

---

