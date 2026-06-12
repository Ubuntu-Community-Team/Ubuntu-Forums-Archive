---
title: "Passwords"
date: 2009-02-26
forum: General Help
---

### Post by Novicerover on 2009-02-26
As I am using the PC on my own,I would like to be able to operate without passwords popping up every few seconds.
Can I stop them appearing altogether.  I have just installed the system and  love it !

---

### Post by linux4me on 2009-02-26
> **Novicerover said:**
> As I am using the PC on my own,I would like to be able to operate without passwords popping up every few seconds.
Can I stop them appearing altogether.  I have just installed the system and  love it !

You need to provide us with a little more information. What program(s) are you using that you're being frequently prompted for passwords?

---

### Post by Novicerover on 2009-02-26
When I start up and select mail or browser for example I get a box telling me I need a password to unlock the keyring
Another message tells me authorization is required by wireless network, with the password box already filled in ( when opened shows idd42371ab386d585alb5.)
I had a D Link router connected and disconnected it as half the time I could not get on the net. At present I am hooked direct to the modem by Ethernet cable ( NTL Broadband ) now at least I connect every time.

---

### Post by mb_webguy on 2009-02-26
Ok... *that* we can help you with.  If you were talking about when you're prompted for your password for administrative tasks, on the other hand... not so much.

Here's what you need to do to disable the keyring.

Go to the ~/.gnome2/keyrings folder. Delete any files you see there. Then logout and log back in. If you are prompted to enter a password for the keyring, leave the textboxes blank and click the Ok button (or the equivalent if it's not actually "Ok"). If you are then prompted to confirm that you want to use an unencrypted keyring, do so.

That should be it.

---

### Post by RequinB4 on 2009-02-26
backup the files somewhere else first.

---

