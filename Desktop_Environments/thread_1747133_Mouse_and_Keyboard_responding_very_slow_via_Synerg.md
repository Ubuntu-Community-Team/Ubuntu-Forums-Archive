---
title: "Mouse and Keyboard responding very slow via Synergy after 11.04 upgrade"
date: 2011-05-02
forum: Desktop Environments
---

### Post by zwilliamson on 2011-05-02
Hi All!

Is anyone else having issues with their mouse/keyboard responsiveness via Synergy after upgrading to 11.04?

If I plug mouse and keyboard directly into the desktop the issue goes away.  But when I connect via QuickSynergy and share my mouse/keyboard the mouse is very slow and has low sensitivity.

---

### Post by zwilliamson on 2011-05-02
More info:

I am running QuickSynergy 0.9.0 and Synergy-1.3.6

---

### Post by zwilliamson on 2011-05-02
Good news - I was able to fix the issue by upgrading the Synergy server (Running on Windows XP) from 1.3.1 to 1.4.2.  

This immediately fixed the issue on the Ubuntu synergy client.

---

### Post by traffas on 2011-05-02
I upgraded my Windows 7 client to 1.4.2 and the problem persists. I'm running Synergy server 1.3.6 on Ubuntu 11.04 64-bit because I couldn't get 1.4.2 to install. Anyone else able to get 1.4.2 working on 64-bit Natty?

---

### Post by GoFishy on 2011-05-08
I had the same issue. I upgraded my server on Windows 7 to 1.4.2 64bit and left my Ubuntu client 1.3.6.

Everything working good so far.

---

