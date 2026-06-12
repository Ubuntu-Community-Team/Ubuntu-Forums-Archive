---
title: "KGpg - broken?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by KubuntuKilledMe on 2006-09-04
I've created a key pair on KGpg as i intended to use it to encrypt text. Then i opened the "editor" window of KGpg which has both the encrypt and decrypt buttons on bottom. I type some text, click encrypt and it becomes the usual encrypted blob with some text above and below. Without editing anything, i click the decrypt button, at which point KGpg crashes.

I've tried different key sizes but that doesn't make any difference. It will ALWAYS crash when decrypting. When i right click a file i can encrypt and decrypt without problems, but i needed to encrypt text without needing to save it to a file first.

Additionally, configuration of KGpg mentions a KDE applet, but that applet is nowhere to be seen, not even in the list of applets to add to the kicker.

Finally, i also needed a program that would perform the KGpg's function for a Xubuntu install on an old computer. Any suggestions? At this point i'd also use it in KDE as KGpg is seriously broken.

---

### Post by KubuntuKilledMe on 2006-09-04
At least someone suggest a replacement, please.

---

### Post by KubuntuKilledMe on 2006-09-06
one last bump for the road - not a single reply...

---

### Post by chris-at on 2006-09-12
I've got the same problem and would also be interested in a replacement or a fix (the bug is listed here: [http://bugs.kde.org/show_bug.cgi?id=132575](http://bugs.kde.org/show_bug.cgi?id=132575)).

Have you found an alternative?

---

### Post by mandragor on 2006-10-12
According to this:
[http://bugs.kde.org/show_bug.cgi?id=129267](http://bugs.kde.org/show_bug.cgi?id=129267)

It would seem that an upgrade to KDE 3.5.5 fixes the issue.
Maybe trying to install from CVS would fix this issue?

EDIT: I can confirm that KDE 3.5.5 fixes this issues,
get it from [http://kubuntu.org/announcements/kde-355.php](http://kubuntu.org/announcements/kde-355.php)

---

