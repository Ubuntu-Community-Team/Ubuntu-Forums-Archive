---
title: "Have to have password?"
date: 2010-11-17
forum: Desktop Environments
---

### Post by Data 1 on 2010-11-17
Hi,
Finally got around to building a 10.10 box to set beside my 10.04 box. When I created a profile for my 6 year old son it considered it disabled and is forcing me to use a password. So I did a 3 letter word and it wouldn't accept it.

My 6 year old isn't going to be able to remember a long password with numbers letters and special characters come on. I would prefer to use no password at all for his profile just like I do in windows and the 10.04 box.

Am I missing something simple?

Jim

---

### Post by dFlyer on 2010-11-17
It's not a good idea to have no password but if you need it, try system/administration/login screen. That should give you the option to allow someone to log in automatically.

---

### Post by asmoore82 on 2010-11-18
I, too, would recommend a reasonable password and automatic login.

You can override the password requirements by setting a password with the command line:
```
sudo passwd *<username>*
```
But be forewarned! An *insecure* password is truly **insecure**.
This can turn ugly if any services such as file sharing or remote login are enabled.

---

### Post by 3Miro on 2010-11-18
You can remember a good password. For a 6 year old, you can type the password on a sticky note next to the computer. Such a young kid should not be allow admin privileges and only basic access, so it doesn't matter if the password get "stolen". On the other hand, consider teaching the kid basic computer security, instead of using their favorite Disney character Pluto, make the password Pluto12 or Mickey3 or something at least a bit more complex.

For a desktop, autologin is a nice option.

---

### Post by TNT1 on 2010-11-18
You should consider teaching your son one of the linux fundamentals, which is the need for a password. As for what word he can remember, why not his name? That's what I use for my 4 year old in his profile on the antiX box, sure, he spells it wrong sometimes, but he's just 4, I say teach em good habits young.

Oh, sorry, pretty much what 3m said then:

"Such a young kid should not be allow admin privileges and only basic  access, so it doesn't matter if the password get "stolen". On the other  hand, consider teaching the kid basic computer security, instead of  using their favorite Disney character Pluto, make the password Pluto12  or Mickey3 or something at least a bit more complex.

For a desktop, autologin is a nice option."

---

### Post by sisco311 on 2010-11-18
> **3Miro said:**
> You can remember a good password. For a 6 year old, you can type the password on a sticky note next to the computer. Such a young kid should not be allow admin privileges and only basic access, so it doesn't matter if the password get "stolen". On the other hand, consider teaching the kid basic computer security, instead of using their favorite Disney character Pluto, make the password Pluto12 or Mickey3 or something at least a bit more complex.

+1

> **3Miro said:**
> 
For a desktop, autologin is a nice option.

Another option is to allow the user to log in without a password:
```
sudo gpasswd -a username nopasswdlogin
```

---

### Post by Data 1 on 2010-11-18
OK Thank you all, I'm marking this as resolved and myself as an idiot. I didn't see where you can make a password then check for it not to ask you for it when you log in.

I'll try not to do any more damage, thank you :)

---

