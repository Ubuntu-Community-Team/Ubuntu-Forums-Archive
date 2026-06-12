---
title: "[SOLVED] Fonts issue in some applications"
date: 2008-02-13
forum: Desktop Environments
---

### Post by josephdaniel on 2008-02-13
I have a problem in the fonts of some applications. I am using ubuntu 7.10 with all available updates. I disabled all desktop effects to try to correct these font problems but it didn't get better.

Please check the attached screenshot. See how aMSN uses very small and strange fonts while Firefox and the main menu are working just fine.

As far as I understand, this can be corrected by editting xorg.conf. But I don't know exactly how?

Any help is appreciated,
Joe

---

### Post by Ek0nomik on 2008-02-13
> **josephdaniel said:**
> I have a problem in the fonts of some applications. I am using ubuntu 7.10 with all available updates. I disabled all desktop effects to try to correct these font problems but it didn't get better.

Please check the attached screenshot. See how aMSN uses very small and strange fonts while Firefox and the main menu are working just fine.

As far as I understand, this can be corrected by editting xorg.conf. But I don't know exactly how?

Any help is appreciated,
Joe

From what I have read there is an option within aMSN to change the font to something else.  Perhaps I am mistaken?  Let me know if you can find it or not.

---

### Post by josephdaniel on 2008-02-14
You can change the fonts inside the chat window but not the titlebar and menu fonts etc.

I got over this problem by running the following:

dpkg-reconfigure xserver-xorg 

as advised inside the xorg.conf file. Fonts returned back to normal but I don't know what caused the problem in the first place.

Thanks for your time anyway.

Joe

---

### Post by kerry_s on 2008-02-14
try turning off bitmap fonts->
sudo dpkg-reconfigure fontconfig-config
logout
and
ctrl+alt+backspace
to restart X

---

### Post by smo0th on 2008-07-07
hey the same **** happened to my amsn, thanx for sharing the solution, it worked here too :D

---

