---
title: "Fresh install Ubuntu Server - Login hangs"
date: 2009-01-09
forum: General Help
---

### Post by capcaunu on 2009-01-09
Hi!

I'm at the point where I wish I had thrown my old computer out the window before having the idea of trying to set it up as a test server. I am a complete newbie when it comes to linux but I just wanted to set up Ubuntu and see what's next. I've installed a lot of other distros some time ago with no problem.

After a fresh Ubuntu Server 8.04 (and also 8.10) install on a p4 desktop with 2 gb ram and a non-partitioned 80 gb HDD I am unable to login. Everything worked like it was supposed to before the login process.

Specifically:
I type the username, hit enter and before I can type the password everything hangs for 60 seconds before giving me a login timeout error.

I've checked the forums, and found that for some people changing the bind_policy to soft  solved the problem. Not for me. I can't find /etc/ldap.conf   , there is only /etc/ldap/ldap.conf and there is no bind policy specified there.

just above the login line there's something about not being able to identify the server's IP adress so it's using 127.0.1.1  Isn't that supposed to be 127.0.0.1  ?

Anyway, help me, or the computer's gonna get it, get it?

Seriously now, I could use your help guys.
Thanks!

---

### Post by geforce123 on 2009-01-09
Sorry I have no idea about your problem.

But I have something to add about 127.0.0.1 address.

In fact, all addresses in the 127.0.0.0/8 range is your loopback network.

Which means everything from 127.0.0.1 to 127.255.255.255 is in the loopback network.

It is described in RFC3330 [http://tools.ietf.org/html/rfc3330](http://tools.ietf.org/html/rfc3330)

---

### Post by capcaunu on 2009-01-09
Thank you for looking at it Geforce.

I've narrowed it down to a hardware or network problem. Tried installing CentOS and it does the EXACT SAME THING. It installs and hangs at the login in the exact same manner.

Mandriva 2009 worked.

Are there any known hardware incompatibilities that result in such a behaviour?

Thank you!

---

### Post by Jose Catre-Vandis on 2009-01-09
Does it actually get to a command prompt asking for a login? i remeber one of my server installs didn't quite get there and required a press on the return key to get me to a prompt. if you are trying to enter your login in name before getting to a prompt it may not work out?

---

### Post by capcaunu on 2009-01-09
Jose, yes, it does ask for a login.

I don't know what you would call a "command prompt"
There is no interface coming up, just another text line
that says **login:**
login: serveradministrator [press enter]
password: [nothing appears while typing]


I've said earlier that it may be a hardware issue. Just 2 minutes ago I've tried booting while the hdd was in another computer. This time it was a quad core with intel mainboard and 4 gb corsair dominator. The result was identical. The only common elements were the hdd, the installation and the network connection, other than that, completely different systems.  Both systems performed flawlessly with windows and mandriva.

So, I can only assume it's a network issue. Did I mention I was behind a router with DHCP? I think I did. Does that even matter at this point?

Thanks!

---

### Post by Jose Catre-Vandis on 2009-01-09
Try recovery mode, see if you can get in that way?

---

### Post by capcaunu on 2009-01-09
I found the problem, or almost.

**I am unable to type into a password field while in a console on any linux distro.**

I currently have Mandriva installed (only one that worked), and while trying to install a package I typed **urpmi package name** and got back "command not found". Researched it and saw that I had to **su -** witch asks me for a password and urpmi would work again.

I did that, and the password field came up in the console.

[B] I was unable to type into it, just like in the Ubuntu Server installations.
[/B]

This made me very very happy somehow! :D 

At least I know there's something wrong with my sistem, drivers, bios, keyboard, mainboard, anyway stuff that I can fix.

So, what do you recomend I should do?

ps 

Recovery won't do anything for me either.

---

### Post by capcaunu on 2009-01-09
HAHAHA = This is crazy!

Linux consoles/terminals don't show * while typing the password. LoL and I thought the keyboard was frozen or the system is halted. I can't belive this. I'm such a noob!
Thanks for your help guys!

---

### Post by Jose Catre-Vandis on 2009-01-09
:) Happy newbie :) Keep practising :)

---

### Post by capcaunu on 2009-01-10
Thanks! I will

---

