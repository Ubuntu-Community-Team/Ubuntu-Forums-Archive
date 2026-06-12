---
title: "Default Firefox works only with Sudo"
date: 2006-02-05
forum: Desktop Environments
---

### Post by kevinc on 2006-02-05
Hi There,

I have just installed Ubuntu 64 bit, and when I tried to start Firefox, all I got was a minimized window with a title "Firefox Starting". Then it disappears.

So, I then tried to run it from the terminal, and I got nothing, not even an error message.

I then used apt-get to remove and reinstall firefox, tried it all again. Didn't work.

However, when I started firefox with Sudo, it starts fine.

Now, it is inconvenient (and probably dangerous) to run firefox from the command line with sudo.

And yes, I am aware that there are other past threads that have discussed this, and I have tried everything recommended.

Any help would be appreciated.

Kevin

Specs:
Athlon 64 3200+
2 Gb OCZ RAM

---

### Post by hw-tph on 2006-02-05
Try moving your profile out of the way and then try again: **mv ~/.mozilla/firefox ~/.mozilla/firefox-old**


Håkan

---

### Post by kevinc on 2006-02-05
Ok, I just tried that, and I get a permission denied error. 

I also tried in sudo, and I can access other hidden folders...

---

### Post by kevinc on 2006-02-05
Ok, I just installed firefox gnome support, and it works fine.

Thanks for your help.

---

