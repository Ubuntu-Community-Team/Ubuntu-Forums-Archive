---
title: "Passwordless updates"
date: 2011-07-11
forum: Desktop Environments
---

### Post by Dr Eigen on 2011-07-11
Hi folks

I'm running "Classic" Natty.

My keyring is unlocked by default.  How can I switch off requiring a password for things like installing updates?

IIRC in Hardy I did this through gconf, but can't find anything to do it in Natty.

(No lectures please.  I understand the implications, the machine is physically secure and I trust myself.)

Ciao

---

### Post by adammarleymtts on 2011-07-11
I have faced the same issue but could not recover the pass word ,can any one help me out .

---

### Post by adit on 2011-07-11
For the user who posted post#2[URL="http://www.psychocats.net/ubuntu/resetpassword"][U]
How to reset your password in Ubuntu[/U][/URL]

---

### Post by Krytarik on 2011-07-11
Dr Eigen, please see this earlier thread, this may work with "/usr/bin/update-manager", too:
[http://ubuntuforums.org/showthread.php?t=1677548](http://ubuntuforums.org/showthread.php?t=1677548)

Greetings.

---

### Post by Dr Eigen on 2011-07-11
Krytarik, I have passwordless sudo already (as one might guess from my OP!) ;)

Is there any reason to suspect sudoers modification might work?  Does gnome call sudo behind the scenes?  (Certainly in Hardy with things set up the way I wanted there was no sign of it in sudoers.)

---

### Post by Krytarik on 2011-07-11
> **Dr Eigen said:**
> Does gnome call sudo behind the scenes?
Yeah, in fact "gksu" is invoked by Update Manager.

---

### Post by Dr Eigen on 2011-07-11
> **Krytarik said:**
> Yeah, in fact "gksu" is invoked by Update Manager.

OK, while I haven't quite got what I was after, the above has reminded me how to do a workaround.

I've simply edited the relevant main menu entries to call the particular config apps I'm interested in with gksudo.

---

### Post by Dr Eigen on 2011-07-12
> **Dr Eigen said:**
> I've simply edited the relevant main menu entries to call the particular config apps I'm interested in with gksudo.

I don't really want to mark this solved with this rather ugly hack.  Can anyone suggest a more elegant solution?

---

