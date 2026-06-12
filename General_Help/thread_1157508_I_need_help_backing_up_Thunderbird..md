---
title: "I need help backing up Thunderbird."
date: 2009-05-12
forum: General Help
---

### Post by rmjohnson144 on 2009-05-12
I'm about to reinstall Ubuntu, but I need to backup my email and address book and everthing else in Thunderbird.  I tried using MozBackup, but it is for Windows only.  

Does anyone know of a utility to do this and maybe for Firefox as well?

Thanks for any help
-=Mark=-

---

### Post by whoop on 2009-05-12
I don't use thunderbird but I expect everything being stored under
~/.thunderbird

---

### Post by 73ckn797 on 2009-05-12
Go to /home/yourname/.mozilla-thunderbird .

Copy the cryptic looking directory to a flash drive. The name would look similar to this: 39yzrvuk.default and profiles.ini in the folder. Copy all contents in the .mozilla-thunderbird folder, or you could just copy the /home/yourname/.mozilla-thunderbird folder completely. You will need to ini file.

Once you have reinstalled Ubuntu and down loaded T'bird, you can then copy the folder/directory back into the /home/yourname/.mozilla-thunderbird folder or the entire directory, over writing the one created during install of T'bird. if it created the directory. Whatever, let it over write. All of your info will be completely as you had it before.

That is how I always do it and do not miss a beat with it.

---

### Post by rmjohnson144 on 2009-05-12
Now, will this work to transfer to Windows?  or does windows handle this differently?

-=Mark=-

---

### Post by 73ckn797 on 2009-05-13
> **rmjohnson144 said:**
> Now, will this work to transfer to Windows?  or does windows handle this differently?

-=Mark=-

Basically the same. There may be a few files in the directory that are Windows specific but will not affect the use in Ubuntu. Your directory path in Windows will look similar to this:
```
Documents and Settings/yourname/Application Data/Thunderbird/Profiles/5s1m3xoa.default
```

Again, just copy the entire folder over via a memory stick or whatever to the new installation. Do this before you start Thunderbird for the first time or it will create its own cryptic named folder.

---

