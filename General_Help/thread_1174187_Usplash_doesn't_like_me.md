---
title: "Usplash doesn't like me"
date: 2009-05-30
forum: General Help
---

### Post by Jolzath on 2009-05-30
When I shut down I get my personal screen, when I boot back into Ubuntu I get the default boot screen. Any ideas? (Will post config files when requested)

---

### Post by jimbob on 2009-05-30
Are you talking about the bootsplash that is the background for the Grub menu?

---

### Post by Jolzath on 2009-05-30
> **jimbob said:**
> Are you talking about the bootsplash that is the background for the Grub menu?

During boot up (That is while Ubuntu is loading) After Grub before the login screen. Normally has the word UBUNTU with a bar that fills up as ubuntu loads

---

### Post by jimbob on 2009-05-30
I think after you change that you have to regenerate the initramfs; something like  ***[COLOR="Blue"]update-initramfs -k all -u[/COLOR]***   (Double check the command in the man pages).

How exactly did you change it?

---

### Post by Jolzath on 2009-05-30
> **jimbob said:**
> I think after you change that you have to regenerate the initramfs; something like  ***[COLOR=Blue]update-initramfs -k all -u[/COLOR]***   (Double check the command in the man pages).

How exactly did you change it?

A .deb file from gnome-look.com

Update@ 10:31 PM GMT: It worked, thank you

---

