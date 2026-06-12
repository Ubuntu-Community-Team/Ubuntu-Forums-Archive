---
title: "Trying to understand user privilages and root in ubuntu"
date: 2009-02-24
forum: General Help
---

### Post by Crash.hm on 2009-02-24
Hi I'm just switching over to linux and a lot of the articles i've read say that you can enhance security by having an admin profile and a general use profile. I've also come to understand that root is not directly part of the ubuntu user profiles, as far as i understand it it is not something i have direct access to with out the sudo command. so my question is this:

Do i benefit in terms of security from having a ubuntu based admin account and a standard desktop account if i'm the only user?

Would it just make more sense to have the ubuntu admin account since i don't have direct root access?
thanx

---

### Post by protodog on 2009-02-24
There are many reasons why there should be a separation between regular users and root privileges. On a single-user system, this separation might seem redundant, but consider this:

If you downloaded a program on your computer, ran it under root privileges, and later discovered that it was malicious program--there would be no way to reverse the damage that the malicious program had done.

As a regular user however, you can run it inside of your home directory and this would shield the program from harming other parts of your system since it would have access to the other parts. In fact, you could even create a sandbox if you were suspicious so that it would protect your user content.

Another thing is that, on a day-to-day basis, you shouldn't really have to use root privileges. It's only in certain instances such as updating your software that you would need it.

Hope this gives you a good intro of permissions in Linux. They're very useful and very important.

---

### Post by mb_webguy on 2009-02-24
In Windows, creating separate Administrator and Limited accounts is a Very Good Thing, since many of the security issues with Windows are because the default account is the equivalent of root on Linux.  There's really no point, however, in creating a separate account on Ubuntu if you're the only user.  In fact, Ubuntu is designed specifically so you don't have to do this.

Making a separate limited account will only make things more difficult for you, and won't make you any safer.  In Ubuntu, programs can only run with elevated privileges if you specifically run them as such.  This is part of the reason you don't have to worry about viruses on Linux -- even if a malicious program could somehow automatically run itself without you initiating it (which it can't), it can't infect your system because it doesn't have the privileges to do so.  The only difference between an admin account and a non-admin account in Ubuntu is that an admin account has the option of running programs with elevated privileges, and you are still required to enter your password to do so.  Since you can't really do damage to your system by accident with an admin account in Ubuntu, there's no reason to make a separate account to avoid doing so.

---

### Post by FluffyElmo on 2009-02-25
Just a quick bit of clarification, hope I don't confuse things more:)

The root user account in Linux is directly equivalent to an Administrator account in Windows. This account is not enabled in Ubuntu, you can enable it but it is not necessary and not recommended. 

User accounts with admin privileges run everything as a normal user but can run some programs as root if you provide a password. For a single user system this is the type of account you want as you are basically restricted to your home directory but can still install software and perform admin tasks when necessary using sudo.

You can create user accounts without admin privileges which are similar to a Guest account in Windows. It's really not necessary in your case. As long as you don't enter your password if you are asked for it unexpectedly there is no difference between this and an account with admin privileges.

---

### Post by mb_webguy on 2009-02-25
Well stated, Elmo.  That's exactly what I was trying to say, but I have a bad earache so I'm not thinking as clearly as usual.  #-o

---

### Post by Crash.hm on 2009-02-25
cool. thanks for the help. it's a lot clearer now.

---

