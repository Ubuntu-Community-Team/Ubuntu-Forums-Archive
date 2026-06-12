---
title: "How to gain root powers?"
date: 2009-02-05
forum: General Help
---

### Post by SF007 on 2009-02-05
Is there a way to enable/gain root powers in my REGULAR ubuntu account?

-I know I can login as root: that is not what I want (it is what I do at the moment)
-I know I can disable the password prompt: that is not what I want
-I know I can go back to windows: I already use Windows (but also use Ubuntu)
-I know I can use *sudo -i* and *sudo -s*: but I really want to use the whole system with root powers without doing stuff before

I don't have any particular problem, all I want is to use a Virtual Machine with no restrictions. I don't care if it blows up, I only use it for testing, and after testing, I always restore to a clean "snapshot"

I understand if nobody helps me to make my system less secure, but could anyone AT LEAST tell me if this is possible?

Thanks.

---

### Post by mb_webguy on 2009-02-05
You actually can't login as root except by booting into recovery mode.  The root account is disabled by default on Ubuntu.

Sudo, and gksu for graphical applications, are the way to gain root privileges.  You can run anything as root using these commands.  For example, you can run nautilus as root with the command "gksu nautilus". 

However, if you absolutely must be root, read [this]("https://help.ubuntu.com/community/RootSudo"), especially the section on enabling the root account.

---

### Post by NT4usB on 2009-02-05
I'll use```
sudo -i
``` when I have a bunch of editing I have to do so I don't have to type sudo over and over. 
Just don't forget to log out ```
exit
``` before touching that has to be accessed by user or user will be locked out of that.

---

### Post by Locutus_of_Borg on 2009-02-05
Having never tried this, I am not certain  it will work, however:

```
sudo -i
usermod -g root LOGIN_NAME
exit

```
After logging out then back in, you *should* now be member of the group root, with root powers, while still retaining your user settings...


let me know if it works though, lol

---

### Post by SF007 on 2009-02-05
@mb_webguy
Yes, I know that, thanks, but I do not want to use the root account, I want to use my own.
Why:
-I want my own username (not "root")
-home is not in the proper place (/root instead of /home/USERNAME)
-I can't autologin being root

@NT4usB
Thanks, but I wanted a slightly different approach.

@Locutus_of_Borg
I tried it and it did not worked: everything looks the same and I need to input the password

I tried lots of method:
-Adding me to the "admin" and "root" groups (at the same time)
-putting my main group as root
-putting my main group as admin
-creating new user with uid (user id) 0
-creating new user with all "powers" checked

And nothing worked!

---

### Post by cariboo on 2009-02-05
If you have to ask here, you're not ready to run as root all the time.

Jim

---

### Post by warp99 on 2009-02-05
The following should work:

```
sudo visudo
```

then scroll down to the following line:

```
# User privilege specification
```

and add your user name just under root:

```
$user ALL=(ALL) ALL
```

If you just don't want to use a password then uncomment 

```
#%sudo ALL=NOPASSWD: ALL
```

---

### Post by aysiu on 2009-02-05
Yes.

Further reading:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

