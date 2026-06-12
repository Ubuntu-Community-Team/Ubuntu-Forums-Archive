---
title: "How to customize live user desktop/environment on Kubuntu while remastering ISO"
date: 2017-06-14
forum: Desktop Environments
---

### Post by kerrygee on 2017-06-14
Hi,

i didnt wanted to cross or double post, but since i got no answer yet, maybe someone here can help me on this:

[https://askubuntu.com/questions/924742/how-to-customize-default-live-session-user-desktop-and-environment-on-kubuntu-wh](https://askubuntu.com/questions/924742/how-to-customize-default-live-session-user-desktop-and-environment-on-kubuntu-wh)

Thanks in advance

K.

---

### Post by &amp;KyT$0P# on 2017-06-14
Did you try putting your customisations in [FONT=Courier New]/etc/skel[/FONT] ?

---

### Post by kerrygee on 2017-06-14
> **halogen2 said:**
> Did you try putting your customisations in [FONT=Courier New]/etc/skel[/FONT] ?

Yes, that method works fine. What i did so far:


[LIST]
[*]Installed a fresh Kubuntu inside VirtualBox and create a persistent shared folder to the guest system from the host system in the Machine configuration
[*]Customized the entire Desktop in the VirtualBox installed environment
[*]Copied the entire customized profile into the shared folder to the host system with rsync excluding temporary and non wanted files
[*]Moved the files to the /etc/skel folder on the expanded ISO structure from Cubic
[*]Packed the ISO with Cubic
[*]Run freshly created ISO as Live-System in VirtualBox
[/LIST]

That worked for me so far. The live session user inherits all the settings from the /etc/skel folder

Thanks for the precious tip!

K.

---

### Post by &amp;KyT$0P# on 2017-06-14
You're welcome! :KS

---

