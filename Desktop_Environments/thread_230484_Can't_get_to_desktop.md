---
title: "Can't get to desktop"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Lrusso on 2006-08-06
I was installing 159 Updates, when the updater frooze, I powered down the computer, and now when i log in i dont get a desktop. Everything is fine with the boot screen, theres no errors?
any idea?

---

### Post by Perfect Storm on 2006-08-06
So you are in non-X now? 

```
sudo apt-get update
sudo apt-get upgrade
```

This should get the missing packages you are missing before the freeze.

then:
```
startx
```

It might need a reboot instead.

---

### Post by Lrusso on 2006-08-06
no im on a different computer, how do i get to non-x?

---

### Post by Jagot on 2006-08-06
By non-x he means without a GUI.

---

### Post by Lrusso on 2006-08-06
Yeah how do I boot without GUI

GRUB > Ubuntu Loading Screen > Ubuntu Login Screen > Freezes with the Mouse and like a brown background

---

### Post by Jagot on 2006-08-06
At Grub there should be an option for Ubuntu in recovery mode - use that.

---

### Post by Lrusso on 2006-08-06
ok

---

### Post by Lrusso on 2006-08-06
alright I ran the command and got, 

an error and it told me to run

dpkg --configure -a`

I ran the command and know its 

Setting up capppers(MY SPELLING MIGHT BE OFF)


thats what it was up to when i frooze it, so just let that go?

---

### Post by Jagot on 2006-08-06
I'd let it run and see what happens.

---

### Post by Lrusso on 2006-08-06
ok, would you say thats a positive or a negative ;)

---

### Post by Jagot on 2006-08-06
I'd say that its the best thing to do at the moment - it isn't negative - it will either work or it won't - but you won't be in any worse situation if it doesn't - we'll just have to find another way.

---

### Post by Lrusso on 2006-08-06
fixed, thanks

---

