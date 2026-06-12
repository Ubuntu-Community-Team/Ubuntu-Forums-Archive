---
title: "passwords"
date: 2009-06-12
forum: General Help
---

### Post by kk5pa on 2009-06-12
is there a way to get rid of all passwords ?  i don't like having to enter password every time i change something..   any help out there..

---

### Post by RudolfMDLT on 2009-06-12
Hi there,

Probably, but it's not the way Ubuntu operates, and no responsible person on this forum will tell you how without good reason.

What problems are you having that you have to keep typing in password?

If you are using the machine just for normal work you should only have to type a login password, and passwords should then not be an annoyance in the first place?

Regards,

Rudolf

PS: If you want to know why you have to keep typing passwords for admin use, [http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security) , a forum member has written a nice article on it. Post back with any questions.

---

### Post by RudolfMDLT on 2009-06-12
> **colau said:**
> 
Now do everything.

Dude - Lets just hear what the guy wants to do? giving someone root privileges and telling them to running everything using the substitute user command isn't smart.

---

### Post by Elfy on 2009-06-12
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by RudolfMDLT on 2009-06-12
> **forestpixie said:**
> [http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Thanks!

---

### Post by t0p on 2009-06-12
> **kk5pa said:**
> is there a way to get rid of all passwords ?  i don't like having to enter password every time i change something..   any help out there..

The **passwd** command in Ubuntu is set up so you can't make your password a simple press of the <Return> key, nor can you make your password too short or too simple.

For example: I tried to change my password to **a**, **aa**, **aaa**, **aaaa** and **aaaaa**, and each time Ubunty told me the new password was too short.  Ubunty told me that **aaaaaa** was not permissable as palindromes are not allowed.  And **aaaaas** was too simple.  I gave up my experiments at this point.

Somewhere there is/are config file(s) that establish the rules for passwd on your computer.  I don't know where they are, or how to alter the rules.  The commands

```
man passwd
```

and 
```
man 5 passwd
```

will reveal some of the rules to you, but do not make it plain how to change or avoid them.  Forum policy will jail any posts that explain how to change or avoid the rules.

Of course, Google is your friend.

Interestingly, the Free Software pioneer Richard Stallman once led an anti-password campaign, wherein he cracked his colleagues' passwords and sent them emails telling them of this fact; then he encouraged them to change their passwords to a simple press of the <Return> key.  Apparently a good number of these people followed his advice.  But what was good enough for Stallman is not good enough for us.

---

### Post by RudolfMDLT on 2009-06-12
LOL @ t0p, like the old forum used to be.... :popcorn:

---

