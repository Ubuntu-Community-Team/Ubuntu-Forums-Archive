---
title: "Xscreensaver - wrong keyboard layout?"
date: 2005-09-14
forum: Desktop Environments
---

### Post by mozz on 2005-09-14
Hi,

it seems that Xscreensaver uses a wrong keyboard layout when I "lock" the screen. It always says "DENIED" when I enter my password (consists of chars, numbers and special chars), it works if I set the password to something "normal" without special chars...

Maybe a bug?

---

### Post by bi9kahuna on 2005-12-02
I just ran into this problem too.  I had to remove my ~/.xscreensaver, and everything worked fine.

---

### Post by teaker1s on 2005-12-02
it's a bug the joy:rolleyes:

---

### Post by eitan on 2005-12-09
i have the same problem.  it's driving me crazy!  each time i lock the screen inadvertantly i have to reboot to get back in.

i tried renaming my .screensaver but it does not solve the problem.

i keep getting that nice DENIED message each time i enter the correct
password.

i need to find a smily icon pulling his hairs out.

---

### Post by eitan on 2005-12-09
ok, after some further searching in the ubuntu forums i found my answer:

  sudo password <username>

solves it.

this problem was brought about after installing kubuntu, and after a week switching back to gnome.

---

