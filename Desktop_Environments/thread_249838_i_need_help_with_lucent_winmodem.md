---
title: "i need help with lucent winmodem"
date: 2006-09-03
forum: Desktop Environments
---

### Post by d3r0 on 2006-09-03
it took me a while to configure the modem driver but i finely got it to work accpet it doesn't work so good :( heres a screen shot. 

Also can someone tell me how to drag and drop into /etc it says i don't have write access because the owner is root, when i try log in as root it says " you can't log in as root" lol no fiar :( i dislike using sudo commands.

Thanks

---

### Post by d3r0 on 2006-09-03
bump

---

### Post by d3r0 on 2006-09-03
bump plz help?

---

### Post by d3r0 on 2006-09-03
...................

---

### Post by d3r0 on 2006-09-04
ok this is the last time i'm gona bump cand then i'm giving up, can anyone help PLZ!

---

### Post by towsonu2003 on 2006-12-05
> **d3r0 said:**
> it took me a while to configure the modem driver but i finely got it to work accpet it doesn't work so good :( heres a screen shot. 
 Try it with wvdial instead of kppp: 
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-277fdde88a3b04feee00e14834388d58d7add4f9)
> 
Also can someone tell me how to drag and drop into /etc it says i don't have write access because the owner is root, when i try log in as root it says " you can't log in as root" lol no fiar :( i dislike using sudo commands.

you could use ```
sudo nautilus
``` to use nautilus with root privileges... but **be careful**. it's very easy to delete everything, bork the installation, do something real stupid when you use nautilus (or anything, for that matter) with root privileges.

---

