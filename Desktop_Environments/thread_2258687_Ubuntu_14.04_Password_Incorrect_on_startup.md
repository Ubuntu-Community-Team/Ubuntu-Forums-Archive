---
title: "Ubuntu 14.04 Password Incorrect on startup"
date: 2014-12-29
forum: Desktop Environments
---

### Post by warmmilk on 2014-12-29
when I turn on my PC, I get the login screen (its set not to lock and not to ask for the password on startup) and it says I'm giving it the wrong password.  I can log in to guest, but that doesn't really do me any good.  Is there a solution to this that doesn't involve reinstalling the OS (which I only installed a couple days ago).

I tried doing this but it didn't help
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password) 

pc specs if it matters:
ASRock B75M-DGS
Intel Celeron G540
G.skill 4GB ram (single stick)
Hitachi 1TB HDD
350 Watt PSU a friend gave me out of his Dell

---

### Post by TheFu on 2014-12-29
Shot in the dark ... 
Ok - don't take this the wrong way, but what is the username EXACTLY?

Bad username: John Smith
Good username: jsmith

Make sense?  I've come across a few Windows domain administrators who insisted on the "bad username" ... which will never work.

You can reset the password, but the instructions are non-trivial and not easy to write in a forum off the top of my head.
HowToGeek has a password reset how-to for Ubuntu using recovery mode. I'd find that and follow it.

---

### Post by warmmilk on 2014-12-30
> **TheFu said:**
> Shot in the dark ... 
Ok - don't take this the wrong way, but what is the username EXACTLY?

Bad username: John Smith
Good username: jsmith

Make sense?  I've come across a few Windows domain administrators who insisted on the "bad username" ... which will never work.

You can reset the password, but the instructions are non-trivial and not easy to write in a forum off the top of my head.
HowToGeek has a password reset how-to for Ubuntu using recovery mode. I'd find that and follow it.


My username is "mass" so thats not an issue

Is this the HowToGeek password reset thing you're refering to?
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

---

### Post by TheFu on 2014-12-30
It was a shot in the dark - did you try the howtogeek method?

Also, is there any chance that the character set used was changed? I think that will break passwords sometimes.

---

### Post by warmmilk on 2014-12-30
> **TheFu said:**
> It was a shot in the dark - did you try the howtogeek method?

Also, is there any chance that the character set used was changed? I think that will break passwords sometimes.

I'll try it tomorrow (midway through swapping cases)

I don't think the charater set was changed, they keyboard typed as it should when I logged in guest mode...

The biggest thing that has me wondering is that I have it set for not asking for the password on startup.  This is the first time its asked for a password on startup since installing the OS (just installed it last week)...

---

### Post by lisati on 2014-12-30
Another shot in the dark here. Capitalization of passwords can matter. For example, *password* is seen as different to *Password* which is different to *passWord*.

---

### Post by TheFu on 2014-12-31
I've never NOT had it ask for a password, but I consider passwords for local logins to be mandatory for security. Lots of people don't require passwords for console access, so I don't think that is it.

The character set used is per-user, not system-wide. Every user can control the language they see.

If you just installed it last week - why not reinstall fresh?  Should take 15 min. Not really a bug deal, is it?

---

### Post by warmmilk on 2014-12-31
> **lisati said:**
> Another shot in the dark here. Capitalization of passwords can matter. For example, *password* is seen as different to *Password* which is different to *passWord*.

yeah, I'm aware of this.  not the case here

> **TheFu said:**
> I've never NOT had it ask for a password, but I consider passwords for local logins to be mandatory for security. Lots of people don't require passwords for console access, so I don't think that is it.

The character set used is per-user, not system-wide. Every user can control the language they see.

If you just installed it last week - why not reinstall fresh?  Should take 15 min. Not really a bug deal, is it?

I'd prefer to have this figured out without reinstalling the OS in case it happens again when I have more than a weeks worth of stuff on it...\

the howtogeek method didn't work.  instead of "password updated successfully" I get "authentication token manipulation error" and on the next line "password unchanged"


I'm gonna try Debian based Linux Mint

---

### Post by steeldriver on 2014-12-31
Are you sure you are following the password reset instructions exactly? That error usually means that you missed the step where the filesystem is remounted with read-write permission

```

mount -o remount,rw /

```

---

### Post by TheFu on 2014-12-31
Did you happen to enable home directory encryption somehow accidentally?

---

### Post by warmmilk on 2014-12-31
> **steeldriver said:**
> Are you sure you are following the password reset instructions exactly? That error usually means that you missed the step where the filesystem is remounted with read-write permission

```

mount -o remount,rw /

```

I didn't see that code anywhere in the howtogeek instructions...

> **TheFu said:**
> Did you happen to enable home directory encryption somehow accidentally?

I honestly have no idea... if I did, I don't know how or when I did it

---

### Post by steeldriver on 2014-12-31
try these instructions ...

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by TheFu on 2015-01-01
> **warmmilk said:**
> I honestly have no idea... if I did, I don't know how or when I did it

There are 50 different ways to reset a password, try Steeldriver's method. Perhaps that will be easier?

Encrypting anything is almost always a conscious decision. I used "accidentally" because you hadn't mentioned it and it would drastically complicate things. 

For unencrypted storage, getting data off is easy even if the OS won't boot. Just boot any liveCD/liveUSB Linux, mount the internal drive and pull the data you want off. It is almost too easy and shows how important physical security is to all computers.

---

