---
title: "Problem with Thunderbird, want to use Sylpheed"
date: 2006-08-14
forum: Desktop Environments
---

### Post by Psquared on 2006-08-14
I installed Xubuntu on a separate partition and then installed Thunderbird. For some reason Thurnderbird is having problems in Xubuntu. It is very, very slow to start and setting up a mailbox takes forever. I tried reinstalling and even some .dev files, but nothing helps. 

So, I decided to try Sylpheed Claws. It works great but i want a shortcut on the panel at the top. However, I cannot find the executable anywhere.

How do I find the executable for Sylpheed and the default icon. Its in the menu and it runs so I know its on my system somewhere.

Thanks in advance.

---

### Post by mgor on 2006-08-14
open up a terminal, at type `which sylpheed` and you'll get the path to the executable. i bet you'll find the icon in /usr/share/pixmaps.

---

### Post by Psquared on 2006-08-14
Yep, that did it. Both worked. Thank you.

Got any ideas why Thunderbird is having so much trouble in Xubuntu? I installed it with Automatix which worked fine for everything else including the Nvidia driver. ](*,)

---

### Post by mgor on 2006-08-15
i've never used xfce. but i'm kind of skeptic that the desktop enviroment has anything todo with it.

what thunderbird version do you have?
```
$ dpkg --list | grep "mozilla-thunderbird" | awk  '{print $3}'
1.5.0.5-0ubuntu0.6.06
```

---

### Post by Psquared on 2006-08-15
ii  mozilla-thunderbird                    1.5.0.5-0ubuntu0.6.06    Mozilla Thunderbird standalone mail client

Installed it using Automatix. Problem is you can't uninstall Thunderbird (to reinstall or use a different version) without uninstalling the Xubuntu-Desktop.

---

### Post by llamakc on 2006-08-15
Yes you can. xubuntu-desktop is only a metapackage. You won't break anything by removing it.

---

