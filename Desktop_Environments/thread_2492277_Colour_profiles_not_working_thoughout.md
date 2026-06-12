---
title: "Colour profiles not working thoughout"
date: 2023-11-06
forum: Desktop Environments
---

### Post by sir-marky on 2023-11-06
During the installation of the update from 23.04 to 22.10, the installer crashed.
I  managed to rescue the situation and update it to 23.10, however, this  section of Gnome does not change the colour profile with the rest of the  GUI.
I don't know why it is green - a colour I have never used.   Changing to any other colour in system preferences will amend the folder  colours but this remains green.

On a separate upgrade on my laptop, this works fine.

Does  anyone know which files are missing or corrupt that require reinstall  or any configs stuck in read-only mode that prevents this changing  colour?


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293012&stc=1[/IMG]

---

### Post by ActionParsnip on 2023-11-07
If you set a different theme, is it still greeny?

---

### Post by sir-marky on 2023-11-07
> **ActionParsnip said:**
> If you set a different theme, is it still greeny?


Yes.  Folder colours change, and this section remains green.

---

### Post by Claus7 on 2023-11-09
Hello,

I came across this situation while in ubuntu 23.10 beta, yet at that time it was a bug. The package in question, as you can see here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2033688](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2033688)

is gnome-shell. You could try to reinstall that package and see what you will get.

Regards!

---

### Post by sir-marky on 2023-11-11
Thank you for the suggestion.
I reinstalled gnome-shell but sadly the situation remains the same.
This is a puzzle to me.



> **Claus7 said:**
> Hello,

I came across this situation while in ubuntu 23.10 beta, yet at that time it was a bug. The package in question, as you can see here:
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2033688](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/2033688)

is gnome-shell. You could try to reinstall that package and see what you will get.

Regards!

---

### Post by Dennis N on 2023-11-11
In Tweaks > Appearance, your Shell may be not be set to the correct theme. It has to match the Yaru theme in Legacy-applications.

---

### Post by sir-marky on 2023-11-12
Thank you!
That was indeed the solution.
The shell theme was Yaru-Sage.  I have never set that so clearly the gremlins have been at work.
Changed to Default and the lovely Ubuntu orange it became.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293048&stc=1[/IMG]


> **Dennis N said:**
> In Tweaks > Appearance, your Shell may not be set to the correct theme. It has to match the Yaru theme in Legacy applications.

---

