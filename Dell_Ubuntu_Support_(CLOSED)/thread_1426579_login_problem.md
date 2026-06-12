---
title: "login problem"
date: 2010-03-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by this name is taken on 2010-03-10
Hey well i'm having a problem loggin in, as my sister thought she was a genius and tried to make a user account and has somehow managed to lock the computer from access. No user accounts are working properlly.

 I have just gotten this and I am wondering if there is a way I can restore the system to factory defaults, or bypass the login prompt. 

Thanks in advance.

---

### Post by iponeverything on 2010-03-10
> I have just gotten this
not really sure what you've gotten. 

> and I am wondering if there is a way I can restore the system to factory defaults

A reinstall is about about is close as you going to get, if you don't have backup.

> , or bypass the login prompt.

In the grub menu and go to rescue. This should just dump you at root prompt. From there edit your /etc/password file with nano.
You will see entries like this:

```
guest:x:114:128:Guest,,,:/tmp/guest-home.zf9421:/bin/bash

```

The fields are colon separated, the second field is password field. Removing the x so the entry looks like:

```
guest::114:128:Guest,,,:/tmp/guest-home.zf9421:/bin/bash

```

will remove the password for that account. 

/etc/group identifies the admin accounts.

look for line that starts with "admin:" 

remove or add accounts as necessary for what you are trying to do.

---

### Post by pizza-is-good on 2010-03-11
If you mean restore to Dell Factory Defaults, you have to do that through the BIOS. You will loose all data and have to reinstall everything that you installed after you got the computer. Even Ubuntu if it didn't come with it.

Edit: My 200th post!!!:popcorn:

---

### Post by lz1dsb on 2010-03-12
[iponeverything]("http://ubuntuforums.org/member.php?u=643833") is this a how I can recover from a lost password? How can I get into the Grub menu. When my laptop is booting I only see "Grub loading" for a few seconds... I'm running 64-bit Karmic, and I haven't lost my password, It's just interesting to know how I can recover if this happens...

---

### Post by iponeverything on 2010-03-12
hold down the shift key while it is booting. See #2 here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

