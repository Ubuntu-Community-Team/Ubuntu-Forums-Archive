---
title: "Turn back failed apt-get"
date: 2009-01-14
forum: General Help
---

### Post by Macamba on 2009-01-14
Hi,

Yesterday I found out I had to install codecs. Searching the Internet brought me to the following page:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Reading the instructions, I found the following command line:
```
sudo apt-get install ubuntu-restricted-extras
```

I thought that the most easy manner to install the wanted codecs. But while installing a license file for Java came by, without a way to acknowledge the license. In the end I closed the window with the failing license. Today I tried to install again, this time using the 'Add/remove...' menu, and I got informed that the installation failed:
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

When I tried to execute dpkg --configure -a in a terminal window I got informed that the 'requested operation requires superuser privilege'. Now I'm at a loss, as 
```
su dpkg --configure -a
```
also fails. What do I need to do?

Abel

---

### Post by redilyn on 2009-01-14
You need to run the command with sudo

```

sudo dpkg --configure -a

```

If that also fails you could try the following

```

sudo -s
dpkg --configure -a

```

When you get to the java license. Press tab to select ok

---

### Post by avtolle on 2009-01-14
Try ```
sudo dpkg --configure -a
``` rather than the command you ran.

---

### Post by Macamba on 2009-01-14
Thanks, that worked. 

As a follow up, I now used the Add/remove... menu. I got the instruction to run.
ubuntu-restricted-extras
as a filter. 

Where do I do that?

---

### Post by redilyn on 2009-01-14
Open add/remove programs

Then type ubuntu-restricted-extras in the search bar.

Make sure to change show to "All Available Applications"

---

