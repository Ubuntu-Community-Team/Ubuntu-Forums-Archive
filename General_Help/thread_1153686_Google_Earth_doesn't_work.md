---
title: "Google Earth doesn't work"
date: 2009-05-09
forum: General Help
---

### Post by Tipped OuT on 2009-05-09
I recently installed Google Earth. After installing it, I tried to launch it, and the window appears and shows everything loading, and then it closes. Any one know why? :confused:

---

### Post by lisati on 2009-05-09
You might have to turn on "accelerated graphics".

---

### Post by DeMus on 2009-05-09
> **Tipped OuT said:**
> I recently installed Google Earth. After installing it, I tried to launch it, and the window appears and shows everything loading, and then it closes. Any one know why? :confused:

Try to find the location of the program, which is probably in your home folder, or in /opt.
When you have found the right folder, look for a file called: libcrypto.so.0.9.8

Open a terminal and
cd to he right folder
ls -l
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8_org 

What it does is this: you rename the file Google sent you, since it is not working. Now when starting the Google Earth program the system will look for the file in it's own system folders. This version of the file is OK.
Now it should work.

---

### Post by Tipped OuT on 2009-05-09
> **lisati said:**
> You might have to turn on "accelerated graphics".
Oh..well, I don't have accelerated drivers for my card, at least I don't think, it's an old ATI Radeon 9100 IGP. Oh well, thanks for the help.
> **DeMus said:**
> Try to find the location of the program, which is probably in your home folder, or in /opt.
When you have found the right folder, look for a file called: libcrypto.so.0.9.8

Open a terminal and
cd to he right folder
ls -l
mv libcrypto.so.0.9.8 libcrypto.so.0.9.8_org 

What it does is this: you rename the file Google sent you, since it is not working. Now when starting the Google Earth program the system will look for the file in it's own system folders. This version of the file is OK.
Now it should work.
Oh okay :D

---

