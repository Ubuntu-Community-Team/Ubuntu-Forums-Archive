---
title: "I installed xubuntu-desktop on my regular Ubuntu computer"
date: 2006-06-04
forum: Desktop Environments
---

### Post by greggh on 2006-06-04
I thought I would be able to switch between the two desktop afterwards, but I can't figure out how to do it. Everything just seems all mixed up. It still has the classic Ubuntu desktop, but when I shutdown it briefly goes to the blue Xubuntu screen. When I boot-up its the Ubuntu brown graphics until I get to the log-in screen then its the blue Xubuntu login screen. After I login it switches back to the brown classic Ubuntu desktop... :confused:

---

### Post by kaamos on 2006-06-04
You can change the desktop by choosing the session in the login manager when logging in. For the bootsplash, to use just the xubuntu splash execute
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by greggh on 2006-06-04
Thanks for the quick help :-D

---

### Post by andy_cowman on 2006-06-05
I installed XFCE in normal ubuntu (under breezy) to play with it as i figured it would tell me if liked it enough to switch to Xubuntu. It was as easy as selecting the session at the login menu. 

Fresh installed Xubuntu after :D I really like it! Hope you didnt screw your system up by installing both!

---

### Post by compsariomike on 2007-07-27
You've got the code for changing the bootsplash to xubuntu bootscreen, but can anyone help me as to changing the bootsplash as the original Ubuntu boot screen?  

Thanks

---

