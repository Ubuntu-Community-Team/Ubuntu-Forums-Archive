---
title: "Yes, another newbie having problems with sudo passwords"
date: 2009-01-12
forum: General Help
---

### Post by happy_5 on 2009-01-12
Hello all, 

New to the forums! I recently installed Ubuntu into my PS3, and it is sweet! :guitar:

I am getting the hang of terminal window commands (after years of typing commands in Windows OS), however, I cannot get a single change done because it always asks for a password. 

When I try typing the password, nothing happens - no characters are written, numbers, I mean nothing. I just press "enter" and it asks for the password again. 

The keyboard works just fine, it is connected through USB (bluetooth keyboards do not work, thank you very much!). 

Any thoughts? It is kind of stupid, but want to ask first.

---

### Post by taurus on 2009-01-12
Are you sure you type in the same password that you're logging in with?

What's the output of this command from a terminal?

```
id
```

---

### Post by happy_5 on 2009-01-12
> **taurus said:**
> Are you sure you type in the same password that you're logging in with?

What's the output of this command from a terminal?

```
id
```

Yes, it is the same password, but nothing is shown on the screen. 

Here is the output you requested:

```
uid=1000(julio) groups=4(adm),20(dialout),24(cdrom),46(plugdev),lll(lpadmin),120(admin),125(sambashare),1000(julio)

```

Also, if it is not too much to ask, you need to explain things in simple terms as again I'm new to this.

Thanks a bunch.

---

### Post by mssever on 2009-01-12
The Linux way is to not show any output when you type a password. Just type the correct password, hit enter, and it'll work, even if you don't see any asterisks on the screen.

---

### Post by hyperdude111 on 2009-01-12
mssever is right, although you wont see anything just imagine you can it is still typing your pass in the background just you cant see it.

---

### Post by happy_5 on 2009-01-12
> **mssever said:**
> The Linux is to not show any output when you type a password. Just type the correct password, hit enter, and it'll work, even if you don't see any asterisks on the screen.

Ok, that worked. Thanks!

Now how to disable it asking me every single time? At least it can ask me once at the beginning of a session, but typing it, despite the obvious security benefits, it a pain.

---

### Post by mssever on 2009-01-12
> **happy_5 said:**
> Ok, that worked. Thanks!

Now how to disable it asking me every single time? At least it can ask me once at the beginning of a session, but typing it, despite the obvious security benefits, it a pain.
You can control that with the sudoers file. Read ```
man sudoers
```for details.

Note that the Ubuntu default is to cache your password for 15 minutes.

---

