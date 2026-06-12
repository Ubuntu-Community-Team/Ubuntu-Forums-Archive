---
title: "Open Office 3.1"
date: 2009-05-09
forum: General Help
---

### Post by sports fan Matt on 2009-05-09
Since I just downloaded the OOO 3.1 deb, which file do I use to install for it? The ooobasis3.1-base?  There a ton of files and not sure which one I need

---

### Post by mikewhatever on 2009-05-09
You probably need all of them. Use **dpkg -i *.deb**.

---

### Post by sports fan Matt on 2009-05-09
hmm...dpkg: error processing *.deb. (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb.
Although the file is still on my desktop...

---

### Post by paradigm2 on 2009-05-09
> **sox fan Matt said:**
> hmm...dpkg: error processing *.deb. (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb.
Although the file is still on my desktop...

```

cd ~/Desktop

```

```

sudo dpkg -i *.deb

```

This will install all *.deb files on your destop.

---

### Post by mikewhatever on 2009-05-09
Can you name the features in 3.1 you want to upgrade for, or is it just an upgrade for the sake of upgrading?

---

### Post by binbash on 2009-05-09
There is a repo for it : 

[http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html](http://www.ubuntu-inside.me/2009/05/openoffice-31-for-ubuntu.html)

---

### Post by sports fan Matt on 2009-05-09
i just got that same message  cd ~/Desktop
office@office-desktop:~/Desktop$ sudo dpkg -i *.deb
[sudo] password for office: 
dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

When I typed in the terminal what paradigm2 suggested..so this is odd, its not a major thing, but I dont know why it would throw up that error

---

### Post by mikewhatever on 2009-05-09
Can you post the output of **ls Desktop**.

---

### Post by sports fan Matt on 2009-05-09
I just realized something..as noted here: build status failed a few days ago..but even though the splash screen shows 3.0..when i go to "about ooo" it shows 3.1..yes i know its confusing

---

