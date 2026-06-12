---
title: "Desktop problem"
date: 2005-05-30
forum: Desktop Environments
---

### Post by ersandgren on 2005-05-30
I Get Permission Denied when trying to Access my Desktop folder I can´t create Dokument/files or anyting on my desktop I´ve checked the perm. and it looks ok, I´ve tried as root but  gets Operation not permitted (I guess you need logon without starting X and that I dont know how to do)

Pleas help! :-|

---

### Post by Alexander Kirillov on 2005-05-31
[QUOTE=ersandgren]I Get Permission Denied when trying to Access my Desktop folder I can´t create Dokument/files or anyting on my desktop I´ve checked the perm. and it looks ok, I´ve tried as root but  gets Operation not permitted (I guess you need logon without starting X and that I dont know how to do)

Pleas help! :-|[/QUOTE]
 Please post more info. What are the permissions? Are they usual local filesystems or you are using some form of file sharing/file server (Samba, NFS,,)? Whta happens if you open a termimal, cd to Desktop directory, and issue command touch test.txt

(touch creates an empty file)

---

### Post by logan2004 on 2005-05-31
try this:

```

su
chmod -R 777 /home/*username*/Desktop

```

---

### Post by shakin on 2005-05-31
[QUOTE=logan2004]try this:

```

su
chmod -R 777 /home/*username*/Desktop

```[/QUOTE]

That could be dangerous and in any case, it's overkill. Try this instead:

```

$ sudo chown -R username:username /home/username

```

---

