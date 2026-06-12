---
title: "Edit /etc/hosts"
date: 2006-03-10
forum: Desktop Environments
---

### Post by kemah201 on 2006-03-10
Hello,

I changed my hostname by using the *hostname -v* command. But now I can't access the root terminal or the software manager. How can I edit the hosts file? I tried editing it in gedit with no success. I tried changing the permissions from the regular terminal but it says I need to be root. I also tried to *su* into the root terminal with no success. How can I edit the read-only hosts file?

Thanks.

Steve

---

### Post by glug101 on 2006-03-10
did you try: ```

sudo su

```

---

### Post by taurus on 2006-03-10
```

sudo gedit /etc/hosts

```

---

### Post by wrtrdood on 2006-03-10
If what has happened is something I experienced recently, you will not be able to edit it because you cannot even execute sudo now.  Reboot to failsafe mode and edit using nano.

---

### Post by kemah201 on 2006-03-13
So I rebooted to recovery mode and I edited the /etc/hostname file and that did not resolve the issue. I still get an error message when I log in and I still can't execute root terminal or Synaptic Package Manager. I have already begun re-installing the OS.

---

