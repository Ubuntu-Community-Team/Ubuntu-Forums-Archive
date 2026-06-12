---
title: "sudo secruity issues"
date: 2005-04-01
forum: Desktop Environments
---

### Post by disturbed1 on 2005-04-01
I can understand the removal of the root account, but I don't like the way sudo is being used.

After a recent upgrade to Hoary, the first thing I did upon logging in is was to run Synaptic. No password was asked for, synaptic was launched right away. Along with the install process.

In Warty there are times when asked for my password (say for synaptic), I'd enter it. Then close synaptic. If I restart synaptic again, the password is remembered. Same for sudo in the console. If I enter the password once, it remembers it.

This is just wrong. Each and every time root access is needed, you should be asked for a password.

Since Ubuntu is caching my password, if I'm away from the PC, a passerby can have access. Should my PC happen to be compromised, that person would also have full access.

---

### Post by fjleal on 2005-04-01
You can always enable the root account and erase the contents of /etc/sudoers...  :-k

---

### Post by disturbed1 on 2005-04-01
Don't have the time to do this to my personal PCs, let alone everyone elses that I've setup.

That's also just a bandaid fix, and doesn't cure the problem of the default install.

This should be fixed with a security update. Just don't know if it's an Ubuntu problem, or gksudo. Though I do believe it's an Ubuntu problem, since the password caching happens in the console also.

---

### Post by cabu on 2005-04-01
From the sudoers manpage:

**timestamp_timeout**
    Number of minutes that can elapse before sudo will ask for a passwd again. The default is 5. Set this to 0 to always prompt for a password. If set to a value less than 0 the user's timestamp will never expire. This can be used to allow users to create or delete their own timestamps via sudo -v and sudo -k respectively.

Check your /etc/sudoers and see what you can do there.

---

### Post by disturbed1 on 2005-04-01
/var/run/sudo    is where timestamps are suposed to be,

I used visudo and changed the defaults from

Defaults          !lectures,tty_tickets

to

Defaults         tty_tickets

The defaults listed make zero sense at all. Both lectures and tty_tickets are turned off by default anyways  :-k 

Looking into /var/run/sudo/%username    there are 7 files. 0 1 2 3 4 5 and unkown. So I moved all files except 0. Issued a sudo command, promt for password. Then issued another sudo command, no password prompt.

5 reappeared in /var/run/sudo/%username :roll:

---

### Post by cabu on 2005-04-02
I changed my /etc/sudoers from:
```
Defaults        !lecture,tty_tickets
```
to:
```
Defaults        !lecture,tty_tickets,timestamp_timeout=0
```
I then ran sudo command after sudo command and was asked for my password each time. Changing it back to the default gives me a grace period of about 5 minutes after the last time I entered the password. This seems reasonable to me for a home desktop, I would definitely change it to 0 for a server environment.

I think that tty_tickets is on by default. I believe the ! operator is on a per item basis, in other words it would have to be:
```
Defaults        !lecture,!tty_tickets
```
for them to both be off.

---

### Post by disturbed1 on 2005-04-02
Thanks, that did the trick.   :mrgreen:

---

### Post by skjantzen on 2006-01-02
I'm not sure what I did, but sudo won't work anymore. I can enter su and then enter the root password and then run root commands, but if I run sudo then a command it will ask for a password but then not complete the command.

What gives?

My problem is further compounded. When I try to add a user, I click System-->Administration--> Users & Groups. It asks me for the password. I enter the password but the Users & Groups window does not open. I can't do any configuration through the GUI that asks for the admin password that sudo requries.

Help!

Scott

---

