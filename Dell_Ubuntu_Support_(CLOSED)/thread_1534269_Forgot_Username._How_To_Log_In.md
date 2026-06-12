---
title: "Forgot Username. How To Log In?"
date: 2010-07-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Pyro Stick on 2010-07-19
Ive forgotten the username for my laptop (pretty sure i still know the password) and now i cant sign in. Its a Dell Inspiron Mini. Can someone please help me reset my username or something so i can get onto my laptop.

---

### Post by solitaire on 2010-07-19
> **Pyro Stick said:**
> Ive forgotten the username for my laptop (pretty sure i still know the password) and now i cant sign in. Its a Dell Inspiron Mini. Can someone please help me reset my username or something so i can get onto my laptop.

If there is not encryption on the laptop:
Use the recovery mode to get into root and then browse to /home and see the names. 
Reboot and login.
Or use a live CD/USB to do the same...

---

### Post by Pyro Stick on 2010-07-19
I cant see a recovery mode anywhere. The Dell screen is the only screen that has options and they are to get into the Bios and to set the Boot Options. How do i get into Recovery Mode?

---

### Post by solitaire on 2010-07-19
you should press "esc" key during boot (after the BIOS) I think!!

can't remember how to get the grub boot menu up..

---

### Post by Pyro Stick on 2010-07-19
> **solitaire said:**
> you should press "esc" key during boot (after the BIOS) I think!!

can't remember how to get the grub boot menu up..

I tried pressing esc everywhere but it doesnt do anything. Heres exactly what happens when i turn the laptop on:

Dell loading screen comes up with Bios and Boot Options options in the corner. After that screen theres a black one with MBR flashing in the top corner. Pressing esc here does nothing. Then the Ubuntu loading screen comes up then the log in screen comes up asking me to put in my username. It has options at the bottom like Change Session etc but i have no idea what they are supposed to do and they dont seem to start up Recovery Mode.

---

### Post by solitaire on 2010-07-19
Try the shift key or the "f10" key, (they have a habit of changing the required key to press to get the grub boot menu up!) lol

Hopefully someone can chime in with the correct key to press!

It's probably quicker getting a Live USB setup and to use that.

---

### Post by ajgreeny on 2010-07-19
If it's grub2 from ubuntu 9.10 or 10.04, it's **shift** you need to press and hold as you switch on.  The grub menu will then appear and should give you the "Recovery mode" option.

---

### Post by stuart.reinke on 2010-07-20
if you know the password, at the login screen enter "root" for the user name.

---

