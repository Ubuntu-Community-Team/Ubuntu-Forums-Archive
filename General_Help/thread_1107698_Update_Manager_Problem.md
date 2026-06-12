---
title: "Update Manager Problem"
date: 2009-03-27
forum: General Help
---

### Post by russki_drewski on 2009-03-27
Hey,when my ubuntu runs update manager it give me some sort of error about authentication:

[INDENT]    W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
    W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
    W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

    W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...pdates/Release](http://us.archive.ubuntu.com/ubuntu/...pdates/Release)

    W: Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

I'm using Intrepid Ibex (8.10).
Does anyone know what to do? I'm still a little new to ubuntu.

I also have this post under Installing and Upgrading, but I think its better to have it here. [http://ubuntuforums.org/showthread.php?t=1107604](http://ubuntuforums.org/showthread.php?t=1107604)

thx,
Drewski

---

### Post by Xiong Chiamiov on 2009-03-27
```

sudo apt-get update && sudo apt-get upgrade

```
then, if that doesn't fix it, post the contents of /etc/apt/sources.list.

---

### Post by russki_drewski on 2009-03-27
Here I've attached sources.list as a .txt

Does it for some reason not like the repositories that I am using?


Thx,
Drewski

---

