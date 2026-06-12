---
title: "Error opening Synpatic Package Manager"
date: 2006-02-19
forum: Desktop Environments
---

### Post by SuTuRa on 2006-02-19
I have the following error when I open Synpatic Package Manager:

```

W: Couldn't stat source package list ftp://ftp.free.fr breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list ftp://ftp.free.fr breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```

I tried to update in the console using:

```

$sudo apt-get update

```

But I have the same error...:( 
Can anyone help?

Thanks

---

### Post by amoser on 2006-02-19
[ftp://ftp.free.fr](ftp://ftp.free.fr) went down a few days ago.  I don't know why.  To get rid of the messages, go to /etc/apt.  type sudo gedit sources.list

Then find these lines:

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

and put a number (#) sign if front of both of them

~Alan

---

### Post by RAOF on 2006-02-19
Alternatively, you can just ignore the warning until the site comes back up.  It should still work.

---

### Post by SuTuRa on 2006-02-19
So... When you say to put (#) in front of those lines the OS is just ignoring them, right?
But if it's just temporary I think the best solution is to ignore the error until it goes online again...

Thanks for your fast answer as usual:)

---

