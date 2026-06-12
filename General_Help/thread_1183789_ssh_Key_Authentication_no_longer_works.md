---
title: "ssh Key Authentication no longer works?"
date: 2009-06-10
forum: General Help
---

### Post by nowhere@cox.net on 2009-06-10
Hi,

I have a desktop system and a laptop. My keys are install in .ssh as they should be and for months have been working fine, including the last month or so I was running 9.04 on my laptop (still on 8.10 on the desktop, too many problems with 9.04 stability so far).

Anyway, yesterday, all of the sudden, when I sshftp to my desktop, it asks for my password. This is not the password to unlock my keyring either. 

Why did this happen? What should I look at first to figure it out? I recopied my public key to the server but it didn't change anything.

Thanks!

EDIT: It also asks for a password if I just ssh to the machine...

---

### Post by ducksun43 on 2009-06-11
did you change /etc/ssh/sshd_config ?

this page [http://sunoano.name/ws/public_xhtml/ssh.html](http://sunoano.name/ws/public_xhtml/ssh.html) has info on how it should look like for password and/or PKA login.

---

### Post by nowhere@cox.net on 2009-11-20
I still haven't gotten this fixed but it's been on the back burner. I'm pretty sure it's a keyring password issue. Is there a way to throw out the old keyring and start a new one? Will it cause problems with my Private folder? 

Thanks!

---

### Post by teward on 2009-11-20
Did someone change the passwords without your knowledge?

You ARE using the password you use to login to the computer with, right?

---

### Post by nowhere@cox.net on 2009-11-20
I can log in fine but it asks for my password whenever I ssh to this (and only this) machine. My public and private keys are installed correctly but I seem to remember getting some kind of keyring error sometime when I'm logged into the console. 

Also, I DID change the password and tried to update passwords of the keyring and such but there is a good chance I got that process wrong since it was the first time I ever changed a ubuntu password. I'm updating more often than needing to change password...

---

### Post by michy99 on 2009-11-20
See if this is any help:

[http://www.greenhughes.com/content/how-change-default-keyring-password-ubuntu-netbook-remix-904](http://www.greenhughes.com/content/how-change-default-keyring-password-ubuntu-netbook-remix-904)

---

### Post by stonebit on 2009-11-21
Just get a new one. Remove the old entry from your ~/.ssh/authorised_keys file. When you try to reconnect, it will get the correct key.

---

