---
title: "[SOLVED] Forgot username(s)"
date: 2008-12-22
forum: General Help
---

### Post by Vista1330 on 2008-12-22
Could someone please help me. In the past I used a theme where u just chosed what profile u wanted to load and enter the password. I just installed a new theme where this option is not possible, u need to enter the individual profile name and then the password. The problem I can not sign in, I know I have the passwod correct but my username(s)?I enabled the administrator account also but what is the login name for this account?and is there any way finding the names for the other account(3 account excactly)

---

### Post by drs305 on 2008-12-22
I think you are talking about the intial login but I am not sure. If so, you can boot to the recovery mode, choose the "Boot to root shell option" and then run:
```

ls /home

```

That will present you with the home folders of all users on the system. You will hopefully recognize your username among the list presented.

---

### Post by Iowan on 2008-12-22
Older systems (like mine) let you boot into recovery mode.  Dunno if newer ones will, or if you need the Live disk.  Either way, you should be able to log into a "safe mode" which will let you view (**less** or **cat**) the */etc/passwd* file.  Your users should be buried in there somewhere (probably toward the bottom).
Here's a [forgot password]("http://www.psychocats.net/ubuntu/resetpassword") link that mentions another way to discover users.

---

### Post by Vista1330 on 2008-12-22
> **drs305 said:**
> I think you are talking about the intial login but I am not sure. If so, you can boot to the recovery mode, choose the "Boot to root shell option" and then run:
```

ls /home

```

That will present you with the home folders of all users on the system. You will hopefully recognize your username among the list presented.

Thanx dude!You are a real lifesaver...I can now work with Ubuntu which I am doing at the moment, JUST hate Vista right now. But still its good to have double boot feature for desperate moments like this:D
Thanx again

---

### Post by Vantrax on 2008-12-22
The other option is to use a live CD and mount the filesystem.

You can then just look at the homes to see what the logins are, or view the passwd file in /etc/

If you dont have a cd you can also do it by booting into single user mode by hitting E at the grub screen and adding *single* to then end of the boot line where the options are.

---

### Post by upapilot on 2008-12-23
> **Vista1330 said:**
> Thanx dude!You are a real lifesaver...I can now work with Ubuntu which I am doing at the moment, JUST hate Vista right now. But still its good to have double boot feature for desperate moments like this:D
Thanx again
Hey if you want thank people for their help then just click thanks button on the reply you found most helpful rather than post another reply just to thank!

---

### Post by upapilot on 2008-12-23
And mark the review as SOLVED

---

