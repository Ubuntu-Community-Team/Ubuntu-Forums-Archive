---
title: "gnome 3 graphics requirements"
date: 2010-10-25
forum: Desktop Environments
---

### Post by ratdude747 on 2010-10-25
ok, this is pretty frustrating.

i tried gnome out on my laptop. very slow. and all the text is a bunch of blocks.

this makes no sense, as my eee pc 1000HE with the atom's mediocre graphics ran the shell fine before the screen got smashed.

my laptop is a dell latitude d400, with the intel 855gm integrated graphics chip. I am using ubuntu 10.10. I was using ppa:ricotz/testing for gnome shell.

any advice?

---

### Post by nilarimogard on 2010-10-25
The Ricotz Testing PPA is empty: [https://launchpad.net/~ricotz/+archive/testing/+packages]("https://launchpad.net/~ricotz/+archive/testing/+packages") so it seems you've actually installed Gnome Shell from the official Ubuntu repositories (which is old).

---

### Post by ratdude747 on 2010-10-25
odd... gnome's site must be way off then.

---

### Post by 3Miro on 2010-10-25
> **ratdude747 said:**
> odd... gnome's site must be way off then.

Gnome shell's site are constantly updating the thing. They are working on it as we type, which is why they are having stability issues.

---

### Post by ratdude747 on 2010-10-25
no, i meant the site said his ppa was the most up to date... still says that even though the ppa is empty.

---

### Post by nilarimogard on 2010-10-28
The PPA used to have Gnome Shell builds... and it will probably have them again after some more testing with the latest Gnome Shell and GTK3.

---

### Post by Harry33 on 2010-10-28
> **ratdude747 said:**
> ok, this is pretty frustrating.
...
I am using ubuntu 10.10. I was using ppa:ricotz/testing for gnome shell.
any advice?

Well for Maverick (10.10) I think there will be no more GS PPA's.
The 2.31.5 version of the official repos is the last one that goes with GTK2.0.

If it is newer GS you need, start upgrading to Natty ( =>11.04).
For Natty you can use GS ppa:ricotz/staging wich is already a working one.
There you will find GS_2.91.1 and GTK3.0_2.91.2 already now.
Still one will find a warning there not use that PPA.

---

### Post by nilarimogard on 2010-10-29
He usually just tests the packages in the staging ppa and then moves it to the testing PPA - so he might copy the packages for Maverick too (if they can be built using the Maverick packages). If not, you can always compile it, it's just a bunch of copy/paste commands (but it's true the actual process takes quite some time...).

---

