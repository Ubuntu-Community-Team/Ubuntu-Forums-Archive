---
title: "Changing computer name = error?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by srunni on 2006-07-25
Hi,

I changed the name of my computer in Kubuntu 6.06. Now when I try to access add/remove programs or sudo apt-get, I get an error. If I try to add/remove programs, I get "Su returned with an error." And if I sudo apt-get, I get "sudo: unable to lookup [computername]-desktop via gethostbyname()". If I try to "sudo kate /etc/hosts", I get the error, so I can't change the name back. Does anyone have a solution?

---

### Post by wpshooter on 2006-07-25
I think I read in another post that you can fix something like this by booting into the recovery mode.

I have no idea as to what you would change/edit, so maybe someone else can give you that info or you can possibly research.

---

### Post by philippe_carlo on 2006-07-25
When changing the host name you have to consistently apply the changes to both /etc/hostname and /etc/hosts or sudo gets angry.

Recovery is possible by booting into recovery mode and applying the fixes.

---

### Post by srunni on 2006-07-25
Yeah, I just found that out, I'm going to boot into recovery mode and change /etc/hosts.

EDIT: However, under normal circumstances, you could boot using Knoppix and edit the file. I can't because this is a VMWare Kubuntu install, but otherwise, it would be very possible.

---

### Post by srunni on 2006-07-25
Worked just fine. You just

```

nano hosts

```

---

