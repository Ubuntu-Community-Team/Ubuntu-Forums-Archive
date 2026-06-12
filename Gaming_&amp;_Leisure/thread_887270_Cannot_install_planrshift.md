---
title: "Cannot install planrshift"
date: 2008-08-12
forum: Gaming &amp; Leisure
---

### Post by Fuzzykins on 2008-08-12
Hello,

I dowloaded the 32bit linux version of planeshift to my desktop and executed the following commands to try and install(after setting terminal to desktop) I am currently running Hardy.

chmod +x PlaneShift-v0.4.01-x86.bin
sudo ./PlaneShift-v0.4.01-x86.bin

And got a "Segmentation Fault" error

I am a noob to linux, and any help would be appreciated.

---

### Post by TheConstruct on 2008-08-12
Try the following in order until one of them works:

* Forget using sudo, just install to your home folder:
**./PlaneShift-v0.4.01-x86.bin**

* Run in text mode (sudo):
**sudo ./PlaneShift-v0.4.01-x86.bin --mode text**

* Run in text mode (no sudo):
**./PlaneShift-v0.4.01-x86.bin --mode text**

---

### Post by Fuzzykins on 2008-08-12
All 3 came back with the same error, i am g oing to try downloading from a different source.

---

### Post by Fuzzykins on 2008-08-12
I got the installer running and tried to install in the usr/local/games directory and it told me

"the directory /usr/local/games is not writable by the current user"

Any help would be greatly appreciated.

---

### Post by patrickaupperle on 2008-08-12
> **Fuzzykins said:**
> I got the installer running and tried to install in the usr/local/games directory and it told me

"the directory /usr/local/games is not writable by the current user"

Any help would be greatly appreciated.

To install to that directory, you need to be root. Try using sudo.

---

### Post by Zeotronic on 2008-08-12
Its been a whole version since I last had the game, but I just installed it in the home directory without consequences.

---

