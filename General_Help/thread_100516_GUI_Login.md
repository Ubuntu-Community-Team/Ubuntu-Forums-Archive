---
title: "GUI Login"
date: 2005-12-07
forum: General Help
---

### Post by raze on 2005-12-07
Hi guys!

Just switched over from Fedora to Ubuntu (5.10), and I am so far pleased! I edited /etc/fstab so that my external harddrive was mounted. That went well. The problem came when I restarted my machine, and was met with the terminal login. I want the GUI login. X starts fine, after typing startx, but it's kinda anoying to do that every time I switch on my computer.

Any tips?

Edit: I should have mentioned it. I tried to edit the default runlevel in /etc/inittab from 2 to 5, with no changes.

---

### Post by Kyral on 2005-12-07
have you tried

sudo dpkg-reconfigure gdm
?

---

