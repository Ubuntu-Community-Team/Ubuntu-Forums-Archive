---
title: "Kubuntu 20.04 LibreOffice not found"
date: 2021-08-14
forum: Desktop Environments
---

### Post by RobertoRecordo on 2021-08-14
I installed kubuntu-20.04.2.0-desktop-amd64.iso and had no problems until I tried to run LibreOffice calc.
I looked in applications, I tried the command line, but it is not there. The entire LibreOffice suite is not in the application menu.

The release announcement  [https://kubuntu.org/news/kubuntu-20-04-lts-has-been-released/](https://kubuntu.org/news/kubuntu-20-04-lts-has-been-released/) specifically mentions LibreOffice.

Surprise!
On a lark I delayed posting this and booted the install disk. LibreOffice is in the applications menu!

In addition, I discovered that on the live DVD I could open LibreOffice with ```
loffice
``` 
That **did not work** on the installed system.

Why is LibreOffice not installed on my system?  What else is missing? Has anyone else seen this?

---

### Post by deadflowr on 2021-08-14
Doesn't Kubuntu have a minimal install option, which does not install libreoffice?
(among a slew of other packages)

---

### Post by RobertoRecordo on 2021-08-15
DeadFlower - I could not find info about "minimal install" in the release notes, but I did see references to it in discussions.

I think that you are right, I may have done a minimal install without considering what was being left behind. 

Thank You,

---

### Post by ActionParsnip on 2021-08-15
```

sudo apt install libreoffice

```

---

