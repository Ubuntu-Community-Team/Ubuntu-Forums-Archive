---
title: "Dell 10v-- who is root?  User?"
date: 2009-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Preserved Killick on 2009-12-05
Hi.

When you boot a new Dell 10v out of the box, does it boot you without a password right into the root account?  I have read the little pamphlet that came loose in the box, and it doesn't mention needing a password at all or any kind of account creation.

I can't just start the little surfboard and look because it's a gift and I want the recipient to be the first person to power it up.  So, can anyone here please tell me how it works?  I will be doing the initial tech support so any tips you can share would be helpful.  I am not a Linux rookie, though, as I've been using it as my desktop since 2001.

Thanks!

-- Killick

---

### Post by ugm6hr on 2009-12-05
From memory, assuming the 10v is the same as the Mini 9, it does ask for a username / password, similar to an OEM install.

But it defaults to auto-login (I think).

Really not 100% certain though....

An alternative option, assuming you are providing tech support would be to just do an OEM install of 9.10 (or whatever Ubuntu version you personally use).

---

### Post by Preserved Killick on 2009-12-05
OK, thanks.  Maybe someone else will reply with an update.  Of course that may be me on 12/25 when it gets opened. ;-)

-- Killick

---

### Post by teward on 2009-12-05
I'm quite certain that ANY install will not log you in as root.  It might, however, prompt you for a setup menu or something, but with Dell netbooks and stuff, I'm not sure.

---

### Post by Preserved Killick on 2009-12-05
The quick start guide that came in the box says only that the Dell Desktop launches when you turn on the computer.  I would expect it to mention account creation if that step were there.  If anyone knows how this works, please enlighten me.

(I did buy a PC with Linux preinstalled once (SuSE) and the root password was on a slip of paper in the box.  That was not a Dell machine and so I don't believe it's relevant here.)

---

### Post by ugm6hr on 2009-12-06
Just to clarify (re: prev post), it definitely does not log in as root.

It does have a "sudoer" login.

I just can't remember how it asked me for those details.

---

### Post by Greyed on 2009-12-06
When it boots up it asks the standard user account creation questions.  Eg username, password, real name, blah, blah, blah.  That will be the first account on the machine (UID 1000, GID 1000) and the only account automatically placed in the sudoers file with ALL:ALL as its entry.

As with any Ubuntu install Root has an invalid password.  Note this is different than no password.  It has a password, just not one that can be obtained by the cypher algorithms in use and thus, can never be matched.  Root is derived from sudo and its GUI cousins.

---

### Post by teward on 2009-12-06
Just like Dells with Windows, they always preprogram it to load up when you get it and be like "ANSWER MY QUESTIONS, THEN I'LL WORK".  It's Dell, and thats usually what they do.

---

### Post by Preserved Killick on 2009-12-07
OK then.  Thanks for the info.  I'm a little surprised that the account creation isn't mentioned at all in the "ubuntu QUICK START GUIDE" but I'm happy to know these machines won't boot straight into root.

Thanks!

-- Killick

---

### Post by gbrainin on 2009-12-07
> **Preserved Killick said:**
> OK then.  Thanks for the info.  I'm a little surprised that the account creation isn't mentioned at all in the "ubuntu QUICK START GUIDE" but I'm happy to know these machines won't boot straight into root.

Thanks!

-- Killick

They don't boot as root (as noted above, root is effectively disabled), but the first account created by default has sudo privileges.  So the first user can do anything that root can, if run using sudo.  Many of the administrative programs run as sudo (or with a sudo-ish mode) by default, so if the user--for example--runs the Synaptic Package Manager from the menu, it will first ask for the user's password.  Once given, the user can mess up the system quite effectively.

---

