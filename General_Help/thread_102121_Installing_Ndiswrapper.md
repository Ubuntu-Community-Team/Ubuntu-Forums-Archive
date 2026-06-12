---
title: "Installing Ndiswrapper"
date: 2005-12-11
forum: General Help
---

### Post by Jammy_Stuff on 2005-12-11
I'm following the [install guide for Ndiswrapper]("https://wiki.ubuntu.com/SetupNdiswrapperHowto") and I've got to this part:

> sed -e "s/misc/kernel\/drivers\/net\/ndiswrapper/g" debian/rules > debian/temp

When I enter that into the terminal it says:

> bash: debain/temp: No such file or directory

What am I doing wrong?

---

### Post by Jammy_Stuff on 2005-12-11
I've got that command to work but i've got another problem now. When I type in:

> make deb

I get the error:

> bash: make: command not found

What is going wrong now?

---

### Post by Ravendark on 2005-12-11
apt-get install make ?

---

### Post by Jammy_Stuff on 2005-12-11
I've tried that and it says:

> /bin/sh: fakeroot: command not found
make: *** [deb] Error 127

---

### Post by Ravendark on 2005-12-11
did u try with sudo in front?

---

### Post by Jammy_Stuff on 2005-12-11
Yes I did. :(

---

### Post by Ravendark on 2005-12-11
sudo apt-get install build-essential
I think this is it

---

### Post by az on 2005-12-11
Have you tried using the latest INF (windows driver) for your card?  The one that comes with the card may be too old for the ndiswrapper version that comes with breezy.

I would try that before recompiling ndiswrapper.

---

### Post by Jammy_Stuff on 2005-12-11
Okay I got the command to run but it comes up with some errors involving commands missing from the linux-headers file. Then when it completes only the utils file is there with no modules file.

---

