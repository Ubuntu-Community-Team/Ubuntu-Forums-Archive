---
title: "Gnoe-Do Keyring On Startup"
date: 2009-08-02
forum: Desktop Environments
---

### Post by distortedecho on 2009-08-02
Hi,

I've searched for an answer but only find threads for Gnome-Do and Wife Connections - I've added the line of text to my conf file with no fix to the problem.

I've installed Gnome-Do and use Docky and love it! But what's annoying me is that each time I boot up, Gnome-Do wants to access Keyring. I can deny, but will be prompted 3 times. So I have to enter my keyring password each time.

How can I stop this???

---

### Post by mcduck on 2009-08-03
Two possible solutions:

1. Don't use automatic login. When you type you password in the login screen the keyring is unlocked at the same time.

2. Remove the keyring password. With no password you are not going to be asked for one. To do this go to Applications/Accessories/Passwords and Encryption Keys, on the passwords-tab right-click the "login:default"-keyring and select "Change password".

(The third possibility is that you are using a normal login, but have changed your login password at some point. In that case change the keyring password to the same as your login password an keyring will be once again unlocked automatically.)

---

### Post by distortedecho on 2009-08-05
> **mcduck said:**
> 

2. Remove the keyring password. With no password you are not going to be asked for one. To do this go to Applications/Accessories/Passwords and Encryption Keys, on the passwords-tab right-click the "login:default"-keyring and select "Change password".



Worked a treat, thanks!

---

### Post by distortedecho on 2009-08-06
OK, now when I boot up, Docky looks like I've "summoned Do" and awaiting keyboard input rather than showing my icon dock?

---

### Post by mcduck on 2009-08-09
Go to Gnome Do's preferences, and under General-tab make sure "Hide window on first launch" is enabled.

---

### Post by distortedecho on 2009-08-09
Is that it??? I thought that was to hide it all together! D'oh!

Thanks!

---

### Post by mcduck on 2009-08-10
With "normal" Gnome-Do themes it prevents Gnome-Do from showing on startup, with Docky it makes Gnome-Do to show the icon dock instead of actual Gnome-Do.

---

### Post by distortedecho on 2009-08-10
Gothcya! Thanks.

I do like Gnome-Do, but I only use it for it's speed. For anything else that I need faster access to; it's docked.

---

